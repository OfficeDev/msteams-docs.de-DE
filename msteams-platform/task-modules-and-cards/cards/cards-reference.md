---
title: Karten Referenz
description: Beschreibt alle Karten-und Karten Aktionen, die Bots in Microsoft Teams zur Verfügung stehen.
keywords: Referenz zu Bots-Karten
ms.openlocfilehash: 76b9cb7e2508d300deb2e3cd4f392fdb9850062d
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674286"
---
# <a name="cards-reference"></a><span data-ttu-id="11969-104">Karten Referenz</span><span class="sxs-lookup"><span data-stu-id="11969-104">Cards Reference</span></span>

<span data-ttu-id="11969-105">Die in diesem Abschnitt aufgelisteten Karten werden in Bots für Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-105">The cards listed in this section are supported in bots for Teams.</span></span> <span data-ttu-id="11969-106">Sie basieren auf Karten, die durch das bot-Framework definiert wurden, aber Teams unterstützen nicht alle bot-Framework-Karten und haben eigene hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="11969-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span> <span data-ttu-id="11969-107">Unterschiede werden in den nachstehenden verweisen aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="11969-107">Differences are called out in the references below.</span></span>

## <a name="card-examples"></a><span data-ttu-id="11969-108">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="11969-108">Card examples</span></span>

<span data-ttu-id="11969-109">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das bot Builder SDK (v3).</span><span class="sxs-lookup"><span data-stu-id="11969-109">You can find additional information on how to use cards in the documentation for the Bot Builder SDK (v3).</span></span> <span data-ttu-id="11969-110">Im Microsoft/BotBuilder-Samples-Repository auf GitHub sind auch Codebeispiele verfügbar.</span><span class="sxs-lookup"><span data-stu-id="11969-110">There are also code samples available in the Microsoft/BotBuilder-Samples repository on GitHub.</span></span>

* <span data-ttu-id="11969-111">.NET</span><span class="sxs-lookup"><span data-stu-id="11969-111">.NET</span></span>
  * [<span data-ttu-id="11969-112">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="11969-112">Add cards as attachments to messages</span></span>](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [<span data-ttu-id="11969-113">Kartenbeispiel Code (bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="11969-113">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* <span data-ttu-id="11969-114">Node.js</span><span class="sxs-lookup"><span data-stu-id="11969-114">Node.js</span></span>
  * [<span data-ttu-id="11969-115">Hinzufügen von Karten als Anlagen zu Nachrichten</span><span class="sxs-lookup"><span data-stu-id="11969-115">Add cards as attachments to messages</span></span>](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [<span data-ttu-id="11969-116">Kartenbeispiel Code (bot Builder v3)</span><span class="sxs-lookup"><span data-stu-id="11969-116">Cards sample code (Bot Builder v3)</span></span>](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a><span data-ttu-id="11969-117">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="11969-117">Types of cards</span></span>

<span data-ttu-id="11969-118">In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="11969-118">This table shows the types of cards available to you.</span></span>

| <span data-ttu-id="11969-119">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="11969-119">Card Type</span></span> | <span data-ttu-id="11969-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-120">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="11969-121">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="11969-121">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="11969-122">Hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="11969-122">Highly customizable card that can contain any combination of text, speech, images, buttons and input fields.</span></span> |
| [<span data-ttu-id="11969-123">Hero Card</span><span class="sxs-lookup"><span data-stu-id="11969-123">Hero Card</span></span>](#hero-card) | <span data-ttu-id="11969-124">Enthält normalerweise ein einzelnes großes Bild, eine oder mehrere Schaltflächen und einen kleinen Textumfang.</span><span class="sxs-lookup"><span data-stu-id="11969-124">Typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="11969-125">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="11969-125">List Card</span></span>](#list-card) | <span data-ttu-id="11969-126">Eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="11969-126">A scrolling list of items.</span></span> |
| [<span data-ttu-id="11969-127">Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="11969-127">Office 365 Connector Card</span></span>](#office-365-connector-card) | <span data-ttu-id="11969-128">Flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="11969-128">Flexible layout with multiple sections, fields, images and actions.</span></span> |
| [<span data-ttu-id="11969-129">Bestätigungs Karte</span><span class="sxs-lookup"><span data-stu-id="11969-129">Receipt Card</span></span>](#receipt-card) | <span data-ttu-id="11969-130">Stellt dem Benutzer eine Quittung zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="11969-130">Provides a receipt to the user.</span></span> |
| [<span data-ttu-id="11969-131">SignIn-Karte</span><span class="sxs-lookup"><span data-stu-id="11969-131">Signin Card</span></span>](#signin-card) | <span data-ttu-id="11969-132">Ermöglicht einem bot, das Anmelden eines Benutzers anzufordern.</span><span class="sxs-lookup"><span data-stu-id="11969-132">Enables a bot to request that a user sign in.</span></span> |
| [<span data-ttu-id="11969-133">Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="11969-133">Thumbnail Card</span></span>](#thumbnail-card) | <span data-ttu-id="11969-134">Enthält normalerweise ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="11969-134">Typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="11969-135">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="11969-135">Card Collections</span></span>](#card-collections) | <span data-ttu-id="11969-136">Wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="11969-136">Used to return multiple items in a single response</span></span> |

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="11969-137">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="11969-137">Common properties for all cards</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="11969-138">Inline Karten Bilder</span><span class="sxs-lookup"><span data-stu-id="11969-138">Inline card images</span></span>

<span data-ttu-id="11969-139">Ihre Karte kann ein Inlinebild enthalten, indem Sie einen Link zu Ihrem öffentlich verfügbaren Bild hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="11969-139">Your card can contain an inline image by including a link to your publically available image.</span></span> <span data-ttu-id="11969-140">Aus Leistungsgründen wird dringend empfohlen, dass Sie Ihr Image in einem öffentlichen Content-Delivery-Netzwerk (CDN) hosten.</span><span class="sxs-lookup"><span data-stu-id="11969-140">For performance purposes we highly recommend you host your image on a public content-delivery network (CDN).</span></span>

<span data-ttu-id="11969-141">Bilder werden in der Größe nach oben oder unten skaliert, wobei das Seitenverhältnis zum Abdecken des Bildbereichs beibehalten und dann vom Center abgeschnitten wurde, um das entsprechende Seitenverhältnis für die Karte zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="11969-141">Images are scaled up or down in size while maintaining the aspect ratio to cover the image area, and then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="11969-142">Bilder müssen im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht offiziell unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-142">Images must be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not officially supported.</span></span>

| <span data-ttu-id="11969-143">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11969-143">Property</span></span> | <span data-ttu-id="11969-144">Typ</span><span class="sxs-lookup"><span data-stu-id="11969-144">Type</span></span>  | <span data-ttu-id="11969-145">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-145">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="11969-146">url</span><span class="sxs-lookup"><span data-stu-id="11969-146">url</span></span> | <span data-ttu-id="11969-147">URL</span><span class="sxs-lookup"><span data-stu-id="11969-147">URL</span></span> | <span data-ttu-id="11969-148">HTTPS-URL zum Bild</span><span class="sxs-lookup"><span data-stu-id="11969-148">HTTPS URL to the image</span></span> |
| <span data-ttu-id="11969-149">alt</span><span class="sxs-lookup"><span data-stu-id="11969-149">alt</span></span> | <span data-ttu-id="11969-150">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="11969-150">String</span></span> | <span data-ttu-id="11969-151">Barrierefreie Beschreibung des Bilds</span><span class="sxs-lookup"><span data-stu-id="11969-151">Accessible description of the image</span></span> |

### <a name="buttons"></a><span data-ttu-id="11969-152">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="11969-152">Buttons</span></span>

<span data-ttu-id="11969-153">Die Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11969-153">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="11969-154">Der Schaltflächentext befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Schaltflächenbreite überschreitet.</span><span class="sxs-lookup"><span data-stu-id="11969-154">Button text is always on a single line and will be truncated if the text exceeds the button width.</span></span> <span data-ttu-id="11969-155">Alle zusätzlichen Schaltflächen jenseits der von der Karte unterstützten Maximalzahl werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11969-155">Any additional buttons beyond the maximum number supported by the card will not be shown.</span></span>

<span data-ttu-id="11969-156">Weitere Informationen finden Sie unter [Karten Aktionen](~/task-modules-and-cards/cards/cards-actions.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-156">See [Card Actions](~/task-modules-and-cards/cards/cards-actions.md) for more information.</span></span>

### <a name="card-formatting"></a><span data-ttu-id="11969-157">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="11969-157">Card Formatting</span></span>

<span data-ttu-id="11969-158">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-158">See [Card Formatting](~/task-modules-and-cards/cards/cards-format.md) for more information on text formatting in cards.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="11969-159">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="11969-159">Adaptive card</span></span>

> [!NOTE]
> <span data-ttu-id="11969-160">Nur Version 1,0 von adaptiven Karten wird für alle Benutzer unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-160">Only version 1.0 of Adaptive Cards is supported for all users.</span></span> <span data-ttu-id="11969-161">Version 1,2 ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="11969-161">Version 1.2 is currently available only in Developer Preview</span></span>

<span data-ttu-id="11969-162">Eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="11969-162">A customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="11969-163">Unterstützung für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="11969-163">Support for Adaptive cards</span></span>

| <span data-ttu-id="11969-164">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-164">Bots in Teams</span></span> | <span data-ttu-id="11969-165">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-165">Messaging Extensions</span></span>  | <span data-ttu-id="11969-166">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-166">Connectors</span></span> | <span data-ttu-id="11969-167">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-167">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-168">✔</span><span class="sxs-lookup"><span data-stu-id="11969-168">✔</span></span> | <span data-ttu-id="11969-169">✔</span><span class="sxs-lookup"><span data-stu-id="11969-169">✔</span></span> | <span data-ttu-id="11969-170">✖</span><span class="sxs-lookup"><span data-stu-id="11969-170">✖</span></span> | <span data-ttu-id="11969-171">✔</span><span class="sxs-lookup"><span data-stu-id="11969-171">✔</span></span> |
|

### <a name="example-adaptive-card"></a><span data-ttu-id="11969-172">Beispiel für eine Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="11969-172">Example Adaptive card</span></span>

![Beispiel für eine Adaptive Karten Karte](~/assets/images/cards/adaptivecard.png)

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

#### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="11969-174">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="11969-174">For more information on Adaptive cards</span></span>

* [<span data-ttu-id="11969-175">Übersicht über Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="11969-175">Adaptive Cards Overview</span></span>](/adaptive-cards/)
* [<span data-ttu-id="11969-176">Adaptive Karten Aktionen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-176">Adaptive card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a><span data-ttu-id="11969-177">Hero Card</span><span class="sxs-lookup"><span data-stu-id="11969-177">Hero card</span></span>

<span data-ttu-id="11969-178">Eine Karte, die normalerweise ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="11969-178">A card that typically contains a single large image, one or more buttons and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="11969-179">Unterstützung für Hero Cards</span><span class="sxs-lookup"><span data-stu-id="11969-179">Support for Hero cards</span></span>

| <span data-ttu-id="11969-180">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-180">Bots in Teams</span></span> | <span data-ttu-id="11969-181">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-181">Messaging Extensions</span></span>  | <span data-ttu-id="11969-182">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-182">Connectors</span></span> | <span data-ttu-id="11969-183">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-183">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-184">✔</span><span class="sxs-lookup"><span data-stu-id="11969-184">✔</span></span> | <span data-ttu-id="11969-185">✔</span><span class="sxs-lookup"><span data-stu-id="11969-185">✔</span></span> | <span data-ttu-id="11969-186">✖</span><span class="sxs-lookup"><span data-stu-id="11969-186">✖</span></span> | <span data-ttu-id="11969-187">✔</span><span class="sxs-lookup"><span data-stu-id="11969-187">✔</span></span> |
|

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="11969-188">Eigenschaften einer Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="11969-188">Properties of a Hero card</span></span>

| <span data-ttu-id="11969-189">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11969-189">Property</span></span> | <span data-ttu-id="11969-190">Typ</span><span class="sxs-lookup"><span data-stu-id="11969-190">Type</span></span>  | <span data-ttu-id="11969-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-191">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="11969-192">title</span><span class="sxs-lookup"><span data-stu-id="11969-192">title</span></span> | <span data-ttu-id="11969-193">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-193">Rich text</span></span> | <span data-ttu-id="11969-194">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-194">Title of the card.</span></span> <span data-ttu-id="11969-195">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-195">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-196">unter</span><span class="sxs-lookup"><span data-stu-id="11969-196">subtitle</span></span> | <span data-ttu-id="11969-197">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-197">Rich text</span></span> | <span data-ttu-id="11969-198">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-198">Subtitle of the card.</span></span> <span data-ttu-id="11969-199">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-199">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-200">text</span><span class="sxs-lookup"><span data-stu-id="11969-200">text</span></span> | <span data-ttu-id="11969-201">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-201">Rich text</span></span> | <span data-ttu-id="11969-202">Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-202">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="11969-203">Bilder</span><span class="sxs-lookup"><span data-stu-id="11969-203">images</span></span> | <span data-ttu-id="11969-204">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="11969-204">Array of images</span></span> | <span data-ttu-id="11969-205">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="11969-205">Image displayed at top of card.</span></span> <span data-ttu-id="11969-206">Seitenverhältnis 16:9</span><span class="sxs-lookup"><span data-stu-id="11969-206">Aspect ratio 16:9</span></span> |
| <span data-ttu-id="11969-207">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="11969-207">buttons</span></span> | <span data-ttu-id="11969-208">Array von Action-Objekten</span><span class="sxs-lookup"><span data-stu-id="11969-208">Array of action objects</span></span> | <span data-ttu-id="11969-209">Eine Gruppe von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="11969-209">Set of actions applicable to the current card.</span></span> <span data-ttu-id="11969-210">Maximal 6</span><span class="sxs-lookup"><span data-stu-id="11969-210">Maximum 6</span></span> |
| <span data-ttu-id="11969-211">Tippen</span><span class="sxs-lookup"><span data-stu-id="11969-211">tap</span></span> | <span data-ttu-id="11969-212">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="11969-212">Action object</span></span> | <span data-ttu-id="11969-213">Diese Aktion wird aktiviert, wenn der Benutzer die Karte selbst anzapft.</span><span class="sxs-lookup"><span data-stu-id="11969-213">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-hero-card"></a><span data-ttu-id="11969-214">Beispiel für Hero Card</span><span class="sxs-lookup"><span data-stu-id="11969-214">Example Hero card</span></span>

![Beispiel für eine Hero Card](~/assets/images/cards/hero.png)

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

### <a name="for-more-information-on-hero-cards"></a><span data-ttu-id="11969-216">Weitere Informationen zu Hero Cards</span><span class="sxs-lookup"><span data-stu-id="11969-216">For more information on Hero cards</span></span>

<span data-ttu-id="11969-217">Bot-Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="11969-217">Bot Framework reference:</span></span>

* [<span data-ttu-id="11969-218">Held-Karten Knoten</span><span class="sxs-lookup"><span data-stu-id="11969-218">Hero card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [<span data-ttu-id="11969-219">Hero Card C #</span><span class="sxs-lookup"><span data-stu-id="11969-219">Hero card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0)

## <a name="list-card"></a><span data-ttu-id="11969-220">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="11969-220">List card</span></span>

<span data-ttu-id="11969-221">Die Listen Karte wurde von Microsoft Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgehen, was die Listen Sammlung bieten kann.</span><span class="sxs-lookup"><span data-stu-id="11969-221">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="11969-222">Die Listen Karte enthält eine Liste mit Elementen im Bildlauf.</span><span class="sxs-lookup"><span data-stu-id="11969-222">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="11969-223">Unterstützung für Listen Karten</span><span class="sxs-lookup"><span data-stu-id="11969-223">Support for List cards</span></span>

| <span data-ttu-id="11969-224">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-224">Bots in Teams</span></span> | <span data-ttu-id="11969-225">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-225">Messaging Extensions</span></span>  | <span data-ttu-id="11969-226">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-226">Connectors</span></span> | <span data-ttu-id="11969-227">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-227">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-228">✔</span><span class="sxs-lookup"><span data-stu-id="11969-228">✔</span></span> | <span data-ttu-id="11969-229">✖</span><span class="sxs-lookup"><span data-stu-id="11969-229">✖</span></span> | <span data-ttu-id="11969-230">✖</span><span class="sxs-lookup"><span data-stu-id="11969-230">✖</span></span> |<span data-ttu-id="11969-231">✔</span><span class="sxs-lookup"><span data-stu-id="11969-231">✔</span></span> |
|

### <a name="properties-of-a-list-card"></a><span data-ttu-id="11969-232">Eigenschaften einer Listen Karte</span><span class="sxs-lookup"><span data-stu-id="11969-232">Properties of a List card</span></span>

| <span data-ttu-id="11969-233">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11969-233">Property</span></span> | <span data-ttu-id="11969-234">Typ</span><span class="sxs-lookup"><span data-stu-id="11969-234">Type</span></span>  | <span data-ttu-id="11969-235">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-235">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="11969-236">title</span><span class="sxs-lookup"><span data-stu-id="11969-236">title</span></span> | <span data-ttu-id="11969-237">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-237">Rich text</span></span> | <span data-ttu-id="11969-238">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-238">Title of the card.</span></span> <span data-ttu-id="11969-239">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-239">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-240">items</span><span class="sxs-lookup"><span data-stu-id="11969-240">items</span></span> | <span data-ttu-id="11969-241">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="11969-241">Array of list items</span></span>  ||
| <span data-ttu-id="11969-242">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="11969-242">buttons</span></span> | <span data-ttu-id="11969-243">Array von Action-Objekten</span><span class="sxs-lookup"><span data-stu-id="11969-243">Array of action objects</span></span> | <span data-ttu-id="11969-244">Eine Gruppe von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="11969-244">Set of actions applicable to the current card.</span></span> <span data-ttu-id="11969-245">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="11969-245">Maximum 6.</span></span> <span data-ttu-id="11969-246">Wird auf mobilen Geräten nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="11969-246">Does not render on mobile.</span></span> |
|

### <a name="example-list-card"></a><span data-ttu-id="11969-247">Beispiel Listen Karte</span><span class="sxs-lookup"><span data-stu-id="11969-247">Example List card</span></span>

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

## <a name="office-365-connector-card"></a><span data-ttu-id="11969-248">Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="11969-248">Office 365 connector card</span></span>

<span data-ttu-id="11969-249">Unterstützt in Microsoft Teams, nicht im bot-Framework.</span><span class="sxs-lookup"><span data-stu-id="11969-249">Supported in Teams, not in Bot Framework.</span></span>

<span data-ttu-id="11969-250">Die Office 365-Anschluss Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="11969-250">The Office 365 Connector card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="11969-251">Diese Karte kapselt eine connectorkarte ein, damit Sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="11969-251">This card encapsulates a connector card so that it can be used by bots.</span></span> <span data-ttu-id="11969-252">Im Abschnitt Hinweise finden Sie Informationen zu den Unterschieden zwischen connectorkarten und der O365-Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-252">See the notes section for differences between connector cards and the O365 card.</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="11969-253">Unterstützung für Office 365-Anschlusskarten</span><span class="sxs-lookup"><span data-stu-id="11969-253">Support for Office 365 connector cards</span></span>

| <span data-ttu-id="11969-254">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-254">Bots in Teams</span></span> | <span data-ttu-id="11969-255">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-255">Messaging Extensions</span></span>  | <span data-ttu-id="11969-256">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-256">Connectors</span></span> | <span data-ttu-id="11969-257">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-257">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-258">✔</span><span class="sxs-lookup"><span data-stu-id="11969-258">✔</span></span> | <span data-ttu-id="11969-259">✔</span><span class="sxs-lookup"><span data-stu-id="11969-259">✔</span></span> | <span data-ttu-id="11969-260">✔</span><span class="sxs-lookup"><span data-stu-id="11969-260">✔</span></span> | <span data-ttu-id="11969-261">✖</span><span class="sxs-lookup"><span data-stu-id="11969-261">✖</span></span> |
|

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="11969-262">Eigenschaften der Office 365-Verbindungskarte</span><span class="sxs-lookup"><span data-stu-id="11969-262">Properties of the Office 365 connector card</span></span>

| <span data-ttu-id="11969-263">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11969-263">Property</span></span> | <span data-ttu-id="11969-264">Typ</span><span class="sxs-lookup"><span data-stu-id="11969-264">Type</span></span>  | <span data-ttu-id="11969-265">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-265">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="11969-266">title</span><span class="sxs-lookup"><span data-stu-id="11969-266">title</span></span> | <span data-ttu-id="11969-267">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-267">Rich text</span></span> | <span data-ttu-id="11969-268">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-268">Title of the card.</span></span> <span data-ttu-id="11969-269">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-269">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-270">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="11969-270">summary</span></span> | <span data-ttu-id="11969-271">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-271">Rich text</span></span> | <span data-ttu-id="11969-272">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-272">Summary of the card.</span></span> <span data-ttu-id="11969-273">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-273">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-274">text</span><span class="sxs-lookup"><span data-stu-id="11969-274">text</span></span> | <span data-ttu-id="11969-275">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-275">Rich text</span></span> | <span data-ttu-id="11969-276">Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-276">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="11969-277">themeColor</span><span class="sxs-lookup"><span data-stu-id="11969-277">themeColor</span></span> | <span data-ttu-id="11969-278">Hex-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="11969-278">HEX string</span></span> | <span data-ttu-id="11969-279">Farbe, die die vom Anwendungsmanifest bereitgestellte accentColor überschreibt</span><span class="sxs-lookup"><span data-stu-id="11969-279">color that overrides the accentColor provided from the application manifest</span></span> |

### <a name="notes-on-the-office-365-connector-card"></a><span data-ttu-id="11969-280">Hinweise auf der Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="11969-280">Notes on the Office 365 connector card</span></span>

<span data-ttu-id="11969-281">Office 365-connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [Action Card-Aktionen](/outlook/actionable-messages/card-reference#actioncard-action).</span><span class="sxs-lookup"><span data-stu-id="11969-281">Office 365 Connector cards function properly on Microsoft Teams, including [ActionCard actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="11969-282">Ein wichtiger Unterschied zwischen der Verwendung von connectorkarten aus einem Konnektor und der Verwendung von Steckkarten in Ihrem bot ist die Handhabung von Karten Aktionen.</span><span class="sxs-lookup"><span data-stu-id="11969-282">One important difference between using Connector cards from a Connector and using Connector cards in your bot is the handling of card actions.</span></span>

* <span data-ttu-id="11969-283">Für einen Connector erhält der Endpunkt die Karten Nutzlast per HTTP-Post.</span><span class="sxs-lookup"><span data-stu-id="11969-283">For a Connector, the endpoint receives the card payload via HTTP POST.</span></span>
* <span data-ttu-id="11969-284">Für einen bot löst die `HttpPOST` Aktion eine `invoke` Aktivität aus, die nur die Aktions-ID und den Textkörper an den bot sendet.</span><span class="sxs-lookup"><span data-stu-id="11969-284">For a bot, the `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>

<span data-ttu-id="11969-285">Jede Verbindungskarte kann maximal 10 Abschnitte anzeigen, und jeder Abschnitt kann maximal 5 Bilder und 5 Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="11969-285">Each Connector card can display a maximum of 10 sections, and each section can contain a maximum of 5 images and 5 actions.</span></span>

> [!NOTE]
> <span data-ttu-id="11969-286">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="11969-286">Any additional sections, images, or actions in a message will not appear.</span></span>

<span data-ttu-id="11969-287">Alle Textfelder unterstützen Abschlag und HTML.</span><span class="sxs-lookup"><span data-stu-id="11969-287">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="11969-288">Sie können steuern, welche Abschnitte "Abschlag" oder "HTML `markdown` " verwenden, indem Sie die Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="11969-288">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="11969-289">Standardmäßig `markdown` ist auf `true`festgelegt; Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` auf `false`fest.</span><span class="sxs-lookup"><span data-stu-id="11969-289">By default, `markdown` is set to `true`; if you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="11969-290">Wenn Sie die `themeColor` Eigenschaft angeben, wird die `accentColor` Eigenschaft im App-Manifest überschrieben.</span><span class="sxs-lookup"><span data-stu-id="11969-290">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="11969-291">Um das Renderingformat für `activityImage`festzulegen, können Sie `activityImageType` Folgendes festlegen.</span><span class="sxs-lookup"><span data-stu-id="11969-291">To specify the rendering style for `activityImage`, you can set `activityImageType` as follows.</span></span>

| <span data-ttu-id="11969-292">Wert</span><span class="sxs-lookup"><span data-stu-id="11969-292">Value</span></span> | <span data-ttu-id="11969-293">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-293">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="11969-294">Standard `activityImage` wird als Kreis abgeschnitten</span><span class="sxs-lookup"><span data-stu-id="11969-294">Default; `activityImage` will be cropped as a circle</span></span> |
| `article` | <span data-ttu-id="11969-295">`activityImage`wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="11969-295">`activityImage` will be displayed as a rectangle and retain its aspect ratio</span></span> |

<span data-ttu-id="11969-296">Weitere Details zu den Eigenschaften von Verbindungskarten finden Sie in der [Referenz zur Nachrichten Karte mit Aktionen](/outlook/actionable-messages/card-reference).</span><span class="sxs-lookup"><span data-stu-id="11969-296">For all other details about Connector card properties, see the [Actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="11969-297">Die einzigen Verbindungskarten Eigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind folgende:</span><span class="sxs-lookup"><span data-stu-id="11969-297">The only Connector card properties that Microsoft Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="11969-298">`startGroup`(immer wie `true` in Teams behandelt)</span><span class="sxs-lookup"><span data-stu-id="11969-298">`startGroup` (always treated as `true` in Teams)</span></span>
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a><span data-ttu-id="11969-299">Beispiel Office 365 Connector-Karte</span><span class="sxs-lookup"><span data-stu-id="11969-299">Example Office 365 connector card</span></span>

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

## <a name="receipt-card"></a><span data-ttu-id="11969-300">Bestätigungs Karte</span><span class="sxs-lookup"><span data-stu-id="11969-300">Receipt card</span></span>

<span data-ttu-id="11969-301">In Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-301">Supported in Teams.</span></span>

<span data-ttu-id="11969-302">Eine Karte, mit der ein bot dem Benutzer eine Quittung zur Verfügung stellen kann.</span><span class="sxs-lookup"><span data-stu-id="11969-302">A card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="11969-303">Sie enthält normalerweise die Liste der Elemente, die in die Empfangs-, Steuer-und Gesamtinformationen sowie anderen Text eingeschlossen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="11969-303">It typically contains the list of items to include on the receipt, tax and total information, and other text.</span></span>

### <a name="support-for-receipts-cards"></a><span data-ttu-id="11969-304">Unterstützung für Empfangs Karten</span><span class="sxs-lookup"><span data-stu-id="11969-304">Support for Receipts cards</span></span>

| <span data-ttu-id="11969-305">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-305">Bots in Teams</span></span> | <span data-ttu-id="11969-306">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-306">Messaging Extensions</span></span>  | <span data-ttu-id="11969-307">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-307">Connectors</span></span> | <span data-ttu-id="11969-308">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-308">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-309">✔</span><span class="sxs-lookup"><span data-stu-id="11969-309">✔</span></span> | <span data-ttu-id="11969-310">✔</span><span class="sxs-lookup"><span data-stu-id="11969-310">✔</span></span> | <span data-ttu-id="11969-311">✖</span><span class="sxs-lookup"><span data-stu-id="11969-311">✖</span></span> | <span data-ttu-id="11969-312">✔</span><span class="sxs-lookup"><span data-stu-id="11969-312">✔</span></span> |
|

### <a name="for-more-information-on-receipt-cards"></a><span data-ttu-id="11969-313">Weitere Informationen zu Empfangs Karten</span><span class="sxs-lookup"><span data-stu-id="11969-313">For more information on Receipt cards</span></span>

<span data-ttu-id="11969-314">Bot-Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="11969-314">Bot Framework reference:</span></span>

* [<span data-ttu-id="11969-315">Zugangskarten Knoten</span><span class="sxs-lookup"><span data-stu-id="11969-315">Receipt card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="11969-316">Quittungs Karte C #</span><span class="sxs-lookup"><span data-stu-id="11969-316">Receipt card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0)

## <a name="signin-card"></a><span data-ttu-id="11969-317">SignIn-Karte</span><span class="sxs-lookup"><span data-stu-id="11969-317">Signin card</span></span>

<span data-ttu-id="11969-318">Eine Karte, mit der ein bot die Anmeldung eines Benutzers anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="11969-318">A card that enables a bot to request that a user sign in.</span></span> <span data-ttu-id="11969-319">Wird in Microsoft Teams in einer etwas anderen Form als im bot-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-319">Supported in Teams in a slightly different form than is found in the Bot Framework.</span></span> <span data-ttu-id="11969-320">Die SignIn-Karte in Microsoft Teams ähnelt der SignIn-Karte im bot-Framework mit der Ausnahme, dass die SignIn-Karte in Microsoft Teams nur `signin` zwei `openUrl`Aktionen unterstützt: und.</span><span class="sxs-lookup"><span data-stu-id="11969-320">The signin card in Teams is similar to the signin card in the bot framework with the exception that the signin card in Teams only supports two actions: `signin` and `openUrl`.</span></span>

<span data-ttu-id="11969-321">Die *SignIn-Aktion* kann von jeder beliebigen Karte in Microsoft Teams und nicht nur von der SignIn-Karte verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="11969-321">The *signin action* can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="11969-322">Weitere Informationen zur Authentifizierung finden Sie im Thema [Microsoft Teams-Authentifizierungs Fluss für Bots](~/bots/how-to/authentication/auth-flow-bot.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-322">See the topic [Microsoft Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md) for more details on authentication.</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="11969-323">Unterstützung für SignIn-Karten</span><span class="sxs-lookup"><span data-stu-id="11969-323">Support for Signin cards</span></span>

| <span data-ttu-id="11969-324">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-324">Bots in Teams</span></span> | <span data-ttu-id="11969-325">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-325">Messaging Extensions</span></span>  | <span data-ttu-id="11969-326">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-326">Connectors</span></span> | <span data-ttu-id="11969-327">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-327">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-328">✔</span><span class="sxs-lookup"><span data-stu-id="11969-328">✔</span></span> | <span data-ttu-id="11969-329">✖</span><span class="sxs-lookup"><span data-stu-id="11969-329">✖</span></span> | <span data-ttu-id="11969-330">✖</span><span class="sxs-lookup"><span data-stu-id="11969-330">✖</span></span> | <span data-ttu-id="11969-331">✔</span><span class="sxs-lookup"><span data-stu-id="11969-331">✔</span></span> |
|

### <a name="for-more-information-on-signin-cards"></a><span data-ttu-id="11969-332">Weitere Informationen zu SignIn-Karten</span><span class="sxs-lookup"><span data-stu-id="11969-332">For more information on Signin cards</span></span>

<span data-ttu-id="11969-333">Bot-Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="11969-333">Bot Framework reference:</span></span>

* [<span data-ttu-id="11969-334">SignIn-Karten Knoten</span><span class="sxs-lookup"><span data-stu-id="11969-334">Signin card Node</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest)
* [<span data-ttu-id="11969-335">SignIn-Karte C #</span><span class="sxs-lookup"><span data-stu-id="11969-335">Signin card C#</span></span>](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0)

## <a name="thumbnail-card"></a><span data-ttu-id="11969-336">Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="11969-336">Thumbnail card</span></span>

<span data-ttu-id="11969-337">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="11969-337">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="11969-338">Unterstützung für Miniatur Ansichtskarten</span><span class="sxs-lookup"><span data-stu-id="11969-338">Support for Thumbnail cards</span></span>

| <span data-ttu-id="11969-339">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-339">Bots in Teams</span></span> | <span data-ttu-id="11969-340">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-340">Messaging Extensions</span></span>  | <span data-ttu-id="11969-341">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-341">Connectors</span></span> | <span data-ttu-id="11969-342">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-342">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-343">✔</span><span class="sxs-lookup"><span data-stu-id="11969-343">✔</span></span> | <span data-ttu-id="11969-344">✔</span><span class="sxs-lookup"><span data-stu-id="11969-344">✔</span></span> | <span data-ttu-id="11969-345">✖</span><span class="sxs-lookup"><span data-stu-id="11969-345">✖</span></span> | <span data-ttu-id="11969-346">✔</span><span class="sxs-lookup"><span data-stu-id="11969-346">✔</span></span> |
|

![Beispiel für eine Miniatur Ansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="11969-348">Eigenschaften einer Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="11969-348">Properties of a Thumbnail card</span></span>

| <span data-ttu-id="11969-349">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11969-349">Property</span></span> | <span data-ttu-id="11969-350">Typ</span><span class="sxs-lookup"><span data-stu-id="11969-350">Type</span></span>  | <span data-ttu-id="11969-351">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="11969-351">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="11969-352">title</span><span class="sxs-lookup"><span data-stu-id="11969-352">title</span></span> | <span data-ttu-id="11969-353">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-353">Rich text</span></span> | <span data-ttu-id="11969-354">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-354">Title of the card.</span></span> <span data-ttu-id="11969-355">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-355">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-356">unter</span><span class="sxs-lookup"><span data-stu-id="11969-356">subtitle</span></span> | <span data-ttu-id="11969-357">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-357">Rich text</span></span> | <span data-ttu-id="11969-358">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-358">Subtitle of the card.</span></span> <span data-ttu-id="11969-359">Maximal 2 Zeilen; Formatierung wird derzeit nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="11969-359">Maximum 2 lines; formatting not currently supported</span></span> |
| <span data-ttu-id="11969-360">text</span><span class="sxs-lookup"><span data-stu-id="11969-360">text</span></span> | <span data-ttu-id="11969-361">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="11969-361">Rich text</span></span> | <span data-ttu-id="11969-362">Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) .</span><span class="sxs-lookup"><span data-stu-id="11969-362">Text appears just below the subtitle; see [Card formatting](~/task-modules-and-cards/cards/cards-format.md) for formatting options</span></span> |
| <span data-ttu-id="11969-363">Bilder</span><span class="sxs-lookup"><span data-stu-id="11969-363">images</span></span> | <span data-ttu-id="11969-364">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="11969-364">Array of images</span></span> | <span data-ttu-id="11969-365">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="11969-365">Image displayed at top of card.</span></span> <span data-ttu-id="11969-366">Seitenverhältnis 1:1 (quadratisch)</span><span class="sxs-lookup"><span data-stu-id="11969-366">Aspect ratio 1:1 (square)</span></span> |
| <span data-ttu-id="11969-367">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="11969-367">buttons</span></span> | <span data-ttu-id="11969-368">Array von Action-Objekten</span><span class="sxs-lookup"><span data-stu-id="11969-368">Array of action objects</span></span> | <span data-ttu-id="11969-369">Eine Gruppe von Aktionen, die für die aktuelle Karte gelten.</span><span class="sxs-lookup"><span data-stu-id="11969-369">Set of actions applicable to the current card.</span></span> <span data-ttu-id="11969-370">Maximal 6</span><span class="sxs-lookup"><span data-stu-id="11969-370">Maximum 6</span></span> |
| <span data-ttu-id="11969-371">Tippen</span><span class="sxs-lookup"><span data-stu-id="11969-371">tap</span></span> | <span data-ttu-id="11969-372">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="11969-372">Action object</span></span> | <span data-ttu-id="11969-373">Diese Aktion wird aktiviert, wenn der Benutzer die Karte selbst anzapft.</span><span class="sxs-lookup"><span data-stu-id="11969-373">This action will be activated when the user taps on the card itself</span></span> |
|

### <a name="example-thumbnail-card"></a><span data-ttu-id="11969-374">Beispiel-Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="11969-374">Example Thumbnail card</span></span>

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

### <a name="for-more-information"></a><span data-ttu-id="11969-375">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="11969-375">For more information</span></span>

<span data-ttu-id="11969-376">Bot-Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="11969-376">Bot Framework reference:</span></span>

* [<span data-ttu-id="11969-377">Miniatur Ansichtskarten Knoten</span><span class="sxs-lookup"><span data-stu-id="11969-377">Thumbnail card Node</span></span>](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest)
* [<span data-ttu-id="11969-378">Miniatur Ansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="11969-378">Thumbnail card C#</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0)

## <a name="card-collections"></a><span data-ttu-id="11969-379">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="11969-379">Card collections</span></span>

<span data-ttu-id="11969-380">Kartensammlungen werden in Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-380">Card collections are supported in Teams.</span></span>

<span data-ttu-id="11969-381">Kartensammlungen werden durch das bot-Framework bereit `builder.AttachmentLayout.carousel` gestellt `builder.AttachmentLayout.list`: und.</span><span class="sxs-lookup"><span data-stu-id="11969-381">Card collections are provided by the Bot Framework: `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="11969-382">Diese Sammlungen können Adaptive, Hero oder Thumbnail-Karten enthalten.</span><span class="sxs-lookup"><span data-stu-id="11969-382">These collections can contain Adaptive, Hero, or Thumbnail cards.</span></span>

## <a name="carousel-collection"></a><span data-ttu-id="11969-383">Carousel-Sammlung</span><span class="sxs-lookup"><span data-stu-id="11969-383">Carousel collection</span></span>

<span data-ttu-id="11969-384">Das [Karussell-Layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) zeigt ein Karussell von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="11969-384">The [carousel layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0) shows a carousel of cards, optionally with associated action buttons.</span></span>

### <a name="support-for-carousel-collections"></a><span data-ttu-id="11969-385">Unterstützung für Karussell Sammlungen</span><span class="sxs-lookup"><span data-stu-id="11969-385">Support for Carousel collections</span></span>

| <span data-ttu-id="11969-386">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-386">Bots in Teams</span></span> | <span data-ttu-id="11969-387">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-387">Messaging Extensions</span></span>  | <span data-ttu-id="11969-388">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-388">Connectors</span></span> | <span data-ttu-id="11969-389">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-389">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-390">✔</span><span class="sxs-lookup"><span data-stu-id="11969-390">✔</span></span> | <span data-ttu-id="11969-391">✖</span><span class="sxs-lookup"><span data-stu-id="11969-391">✖</span></span> | <span data-ttu-id="11969-392">✖</span><span class="sxs-lookup"><span data-stu-id="11969-392">✖</span></span> | <span data-ttu-id="11969-393">✔</span><span class="sxs-lookup"><span data-stu-id="11969-393">✔</span></span> |
|

> [!NOTE]
> <span data-ttu-id="11969-394">Ein Karussell kann maximal 10 Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="11969-394">A carousel can display a maximum of 10 cards per message.</span></span>

### <a name="example-carousel-collection"></a><span data-ttu-id="11969-395">Beispiel für eine Karussell Sammlung</span><span class="sxs-lookup"><span data-stu-id="11969-395">Example Carousel collection</span></span>

![Beispiel für ein Karten Karussell](~/assets/images/cards/carousel.png)

<span data-ttu-id="11969-397">Eigenschaften entsprechen denen für die Hero-oder Thumbnail-Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-397">Properties are the same as for the hero or thumbnail card.</span></span>

### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="11969-398">Syntax für Karussell Sammlungen</span><span class="sxs-lookup"><span data-stu-id="11969-398">Syntax for Carousel collections</span></span>

`builder.AttachmentLayout.carousel`

## <a name="list-collection"></a><span data-ttu-id="11969-399">List-Auflistung</span><span class="sxs-lookup"><span data-stu-id="11969-399">List collection</span></span>

### <a name="support-for-list-collections"></a><span data-ttu-id="11969-400">Unterstützung für Listen Auflistungen</span><span class="sxs-lookup"><span data-stu-id="11969-400">Support for List collections</span></span>

<span data-ttu-id="11969-401">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="11969-401">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

| <span data-ttu-id="11969-402">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="11969-402">Bots in Teams</span></span> | <span data-ttu-id="11969-403">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="11969-403">Messaging Extensions</span></span>  | <span data-ttu-id="11969-404">Connectors</span><span class="sxs-lookup"><span data-stu-id="11969-404">Connectors</span></span> | <span data-ttu-id="11969-405">Bot-Framework</span><span class="sxs-lookup"><span data-stu-id="11969-405">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="11969-406">✔</span><span class="sxs-lookup"><span data-stu-id="11969-406">✔</span></span> | <span data-ttu-id="11969-407">✔</span><span class="sxs-lookup"><span data-stu-id="11969-407">✔</span></span> | <span data-ttu-id="11969-408">✖</span><span class="sxs-lookup"><span data-stu-id="11969-408">✖</span></span> | <span data-ttu-id="11969-409">✔</span><span class="sxs-lookup"><span data-stu-id="11969-409">✔</span></span> |
|

### <a name="example-list-collection"></a><span data-ttu-id="11969-410">Beispiel Listen Sammlung</span><span class="sxs-lookup"><span data-stu-id="11969-410">Example List collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="11969-412">Eigenschaften entsprechen denen für die Hero-oder Thumbnail-Karte.</span><span class="sxs-lookup"><span data-stu-id="11969-412">Properties are the same as for the hero or thumbnail card.</span></span>

<span data-ttu-id="11969-413">In einer Liste können maximal 10 Karten pro Nachricht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="11969-413">A list can display a maximum of 10 cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="11969-414">Einige Kombinationen aus Listen Karten werden auf IOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-414">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

### <a name="syntax-for-list-collections"></a><span data-ttu-id="11969-415">Syntax für Listen Auflistungen</span><span class="sxs-lookup"><span data-stu-id="11969-415">Syntax for List collections</span></span>

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="11969-416">In Microsoft Teams nicht unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="11969-416">Cards not supported in Teams</span></span>

<span data-ttu-id="11969-417">Die folgenden Karten werden vom bot-Framework implementiert, werden jedoch von Microsoft Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="11969-417">The following cards are implemented by the Bot Framework, but are NOT supported by Teams.</span></span>

* <span data-ttu-id="11969-418">Animations Karten</span><span class="sxs-lookup"><span data-stu-id="11969-418">Animation cards</span></span>
* <span data-ttu-id="11969-419">Audio-Karten</span><span class="sxs-lookup"><span data-stu-id="11969-419">Audio cards</span></span>
* <span data-ttu-id="11969-420">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="11969-420">Video cards</span></span>
