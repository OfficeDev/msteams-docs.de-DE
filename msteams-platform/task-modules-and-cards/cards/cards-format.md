---
title: Text Formatierung in Karten
description: Beschreibt die Formatierung von Karten Texten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: e857a1250593c135aa23ad38a571a5561bb91431
ms.sourcegitcommit: b9e8839858ea8e9e33fe5e20e14bbe86c75fd510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "44210687"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="78a10-104">Formatieren von Karten in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="78a10-104">Format cards in Teams</span></span>

<span data-ttu-id="78a10-105">Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie entweder "Abschlag" oder "HTML" verwenden.</span><span class="sxs-lookup"><span data-stu-id="78a10-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="78a10-106">Karten unterstützen die Formatierung nur in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle.</span><span class="sxs-lookup"><span data-stu-id="78a10-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="78a10-107">Die Formatierung kann anhand einer Teilmenge der XML-Formatierung (HTML) oder eines Abschlags je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="78a10-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="78a10-108">Für die aktuelle und zukünftige Entwicklung werden Adaptive Karten mit Abschlag Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="78a10-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="78a10-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendering der Karte kann sich geringfügig zwischen dem Desktop und den Clients für Mobile Teams sowie Microsoft Teams im Desktop Browser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="78a10-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="78a10-110">Sie können ein Inlinebild mit einer beliebigen Teams-Karte einfügen.</span><span class="sxs-lookup"><span data-stu-id="78a10-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="78a10-111">Bilder werden als `.png` , `.jpg` oder `.gif` Dateien formatiert und dürfen nicht mehr als 1024 × 1024 px oder 1 MB betragen.</span><span class="sxs-lookup"><span data-stu-id="78a10-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="78a10-112">Animierte GIF-Zeichen werden nicht offiziell unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="78a10-113">*Siehe* [Karten Referenz](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="78a10-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="78a10-114">Formatieren von Karten mit Abschlag</span><span class="sxs-lookup"><span data-stu-id="78a10-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="78a10-115">Es gibt zwei Kartentypen, die das Abschlag in Microsoft Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="78a10-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="78a10-116">**Adaptive Karten**: das Abschlag wird sowohl im Feld Adaptive Karten `Textblock` als auch unterstützt `Fact.Title` `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="78a10-116">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="78a10-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-117">HTML is not supported in adaptive cards.</span></span>
> * <span data-ttu-id="78a10-118">**O365-connectorkarten**: Abschlag und limitierter HTML-Code werden in Office 365-connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="78a10-119">**Abschlag Formatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="78a10-119">**Markdown formatting: Adaptive Cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="78a10-120">Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="78a10-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="78a10-121">Format</span><span class="sxs-lookup"><span data-stu-id="78a10-121">Style</span></span> | <span data-ttu-id="78a10-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="78a10-122">Example</span></span> | <span data-ttu-id="78a10-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="78a10-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="78a10-124">bold</span><span class="sxs-lookup"><span data-stu-id="78a10-124">bold</span></span> | <span data-ttu-id="78a10-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="78a10-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="78a10-126">italic</span><span class="sxs-lookup"><span data-stu-id="78a10-126">italic</span></span> | <span data-ttu-id="78a10-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="78a10-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="78a10-128">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-128">unordered list</span></span> | <ul><li><span data-ttu-id="78a10-129">text</span><span class="sxs-lookup"><span data-stu-id="78a10-129">text</span></span></li><li><span data-ttu-id="78a10-130">text</span><span class="sxs-lookup"><span data-stu-id="78a10-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="78a10-131">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-131">ordered list</span></span> | <ol><li><span data-ttu-id="78a10-132">text</span><span class="sxs-lookup"><span data-stu-id="78a10-132">text</span></span></li><li><span data-ttu-id="78a10-133">text</span><span class="sxs-lookup"><span data-stu-id="78a10-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="78a10-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="78a10-134">Hyperlinks</span></span> |[<span data-ttu-id="78a10-135">Bing</span><span class="sxs-lookup"><span data-stu-id="78a10-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="78a10-136">Die folgenden Abschlag Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="78a10-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="78a10-137">Header</span><span class="sxs-lookup"><span data-stu-id="78a10-137">Headers</span></span>
* <span data-ttu-id="78a10-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="78a10-138">Tables</span></span>
* <span data-ttu-id="78a10-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="78a10-139">Images</span></span>
* <span data-ttu-id="78a10-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="78a10-140">Preformatted text</span></span>
* <span data-ttu-id="78a10-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="78a10-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78a10-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="78a10-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="78a10-143">Neugliederungen für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-143">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="78a10-144">In Listen können Sie die `\r` oder `\n` Escape-Sequenzen für "reinlines" verwenden.</span><span class="sxs-lookup"><span data-stu-id="78a10-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="78a10-145">`\n\n`Die Verwendung in einer Liste bewirkt, dass das nächste Element in der Liste eingerückt wird.</span><span class="sxs-lookup"><span data-stu-id="78a10-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="78a10-146">Wenn Sie an einer anderen Stelle im TextBlock eine Umrisse benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="78a10-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="78a10-147">Unterschiede zwischen Mobilgeräten und Desktops für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-147">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="78a10-148">Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="78a10-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="78a10-149">Auf dem Desktop wird die Formatierung für das Abgleichen von adaptiven Karten in beiden Webbrowsern und in der Microsoft Teams-Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-149">On the desktop, Adaptive Card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatieren von adaptiven Karten Abschlägen im Desktop Client](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="78a10-151">Auf IOS wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-151">On iOS, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in ios](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="78a10-153">Auf Android wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="78a10-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-155">More information on Adaptive Cards</span></span>

<span data-ttu-id="78a10-156">[Text Features in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums-und Lokalisierungsfeatures werden in Microsoft Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="78a10-157">Formatierungs Beispiel für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-157">Formatting sample for Adaptive cards</span></span>

``` json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="78a10-158">Erwähnung der Unterstützung in Adaptive Cards v 1.2</span><span class="sxs-lookup"><span data-stu-id="78a10-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="78a10-159">Kartenbasierte Erwähnungen werden in den Netz-, Desktop-und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="78a10-160">Sie können @ Mentions in einem adaptiven Kartentext für Bots und Messaging-Erweiterungs Antworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="78a10-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="78a10-161">Um @ Mentions in Cards hinzuzufügen, befolgten Sie die gleiche Benachrichtigungslogik und die gleiche Darstellung wie die nachrichtenbasierte [Erwähnungen in Kanal-und Gruppenchat Unterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span><span class="sxs-lookup"><span data-stu-id="78a10-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="78a10-162">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet](https://adaptivecards.io/explorer/FactSet.html) -Elementen enthalten.</span><span class="sxs-lookup"><span data-stu-id="78a10-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
><span data-ttu-id="78a10-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in Adaptive Cards v 1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="78a10-164">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="78a10-164">Constructing mentions</span></span>

<span data-ttu-id="78a10-165">Um eine Erwähnung in eine Adaptive Karte aufzunehmen, muss Ihre APP die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="78a10-165">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="78a10-166">`<at>username</at>`in den unterstützten Adaptive Card-Elementen</span><span class="sxs-lookup"><span data-stu-id="78a10-166">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="78a10-167">Das `mention` Objekt innerhalb einer `msteams` Eigenschaft im Karteninhalt, das die Teams-Benutzer-ID des erwähnten Benutzers enthält</span><span class="sxs-lookup"><span data-stu-id="78a10-167">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="78a10-168">Beispiel Adaptive Karte mit Erwähnung</span><span class="sxs-lookup"><span data-stu-id="78a10-168">Sample Adaptive card with a mention</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "type": "AdaptiveCard",
    "body": [
      {
        "type": "TextBlock",
        "text": "Hi <at>John Doe</at>"
      }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "msteams": {
      "entities": [
        {
          "type": "mention",
          "text": "<at>John Doe</at>",
          "mentioned": {
            "id": "29:123124124124",
            "name": "John Doe"
          }
        }
      ]
    }
  }
}
```

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="78a10-169">**Abschlag Formatierung: O365-Verbindungskarten**</span><span class="sxs-lookup"><span data-stu-id="78a10-169">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="78a10-170">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="78a10-170">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="78a10-171">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="78a10-171">HTML support is described in the last section.</span></span>

| <span data-ttu-id="78a10-172">Format</span><span class="sxs-lookup"><span data-stu-id="78a10-172">Style</span></span> | <span data-ttu-id="78a10-173">Beispiel</span><span class="sxs-lookup"><span data-stu-id="78a10-173">Example</span></span> | <span data-ttu-id="78a10-174">Markdown</span><span class="sxs-lookup"><span data-stu-id="78a10-174">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="78a10-175">bold</span><span class="sxs-lookup"><span data-stu-id="78a10-175">bold</span></span> | <span data-ttu-id="78a10-176">**text**</span><span class="sxs-lookup"><span data-stu-id="78a10-176">**text**</span></span> | `**text**` |
| <span data-ttu-id="78a10-177">italic</span><span class="sxs-lookup"><span data-stu-id="78a10-177">italic</span></span> | <span data-ttu-id="78a10-178">*text*</span><span class="sxs-lookup"><span data-stu-id="78a10-178">*text*</span></span> | `*text*` |
| <span data-ttu-id="78a10-179">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="78a10-179">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="78a10-180">**Text**</span><span class="sxs-lookup"><span data-stu-id="78a10-180">**Text**</span></span> | `### Text`|
| <span data-ttu-id="78a10-181">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="78a10-181">strikethrough</span></span> | <span data-ttu-id="78a10-182">~~text~~</span><span class="sxs-lookup"><span data-stu-id="78a10-182">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="78a10-183">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-183">unordered list</span></span> | <ul><li><span data-ttu-id="78a10-184">text</span><span class="sxs-lookup"><span data-stu-id="78a10-184">text</span></span></li><li><span data-ttu-id="78a10-185">text</span><span class="sxs-lookup"><span data-stu-id="78a10-185">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="78a10-186">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-186">ordered list</span></span> | <ol><li><span data-ttu-id="78a10-187">text</span><span class="sxs-lookup"><span data-stu-id="78a10-187">text</span></span></li><li><span data-ttu-id="78a10-188">text</span><span class="sxs-lookup"><span data-stu-id="78a10-188">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="78a10-189">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="78a10-189">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="78a10-190">blockquote</span><span class="sxs-lookup"><span data-stu-id="78a10-190">blockquote</span></span> | <span data-ttu-id="78a10-191">>blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="78a10-191">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="78a10-192">Link</span><span class="sxs-lookup"><span data-stu-id="78a10-192">hyperlink</span></span> | [<span data-ttu-id="78a10-193">Bing</span><span class="sxs-lookup"><span data-stu-id="78a10-193">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="78a10-194">Bild Link</span><span class="sxs-lookup"><span data-stu-id="78a10-194">image link</span></span> |![Duck on a Rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="78a10-196">In connectorkarten werden für die neureihen für `\n\n` , jedoch nicht für `\n` oder gerendert `\r` .</span><span class="sxs-lookup"><span data-stu-id="78a10-196">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="78a10-197">Unterschiede bei Mobiltelefonen und Desktops für connectorkarten mit Abschlag</span><span class="sxs-lookup"><span data-stu-id="78a10-197">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="78a10-198">Auf dem Desktop sieht die Abschlag Formatierung für connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-198">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im Desktop Client](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="78a10-200">Auf IOS sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-200">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im IOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="78a10-202">Probleme:</span><span class="sxs-lookup"><span data-stu-id="78a10-202">Issues:</span></span>

* <span data-ttu-id="78a10-203">Der IOS-Client für Microsoft Teams rendert keine Abschlag-oder HTML-Inline Bilder in Steckkarten.</span><span class="sxs-lookup"><span data-stu-id="78a10-203">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="78a10-204">Block Zitate werden als Einzüge, jedoch ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="78a10-204">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="78a10-205">Auf Android sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-205">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="78a10-207">Formatierungs Beispiel für Abschlag-konnektorkarten</span><span class="sxs-lookup"><span data-stu-id="78a10-207">Formatting example for Markdown Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card Markdown formatting",
    "sections": [
        {
            "text": "This is some **bold** text"
        },
        {
            "text": "This is some _italic_ text"
        },
        {
            "text": "# Header 1\r## Header 2\r### Header 3"
        },
        {
            "text": "- Bullet \r- List \r"
        },
        {
            "text": "1. Numbered\r1. List \r"
        },
        {
            "text": "Link: [Bing](https://www.bing.com)"
        },
        {
            "text": "embedded image link: ![Duck on a rock](http://aka.ms/Fo983c)"
        },
        {
            "text": "`preformatted text`"
        },
        {
            "text": "Newlines (backslash n, backslash n):\n\nline a\n\nline b\n\nline c"
        },
        {
            "text": ">This is a blockquote"
        }
     ]
  }
}

```

---

## <a name="formatting-cards-with-html"></a><span data-ttu-id="78a10-208">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="78a10-208">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="78a10-209">**HTML-Formatierung: O365-Verbindungskarten**</span><span class="sxs-lookup"><span data-stu-id="78a10-209">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="78a10-210">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="78a10-210">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="78a10-211">Das Abschlag wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="78a10-211">Markdown is described in the next section.</span></span>

| <span data-ttu-id="78a10-212">Format</span><span class="sxs-lookup"><span data-stu-id="78a10-212">Style</span></span> | <span data-ttu-id="78a10-213">Beispiel</span><span class="sxs-lookup"><span data-stu-id="78a10-213">Example</span></span> | <span data-ttu-id="78a10-214">HTML</span><span class="sxs-lookup"><span data-stu-id="78a10-214">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="78a10-215">bold</span><span class="sxs-lookup"><span data-stu-id="78a10-215">bold</span></span> | <span data-ttu-id="78a10-216">**text**</span><span class="sxs-lookup"><span data-stu-id="78a10-216">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="78a10-217">italic</span><span class="sxs-lookup"><span data-stu-id="78a10-217">italic</span></span> | <span data-ttu-id="78a10-218">*text*</span><span class="sxs-lookup"><span data-stu-id="78a10-218">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="78a10-219">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="78a10-219">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="78a10-220">**Text**</span><span class="sxs-lookup"><span data-stu-id="78a10-220">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="78a10-221">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="78a10-221">strikethrough</span></span> | <span data-ttu-id="78a10-222">~~text~~</span><span class="sxs-lookup"><span data-stu-id="78a10-222">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="78a10-223">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-223">unordered list</span></span> | <ul><li><span data-ttu-id="78a10-224">text</span><span class="sxs-lookup"><span data-stu-id="78a10-224">text</span></span></li><li><span data-ttu-id="78a10-225">text</span><span class="sxs-lookup"><span data-stu-id="78a10-225">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="78a10-226">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-226">ordered list</span></span> | <ol><li><span data-ttu-id="78a10-227">text</span><span class="sxs-lookup"><span data-stu-id="78a10-227">text</span></span></li><li><span data-ttu-id="78a10-228">text</span><span class="sxs-lookup"><span data-stu-id="78a10-228">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="78a10-229">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="78a10-229">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="78a10-230">blockquote</span><span class="sxs-lookup"><span data-stu-id="78a10-230">blockquote</span></span> | <blockquote><span data-ttu-id="78a10-231">text</span><span class="sxs-lookup"><span data-stu-id="78a10-231">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="78a10-232">Link</span><span class="sxs-lookup"><span data-stu-id="78a10-232">hyperlink</span></span> | [<span data-ttu-id="78a10-233">Bing</span><span class="sxs-lookup"><span data-stu-id="78a10-233">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="78a10-234">Bild Link</span><span class="sxs-lookup"><span data-stu-id="78a10-234">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="78a10-235">In connectorkarten werden die Neubuchungen in HTML mithilfe des- `<p>` Tags gerendert.</span><span class="sxs-lookup"><span data-stu-id="78a10-235">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="78a10-236">Unterschiede zwischen Mobiltelefonen und Desktops für connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="78a10-236">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="78a10-237">Auf dem Desktop sieht die HTML-Formatierung für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-237">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Desktop Client](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="78a10-239">Auf IOS sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-239">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im IOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="78a10-241">Probleme:</span><span class="sxs-lookup"><span data-stu-id="78a10-241">Issues:</span></span>

* <span data-ttu-id="78a10-242">Inline Bilder werden nicht in ios unter Verwendung von "Abschlag" oder "HTML in"-Steckkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="78a10-242">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="78a10-243">Vorformatierter Text wird gerendert, weist jedoch keinen grauen Hintergrund auf.</span><span class="sxs-lookup"><span data-stu-id="78a10-243">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="78a10-244">Auf Android sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="78a10-244">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="78a10-246">Formatierungs Beispiel für HTML-Verbindungskarten</span><span class="sxs-lookup"><span data-stu-id="78a10-246">Formatting sample for HTML Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card HTML formatting",
    "sections": [
        {
            "text": "This is some <strong>bold</strong> text"
        },
        {
            "text": "This is some <em>italic</em> text"
        },
        {
            "text": "This is some <strike>strikethrough</strike> text"
        },
        {
            "text": "<h1>Header 1</h1>\r<h2>Header 2</h2>\r <h3>Header 3</h3>"
        },
        {
            "text": "bullet list <ul><li>text</li><li>text</li></ul>"
        },
        {
            "text": "ordered list <ol><li>text</li><li>text</li></ol>"
        },
        {
            "text": "hyperlink <a href=\"https://www.bing.com/\">Bing</a>"
        },
        {
            "text": "embedded image <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
        },
        {
            "text": "preformatted text <pre>text</pre>"
        },
        {
            "text": "Paragraphs <p>Line a</p><p>Line b</p>"
        },
        {
            "text": "<blockquote>Blockquote text</blockquote>"
        }
     ]
  }
}

```

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="78a10-247">**HTML-Formatierung: Hero-und Miniatur Ansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="78a10-247">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="78a10-248">HTML-Tags werden für einfache Karten wie die Hero-und die Thumbnail-Karte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-248">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="78a10-249">Abschläge werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a10-249">Markdown is not supported.</span></span>

| <span data-ttu-id="78a10-250">Format</span><span class="sxs-lookup"><span data-stu-id="78a10-250">Style</span></span> | <span data-ttu-id="78a10-251">Beispiel</span><span class="sxs-lookup"><span data-stu-id="78a10-251">Example</span></span> | <span data-ttu-id="78a10-252">HTML</span><span class="sxs-lookup"><span data-stu-id="78a10-252">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="78a10-253">bold</span><span class="sxs-lookup"><span data-stu-id="78a10-253">bold</span></span> | <span data-ttu-id="78a10-254">**text**</span><span class="sxs-lookup"><span data-stu-id="78a10-254">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="78a10-255">italic</span><span class="sxs-lookup"><span data-stu-id="78a10-255">italic</span></span> | <span data-ttu-id="78a10-256">*text*</span><span class="sxs-lookup"><span data-stu-id="78a10-256">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="78a10-257">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="78a10-257">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="78a10-258">**Text**</span><span class="sxs-lookup"><span data-stu-id="78a10-258">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="78a10-259">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="78a10-259">strikethrough</span></span> | <span data-ttu-id="78a10-260">~~text~~</span><span class="sxs-lookup"><span data-stu-id="78a10-260">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="78a10-261">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-261">unordered list</span></span> | <ul><li><span data-ttu-id="78a10-262">text</span><span class="sxs-lookup"><span data-stu-id="78a10-262">text</span></span></li><li><span data-ttu-id="78a10-263">text</span><span class="sxs-lookup"><span data-stu-id="78a10-263">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="78a10-264">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="78a10-264">ordered list</span></span> | <ol><li><span data-ttu-id="78a10-265">text</span><span class="sxs-lookup"><span data-stu-id="78a10-265">text</span></span></li><li><span data-ttu-id="78a10-266">text</span><span class="sxs-lookup"><span data-stu-id="78a10-266">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="78a10-267">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="78a10-267">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="78a10-268">blockquote</span><span class="sxs-lookup"><span data-stu-id="78a10-268">blockquote</span></span> | <blockquote><span data-ttu-id="78a10-269">text</span><span class="sxs-lookup"><span data-stu-id="78a10-269">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="78a10-270">Link</span><span class="sxs-lookup"><span data-stu-id="78a10-270">hyperlink</span></span> | [<span data-ttu-id="78a10-271">Bing</span><span class="sxs-lookup"><span data-stu-id="78a10-271">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="78a10-272">Bild Link</span><span class="sxs-lookup"><span data-stu-id="78a10-272">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="78a10-273">Unterschiede zwischen Mobilgeräten und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-273">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="78a10-274">Aufgrund der Unterschiede zwischen Desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="78a10-274">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="78a10-275">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-275">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktop Client](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="78a10-277">Auf IOS wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-277">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im IOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="78a10-279">Probleme:</span><span class="sxs-lookup"><span data-stu-id="78a10-279">Issues:</span></span>

* <span data-ttu-id="78a10-280">Zeichenformatierungen wie Fett und kursiv werden auf IOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="78a10-280">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="78a10-281">Auf Android wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="78a10-281">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="78a10-283">Zeichenformatierungen wie Fett und kursiv werden auf Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78a10-283">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="78a10-284">Formatierungs Beispiel für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="78a10-284">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="78a10-285">Diese Screenshots wurden mit Microsoft Teams AppStudio erstellt, wobei die Text-Eigenschaft einer Hero Card auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="78a10-285">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="78a10-286">Sie können die Formatierung in ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="78a10-286">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
