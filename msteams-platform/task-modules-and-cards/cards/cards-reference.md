---
title: Kartenreferenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams zur Verfügung stehen
keywords: Referenz zu Bots-Karten
ms.topic: reference
ms.openlocfilehash: 839430baa5ce5e8950a21a1472036c6fd96f4edf
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911895"
---
# <a name="cards-reference"></a><span data-ttu-id="b554a-104">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="b554a-104">Cards reference</span></span>

<span data-ttu-id="b554a-105">Die in diesem Abschnitt aufgeführten Karten werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-105">The cards listed in this section are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="b554a-106">Sie basieren auf Karten, die vom Bot Framework definiert werden, teams unterstützt jedoch nicht alle Bot Framework-Karten und hat eigene Karten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b554a-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="b554a-107">Unterschiede werden in den Verweisen in diesem Dokument genannt.</span><span class="sxs-lookup"><span data-stu-id="b554a-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="b554a-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="b554a-108">Card examples</span></span>

<span data-ttu-id="b554a-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK (v3).</span><span class="sxs-lookup"><span data-stu-id="b554a-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="b554a-110">Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b554a-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="b554a-111">.NET</span><span class="sxs-lookup"><span data-stu-id="b554a-111">.NET</span></span>
  * [<span data-ttu-id="b554a-112">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="b554a-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="b554a-113">Beispielcode für Karten (Bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="b554a-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="b554a-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="b554a-114">Node.js</span></span>
  * [<span data-ttu-id="b554a-115">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="b554a-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="b554a-116">Beispielcode für Karten (Bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="b554a-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="b554a-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="b554a-117">Types of cards</span></span>

<span data-ttu-id="b554a-118">In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="b554a-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="b554a-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="b554a-119">Card type</span></span> | <span data-ttu-id="b554a-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="b554a-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="b554a-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="b554a-122">Hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="b554a-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="b554a-123">Herokarte</span><span class="sxs-lookup"><span data-stu-id="b554a-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="b554a-124">Enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="b554a-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="b554a-125">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-125">List card</span></span>](#list-card) | <span data-ttu-id="b554a-126">Eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="b554a-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="b554a-127">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="b554a-128">Flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="b554a-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="b554a-129">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="b554a-130">Stellt eine Empfangsbestätigung für den Benutzer zur Verf tung.</span><span class="sxs-lookup"><span data-stu-id="b554a-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="b554a-131">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="b554a-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="b554a-132">Ermöglicht einem Bot die Anforderung, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="b554a-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="b554a-133">Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="b554a-134">Enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="b554a-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="b554a-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="b554a-136">Wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="b554a-136">Used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="b554a-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="b554a-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="b554a-138">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="b554a-138">Inline card images</span></span>

<span data-ttu-id="b554a-139">Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich verfügbaren Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="b554a-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="b554a-140">Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Content Delivery Network (CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="b554a-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="b554a-141">Bilder werden nach oben oder unten skaliert, während das Seitenverhältnis beibehalten wird, um den Bildbereich zu abdecken, und dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="b554a-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="b554a-142">Bilder müssen mindestens 1024×1024 im PNG-, JPEG- oder GIF-Format sein, und animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-142">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and animated GIF is not supported.</span></span>

| <span data-ttu-id="b554a-143">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b554a-143">Property</span></span> | <span data-ttu-id="b554a-144">Typ</span><span class="sxs-lookup"><span data-stu-id="b554a-144">Type</span></span>  | <span data-ttu-id="b554a-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b554a-146">url</span><span class="sxs-lookup"><span data-stu-id="b554a-146">url</span></span> | <span data-ttu-id="b554a-147">URL</span><span class="sxs-lookup"><span data-stu-id="b554a-147">URL</span></span> | <span data-ttu-id="b554a-148">HTTPS-URL zum Bild</span><span class="sxs-lookup"><span data-stu-id="b554a-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="b554a-149">alt</span><span class="sxs-lookup"><span data-stu-id="b554a-149">alt</span></span> | <span data-ttu-id="b554a-150">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b554a-150">String</span></span> | <span data-ttu-id="b554a-151">Barrierefreie Beschreibung des Bilds</span><span class="sxs-lookup"><span data-stu-id="b554a-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="b554a-152">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="b554a-152">Buttons</span></span>

<span data-ttu-id="b554a-153">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b554a-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="b554a-154">Der Text der Schaltfläche befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="b554a-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="b554a-155">Alle zusätzlichen Schaltflächen, die über die maximale Anzahl hinausgehen, die von der Karte unterstützt wird, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b554a-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="b554a-156">Weitere [Informationen finden Sie unter "Kartenaktionen".](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="b554a-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="b554a-157">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="b554a-157">Card formatting</span></span>

<span data-ttu-id="b554a-158">Weitere [Informationen zur Textformatierung](~/task-modules-and-cards/cards/cards-format.md) in Karten finden Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="b554a-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="b554a-159">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="b554a-159">Adaptive card</span></span>

<span data-ttu-id="b554a-160">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="b554a-160">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="b554a-161">Siehe [adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="b554a-161">See [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="b554a-162">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="b554a-162">Support for adaptive cards</span></span>

| <span data-ttu-id="b554a-163">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-163">Bots in Teams</span></span> | <span data-ttu-id="b554a-164">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-164">Messaging extensions</span></span>  | <span data-ttu-id="b554a-165">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-165">Connectors</span></span> | <span data-ttu-id="b554a-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-167">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-167">✔</span></span> | <span data-ttu-id="b554a-168">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-168">✔</span></span> | <span data-ttu-id="b554a-169">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-169">✖</span></span> | <span data-ttu-id="b554a-170">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-170">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="b554a-171">Die Plattform Teams unterstützt Version 1.2 oder früher von Features für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="b554a-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="b554a-172">Medienelemente werden derzeit in der adaptiven Karte v1.2 auf der Plattform Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="b554a-173">Beispiel für eine adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="b554a-173">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="b554a-175">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="b554a-175">Additional information on adaptive cards</span></span>

* [<span data-ttu-id="b554a-176">Übersicht über adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="b554a-176">Adaptive cards overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="b554a-177">Aktionen für adaptive Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-177">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="b554a-178">Herokarte</span><span class="sxs-lookup"><span data-stu-id="b554a-178">Hero card</span></span>

<span data-ttu-id="b554a-179">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="b554a-179">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="b554a-180">Unterstützung für Herokarten</span><span class="sxs-lookup"><span data-stu-id="b554a-180">Support for hero cards</span></span>

| <span data-ttu-id="b554a-181">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-181">Bots in Teams</span></span> | <span data-ttu-id="b554a-182">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-182">Messaging Extensions</span></span>  | <span data-ttu-id="b554a-183">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-183">Connectors</span></span> | <span data-ttu-id="b554a-184">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-184">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-185">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-185">✔</span></span> | <span data-ttu-id="b554a-186">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-186">✔</span></span> | <span data-ttu-id="b554a-187">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-187">✖</span></span> | <span data-ttu-id="b554a-188">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-188">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="b554a-189">Eigenschaften einer Herokarte</span><span class="sxs-lookup"><span data-stu-id="b554a-189">Properties of a hero card</span></span>

| <span data-ttu-id="b554a-190">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b554a-190">Property</span></span> | <span data-ttu-id="b554a-191">Typ</span><span class="sxs-lookup"><span data-stu-id="b554a-191">Type</span></span>  | <span data-ttu-id="b554a-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-192">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b554a-193">title</span><span class="sxs-lookup"><span data-stu-id="b554a-193">title</span></span> | <span data-ttu-id="b554a-194">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-194">Rich text</span></span> | <span data-ttu-id="b554a-195">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-195">Title of the card.</span></span> <span data-ttu-id="b554a-196">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-196">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b554a-197">subtitle</span><span class="sxs-lookup"><span data-stu-id="b554a-197">subtitle</span></span> | <span data-ttu-id="b554a-198">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-198">Rich text</span></span> | <span data-ttu-id="b554a-199">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-199">Subtitle of the card.</span></span> <span data-ttu-id="b554a-200">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-200">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b554a-201">text</span><span class="sxs-lookup"><span data-stu-id="b554a-201">text</span></span> | <span data-ttu-id="b554a-202">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-202">Rich text</span></span> | <span data-ttu-id="b554a-203">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="b554a-203">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b554a-204">images</span><span class="sxs-lookup"><span data-stu-id="b554a-204">images</span></span> | <span data-ttu-id="b554a-205">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="b554a-205">Array of images</span></span> | <span data-ttu-id="b554a-206">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b554a-206">Image displayed at top of card.</span></span> <span data-ttu-id="b554a-207">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="b554a-207">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="b554a-208">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="b554a-208">buttons</span></span> | <span data-ttu-id="b554a-209">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="b554a-209">Array of action objects</span></span> | <span data-ttu-id="b554a-210">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="b554a-210">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b554a-211">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="b554a-211">Maximum 6.</span></span> |
| <span data-ttu-id="b554a-212">Tippen</span><span class="sxs-lookup"><span data-stu-id="b554a-212">tap</span></span> | <span data-ttu-id="b554a-213">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="b554a-213">Action object</span></span> | <span data-ttu-id="b554a-214">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="b554a-214">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="b554a-215">Beispiel für eine Herokarte</span><span class="sxs-lookup"><span data-stu-id="b554a-215">Example of a hero card</span></span>

![Beispiel für eine Herokarte](~/assets/images/cards/hero.png)

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="b554a-217">Zusätzliche Informationen zu Herokarten</span><span class="sxs-lookup"><span data-stu-id="b554a-217">Additional information on hero cards</span></span>

<span data-ttu-id="b554a-218">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="b554a-218">Bot Framework reference:</span></span>

* [<span data-ttu-id="b554a-219">Hero card Node</span><span class="sxs-lookup"><span data-stu-id="b554a-219">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="b554a-220">#A0 C #</span><span class="sxs-lookup"><span data-stu-id="b554a-220">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="b554a-221">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-221">List card</span></span>

<span data-ttu-id="b554a-222">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen zu bieten, die über das hinausgehen, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="b554a-222">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="b554a-223">Die Listenkarte bietet eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="b554a-223">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="b554a-224">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="b554a-224">Support for list cards</span></span>

| <span data-ttu-id="b554a-225">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-225">Bots in Teams</span></span> | <span data-ttu-id="b554a-226">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-226">Messaging extensions</span></span>  | <span data-ttu-id="b554a-227">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-227">Connectors</span></span> | <span data-ttu-id="b554a-228">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-228">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-229">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-229">✔</span></span> | <span data-ttu-id="b554a-230">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-230">✖</span></span> | <span data-ttu-id="b554a-231">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-231">✖</span></span> |<span data-ttu-id="b554a-232">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-232">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="b554a-233">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-233">Properties of a list card</span></span>

| <span data-ttu-id="b554a-234">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b554a-234">Property</span></span> | <span data-ttu-id="b554a-235">Typ</span><span class="sxs-lookup"><span data-stu-id="b554a-235">Type</span></span>  | <span data-ttu-id="b554a-236">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-236">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b554a-237">title</span><span class="sxs-lookup"><span data-stu-id="b554a-237">title</span></span> | <span data-ttu-id="b554a-238">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-238">Rich text</span></span> | <span data-ttu-id="b554a-239">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-239">Title of the card.</span></span> <span data-ttu-id="b554a-240">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-240">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b554a-241">items</span><span class="sxs-lookup"><span data-stu-id="b554a-241">items</span></span> | <span data-ttu-id="b554a-242">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="b554a-242">Array of list items</span></span>  ||
| <span data-ttu-id="b554a-243">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="b554a-243">buttons</span></span> | <span data-ttu-id="b554a-244">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="b554a-244">Array of action objects</span></span> | <span data-ttu-id="b554a-245">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="b554a-245">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b554a-246">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="b554a-246">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="b554a-247">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-247">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="b554a-248">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-248">Office 365 connector card</span></span>

<span data-ttu-id="b554a-249">Die Office 365 -Connector-Karte wird in Teams und nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-249">The Office 365 Connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="b554a-250">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="b554a-250">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="b554a-251">Diese Karte kapselt eine Connectorkarte, damit sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b554a-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="b554a-252">Im Abschnitt "Hinweise" finden Sie Unterschiede zwischen Connectorkarten und der O365-Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="b554a-253">Unterstützung für Office 365-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="b554a-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="b554a-254">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-254">Bots in Teams</span></span> | <span data-ttu-id="b554a-255">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-255">Messaging extensions</span></span>  | <span data-ttu-id="b554a-256">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-256">Connectors</span></span> | <span data-ttu-id="b554a-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-258">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-258">✔</span></span> | <span data-ttu-id="b554a-259">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-259">✔</span></span> | <span data-ttu-id="b554a-260">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-260">✔</span></span> | <span data-ttu-id="b554a-261">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-261">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="b554a-262">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="b554a-263">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b554a-263">Property</span></span> | <span data-ttu-id="b554a-264">Typ</span><span class="sxs-lookup"><span data-stu-id="b554a-264">Type</span></span>  | <span data-ttu-id="b554a-265">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b554a-266">title</span><span class="sxs-lookup"><span data-stu-id="b554a-266">title</span></span> | <span data-ttu-id="b554a-267">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-267">Rich text</span></span> | <span data-ttu-id="b554a-268">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-268">Title of the card.</span></span> <span data-ttu-id="b554a-269">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-269">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b554a-270">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="b554a-270">summary</span></span> | <span data-ttu-id="b554a-271">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-271">Rich text</span></span> | <span data-ttu-id="b554a-272">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-272">Summary of the card.</span></span> <span data-ttu-id="b554a-273">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-273">Maximum 2 lines.</span></span> |
| <span data-ttu-id="b554a-274">text</span><span class="sxs-lookup"><span data-stu-id="b554a-274">text</span></span> | <span data-ttu-id="b554a-275">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-275">Rich text</span></span> | <span data-ttu-id="b554a-276">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="b554a-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b554a-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="b554a-277">themeColor</span></span> | <span data-ttu-id="b554a-278">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b554a-278">HEX string</span></span> | <span data-ttu-id="b554a-279">Farbe, die die im Anwendungsmanifest bereitgestellte AccentColor überschreibt.</span><span class="sxs-lookup"><span data-stu-id="b554a-279">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="b554a-280">Hinweise auf der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="b554a-281">Office 365-Connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="b554a-281">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="b554a-282">Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten von einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="b554a-282">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="b554a-283">Bei einem Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b554a-283">For a connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="b554a-284">Bei einem Bot löst die Aktion eine Aktivität aus, die nur die Aktions-ID und den `HttpPOST` `invoke` Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="b554a-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="b554a-285">Jede Connectorkarte kann maximal 10 Abschnitte anzeigen, und jeder Abschnitt kann maximal 5 Bilder und 5 Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b554a-285">Each connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="b554a-286">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b554a-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="b554a-287">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="b554a-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="b554a-288">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie `markdown` die Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="b554a-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="b554a-289">Standardmäßig ist der Standardwert auf ; wenn Sie stattdessen `markdown` `true` HTML verwenden möchten, legen Sie diesen auf `markdown` . `false`</span><span class="sxs-lookup"><span data-stu-id="b554a-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="b554a-290">Wenn Sie die Eigenschaft `themeColor` angeben, überschreibt sie die Eigenschaft im `accentColor` App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="b554a-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="b554a-291">Zum Angeben des Renderingstils für `activityImage` können Sie Folgendes `activityImageType` festlegen:</span><span class="sxs-lookup"><span data-stu-id="b554a-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="b554a-292">Wert</span><span class="sxs-lookup"><span data-stu-id="b554a-292">Value</span></span> | <span data-ttu-id="b554a-293">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="b554a-294">Standard; `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="b554a-294">Default; `activityImage` will be cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="b554a-295">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="b554a-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio.</span></span> |

<span data-ttu-id="b554a-296">Weitere Informationen zu den Eigenschaften von Connectorkarten finden Sie in der Referenz zur Nachrichtenkarte mit [Aktionen.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="b554a-296">For all other details about connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="b554a-297">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:</span><span class="sxs-lookup"><span data-stu-id="b554a-297">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="b554a-298">`startGroup` (immer wie `true` in Teams behandelt)</span><span class="sxs-lookup"><span data-stu-id="b554a-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="b554a-299">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-299">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="b554a-300">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-300">Receipt card</span></span>

<span data-ttu-id="b554a-301">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="b554a-301">Teams supports receipt card.</span></span> <span data-ttu-id="b554a-302">Es handelt sich um eine Karte, mit der ein Bot dem Benutzer eine Empfangsbestätigung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="b554a-302">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="b554a-303">Sie enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="b554a-303">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="b554a-304">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="b554a-304">Support for receipt cards</span></span>

| <span data-ttu-id="b554a-305">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-305">Bots in Teams</span></span> | <span data-ttu-id="b554a-306">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-306">Messaging extensions</span></span>  | <span data-ttu-id="b554a-307">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-307">Connectors</span></span> | <span data-ttu-id="b554a-308">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-309">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-309">✔</span></span> | <span data-ttu-id="b554a-310">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-310">✔</span></span> | <span data-ttu-id="b554a-311">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-311">✖</span></span> | <span data-ttu-id="b554a-312">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-312">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="b554a-313">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-313">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="b554a-315">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="b554a-315">Additional information on receipt cards</span></span>

<span data-ttu-id="b554a-316">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="b554a-316">Bot Framework reference:</span></span>

* [<span data-ttu-id="b554a-317">Belegkartenknoten</span><span class="sxs-lookup"><span data-stu-id="b554a-317">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b554a-318">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="b554a-318">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="b554a-319">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="b554a-319">Signin card</span></span>

<span data-ttu-id="b554a-320">Mit der Anmeldekarte kann ein Bot einen Benutzer zur Anmeldung anfordern.</span><span class="sxs-lookup"><span data-stu-id="b554a-320">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="b554a-321">Wird in Teams in einer etwas anderen Form unterstützt als im Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="b554a-321">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="b554a-322">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` unterstützt: und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="b554a-322">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="b554a-323">Die *Anmeldeaktion* kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="b554a-323">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="b554a-324">Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams-Authentifizierungsfluss für Bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="b554a-324">For more details on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="b554a-325">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="b554a-325">Support for Signin cards</span></span>

| <span data-ttu-id="b554a-326">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-326">Bots in Teams</span></span> | <span data-ttu-id="b554a-327">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-327">Messaging extensions</span></span>  | <span data-ttu-id="b554a-328">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-328">Connectors</span></span> | <span data-ttu-id="b554a-329">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-329">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-330">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-330">✔</span></span> | <span data-ttu-id="b554a-331">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-331">✖</span></span> | <span data-ttu-id="b554a-332">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-332">✖</span></span> | <span data-ttu-id="b554a-333">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-333">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="b554a-334">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="b554a-334">Additional information on signin cards</span></span>

<span data-ttu-id="b554a-335">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="b554a-335">Bot Framework reference:</span></span>

* [<span data-ttu-id="b554a-336">Anmeldekartenknoten</span><span class="sxs-lookup"><span data-stu-id="b554a-336">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b554a-337">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="b554a-337">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="b554a-338">Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-338">Thumbnail card</span></span>

<span data-ttu-id="b554a-339">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="b554a-339">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="b554a-340">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="b554a-340">Support for thumbnail cards</span></span>

| <span data-ttu-id="b554a-341">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-341">Bots in Teams</span></span> | <span data-ttu-id="b554a-342">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-342">Messaging extensions</span></span>  | <span data-ttu-id="b554a-343">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-343">Connectors</span></span> | <span data-ttu-id="b554a-344">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-344">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-345">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-345">✔</span></span> | <span data-ttu-id="b554a-346">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-346">✔</span></span> | <span data-ttu-id="b554a-347">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-347">✖</span></span> | <span data-ttu-id="b554a-348">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-348">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="b554a-350">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="b554a-350">Properties of a thumbnail card</span></span>

| <span data-ttu-id="b554a-351">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b554a-351">Property</span></span> | <span data-ttu-id="b554a-352">Typ</span><span class="sxs-lookup"><span data-stu-id="b554a-352">Type</span></span>  | <span data-ttu-id="b554a-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b554a-353">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b554a-354">title</span><span class="sxs-lookup"><span data-stu-id="b554a-354">title</span></span> | <span data-ttu-id="b554a-355">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-355">Rich text</span></span> | <span data-ttu-id="b554a-356">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-356">Title of the card.</span></span> <span data-ttu-id="b554a-357">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-357">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b554a-358">subtitle</span><span class="sxs-lookup"><span data-stu-id="b554a-358">subtitle</span></span> | <span data-ttu-id="b554a-359">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-359">Rich text</span></span> | <span data-ttu-id="b554a-360">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="b554a-360">Subtitle of the card.</span></span> <span data-ttu-id="b554a-361">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="b554a-361">Maximum 2 lines.</span></span>|
| <span data-ttu-id="b554a-362">text</span><span class="sxs-lookup"><span data-stu-id="b554a-362">text</span></span> | <span data-ttu-id="b554a-363">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="b554a-363">Rich text</span></span> | <span data-ttu-id="b554a-364">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="b554a-364">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options.</span></span> |
| <span data-ttu-id="b554a-365">images</span><span class="sxs-lookup"><span data-stu-id="b554a-365">images</span></span> | <span data-ttu-id="b554a-366">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="b554a-366">Array of images</span></span> | <span data-ttu-id="b554a-367">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b554a-367">Image displayed at top of card.</span></span> <span data-ttu-id="b554a-368">Seitenverhältnis 1:1 (Quadrat).</span><span class="sxs-lookup"><span data-stu-id="b554a-368">Aspect ratio 1:1 (square).</span></span> |
| <span data-ttu-id="b554a-369">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="b554a-369">buttons</span></span> | <span data-ttu-id="b554a-370">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="b554a-370">Array of action objects</span></span> | <span data-ttu-id="b554a-371">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="b554a-371">Set of actions applicable to the current card.</span></span> <span data-ttu-id="b554a-372">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="b554a-372">Maximum 6.</span></span> |
| <span data-ttu-id="b554a-373">Tippen</span><span class="sxs-lookup"><span data-stu-id="b554a-373">tap</span></span> | <span data-ttu-id="b554a-374">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="b554a-374">Action object</span></span> | <span data-ttu-id="b554a-375">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="b554a-375">This action will be activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="b554a-376">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="b554a-376">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="b554a-377">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b554a-377">Additional information</span></span>

<span data-ttu-id="b554a-378">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="b554a-378">Bot Framework reference:</span></span>

* [<span data-ttu-id="b554a-379">Knoten der Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-379">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="b554a-380">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="b554a-380">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="b554a-381">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-381">Card collections</span></span>

<span data-ttu-id="b554a-382">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="b554a-382">Teams supports Card collections.</span></span>

<span data-ttu-id="b554a-383">Kartensammlungen: `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="b554a-383">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="b554a-384">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="b554a-384">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="b554a-385">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="b554a-385">Carousel collection</span></span>

<span data-ttu-id="b554a-386">Das [Karusselllayout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) zeigt ein Karussell von Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="b554a-386">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="b554a-387">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-387">Support for carousel collections</span></span>

| <span data-ttu-id="b554a-388">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-388">Bots in Teams</span></span> | <span data-ttu-id="b554a-389">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-389">Messaging extensions</span></span>  | <span data-ttu-id="b554a-390">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-390">Connectors</span></span> | <span data-ttu-id="b554a-391">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-391">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-392">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-392">✔</span></span> | <span data-ttu-id="b554a-393">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-393">✖</span></span> | <span data-ttu-id="b554a-394">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-394">✖</span></span> | <span data-ttu-id="b554a-395">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-395">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="b554a-396">Ein Karussell kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b554a-396">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="b554a-397">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="b554a-397">Properties of a carousel card</span></span>

<span data-ttu-id="b554a-398">Die Eigenschaften einer Karussellkarte sind mit denen der Hero- und Miniaturansichtskarten identisch.</span><span class="sxs-lookup"><span data-stu-id="b554a-398">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="b554a-399">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="b554a-399">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="b554a-401">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-401">Syntax for carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="b554a-402">Listensammlung</span><span class="sxs-lookup"><span data-stu-id="b554a-402">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="b554a-403">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-403">Support for list collections</span></span>

<span data-ttu-id="b554a-404">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="b554a-404">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="b554a-405">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="b554a-405">Bots in Teams</span></span> | <span data-ttu-id="b554a-406">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b554a-406">Messaging extensions</span></span>  | <span data-ttu-id="b554a-407">Connectors</span><span class="sxs-lookup"><span data-stu-id="b554a-407">Connectors</span></span> | <span data-ttu-id="b554a-408">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="b554a-408">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b554a-409">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-409">✔</span></span> | <span data-ttu-id="b554a-410">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-410">✔</span></span> | <span data-ttu-id="b554a-411">✖</span><span class="sxs-lookup"><span data-stu-id="b554a-411">✖</span></span> | <span data-ttu-id="b554a-412">✔</span><span class="sxs-lookup"><span data-stu-id="b554a-412">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="b554a-413">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="b554a-413">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="b554a-415">Die Eigenschaften sind mit den Eigenschaften für die Hero- oder Miniaturansichtskarte identisch.</span><span class="sxs-lookup"><span data-stu-id="b554a-415">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="b554a-416">Eine Liste kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b554a-416">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="b554a-417">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-417">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="b554a-418">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="b554a-418">Syntax for list collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="b554a-419">In Teams nicht unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="b554a-419">Cards not supported in Teams</span></span>

<span data-ttu-id="b554a-420">Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch NICHT von Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b554a-420">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="b554a-421">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="b554a-421">Animation cards</span></span>
* <span data-ttu-id="b554a-422">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="b554a-422">Audio cards</span></span>
* <span data-ttu-id="b554a-423">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="b554a-423">Video cards</span></span>
