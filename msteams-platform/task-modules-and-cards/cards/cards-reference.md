---
title: Karten-Referenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
localization_priority: Normal
keywords: Referenz zu Bots-Karten
ms.topic: reference
ms.openlocfilehash: 741980ea79dd23659dd2b8a240d767b8292ca251
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994385"
---
# <a name="cards-reference"></a><span data-ttu-id="3a2d2-104">Karten-Referenz</span><span class="sxs-lookup"><span data-stu-id="3a2d2-104">Cards reference</span></span>

<span data-ttu-id="3a2d2-105">Die in diesem Dokument aufgeführten Karten werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-105">The cards listed in this document are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="3a2d2-106">Sie basieren auf Vom Bot Framework (BF) definierten Karten, aber Teams unterstützt nicht alle Bot Framework-Karten und stattdessen wurden einige Teams Karten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-106">They are based on cards defined by the Bot Framework (BF), but Teams does not support all Bot Framework cards and instead some Teams cards have been added.</span></span> <span data-ttu-id="3a2d2-107">Unterschiede werden in den Verweisen in diesem Dokument genannt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-107">Differences are called out in the references in this document.</span></span>

## <a name="card-examples"></a><span data-ttu-id="3a2d2-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="3a2d2-108">Card examples</span></span>

<span data-ttu-id="3a2d2-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="3a2d2-110">Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-110">Code samples are also available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="3a2d2-111">.NET</span><span class="sxs-lookup"><span data-stu-id="3a2d2-111">.NET</span></span>
  * <span data-ttu-id="3a2d2-112">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-112">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="3a2d2-113">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="3a2d2-113">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="3a2d2-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-114">Node.js</span></span>
  * <span data-ttu-id="3a2d2-115">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-115">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="3a2d2-116">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="3a2d2-116">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="types-of-cards"></a><span data-ttu-id="3a2d2-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-117">Types of cards</span></span>

<span data-ttu-id="3a2d2-118">In dieser Tabelle sind die Kartentypen aufgeführt, die Ihnen zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-118">This table shows the types of cards available to you:</span></span>

| <span data-ttu-id="3a2d2-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="3a2d2-119">Card type</span></span> | <span data-ttu-id="3a2d2-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="3a2d2-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-121">Adaptive card</span></span>](#adaptive-card) | <span data-ttu-id="3a2d2-122">Diese Karte ist in hohem Maße anpassbar und kann eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-122">This card is highly customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="3a2d2-123">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-123">Hero card</span></span>](#hero-card) | <span data-ttu-id="3a2d2-124">Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-124">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="3a2d2-125">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-125">List card</span></span>](#list-card) | <span data-ttu-id="3a2d2-126">Diese Karte ist eine Bildlaufliste von Elementen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-126">This card is a scrolling list of items.</span></span> |
| [<span data-ttu-id="3a2d2-127">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-127">Office 365 connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="3a2d2-128">Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-128">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="3a2d2-129">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-129">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="3a2d2-130">Diese Karte stellt dem Benutzer einen Beleg bereit.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-130">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="3a2d2-131">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-131">Signin card</span></span>](#signin-card) | <span data-ttu-id="3a2d2-132">Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-132">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="3a2d2-133">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-133">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="3a2d2-134">Diese Karte enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-134">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="3a2d2-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-135">Card collections</span></span>](#card-collections) | <span data-ttu-id="3a2d2-136">Diese Karten werden verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-136">This cards is used to return multiple items in a single response.</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="3a2d2-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="3a2d2-138">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="3a2d2-138">Inline card images</span></span>

<span data-ttu-id="3a2d2-139">Die Karte kann ein Inlinebild enthalten, indem ein Link zum öffentlich verfügbaren Bild eingeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-139">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="3a2d2-140">Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Netzwerk für die Inhaltsübermittlung (CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-140">For performance purposes, it is highly recommended you host the image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="3a2d2-141">Bilder werden in der Größe nach oben oder unten skaliert, während das Seitenverhältnis beibehalten wird, um den Bildbereich abzudecken.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area.</span></span> <span data-ttu-id="3a2d2-142">Bilder werden dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-142">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="3a2d2-143">Bilder dürfen höchstens 1024×1024 im PNG-, JPEG- oder GIF-Format sein und unterstützen keine animierte GIF-Datei.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-143">Images must be at most 1024×1024, in PNG, JPEG, or GIF format, and do not support animated GIF.</span></span>

| <span data-ttu-id="3a2d2-144">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a2d2-144">Property</span></span> | <span data-ttu-id="3a2d2-145">Typ</span><span class="sxs-lookup"><span data-stu-id="3a2d2-145">Type</span></span>  | <span data-ttu-id="3a2d2-146">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-146">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3a2d2-147">url</span><span class="sxs-lookup"><span data-stu-id="3a2d2-147">url</span></span> | <span data-ttu-id="3a2d2-148">URL</span><span class="sxs-lookup"><span data-stu-id="3a2d2-148">URL</span></span> | <span data-ttu-id="3a2d2-149">HTTPS-URL zum Bild.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-149">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="3a2d2-150">alt</span><span class="sxs-lookup"><span data-stu-id="3a2d2-150">alt</span></span> | <span data-ttu-id="3a2d2-151">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="3a2d2-151">String</span></span> | <span data-ttu-id="3a2d2-152">Beschreibung des Bilds, auf das zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-152">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="3a2d2-153">Wenn eine Karte eine Bild-URL enthält, die eine Umleitung vor dem endgültigen Bild durchläuft, wird die Umleitung in der Bild-URL nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-153">If a card includes an image URL that goes through a redirect before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="3a2d2-154">Dies geschieht für Bilder, die in der öffentlichen Cloud freigegeben sind.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-154">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="3a2d2-155">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-155">Buttons</span></span>

<span data-ttu-id="3a2d2-156">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-156">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="3a2d2-157">Schaltflächentext befindet sich immer in einer zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-157">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="3a2d2-158">Zusätzliche Schaltflächen, die über die von der Karte maximal unterstützte Anzahl hinausgehen, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-158">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="3a2d2-159">Weitere Informationen finden Sie unter [Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-159">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="3a2d2-160">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-160">Card formatting</span></span>

<span data-ttu-id="3a2d2-161">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-161">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="3a2d2-162">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-162">Adaptive card</span></span>

<span data-ttu-id="3a2d2-163">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-163">An adaptive card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="3a2d2-164">Weitere Informationen finden Sie unter [adaptive Karten v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-164">For more information, see [adaptive cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="3a2d2-165">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-165">Support for adaptive cards</span></span>

| <span data-ttu-id="3a2d2-166">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-166">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-167">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-167">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-168">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-168">Connectors</span></span> | <span data-ttu-id="3a2d2-169">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-169">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-170">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-170">✔</span></span> | <span data-ttu-id="3a2d2-171">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-171">✔</span></span> | <span data-ttu-id="3a2d2-172">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-172">✖</span></span> | <span data-ttu-id="3a2d2-173">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-173">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="3a2d2-174">Teams Plattform unterstützt Version 1.2 oder frühere Adaptive Kartenfeatures.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-174">Teams platform supports v1.2 or earlier of adaptive card features.</span></span>
> * <span data-ttu-id="3a2d2-175">Das Formatieren positiver oder destruktiver Aktionen wird in adaptiven Karten auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-175">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="3a2d2-176">Medienelemente werden derzeit in adaptiven Karten auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-176">Media elements are currently not supported in Adaptive Cards on the Teams platform.</span></span>

### <a name="example-of-an-adaptive-card"></a><span data-ttu-id="3a2d2-177">Beispiel für eine adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-177">Example of an adaptive card</span></span>

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

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="3a2d2-179">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-179">Additional information on adaptive cards</span></span>

<span data-ttu-id="3a2d2-180">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-180">Bot Framework reference:</span></span>

* [<span data-ttu-id="3a2d2-181">Adaptive Karten Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-181">Adaptive cards Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="3a2d2-182">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="3a2d2-182">Adaptive card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a><span data-ttu-id="3a2d2-183">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-183">Hero card</span></span>

<span data-ttu-id="3a2d2-184">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-184">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="3a2d2-185">Unterstützung für Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-185">Support for hero cards</span></span>

| <span data-ttu-id="3a2d2-186">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-186">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-187">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-187">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-188">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-188">Connectors</span></span> | <span data-ttu-id="3a2d2-189">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-189">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-190">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-190">✔</span></span> | <span data-ttu-id="3a2d2-191">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-191">✔</span></span> | <span data-ttu-id="3a2d2-192">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-192">✖</span></span> | <span data-ttu-id="3a2d2-193">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-193">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="3a2d2-194">Eigenschaften einer Favoritenkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-194">Properties of a hero card</span></span>

| <span data-ttu-id="3a2d2-195">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a2d2-195">Property</span></span> | <span data-ttu-id="3a2d2-196">Typ</span><span class="sxs-lookup"><span data-stu-id="3a2d2-196">Type</span></span>  | <span data-ttu-id="3a2d2-197">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-197">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3a2d2-198">title</span><span class="sxs-lookup"><span data-stu-id="3a2d2-198">title</span></span> | <span data-ttu-id="3a2d2-199">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-199">Rich text</span></span> | <span data-ttu-id="3a2d2-200">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-200">Title of the card.</span></span> <span data-ttu-id="3a2d2-201">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-201">Maximum 2 lines.</span></span> |
| <span data-ttu-id="3a2d2-202">Untertitel</span><span class="sxs-lookup"><span data-stu-id="3a2d2-202">subtitle</span></span> | <span data-ttu-id="3a2d2-203">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-203">Rich text</span></span> | <span data-ttu-id="3a2d2-204">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-204">Subtitle of the card.</span></span> <span data-ttu-id="3a2d2-205">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-205">Maximum 2 lines.</span></span>|
| <span data-ttu-id="3a2d2-206">text</span><span class="sxs-lookup"><span data-stu-id="3a2d2-206">text</span></span> | <span data-ttu-id="3a2d2-207">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-207">Rich text</span></span> | <span data-ttu-id="3a2d2-208">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-208">Text appears under the subtitle.</span></span> <span data-ttu-id="3a2d2-209">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-209">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="3a2d2-210">Bilder</span><span class="sxs-lookup"><span data-stu-id="3a2d2-210">images</span></span> | <span data-ttu-id="3a2d2-211">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="3a2d2-211">Array of images</span></span> | <span data-ttu-id="3a2d2-212">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-212">Image displayed at the top of the card.</span></span> <span data-ttu-id="3a2d2-213">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-213">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="3a2d2-214">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-214">buttons</span></span> | <span data-ttu-id="3a2d2-215">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-215">Array of action objects</span></span> | <span data-ttu-id="3a2d2-216">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-216">Set of actions applicable to the current card.</span></span> <span data-ttu-id="3a2d2-217">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-217">Maximum 6.</span></span> |
| <span data-ttu-id="3a2d2-218">Tippen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-218">tap</span></span> | <span data-ttu-id="3a2d2-219">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="3a2d2-219">Action object</span></span> | <span data-ttu-id="3a2d2-220">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-220">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="3a2d2-221">Beispiel für eine Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-221">Example of a hero card</span></span>

![Beispiel für eine Hero-Karte](~/assets/images/cards/hero.png)

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

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="3a2d2-223">Zusätzliche Informationen zu Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-223">Additional information on hero cards</span></span>

<span data-ttu-id="3a2d2-224">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-224">Bot Framework reference:</span></span>

* [<span data-ttu-id="3a2d2-225">Hero card Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-225">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="3a2d2-226">Hero-Karte C #</span><span class="sxs-lookup"><span data-stu-id="3a2d2-226">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="3a2d2-227">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-227">List card</span></span>

<span data-ttu-id="3a2d2-228">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgeht, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-228">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="3a2d2-229">Die Listenkarte enthält eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-229">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="3a2d2-230">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-230">Support for list cards</span></span>

| <span data-ttu-id="3a2d2-231">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-231">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-232">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-232">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-233">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-233">Connectors</span></span> | <span data-ttu-id="3a2d2-234">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-234">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-235">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-235">✔</span></span> | <span data-ttu-id="3a2d2-236">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-236">✖</span></span> | <span data-ttu-id="3a2d2-237">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-237">✖</span></span> |<span data-ttu-id="3a2d2-238">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-238">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="3a2d2-239">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-239">Properties of a list card</span></span>

| <span data-ttu-id="3a2d2-240">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a2d2-240">Property</span></span> | <span data-ttu-id="3a2d2-241">Typ</span><span class="sxs-lookup"><span data-stu-id="3a2d2-241">Type</span></span>  | <span data-ttu-id="3a2d2-242">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-242">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3a2d2-243">title</span><span class="sxs-lookup"><span data-stu-id="3a2d2-243">title</span></span> | <span data-ttu-id="3a2d2-244">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-244">Rich text</span></span> | <span data-ttu-id="3a2d2-245">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-245">Title of the card.</span></span> <span data-ttu-id="3a2d2-246">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-246">Maximum 2 lines.</span></span>|
| <span data-ttu-id="3a2d2-247">Elemente</span><span class="sxs-lookup"><span data-stu-id="3a2d2-247">items</span></span> | <span data-ttu-id="3a2d2-248">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-248">Array of list items</span></span> ||
| <span data-ttu-id="3a2d2-249">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-249">buttons</span></span> | <span data-ttu-id="3a2d2-250">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-250">Array of action objects</span></span> | <span data-ttu-id="3a2d2-251">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-251">Set of actions applicable to the current card.</span></span> <span data-ttu-id="3a2d2-252">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-252">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="3a2d2-253">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-253">Example of a list card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="3a2d2-254">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-254">Office 365 connector card</span></span>

<span data-ttu-id="3a2d2-255">Die Office 365 Connectorkarte wird in Teams und nicht in Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-255">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="3a2d2-256">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-256">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="3a2d2-257">Diese Karte kapselt eine Connectorkarte, damit sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-257">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="3a2d2-258">Informationen zu Unterschieden zwischen Connectorkarten und der O365-Karte finden Sie in [den Hinweisen auf der Office 365 Connectorkarte.](#notes-on-the-office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-258">For differences between connector cards and the O365 card, see [Notes on the Office 365 connector card](#notes-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="3a2d2-259">Unterstützung für Office 365 Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-259">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="3a2d2-260">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-260">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-261">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-261">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-262">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-262">Connectors</span></span> | <span data-ttu-id="3a2d2-263">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-263">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-264">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-264">✔</span></span> | <span data-ttu-id="3a2d2-265">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-265">✔</span></span> | <span data-ttu-id="3a2d2-266">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-266">✔</span></span> | <span data-ttu-id="3a2d2-267">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-267">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="3a2d2-268">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-268">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="3a2d2-269">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a2d2-269">Property</span></span> | <span data-ttu-id="3a2d2-270">Typ</span><span class="sxs-lookup"><span data-stu-id="3a2d2-270">Type</span></span>  | <span data-ttu-id="3a2d2-271">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-271">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3a2d2-272">title</span><span class="sxs-lookup"><span data-stu-id="3a2d2-272">title</span></span> | <span data-ttu-id="3a2d2-273">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-273">Rich text</span></span> | <span data-ttu-id="3a2d2-274">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-274">Title of the card.</span></span> <span data-ttu-id="3a2d2-275">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-275">Maximum 2 lines.</span></span> |
| <span data-ttu-id="3a2d2-276">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-276">summary</span></span> | <span data-ttu-id="3a2d2-277">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-277">Rich text</span></span> | <span data-ttu-id="3a2d2-278">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-278">Summary of the card.</span></span> <span data-ttu-id="3a2d2-279">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-279">Maximum 2 lines.</span></span> |
| <span data-ttu-id="3a2d2-280">text</span><span class="sxs-lookup"><span data-stu-id="3a2d2-280">text</span></span> | <span data-ttu-id="3a2d2-281">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-281">Rich text</span></span> | <span data-ttu-id="3a2d2-282">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-282">Text appears under the subtitle.</span></span> <span data-ttu-id="3a2d2-283">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-283">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="3a2d2-284">themeColor</span><span class="sxs-lookup"><span data-stu-id="3a2d2-284">themeColor</span></span> | <span data-ttu-id="3a2d2-285">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="3a2d2-285">HEX string</span></span> | <span data-ttu-id="3a2d2-286">Farbe, die die im Anwendungsmanifest bereitgestellte AccentColor überschreibt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-286">Color that overrides the accentColor provided from the application manifest.</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="3a2d2-287">Hinweise auf der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-287">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="3a2d2-288">Office 365 Connectorkarten funktionieren ordnungsgemäß in Microsoft Teams, einschließlich [ActionCard-Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-288">Office 365 connector cards function properly in Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="3a2d2-289">Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten aus einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-289">One important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="3a2d2-290">Für einen Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-290">For a connector, the endpoint receives the card payload through HTTP POST.</span></span>
* <span data-ttu-id="3a2d2-291">Bei einem Bot löst die Aktion eine Aktivität aus, `HttpPOST` `invoke` die nur die Aktions-ID und den Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-291">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="3a2d2-292">Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-292">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="3a2d2-293">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-293">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="3a2d2-294">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-294">All text fields support markdown and HTML.</span></span> <span data-ttu-id="3a2d2-295">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-295">You can control which sections use markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="3a2d2-296">Standardmäßig `markdown` ist auf `true` .</span><span class="sxs-lookup"><span data-stu-id="3a2d2-296">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="3a2d2-297">Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` dies auf `false` fest.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-297">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="3a2d2-298">Wenn Sie die `themeColor` Eigenschaft angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-298">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="3a2d2-299">Um den Renderingstil für `activityImage` anzugeben, können Sie `activityImageType` Folgendes festlegen:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-299">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows:</span></span>

| <span data-ttu-id="3a2d2-300">Wert</span><span class="sxs-lookup"><span data-stu-id="3a2d2-300">Value</span></span> | <span data-ttu-id="3a2d2-301">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-301">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="3a2d2-302">Standard; `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-302">Default; `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="3a2d2-303">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-303">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="3a2d2-304">Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Referenz zu Nachrichtenkarten](/outlook/actionable-messages/card-reference)mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-304">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="3a2d2-305">Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützen, sind:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-305">The only connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="3a2d2-306">`startGroup`immer wie in Teams behandelt `true`</span><span class="sxs-lookup"><span data-stu-id="3a2d2-306">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="3a2d2-307">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-307">Example of an Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="3a2d2-308">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-308">Receipt card</span></span>

<span data-ttu-id="3a2d2-309">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-309">Teams supports receipt card.</span></span> <span data-ttu-id="3a2d2-310">Es handelt sich um eine Karte, die es einem Bot ermöglicht, dem Benutzer einen Beleg bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-310">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="3a2d2-311">Es enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-311">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="3a2d2-312">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-312">Support for receipt cards</span></span>

| <span data-ttu-id="3a2d2-313">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-313">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-314">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-314">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-315">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-315">Connectors</span></span> | <span data-ttu-id="3a2d2-316">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-316">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-317">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-317">✔</span></span> | <span data-ttu-id="3a2d2-318">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-318">✔</span></span> | <span data-ttu-id="3a2d2-319">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-319">✖</span></span> | <span data-ttu-id="3a2d2-320">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-320">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="3a2d2-321">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-321">Example of a receipt card</span></span>

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

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="3a2d2-323">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-323">Additional information on receipt cards</span></span>

<span data-ttu-id="3a2d2-324">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-324">Bot Framework reference:</span></span>

* [<span data-ttu-id="3a2d2-325">Belegkarte Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-325">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="3a2d2-326">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="3a2d2-326">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="3a2d2-327">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-327">Signin card</span></span>

<span data-ttu-id="3a2d2-328">Mit der Anmeldekarte kann ein Bot einen Benutzer auffordern, sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-328">Signin card enables a bot to request a user to sign in.</span></span> <span data-ttu-id="3a2d2-329">Es wird in Teams in einer etwas anderen Form als im Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-329">It is supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="3a2d2-330">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen unterstützt: `signin` und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="3a2d2-330">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="3a2d2-331">Die Anmeldeaktion kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-331">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="3a2d2-332">Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams Authentifizierungsfluss für Bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-332">For more information on authentication, see [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="3a2d2-333">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-333">Support for signin cards</span></span>

| <span data-ttu-id="3a2d2-334">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-334">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-335">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-335">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-336">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-336">Connectors</span></span> | <span data-ttu-id="3a2d2-337">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-337">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-338">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-338">✔</span></span> | <span data-ttu-id="3a2d2-339">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-339">✖</span></span> | <span data-ttu-id="3a2d2-340">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-340">✖</span></span> | <span data-ttu-id="3a2d2-341">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-341">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="3a2d2-342">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-342">Additional information on signin cards</span></span>

<span data-ttu-id="3a2d2-343">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-343">Bot Framework reference:</span></span>

* [<span data-ttu-id="3a2d2-344">Anmeldekarten-Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-344">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="3a2d2-345">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="3a2d2-345">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="3a2d2-346">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-346">Thumbnail card</span></span>

<span data-ttu-id="3a2d2-347">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-347">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="3a2d2-348">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-348">Support for thumbnail cards</span></span>

| <span data-ttu-id="3a2d2-349">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-349">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-350">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-350">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-351">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-351">Connectors</span></span> | <span data-ttu-id="3a2d2-352">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-352">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-353">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-353">✔</span></span> | <span data-ttu-id="3a2d2-354">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-354">✔</span></span> | <span data-ttu-id="3a2d2-355">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-355">✖</span></span> | <span data-ttu-id="3a2d2-356">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-356">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="3a2d2-358">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-358">Properties of a thumbnail card</span></span>

| <span data-ttu-id="3a2d2-359">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a2d2-359">Property</span></span> | <span data-ttu-id="3a2d2-360">Typ</span><span class="sxs-lookup"><span data-stu-id="3a2d2-360">Type</span></span>  | <span data-ttu-id="3a2d2-361">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-361">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3a2d2-362">title</span><span class="sxs-lookup"><span data-stu-id="3a2d2-362">title</span></span> | <span data-ttu-id="3a2d2-363">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-363">Rich text</span></span> | <span data-ttu-id="3a2d2-364">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-364">Title of the card.</span></span> <span data-ttu-id="3a2d2-365">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-365">Maximum 2 lines.</span></span>|
| <span data-ttu-id="3a2d2-366">Untertitel</span><span class="sxs-lookup"><span data-stu-id="3a2d2-366">subtitle</span></span> | <span data-ttu-id="3a2d2-367">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-367">Rich text</span></span> | <span data-ttu-id="3a2d2-368">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-368">Subtitle of the card.</span></span> <span data-ttu-id="3a2d2-369">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-369">Maximum 2 lines.</span></span>|
| <span data-ttu-id="3a2d2-370">text</span><span class="sxs-lookup"><span data-stu-id="3a2d2-370">text</span></span> | <span data-ttu-id="3a2d2-371">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="3a2d2-371">Rich text</span></span> | <span data-ttu-id="3a2d2-372">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-372">Text appears under the subtitle.</span></span> <span data-ttu-id="3a2d2-373">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="3a2d2-373">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="3a2d2-374">Bilder</span><span class="sxs-lookup"><span data-stu-id="3a2d2-374">images</span></span> | <span data-ttu-id="3a2d2-375">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="3a2d2-375">Array of images</span></span> | <span data-ttu-id="3a2d2-376">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-376">Image displayed at the top of the card.</span></span> <span data-ttu-id="3a2d2-377">Seitenverhältnis 1:1 Quadrat.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-377">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="3a2d2-378">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-378">buttons</span></span> | <span data-ttu-id="3a2d2-379">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-379">Array of action objects</span></span> | <span data-ttu-id="3a2d2-380">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-380">Set of actions applicable to the current card.</span></span> <span data-ttu-id="3a2d2-381">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-381">Maximum 6.</span></span> |
| <span data-ttu-id="3a2d2-382">Tippen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-382">tap</span></span> | <span data-ttu-id="3a2d2-383">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="3a2d2-383">Action object</span></span> | <span data-ttu-id="3a2d2-384">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-384">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="3a2d2-385">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-385">Example of a thumbnail card</span></span>

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

### <a name="additional-information"></a><span data-ttu-id="3a2d2-386">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-386">Additional information</span></span>

<span data-ttu-id="3a2d2-387">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-387">Bot Framework reference:</span></span>

* [<span data-ttu-id="3a2d2-388">Miniaturansichtskarte Node.js</span><span class="sxs-lookup"><span data-stu-id="3a2d2-388">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="3a2d2-389">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="3a2d2-389">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="3a2d2-390">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-390">Card collections</span></span>

<span data-ttu-id="3a2d2-391">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-391">Teams supports Card collections.</span></span>

<span data-ttu-id="3a2d2-392">Kartensammlungen enthalten `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="3a2d2-392">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="3a2d2-393">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-393">These collections contain adaptive, hero, or thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="3a2d2-394">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-394">Carousel collection</span></span>

<span data-ttu-id="3a2d2-395">Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-395">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="3a2d2-396">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-396">Support for carousel collections</span></span>

| <span data-ttu-id="3a2d2-397">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-397">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-398">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-398">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-399">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-399">Connectors</span></span> | <span data-ttu-id="3a2d2-400">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-400">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-401">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-401">✔</span></span> | <span data-ttu-id="3a2d2-402">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-402">✖</span></span> | <span data-ttu-id="3a2d2-403">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-403">✖</span></span> | <span data-ttu-id="3a2d2-404">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-404">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="3a2d2-405">Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-405">A carousel can display a maximum of ten cards per message.</span></span>

### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="3a2d2-406">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="3a2d2-406">Properties of a carousel card</span></span>

<span data-ttu-id="3a2d2-407">Die Eigenschaften einer Karussellkarte sind mit denen der Favoriten- und Miniaturansichtskarten identisch.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-407">Properties of a carousel card are same as those of the hero and thumbnail cards.</span></span>

### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="3a2d2-408">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-408">Example of a carousel collection</span></span>

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

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="3a2d2-410">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-410">Syntax for carousel collections</span></span>

<span data-ttu-id="3a2d2-411">`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-411">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

## <a name="list-collection"></a><span data-ttu-id="3a2d2-412">Sammlung auflisten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-412">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="3a2d2-413">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-413">Support for list collections</span></span>

<span data-ttu-id="3a2d2-414">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-414">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="3a2d2-415">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="3a2d2-415">Bots in Teams</span></span> | <span data-ttu-id="3a2d2-416">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-416">Messaging extensions</span></span>  | <span data-ttu-id="3a2d2-417">Connectors</span><span class="sxs-lookup"><span data-stu-id="3a2d2-417">Connectors</span></span> | <span data-ttu-id="3a2d2-418">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3a2d2-418">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="3a2d2-419">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-419">✔</span></span> | <span data-ttu-id="3a2d2-420">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-420">✔</span></span> | <span data-ttu-id="3a2d2-421">✖</span><span class="sxs-lookup"><span data-stu-id="3a2d2-421">✖</span></span> | <span data-ttu-id="3a2d2-422">✔</span><span class="sxs-lookup"><span data-stu-id="3a2d2-422">✔</span></span> |

### <a name="example-of-a-list-collection"></a><span data-ttu-id="3a2d2-423">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="3a2d2-423">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="3a2d2-425">Die Eigenschaften sind die gleichen wie für die Favoriten- oder Miniaturansichtskarte.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-425">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="3a2d2-426">Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-426">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="3a2d2-427">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-427">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="3a2d2-428">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="3a2d2-428">Syntax for list collections</span></span>

<span data-ttu-id="3a2d2-429">`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.</span><span class="sxs-lookup"><span data-stu-id="3a2d2-429">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="3a2d2-430">Karten werden in Teams nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="3a2d2-430">Cards not supported in Teams</span></span>

<span data-ttu-id="3a2d2-431">Die folgenden Karten werden vom Bot Framework implementiert, aber nicht von Teams unterstützt:</span><span class="sxs-lookup"><span data-stu-id="3a2d2-431">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="3a2d2-432">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-432">Animation cards</span></span>
* <span data-ttu-id="3a2d2-433">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-433">Audio cards</span></span>
* <span data-ttu-id="3a2d2-434">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="3a2d2-434">Video cards</span></span>
