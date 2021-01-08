---
title: Kartenreferenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams zur Verfügung stehen
keywords: Referenz zu Bots-Karten
ms.openlocfilehash: 22a4faa932173387cbefe900e30106d063c49e50
ms.sourcegitcommit: 5739245903278d521ec920427248b6b48676e637
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "49778394"
---
# <a name="cards-reference"></a><span data-ttu-id="863e8-104">Kartenreferenz</span><span class="sxs-lookup"><span data-stu-id="863e8-104">Cards Reference</span></span>

<span data-ttu-id="863e8-105">Die in diesem Abschnitt aufgeführten Karten werden in Bots für Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-105">The cards listed in this section are supported in bots for Teams.</span></span> <span data-ttu-id="863e8-106">Sie basieren auf Karten, die vom Bot Framework definiert werden, teams unterstützt jedoch nicht alle Bot Framework-Karten und hat eigene Karten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="863e8-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="863e8-107">Unterschiede werden in den folgenden Verweisen genannt.</span><span class="sxs-lookup"><span data-stu-id="863e8-107">Differences are called out in the references below.</span></span>

## <a name="card-examples"></a><span data-ttu-id="863e8-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="863e8-108">Card examples</span></span>

<span data-ttu-id="863e8-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK (v3).</span><span class="sxs-lookup"><span data-stu-id="863e8-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="863e8-110">Es sind auch Codebeispiele im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="863e8-110">There are also code samples available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="863e8-111">.NET</span><span class="sxs-lookup"><span data-stu-id="863e8-111">.NET</span></span>
  * [<span data-ttu-id="863e8-112">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="863e8-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="863e8-113">Beispielcode für Karten (Bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="863e8-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="863e8-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="863e8-114">Node.js</span></span>
  * [<span data-ttu-id="863e8-115">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="863e8-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="863e8-116">Beispielcode für Karten (Bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="863e8-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="863e8-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="863e8-117">Types of cards</span></span>

<span data-ttu-id="863e8-118">In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="863e8-118">This table shows the types of cards available to you.</span></span>

| <span data-ttu-id="863e8-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="863e8-119">Card Type</span></span> | <span data-ttu-id="863e8-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="863e8-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="863e8-121">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="863e8-122">Hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="863e8-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="863e8-123">Hero Card</span><span class="sxs-lookup"><span data-stu-id="863e8-123">Hero Card</span></span>](#hero-card) | <span data-ttu-id="863e8-124">Enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="863e8-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="863e8-125">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-125">List Card</span></span>](#list-card) | <span data-ttu-id="863e8-126">Eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="863e8-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="863e8-127">Office 365 Connector Card</span><span class="sxs-lookup"><span data-stu-id="863e8-127">Office 365 Connector Card</span></span>](#office-365-connector-card) | <span data-ttu-id="863e8-128">Flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="863e8-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="863e8-129">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-129">Receipt Card</span></span>](#receipt-card) | <span data-ttu-id="863e8-130">Stellt eine Empfangsbestätigung für den Benutzer zur Verf tung.</span><span class="sxs-lookup"><span data-stu-id="863e8-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="863e8-131">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="863e8-131">Signin Card</span></span>](#signin-card) | <span data-ttu-id="863e8-132">Ermöglicht einem Bot die Anforderung, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="863e8-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="863e8-133">Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-133">Thumbnail Card</span></span>](#thumbnail-card) | <span data-ttu-id="863e8-134">Enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="863e8-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="863e8-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-135">Card Collections</span></span>](#card-collections) | <span data-ttu-id="863e8-136">Wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzukehren</span><span class="sxs-lookup"><span data-stu-id="863e8-136">Used to return multiple items in a single response</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="863e8-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="863e8-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="863e8-138">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="863e8-138">Inline card images</span></span>

<span data-ttu-id="863e8-139">Ihre Karte kann ein Inlinebild enthalten, indem sie einen Link zu Ihrem öffentlich verfügbaren Bild enthält.</span><span class="sxs-lookup"><span data-stu-id="863e8-139">Your card can contain an inline image by including a link to your publicly available image.</span></span> <span data-ttu-id="863e8-140">Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Netzwerk zur Inhaltszustellung (Content Delivery Network, CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="863e8-140">For performance purposes we highly recommend you host your image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="863e8-141">Bilder werden nach oben oder unten skaliert, während das Seitenverhältnis beibehalten wird, um den Bildbereich zu abdecken, und dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="863e8-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="863e8-142">Bilder müssen mindestens 1024×1024 im PNG-, JPEG- oder #A0 vorliegen. Animierte GIF wird offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-142">Images must be at most 1024×1024 in PNG, JPEG, or GIF format; animated GIF is not officially supported.</span></span>

| <span data-ttu-id="863e8-143">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="863e8-143">Property</span></span> | <span data-ttu-id="863e8-144">Typ</span><span class="sxs-lookup"><span data-stu-id="863e8-144">Type</span></span>  | <span data-ttu-id="863e8-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="863e8-146">url</span><span class="sxs-lookup"><span data-stu-id="863e8-146">url</span></span> | <span data-ttu-id="863e8-147">URL</span><span class="sxs-lookup"><span data-stu-id="863e8-147">URL</span></span> | <span data-ttu-id="863e8-148">HTTPS-URL zum Bild</span><span class="sxs-lookup"><span data-stu-id="863e8-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="863e8-149">alt</span><span class="sxs-lookup"><span data-stu-id="863e8-149">alt</span></span> | <span data-ttu-id="863e8-150">String</span><span class="sxs-lookup"><span data-stu-id="863e8-150">String</span></span> | <span data-ttu-id="863e8-151">Barrierefreie Beschreibung des Bilds</span><span class="sxs-lookup"><span data-stu-id="863e8-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="863e8-152">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="863e8-152">Buttons</span></span>

<span data-ttu-id="863e8-153">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="863e8-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="863e8-154">Der Text der Schaltfläche befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="863e8-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="863e8-155">Alle zusätzlichen Schaltflächen, die über die maximale Anzahl hinausgehen, die von der Karte unterstützt wird, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="863e8-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="863e8-156">Weitere [Informationen finden Sie unter "Kartenaktionen".](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="863e8-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="863e8-157">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="863e8-157">Card Formatting</span></span>

<span data-ttu-id="863e8-158">Weitere [Informationen zur Textformatierung](~/task-modules-and-cards/cards/cards-format.md) in Karten finden Sie unter Kartenformatierung.</span><span class="sxs-lookup"><span data-stu-id="863e8-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="863e8-159">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="863e8-159">Adaptive card</span></span>

<span data-ttu-id="863e8-160">Eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="863e8-160">A customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="863e8-161">*Siehe* [adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span><span class="sxs-lookup"><span data-stu-id="863e8-161">*See* [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="863e8-162">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="863e8-162">Support for Adaptive cards</span></span>

| <span data-ttu-id="863e8-163">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-163">Bots in Teams</span></span> | <span data-ttu-id="863e8-164">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-164">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-165">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-165">Connectors</span></span> | <span data-ttu-id="863e8-166">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-166">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-167">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-167">✔</span></span> | <span data-ttu-id="863e8-168">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-168">✔</span></span> | <span data-ttu-id="863e8-169">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-169">✖</span></span> | <span data-ttu-id="863e8-170">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-170">✔</span></span> |
|

> [!NOTE]
> * <span data-ttu-id="863e8-171">Die Plattform Teams unterstützt Version 1.2 oder früher von Features für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="863e8-171">Teams platform supports v1.2 or earlier of Adaptive card features.</span></span>
> * <span data-ttu-id="863e8-172">Medienelemente werden derzeit in der adaptiven Karte v1.2 auf der Plattform Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-172">Media elements are currently not supported in Adaptive card v1.2 on the Teams platform.</span></span>
### <a name="example-adaptive-card"></a><span data-ttu-id="863e8-173">Beispiel für adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="863e8-173">Example Adaptive card</span></span>

![Beispiel für eine adaptive Kartenkarte](~/assets/images/cards/adaptivecard.png)

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

#### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="863e8-175">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="863e8-175">For more information on Adaptive cards</span></span>

* [<span data-ttu-id="863e8-176">Adaptive Karten – Übersicht</span><span class="sxs-lookup"><span data-stu-id="863e8-176">Adaptive Cards Overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="863e8-177">Aktionen für adaptive Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-177">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="863e8-178">Herokarte</span><span class="sxs-lookup"><span data-stu-id="863e8-178">Hero card</span></span>

<span data-ttu-id="863e8-179">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="863e8-179">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="863e8-180">Unterstützung für Herokarten</span><span class="sxs-lookup"><span data-stu-id="863e8-180">Support for Hero cards</span></span>

| <span data-ttu-id="863e8-181">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-181">Bots in Teams</span></span> | <span data-ttu-id="863e8-182">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-182">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-183">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-183">Connectors</span></span> | <span data-ttu-id="863e8-184">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-184">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-185">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-185">✔</span></span> | <span data-ttu-id="863e8-186">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-186">✔</span></span> | <span data-ttu-id="863e8-187">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-187">✖</span></span> | <span data-ttu-id="863e8-188">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-188">✔</span></span> |
|

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="863e8-189">Eigenschaften einer Herokarte</span><span class="sxs-lookup"><span data-stu-id="863e8-189">Properties of a Hero card</span></span>

| <span data-ttu-id="863e8-190">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="863e8-190">Property</span></span> | <span data-ttu-id="863e8-191">Typ</span><span class="sxs-lookup"><span data-stu-id="863e8-191">Type</span></span>  | <span data-ttu-id="863e8-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-192">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="863e8-193">title</span><span class="sxs-lookup"><span data-stu-id="863e8-193">title</span></span> | <span data-ttu-id="863e8-194">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-194">Rich text</span></span> | <span data-ttu-id="863e8-195">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-195">Title of the card.</span></span> <span data-ttu-id="863e8-196">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-196">Maximum 2 lines.</span></span> |
| <span data-ttu-id="863e8-197">subtitle</span><span class="sxs-lookup"><span data-stu-id="863e8-197">subtitle</span></span> | <span data-ttu-id="863e8-198">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-198">Rich text</span></span> | <span data-ttu-id="863e8-199">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-199">Subtitle of the card.</span></span> <span data-ttu-id="863e8-200">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-200">Maximum 2 lines.</span></span>|
| <span data-ttu-id="863e8-201">text</span><span class="sxs-lookup"><span data-stu-id="863e8-201">text</span></span> | <span data-ttu-id="863e8-202">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-202">Rich text</span></span> | <span data-ttu-id="863e8-203">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="863e8-203">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="863e8-204">images</span><span class="sxs-lookup"><span data-stu-id="863e8-204">images</span></span> | <span data-ttu-id="863e8-205">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="863e8-205">Array of images</span></span> | <span data-ttu-id="863e8-206">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="863e8-206">Image displayed at top of card.</span></span> <span data-ttu-id="863e8-207">Seitenverhältnis 16:9</span><span class="sxs-lookup"><span data-stu-id="863e8-207">Aspect ratio 16:9</span></span> |
| <span data-ttu-id="863e8-208">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="863e8-208">buttons</span></span> | <span data-ttu-id="863e8-209">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="863e8-209">Array of action objects</span></span> | <span data-ttu-id="863e8-210">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="863e8-210">Set of actions applicable to the current card.</span></span> <span data-ttu-id="863e8-211">Maximal 6</span><span class="sxs-lookup"><span data-stu-id="863e8-211">Maximum 6</span></span> |
| <span data-ttu-id="863e8-212">Tippen</span><span class="sxs-lookup"><span data-stu-id="863e8-212">tap</span></span> | <span data-ttu-id="863e8-213">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="863e8-213">Action object</span></span> | <span data-ttu-id="863e8-214">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="863e8-214">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-hero-card"></a><span data-ttu-id="863e8-215">Beispiel für Eine Herokarte</span><span class="sxs-lookup"><span data-stu-id="863e8-215">Example Hero card</span></span>

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

### <a name="for-more-information-on-hero-cards"></a><span data-ttu-id="863e8-217">Weitere Informationen zu Herokarten</span><span class="sxs-lookup"><span data-stu-id="863e8-217">For more information on Hero cards</span></span>

<span data-ttu-id="863e8-218">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="863e8-218">Bot Framework reference:</span></span>

* [<span data-ttu-id="863e8-219">Hero card Node</span><span class="sxs-lookup"><span data-stu-id="863e8-219">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="863e8-220">#A0 C #</span><span class="sxs-lookup"><span data-stu-id="863e8-220">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="863e8-221">Listenkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-221">List card</span></span>

<span data-ttu-id="863e8-222">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen zu bieten, die über das hinausgehen, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="863e8-222">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="863e8-223">Die Listenkarte bietet eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="863e8-223">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="863e8-224">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="863e8-224">Support for List cards</span></span>

| <span data-ttu-id="863e8-225">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-225">Bots in Teams</span></span> | <span data-ttu-id="863e8-226">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-226">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-227">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-227">Connectors</span></span> | <span data-ttu-id="863e8-228">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-228">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-229">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-229">✔</span></span> | <span data-ttu-id="863e8-230">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-230">✖</span></span> | <span data-ttu-id="863e8-231">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-231">✖</span></span> |<span data-ttu-id="863e8-232">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-232">✔</span></span> |
|

### <a name="properties-of-a-list-card"></a><span data-ttu-id="863e8-233">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-233">Properties of a List card</span></span>

| <span data-ttu-id="863e8-234">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="863e8-234">Property</span></span> | <span data-ttu-id="863e8-235">Typ</span><span class="sxs-lookup"><span data-stu-id="863e8-235">Type</span></span>  | <span data-ttu-id="863e8-236">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-236">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="863e8-237">title</span><span class="sxs-lookup"><span data-stu-id="863e8-237">title</span></span> | <span data-ttu-id="863e8-238">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-238">Rich text</span></span> | <span data-ttu-id="863e8-239">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-239">Title of the card.</span></span> <span data-ttu-id="863e8-240">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-240">Maximum 2 lines.</span></span>|
| <span data-ttu-id="863e8-241">items</span><span class="sxs-lookup"><span data-stu-id="863e8-241">items</span></span> | <span data-ttu-id="863e8-242">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="863e8-242">Array of list items</span></span>  ||
| <span data-ttu-id="863e8-243">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="863e8-243">buttons</span></span> | <span data-ttu-id="863e8-244">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="863e8-244">Array of action objects</span></span> | <span data-ttu-id="863e8-245">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="863e8-245">Set of actions applicable to the current card.</span></span> <span data-ttu-id="863e8-246">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="863e8-246">Maximum 6.</span></span> |

### <a name="example-list-card"></a><span data-ttu-id="863e8-247">Beispielkarte für Listen</span><span class="sxs-lookup"><span data-stu-id="863e8-247">Example List card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="863e8-248">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-248">Office 365 connector card</span></span>

<span data-ttu-id="863e8-249">Unterstützt in Teams, nicht in Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="863e8-249">Supported in Teams, not in Bot Framework.</span></span>

<span data-ttu-id="863e8-250">Die Office 365-Connectorkarte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="863e8-250">The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="863e8-251">Diese Karte kapselt eine Connectorkarte, damit sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="863e8-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="863e8-252">Im Abschnitt "Hinweise" finden Sie Unterschiede zwischen Connectorkarten und der O365-Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="863e8-253">Unterstützung für Office 365-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="863e8-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="863e8-254">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-254">Bots in Teams</span></span> | <span data-ttu-id="863e8-255">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-255">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-256">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-256">Connectors</span></span> | <span data-ttu-id="863e8-257">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-258">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-258">✔</span></span> | <span data-ttu-id="863e8-259">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-259">✔</span></span> | <span data-ttu-id="863e8-260">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-260">✔</span></span> | <span data-ttu-id="863e8-261">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-261">✖</span></span> |
|

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="863e8-262">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="863e8-263">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="863e8-263">Property</span></span> | <span data-ttu-id="863e8-264">Typ</span><span class="sxs-lookup"><span data-stu-id="863e8-264">Type</span></span>  | <span data-ttu-id="863e8-265">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="863e8-266">title</span><span class="sxs-lookup"><span data-stu-id="863e8-266">title</span></span> | <span data-ttu-id="863e8-267">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-267">Rich text</span></span> | <span data-ttu-id="863e8-268">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-268">Title of the card.</span></span> <span data-ttu-id="863e8-269">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-269">Maximum 2 lines.</span></span> |
| <span data-ttu-id="863e8-270">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="863e8-270">summary</span></span> | <span data-ttu-id="863e8-271">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-271">Rich text</span></span> | <span data-ttu-id="863e8-272">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-272">Summary of the card.</span></span> <span data-ttu-id="863e8-273">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-273">Maximum 2 lines.</span></span> |
| <span data-ttu-id="863e8-274">text</span><span class="sxs-lookup"><span data-stu-id="863e8-274">text</span></span> | <span data-ttu-id="863e8-275">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-275">Rich text</span></span> | <span data-ttu-id="863e8-276">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="863e8-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="863e8-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="863e8-277">themeColor</span></span> | <span data-ttu-id="863e8-278">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="863e8-278">HEX string</span></span> | <span data-ttu-id="863e8-279">Farbe, die die vom Anwendungsmanifest bereitgestellte AccentColor überschreibt</span><span class="sxs-lookup"><span data-stu-id="863e8-279">color that overrides the accentColor provided from the application manifest</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="863e8-280">Hinweise auf der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="863e8-281">Office 365 -Connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="863e8-281">Office 365 Connector cards function properly on Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="863e8-282">Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten von einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="863e8-282">One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="863e8-283">Bei einem Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="863e8-283">For a Connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="863e8-284">Bei einem Bot löst die Aktion eine Aktivität aus, die nur die Aktions-ID und den `HttpPOST` `invoke` Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="863e8-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="863e8-285">Jede Connectorkarte kann maximal 10 Abschnitte anzeigen, und jeder Abschnitt kann maximal 5 Bilder und 5 Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="863e8-285">Each Connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="863e8-286">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="863e8-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="863e8-287">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="863e8-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="863e8-288">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie `markdown` die Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="863e8-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="863e8-289">Standardmäßig ist der Standardwert auf ; wenn Sie stattdessen `markdown` `true` HTML verwenden möchten, legen Sie diesen auf `markdown` . `false`</span><span class="sxs-lookup"><span data-stu-id="863e8-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="863e8-290">Wenn Sie die Eigenschaft `themeColor` angeben, überschreibt sie die Eigenschaft im `accentColor` App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="863e8-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="863e8-291">Zum Angeben des Renderingstils für `activityImage` können Sie Folgendes `activityImageType` festlegen.</span><span class="sxs-lookup"><span data-stu-id="863e8-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows.</span></span>

| <span data-ttu-id="863e8-292">Wert</span><span class="sxs-lookup"><span data-stu-id="863e8-292">Value</span></span> | <span data-ttu-id="863e8-293">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="863e8-294">Standard; `activityImage` wird als Kreis zugeschnitten</span><span class="sxs-lookup"><span data-stu-id="863e8-294">Default; `activityImage` will be cropped as a circle</span></span> |
| `article` | <span data-ttu-id="863e8-295">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei</span><span class="sxs-lookup"><span data-stu-id="863e8-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio</span></span> |

<span data-ttu-id="863e8-296">Weitere Informationen zu den Eigenschaften von Connectorkarten finden Sie in der Referenz zur [Aktions-Nachrichtenkarte.](/outlook/actionable-messages/card-reference)</span><span class="sxs-lookup"><span data-stu-id="863e8-296">For all other details about Connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="863e8-297">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:</span><span class="sxs-lookup"><span data-stu-id="863e8-297">The only Connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="863e8-298">`startGroup` (immer wie `true` in Teams behandelt)</span><span class="sxs-lookup"><span data-stu-id="863e8-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a><span data-ttu-id="863e8-299">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-299">Example Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="863e8-300">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-300">Receipt card</span></span>

<span data-ttu-id="863e8-301">Unterstützt in Teams.</span><span class="sxs-lookup"><span data-stu-id="863e8-301">Supported in Teams.</span></span>

<span data-ttu-id="863e8-302">Eine Karte, mit der ein Bot dem Benutzer eine Empfangsbestätigung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="863e8-302">A card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="863e8-303">Sie enthält in der Regel die Liste der Elemente, die in den Beleg, die Steuer- und Gesamtinformationen sowie anderen Text aufgenommen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="863e8-303">It typically contains the list of items to include on the receipt, tax and total information, and other text.</span></span>

### <a name="support-for-receipts-cards"></a><span data-ttu-id="863e8-304">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="863e8-304">Support for Receipts cards</span></span>

| <span data-ttu-id="863e8-305">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-305">Bots in Teams</span></span> | <span data-ttu-id="863e8-306">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-306">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-307">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-307">Connectors</span></span> | <span data-ttu-id="863e8-308">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-309">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-309">✔</span></span> | <span data-ttu-id="863e8-310">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-310">✔</span></span> | <span data-ttu-id="863e8-311">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-311">✖</span></span> | <span data-ttu-id="863e8-312">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-312">✔</span></span> |
|

### <a name="for-more-information-on-receipt-cards"></a><span data-ttu-id="863e8-313">Weitere Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="863e8-313">For more information on Receipt cards</span></span>

<span data-ttu-id="863e8-314">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="863e8-314">Bot Framework reference:</span></span>

* [<span data-ttu-id="863e8-315">Belegkartenknoten</span><span class="sxs-lookup"><span data-stu-id="863e8-315">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="863e8-316">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="863e8-316">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="863e8-317">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="863e8-317">Signin card</span></span>

<span data-ttu-id="863e8-318">Eine Karte, mit der ein Bot anfordern kann, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="863e8-318">A card that enables a bot to request that a user sign in.</span></span> <span data-ttu-id="863e8-319">Wird in Teams in einer etwas anderen Form unterstützt als im Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="863e8-319">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="863e8-320">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot-Framework mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen unterstützt: und `signin` `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="863e8-320">The signin card in Teams is similar to the signin card in the bot framework with the exception that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="863e8-321">Die *Anmeldeaktion* kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="863e8-321">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="863e8-322">Weitere Informationen zur Authentifizierung finden Sie im Thema ["Microsoft Teams-Authentifizierungsfluss](~/bots/how-to/authentication/auth-flow-bot.md) für Bots".</span><span class="sxs-lookup"><span data-stu-id="863e8-322">See the topic [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md) for more details on authentication.</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="863e8-323">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="863e8-323">Support for Signin cards</span></span>

| <span data-ttu-id="863e8-324">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-324">Bots in Teams</span></span> | <span data-ttu-id="863e8-325">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-325">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-326">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-326">Connectors</span></span> | <span data-ttu-id="863e8-327">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-327">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-328">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-328">✔</span></span> | <span data-ttu-id="863e8-329">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-329">✖</span></span> | <span data-ttu-id="863e8-330">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-330">✖</span></span> | <span data-ttu-id="863e8-331">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-331">✔</span></span> |
|

### <a name="for-more-information-on-signin-cards"></a><span data-ttu-id="863e8-332">Weitere Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="863e8-332">For more information on Signin cards</span></span>

<span data-ttu-id="863e8-333">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="863e8-333">Bot Framework reference:</span></span>

* [<span data-ttu-id="863e8-334">Anmeldekartenknoten</span><span class="sxs-lookup"><span data-stu-id="863e8-334">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="863e8-335">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="863e8-335">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="863e8-336">Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-336">Thumbnail card</span></span>

<span data-ttu-id="863e8-337">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="863e8-337">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="863e8-338">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="863e8-338">Support for Thumbnail cards</span></span>

| <span data-ttu-id="863e8-339">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-339">Bots in Teams</span></span> | <span data-ttu-id="863e8-340">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-340">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-341">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-341">Connectors</span></span> | <span data-ttu-id="863e8-342">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-342">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-343">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-343">✔</span></span> | <span data-ttu-id="863e8-344">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-344">✔</span></span> | <span data-ttu-id="863e8-345">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-345">✖</span></span> | <span data-ttu-id="863e8-346">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-346">✔</span></span> |
|

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="863e8-348">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="863e8-348">Properties of a Thumbnail card</span></span>

| <span data-ttu-id="863e8-349">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="863e8-349">Property</span></span> | <span data-ttu-id="863e8-350">Typ</span><span class="sxs-lookup"><span data-stu-id="863e8-350">Type</span></span>  | <span data-ttu-id="863e8-351">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="863e8-351">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="863e8-352">title</span><span class="sxs-lookup"><span data-stu-id="863e8-352">title</span></span> | <span data-ttu-id="863e8-353">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-353">Rich text</span></span> | <span data-ttu-id="863e8-354">Der Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-354">Title of the card.</span></span> <span data-ttu-id="863e8-355">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-355">Maximum 2 lines.</span></span>|
| <span data-ttu-id="863e8-356">subtitle</span><span class="sxs-lookup"><span data-stu-id="863e8-356">subtitle</span></span> | <span data-ttu-id="863e8-357">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-357">Rich text</span></span> | <span data-ttu-id="863e8-358">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="863e8-358">Subtitle of the card.</span></span> <span data-ttu-id="863e8-359">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="863e8-359">Maximum 2 lines.</span></span>|
| <span data-ttu-id="863e8-360">text</span><span class="sxs-lookup"><span data-stu-id="863e8-360">text</span></span> | <span data-ttu-id="863e8-361">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="863e8-361">Rich text</span></span> | <span data-ttu-id="863e8-362">Text wird direkt unterhalb des Untertitels angezeigt. Informationen [zu Formatierungsoptionen finden](~/task-modules-and-cards/cards/cards-format.md) Sie unter Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="863e8-362">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="863e8-363">images</span><span class="sxs-lookup"><span data-stu-id="863e8-363">images</span></span> | <span data-ttu-id="863e8-364">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="863e8-364">Array of images</span></span> | <span data-ttu-id="863e8-365">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="863e8-365">Image displayed at top of card.</span></span> <span data-ttu-id="863e8-366">Seitenverhältnis 1:1 (Quadrat)</span><span class="sxs-lookup"><span data-stu-id="863e8-366">Aspect ratio 1:1 (square)</span></span> |
| <span data-ttu-id="863e8-367">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="863e8-367">buttons</span></span> | <span data-ttu-id="863e8-368">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="863e8-368">Array of action objects</span></span> | <span data-ttu-id="863e8-369">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="863e8-369">Set of actions applicable to the current card.</span></span> <span data-ttu-id="863e8-370">Maximal 6</span><span class="sxs-lookup"><span data-stu-id="863e8-370">Maximum 6</span></span> |
| <span data-ttu-id="863e8-371">Tippen</span><span class="sxs-lookup"><span data-stu-id="863e8-371">tap</span></span> | <span data-ttu-id="863e8-372">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="863e8-372">Action object</span></span> | <span data-ttu-id="863e8-373">Diese Aktion wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="863e8-373">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-thumbnail-card"></a><span data-ttu-id="863e8-374">Beispiel für Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-374">Example Thumbnail card</span></span>

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

### <a name="for-more-information"></a><span data-ttu-id="863e8-375">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="863e8-375">For more information</span></span>

<span data-ttu-id="863e8-376">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="863e8-376">Bot Framework reference:</span></span>

* [<span data-ttu-id="863e8-377">Knoten der Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-377">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="863e8-378">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="863e8-378">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="863e8-379">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-379">Card collections</span></span>

<span data-ttu-id="863e8-380">Kartensammlungen werden in Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-380">Card collections are supported in Teams.</span></span>

<span data-ttu-id="863e8-381">Kartensammlungen: `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="863e8-381">Card collections: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="863e8-382">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="863e8-382">These collections contain Adaptive, Hero, or Thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="863e8-383">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="863e8-383">Carousel collection</span></span>

<span data-ttu-id="863e8-384">Das [Karusselllayout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) zeigt ein Karussell von Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="863e8-384">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="863e8-385">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-385">Support for Carousel collections</span></span>

| <span data-ttu-id="863e8-386">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-386">Bots in Teams</span></span> | <span data-ttu-id="863e8-387">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-387">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-388">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-388">Connectors</span></span> | <span data-ttu-id="863e8-389">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-389">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-390">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-390">✔</span></span> | <span data-ttu-id="863e8-391">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-391">✖</span></span> | <span data-ttu-id="863e8-392">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-392">✖</span></span> | <span data-ttu-id="863e8-393">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-393">✔</span></span> |
|

> [!NOTE]
> <span data-ttu-id="863e8-394">Ein Karussell kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="863e8-394">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="863e8-395">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="863e8-395">Properties of a Carousel card</span></span>

<span data-ttu-id="863e8-396">Die Eigenschaften einer Karussellkarte sind mit denen der Hero- und Miniaturansichtskarten identisch.</span><span class="sxs-lookup"><span data-stu-id="863e8-396">Properties of a Carousel card are same as those of the Hero and Thumbnail cards.</span></span>

### <a name="example-carousel-collection"></a><span data-ttu-id="863e8-397">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="863e8-397">Example Carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="863e8-399">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-399">Syntax for Carousel collections</span></span>

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a><span data-ttu-id="863e8-400">Listensammlung</span><span class="sxs-lookup"><span data-stu-id="863e8-400">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="863e8-401">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-401">Support for List collections</span></span>

<span data-ttu-id="863e8-402">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="863e8-402">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="863e8-403">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="863e8-403">Bots in Teams</span></span> | <span data-ttu-id="863e8-404">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="863e8-404">Messaging Extensions</span></span>  | <span data-ttu-id="863e8-405">Connectors</span><span class="sxs-lookup"><span data-stu-id="863e8-405">Connectors</span></span> | <span data-ttu-id="863e8-406">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="863e8-406">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="863e8-407">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-407">✔</span></span> | <span data-ttu-id="863e8-408">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-408">✔</span></span> | <span data-ttu-id="863e8-409">✖</span><span class="sxs-lookup"><span data-stu-id="863e8-409">✖</span></span> | <span data-ttu-id="863e8-410">✔</span><span class="sxs-lookup"><span data-stu-id="863e8-410">✔</span></span> |
|

### <a name="example-list-collection"></a><span data-ttu-id="863e8-411">Beispielliste (Auflistung)</span><span class="sxs-lookup"><span data-stu-id="863e8-411">Example List collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="863e8-413">Die Eigenschaften sind mit den Eigenschaften für die Hero- oder Miniaturansichtskarte identisch.</span><span class="sxs-lookup"><span data-stu-id="863e8-413">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="863e8-414">Eine Liste kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="863e8-414">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="863e8-415">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-415">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="863e8-416">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="863e8-416">Syntax for List collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="863e8-417">In Teams nicht unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="863e8-417">Cards not supported in Teams</span></span>

<span data-ttu-id="863e8-418">Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch NICHT von Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="863e8-418">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="863e8-419">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="863e8-419">Animation cards</span></span>
* <span data-ttu-id="863e8-420">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="863e8-420">Audio cards</span></span>
* <span data-ttu-id="863e8-421">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="863e8-421">Video cards</span></span>
