---
title: Kartenreferenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams zur Verfügung stehen
keywords: Bots-Kartenreferenz
ms.topic: reference
ms.openlocfilehash: 5cb289738f379dedf53f3a96a7dcff61b908e901
ms.sourcegitcommit: 1ce74ed167bb81bf09f7f6f8d518093efafb549e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "50827935"
---
# <a name="cards-reference"></a><span data-ttu-id="6e668-104">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="6e668-104">Cards reference</span></span>

<span data-ttu-id="6e668-105">Die in diesem Abschnitt aufgeführten Karten werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-105">The cards listed in this section are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="6e668-106">Sie basieren auf Karten, die vom Bot Framework definiert wurden, aber Teams unterstützt nicht alle Bot Framework-Karten und hat eigene Karten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6e668-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="6e668-107">Unterschiede werden in den Verweisen in diesem Dokument aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="6e668-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="6e668-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="6e668-108">Card examples</span></span>

<span data-ttu-id="6e668-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK (v3).</span><span class="sxs-lookup"><span data-stu-id="6e668-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="6e668-110">Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6e668-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="6e668-111">.NET</span><span class="sxs-lookup"><span data-stu-id="6e668-111">.NET</span></span>
  * [<span data-ttu-id="6e668-112">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="6e668-112">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="6e668-113">Kartenbeispielcode (Bot Builder v4)</span><span class="sxs-lookup"><span data-stu-id="6e668-113">Cards sample code (Bot Builder v4)</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards)

* <span data-ttu-id="6e668-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="6e668-114">Node.js</span></span>
  * [<span data-ttu-id="6e668-115">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="6e668-115">Add cards as attachments to messages</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [<span data-ttu-id="6e668-116">Kartenbeispielcode (Bot Builder v4)</span><span class="sxs-lookup"><span data-stu-id="6e668-116">Cards sample code (Bot Builder v4)</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards)

## <a name="types-of-cards"></a><span data-ttu-id="6e668-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="6e668-117">Types of cards</span></span>

<span data-ttu-id="6e668-118">In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="6e668-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="6e668-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="6e668-119">Card type</span></span> | <span data-ttu-id="6e668-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="6e668-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="6e668-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="6e668-122">Hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="6e668-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="6e668-123">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="6e668-124">In der Regel enthält ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="6e668-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="6e668-125">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-125">List card</span></span>](#list-card) | <span data-ttu-id="6e668-126">Eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="6e668-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="6e668-127">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="6e668-128">Flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="6e668-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="6e668-129">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="6e668-130">Stellt eine Quittung für den Benutzer zur</span><span class="sxs-lookup"><span data-stu-id="6e668-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="6e668-131">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="6e668-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="6e668-132">Ermöglicht einem Bot die Anforderung, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="6e668-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="6e668-133">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="6e668-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="6e668-134">Enthält in der Regel ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="6e668-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="6e668-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="6e668-136">Wird verwendet, um mehrere Elemente in einer einzigen Antwort zurück zu geben.</span><span class="sxs-lookup"><span data-stu-id="6e668-136">Used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="6e668-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="6e668-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="6e668-138">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="6e668-138">Inline card images</span></span>

<span data-ttu-id="6e668-139">Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich verfügbaren Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="6e668-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="6e668-140">Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Netzwerk für die Inhaltszustellung (Public Content Delivery Network, CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="6e668-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="6e668-141">Bilder werden in der Größe nach oben oder unten skaliert, wobei das Seitenverhältnis beibehalten wird, um den Bildbereich zu decken, und dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="6e668-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="6e668-142">Bilder müssen mindestens 1024×1024 im PNG-, JPEG- oder GIF-Format vorliegen, und animierte GIF-Dateien werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-142">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and animated GIF is not supported.</span></span>

| <span data-ttu-id="6e668-143">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6e668-143">Property</span></span> | <span data-ttu-id="6e668-144">Typ</span><span class="sxs-lookup"><span data-stu-id="6e668-144">Type</span></span>  | <span data-ttu-id="6e668-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6e668-146">url</span><span class="sxs-lookup"><span data-stu-id="6e668-146">url</span></span> | <span data-ttu-id="6e668-147">URL</span><span class="sxs-lookup"><span data-stu-id="6e668-147">URL</span></span> | <span data-ttu-id="6e668-148">HTTPS-URL zum Bild</span><span class="sxs-lookup"><span data-stu-id="6e668-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="6e668-149">alt</span><span class="sxs-lookup"><span data-stu-id="6e668-149">alt</span></span> | <span data-ttu-id="6e668-150">String</span><span class="sxs-lookup"><span data-stu-id="6e668-150">String</span></span> | <span data-ttu-id="6e668-151">Barrierefreie Beschreibung des Bilds</span><span class="sxs-lookup"><span data-stu-id="6e668-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="6e668-152">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6e668-152">Buttons</span></span>

<span data-ttu-id="6e668-153">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6e668-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="6e668-154">Der Text der Schaltfläche befindet sich immer in einer einzigen Zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="6e668-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="6e668-155">Alle zusätzlichen Schaltflächen, die über die maximale Anzahl hinausgehen, die von der Karte unterstützt wird, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6e668-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="6e668-156">Weitere [Informationen finden Sie](~/task-modules-and-cards/cards/cards-actions.md) unter Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="6e668-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="6e668-157">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="6e668-157">Card formatting</span></span>

<span data-ttu-id="6e668-158">Weitere [Informationen zur Textformatierung](~/task-modules-and-cards/cards/cards-format.md) in Karten finden Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="6e668-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="6e668-159">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="6e668-159">Adaptive card</span></span>

<span data-ttu-id="6e668-160">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="6e668-160">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="6e668-161">Weitere [Informationen finden Sie unter Adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="6e668-161">See [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="6e668-162">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="6e668-162">Support for adaptive cards</span></span>

| <span data-ttu-id="6e668-163">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-163">Bots in Teams</span></span> | <span data-ttu-id="6e668-164">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-164">Messaging extensions</span></span>  | <span data-ttu-id="6e668-165">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-165">Connectors</span></span> | <span data-ttu-id="6e668-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-167">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-167">✔</span></span> | <span data-ttu-id="6e668-168">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-168">✔</span></span> | <span data-ttu-id="6e668-169">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-169">✖</span></span> | <span data-ttu-id="6e668-170">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-170">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="6e668-171">Die Teams-Plattform unterstützt Version 1.2 oder früher von adaptiven Kartenfeatures.</span><span class="sxs-lookup"><span data-stu-id="6e668-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="6e668-172">Medienelemente werden derzeit in adaptiver Karte v1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="6e668-173">Beispiel für eine adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="6e668-173">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="6e668-175">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="6e668-175">Additional information on adaptive cards</span></span>

<span data-ttu-id="6e668-176">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="6e668-176">Bot Framework reference:</span></span>

* [<span data-ttu-id="6e668-177">Knoten "Adaptive Karten"</span><span class="sxs-lookup"><span data-stu-id="6e668-177">Adaptive cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="6e668-178">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="6e668-178">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="6e668-179">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-179">Hero card</span></span>

<span data-ttu-id="6e668-180">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="6e668-180">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="6e668-181">Unterstützung für Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-181">Support for hero cards</span></span>

| <span data-ttu-id="6e668-182">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-182">Bots in Teams</span></span> | <span data-ttu-id="6e668-183">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-183">Messaging Extensions</span></span>  | <span data-ttu-id="6e668-184">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-184">Connectors</span></span> | <span data-ttu-id="6e668-185">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-185">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-186">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-186">✔</span></span> | <span data-ttu-id="6e668-187">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-187">✔</span></span> | <span data-ttu-id="6e668-188">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-188">✖</span></span> | <span data-ttu-id="6e668-189">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-189">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="6e668-190">Eigenschaften einer Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-190">Properties of a hero card</span></span>

| <span data-ttu-id="6e668-191">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6e668-191">Property</span></span> | <span data-ttu-id="6e668-192">Typ</span><span class="sxs-lookup"><span data-stu-id="6e668-192">Type</span></span>  | <span data-ttu-id="6e668-193">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-193">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6e668-194">title</span><span class="sxs-lookup"><span data-stu-id="6e668-194">title</span></span> | <span data-ttu-id="6e668-195">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-195">Rich text</span></span> | <span data-ttu-id="6e668-196">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-196">Title of the card.</span></span> <span data-ttu-id="6e668-197">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-197">Maximum 2 lines.</span></span> |
| <span data-ttu-id="6e668-198">subtitle</span><span class="sxs-lookup"><span data-stu-id="6e668-198">subtitle</span></span> | <span data-ttu-id="6e668-199">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-199">Rich text</span></span> | <span data-ttu-id="6e668-200">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-200">Subtitle of the card.</span></span> <span data-ttu-id="6e668-201">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-201">Maximum 2 lines.</span></span>|
| <span data-ttu-id="6e668-202">text</span><span class="sxs-lookup"><span data-stu-id="6e668-202">text</span></span> | <span data-ttu-id="6e668-203">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-203">Rich text</span></span> | <span data-ttu-id="6e668-204">Text wird unter dem Untertitel angezeigt. Formatierungsoptionen [finden Sie](~/task-modules-and-cards/cards/cards-format.md) unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="6e668-204">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="6e668-205">Bilder</span><span class="sxs-lookup"><span data-stu-id="6e668-205">images</span></span> | <span data-ttu-id="6e668-206">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="6e668-206">Array of images</span></span> | <span data-ttu-id="6e668-207">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e668-207">Image displayed at top of card.</span></span> <span data-ttu-id="6e668-208">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="6e668-208">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="6e668-209">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6e668-209">buttons</span></span> | <span data-ttu-id="6e668-210">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="6e668-210">Array of action objects</span></span> | <span data-ttu-id="6e668-211">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="6e668-211">Set of actions applicable to the current card.</span></span> <span data-ttu-id="6e668-212">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="6e668-212">Maximum 6.</span></span> |
| <span data-ttu-id="6e668-213">tippen</span><span class="sxs-lookup"><span data-stu-id="6e668-213">tap</span></span> | <span data-ttu-id="6e668-214">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="6e668-214">Action object</span></span> | <span data-ttu-id="6e668-215">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="6e668-215">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="6e668-216">Beispiel für eine Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-216">Example of a hero card</span></span>

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="6e668-218">Zusätzliche Informationen zu Heldenkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-218">Additional information on hero cards</span></span>

<span data-ttu-id="6e668-219">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="6e668-219">Bot Framework reference:</span></span>

* [<span data-ttu-id="6e668-220">Knoten der Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-220">Hero card Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="6e668-221">Heldenkarte C #</span><span class="sxs-lookup"><span data-stu-id="6e668-221">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="6e668-222">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-222">List card</span></span>

<span data-ttu-id="6e668-223">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen zu bieten, die über das hinaus gehen, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="6e668-223">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="6e668-224">Die Listenkarte enthält eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="6e668-224">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="6e668-225">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-225">Support for list cards</span></span>

| <span data-ttu-id="6e668-226">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-226">Bots in Teams</span></span> | <span data-ttu-id="6e668-227">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-227">Messaging extensions</span></span>  | <span data-ttu-id="6e668-228">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-228">Connectors</span></span> | <span data-ttu-id="6e668-229">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-229">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-230">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-230">✔</span></span> | <span data-ttu-id="6e668-231">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-231">✖</span></span> | <span data-ttu-id="6e668-232">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-232">✖</span></span> |<span data-ttu-id="6e668-233">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-233">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="6e668-234">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-234">Properties of a list card</span></span>

| <span data-ttu-id="6e668-235">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6e668-235">Property</span></span> | <span data-ttu-id="6e668-236">Typ</span><span class="sxs-lookup"><span data-stu-id="6e668-236">Type</span></span>  | <span data-ttu-id="6e668-237">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-237">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6e668-238">title</span><span class="sxs-lookup"><span data-stu-id="6e668-238">title</span></span> | <span data-ttu-id="6e668-239">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-239">Rich text</span></span> | <span data-ttu-id="6e668-240">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-240">Title of the card.</span></span> <span data-ttu-id="6e668-241">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-241">Maximum 2 lines.</span></span>|
| <span data-ttu-id="6e668-242">items</span><span class="sxs-lookup"><span data-stu-id="6e668-242">items</span></span> | <span data-ttu-id="6e668-243">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="6e668-243">Array of list items</span></span>  ||
| <span data-ttu-id="6e668-244">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6e668-244">buttons</span></span> | <span data-ttu-id="6e668-245">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="6e668-245">Array of action objects</span></span> | <span data-ttu-id="6e668-246">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="6e668-246">Set of actions applicable to the current card.</span></span> <span data-ttu-id="6e668-247">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="6e668-247">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="6e668-248">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-248">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="6e668-249">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-249">Office 365 connector card</span></span>

<span data-ttu-id="6e668-250">Die Office 365 Connector-Karte wird in Teams und nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-250">The Office 365 Connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="6e668-251">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="6e668-251">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="6e668-252">Diese Karte kapselt eine Connectorkarte, sodass sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6e668-252">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="6e668-253">Im Abschnitt Notizen finden Sie Unterschiede zwischen Connectorkarten und der O365-Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-253">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="6e668-254">Unterstützung für Office 365-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-254">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="6e668-255">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-255">Bots in Teams</span></span> | <span data-ttu-id="6e668-256">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-256">Messaging extensions</span></span>  | <span data-ttu-id="6e668-257">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-257">Connectors</span></span> | <span data-ttu-id="6e668-258">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-258">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-259">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-259">✔</span></span> | <span data-ttu-id="6e668-260">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-260">✔</span></span> | <span data-ttu-id="6e668-261">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-261">✔</span></span> | <span data-ttu-id="6e668-262">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-262">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="6e668-263">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-263">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="6e668-264">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6e668-264">Property</span></span> | <span data-ttu-id="6e668-265">Typ</span><span class="sxs-lookup"><span data-stu-id="6e668-265">Type</span></span>  | <span data-ttu-id="6e668-266">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-266">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6e668-267">title</span><span class="sxs-lookup"><span data-stu-id="6e668-267">title</span></span> | <span data-ttu-id="6e668-268">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-268">Rich text</span></span> | <span data-ttu-id="6e668-269">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-269">Title of the card.</span></span> <span data-ttu-id="6e668-270">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-270">Maximum 2 lines.</span></span> |
| <span data-ttu-id="6e668-271">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="6e668-271">summary</span></span> | <span data-ttu-id="6e668-272">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-272">Rich text</span></span> | <span data-ttu-id="6e668-273">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-273">Summary of the card.</span></span> <span data-ttu-id="6e668-274">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-274">Maximum 2 lines.</span></span> |
| <span data-ttu-id="6e668-275">text</span><span class="sxs-lookup"><span data-stu-id="6e668-275">text</span></span> | <span data-ttu-id="6e668-276">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-276">Rich text</span></span> | <span data-ttu-id="6e668-277">Text wird unter dem Untertitel angezeigt. Formatierungsoptionen [finden Sie](~/task-modules-and-cards/cards/cards-format.md) unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="6e668-277">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="6e668-278">themeColor</span><span class="sxs-lookup"><span data-stu-id="6e668-278">themeColor</span></span> | <span data-ttu-id="6e668-279">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6e668-279">HEX string</span></span> | <span data-ttu-id="6e668-280">Farbe, die die im Anwendungsmanifest bereitgestellte accentColor überschreibt.</span><span class="sxs-lookup"><span data-stu-id="6e668-280">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="6e668-281">Hinweise auf der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-281">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="6e668-282">Office 365-Connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="6e668-282">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="6e668-283">Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten von einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="6e668-283">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="6e668-284">Für einen Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="6e668-284">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="6e668-285">Bei einem Bot löst die Aktion eine Aktivität aus, die nur die `HttpPOST` `invoke` Aktions-ID und den Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="6e668-285">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="6e668-286">Jede Connectorkarte kann maximal 10 Abschnitte anzeigen, und jeder Abschnitt kann maximal 5 Bilder und 5 Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="6e668-286">Each connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="6e668-287">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6e668-287">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="6e668-288">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="6e668-288">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="6e668-289">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie `markdown` die Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="6e668-289">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="6e668-290">Standardmäßig ist auf festgelegt; wenn Sie stattdessen `markdown` HTML verwenden `true` möchten, legen Sie auf `markdown` . `false`</span><span class="sxs-lookup"><span data-stu-id="6e668-290">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="6e668-291">Wenn Sie die Eigenschaft `themeColor` angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="6e668-291">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="6e668-292">Zum Angeben des Renderingstils für `activityImage` können Sie `activityImageType` folgendes festlegen:</span><span class="sxs-lookup"><span data-stu-id="6e668-292">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="6e668-293">Wert</span><span class="sxs-lookup"><span data-stu-id="6e668-293">Value</span></span> | <span data-ttu-id="6e668-294">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-294">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="6e668-295">Standard; `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="6e668-295">Default; `activityImage` will be cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="6e668-296">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="6e668-296">`activityImage` will be displayed as a rectangle and retain its aspect ratio.</span></span> |

<span data-ttu-id="6e668-297">Weitere Informationen zu den Eigenschaften von Connectorkarten finden Sie unter Referenz zur [Aktionsfähige Nachrichtenkarte](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="6e668-297">For all other details about connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="6e668-298">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:</span><span class="sxs-lookup"><span data-stu-id="6e668-298">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="6e668-299">`startGroup` (immer wie `true` in Teams behandelt)</span><span class="sxs-lookup"><span data-stu-id="6e668-299">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="6e668-300">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-300">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="6e668-301">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-301">Receipt card</span></span>

<span data-ttu-id="6e668-302">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="6e668-302">Teams supports receipt card.</span></span> <span data-ttu-id="6e668-303">Es handelt sich um eine Karte, mit der ein Bot dem Benutzer eine Quittung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="6e668-303">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="6e668-304">Sie enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="6e668-304">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="6e668-305">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-305">Support for receipt cards</span></span>

| <span data-ttu-id="6e668-306">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-306">Bots in Teams</span></span> | <span data-ttu-id="6e668-307">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-307">Messaging extensions</span></span>  | <span data-ttu-id="6e668-308">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-308">Connectors</span></span> | <span data-ttu-id="6e668-309">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-309">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-310">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-310">✔</span></span> | <span data-ttu-id="6e668-311">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-311">✔</span></span> | <span data-ttu-id="6e668-312">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-312">✖</span></span> | <span data-ttu-id="6e668-313">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-313">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="6e668-314">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-314">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="6e668-316">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-316">Additional information on receipt cards</span></span>

<span data-ttu-id="6e668-317">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="6e668-317">Bot Framework reference:</span></span>

* [<span data-ttu-id="6e668-318">Knoten "Belegkarte"</span><span class="sxs-lookup"><span data-stu-id="6e668-318">Receipt card Node</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="6e668-319">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="6e668-319">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="6e668-320">Signin-Karte</span><span class="sxs-lookup"><span data-stu-id="6e668-320">Signin card</span></span>

<span data-ttu-id="6e668-321">Mit der Anmeldekarte kann ein Bot einen Benutzer zur Anmeldung anfordern.</span><span class="sxs-lookup"><span data-stu-id="6e668-321">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="6e668-322">Wird in Teams in einer etwas anderen Form als im Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-322">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="6e668-323">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` unterstützt: und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="6e668-323">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="6e668-324">Die **Anmeldeaktion** kann von jeder beliebigen Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="6e668-324">The **signin action** can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="6e668-325">Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span><span class="sxs-lookup"><span data-stu-id="6e668-325">For more details on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="6e668-326">Unterstützung für Signin-Karten</span><span class="sxs-lookup"><span data-stu-id="6e668-326">Support for Signin cards</span></span>

| <span data-ttu-id="6e668-327">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-327">Bots in Teams</span></span> | <span data-ttu-id="6e668-328">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-328">Messaging extensions</span></span>  | <span data-ttu-id="6e668-329">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-329">Connectors</span></span> | <span data-ttu-id="6e668-330">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-330">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-331">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-331">✔</span></span> | <span data-ttu-id="6e668-332">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-332">✖</span></span> | <span data-ttu-id="6e668-333">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-333">✖</span></span> | <span data-ttu-id="6e668-334">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-334">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="6e668-335">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="6e668-335">Additional information on signin cards</span></span>

<span data-ttu-id="6e668-336">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="6e668-336">Bot Framework reference:</span></span>

* [<span data-ttu-id="6e668-337">Signin card Node</span><span class="sxs-lookup"><span data-stu-id="6e668-337">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="6e668-338">Signin-Karte C #</span><span class="sxs-lookup"><span data-stu-id="6e668-338">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="6e668-339">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="6e668-339">Thumbnail card</span></span>

<span data-ttu-id="6e668-340">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="6e668-340">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="6e668-341">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="6e668-341">Support for thumbnail cards</span></span>

| <span data-ttu-id="6e668-342">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-342">Bots in Teams</span></span> | <span data-ttu-id="6e668-343">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-343">Messaging extensions</span></span>  | <span data-ttu-id="6e668-344">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-344">Connectors</span></span> | <span data-ttu-id="6e668-345">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-345">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-346">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-346">✔</span></span> | <span data-ttu-id="6e668-347">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-347">✔</span></span> | <span data-ttu-id="6e668-348">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-348">✖</span></span> | <span data-ttu-id="6e668-349">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-349">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="6e668-351">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="6e668-351">Properties of a thumbnail card</span></span>

| <span data-ttu-id="6e668-352">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6e668-352">Property</span></span> | <span data-ttu-id="6e668-353">Typ</span><span class="sxs-lookup"><span data-stu-id="6e668-353">Type</span></span>  | <span data-ttu-id="6e668-354">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e668-354">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="6e668-355">title</span><span class="sxs-lookup"><span data-stu-id="6e668-355">title</span></span> | <span data-ttu-id="6e668-356">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-356">Rich text</span></span> | <span data-ttu-id="6e668-357">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-357">Title of the card.</span></span> <span data-ttu-id="6e668-358">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-358">Maximum 2 lines.</span></span>|
| <span data-ttu-id="6e668-359">subtitle</span><span class="sxs-lookup"><span data-stu-id="6e668-359">subtitle</span></span> | <span data-ttu-id="6e668-360">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-360">Rich text</span></span> | <span data-ttu-id="6e668-361">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="6e668-361">Subtitle of the card.</span></span> <span data-ttu-id="6e668-362">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="6e668-362">Maximum 2 lines.</span></span>|
| <span data-ttu-id="6e668-363">text</span><span class="sxs-lookup"><span data-stu-id="6e668-363">text</span></span> | <span data-ttu-id="6e668-364">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="6e668-364">Rich text</span></span> | <span data-ttu-id="6e668-365">Text wird unter dem Untertitel angezeigt. Formatierungsoptionen [finden Sie](~/task-modules-and-cards/cards/cards-format.md) unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="6e668-365">Text appears under the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="6e668-366">Bilder</span><span class="sxs-lookup"><span data-stu-id="6e668-366">images</span></span> | <span data-ttu-id="6e668-367">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="6e668-367">Array of images</span></span> | <span data-ttu-id="6e668-368">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e668-368">Image displayed at top of card.</span></span> <span data-ttu-id="6e668-369">Seitenverhältnis 1:1 (quadratisch).</span><span class="sxs-lookup"><span data-stu-id="6e668-369">Aspect ratio 1:1 (square).</span></span> |
| <span data-ttu-id="6e668-370">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="6e668-370">buttons</span></span> | <span data-ttu-id="6e668-371">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="6e668-371">Array of action objects</span></span> | <span data-ttu-id="6e668-372">Aktionssatz, der auf die aktuelle Karte anwendbar ist.</span><span class="sxs-lookup"><span data-stu-id="6e668-372">Set of actions applicable to the current card.</span></span> <span data-ttu-id="6e668-373">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="6e668-373">Maximum 6.</span></span> |
| <span data-ttu-id="6e668-374">tippen</span><span class="sxs-lookup"><span data-stu-id="6e668-374">tap</span></span> | <span data-ttu-id="6e668-375">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="6e668-375">Action object</span></span> | <span data-ttu-id="6e668-376">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="6e668-376">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="6e668-377">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="6e668-377">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="6e668-378">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6e668-378">Additional information</span></span>

<span data-ttu-id="6e668-379">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="6e668-379">Bot Framework reference:</span></span>

* [<span data-ttu-id="6e668-380">Miniaturansichtskartenknoten</span><span class="sxs-lookup"><span data-stu-id="6e668-380">Thumbnail card Node</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="6e668-381">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="6e668-381">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="6e668-382">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-382">Card collections</span></span>

<span data-ttu-id="6e668-383">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="6e668-383">Teams supports Card collections.</span></span>

<span data-ttu-id="6e668-384">`builder.AttachmentLayout.carousel`Kartensammlungen: und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="6e668-384">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="6e668-385">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="6e668-385">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="6e668-386">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="6e668-386">Carousel collection</span></span>

<span data-ttu-id="6e668-387">Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="6e668-387">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="6e668-388">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-388">Support for carousel collections</span></span>

| <span data-ttu-id="6e668-389">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-389">Bots in Teams</span></span> | <span data-ttu-id="6e668-390">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-390">Messaging extensions</span></span>  | <span data-ttu-id="6e668-391">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-391">Connectors</span></span> | <span data-ttu-id="6e668-392">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-392">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-393">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-393">✔</span></span> | <span data-ttu-id="6e668-394">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-394">✖</span></span> | <span data-ttu-id="6e668-395">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-395">✖</span></span> | <span data-ttu-id="6e668-396">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-396">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="6e668-397">Ein Karussell kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="6e668-397">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="6e668-398">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="6e668-398">Properties of a carousel card</span></span>

<span data-ttu-id="6e668-399">Die Eigenschaften einer Karussellkarte sind mit denen der Hero- und Miniaturansichtskarten identisch.</span><span class="sxs-lookup"><span data-stu-id="6e668-399">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="6e668-400">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="6e668-400">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="6e668-402">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-402">Syntax for carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="6e668-403">Listensammlung</span><span class="sxs-lookup"><span data-stu-id="6e668-403">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="6e668-404">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-404">Support for list collections</span></span>

<span data-ttu-id="6e668-405">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="6e668-405">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="6e668-406">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="6e668-406">Bots in Teams</span></span> | <span data-ttu-id="6e668-407">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="6e668-407">Messaging extensions</span></span>  | <span data-ttu-id="6e668-408">Connectors</span><span class="sxs-lookup"><span data-stu-id="6e668-408">Connectors</span></span> | <span data-ttu-id="6e668-409">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="6e668-409">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="6e668-410">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-410">✔</span></span> | <span data-ttu-id="6e668-411">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-411">✔</span></span> | <span data-ttu-id="6e668-412">✖</span><span class="sxs-lookup"><span data-stu-id="6e668-412">✖</span></span> | <span data-ttu-id="6e668-413">✔</span><span class="sxs-lookup"><span data-stu-id="6e668-413">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="6e668-414">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="6e668-414">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="6e668-416">Die Eigenschaften sind identisch mit der Hero- oder Miniaturansichtskarte.</span><span class="sxs-lookup"><span data-stu-id="6e668-416">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="6e668-417">Eine Liste kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="6e668-417">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="6e668-418">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-418">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="6e668-419">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="6e668-419">Syntax for list collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="6e668-420">In Teams nicht unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="6e668-420">Cards not supported in Teams</span></span>

<span data-ttu-id="6e668-421">Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch NICHT von Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6e668-421">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="6e668-422">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="6e668-422">Animation cards</span></span>
* <span data-ttu-id="6e668-423">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="6e668-423">Audio cards</span></span>
* <span data-ttu-id="6e668-424">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="6e668-424">Video cards</span></span>
