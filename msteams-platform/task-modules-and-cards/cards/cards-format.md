---
title: Text Formatierung in Karten
description: Beschreibt die Formatierung von Karten Texten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: 944e6a69c68d284b3a7309063587bd4b75319bc7
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587811"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="97ac2-104">Formatieren von Karten in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="97ac2-104">Format cards in Teams</span></span>

<span data-ttu-id="97ac2-105">Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie entweder "Abschlag" oder "HTML" verwenden.</span><span class="sxs-lookup"><span data-stu-id="97ac2-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="97ac2-106">Karten unterstützen die Formatierung nur in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle.</span><span class="sxs-lookup"><span data-stu-id="97ac2-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="97ac2-107">Die Formatierung kann anhand einer Teilmenge der XML-Formatierung (HTML) oder eines Abschlags je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="97ac2-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="97ac2-108">Für die aktuelle und zukünftige Entwicklung werden Adaptive Karten mit Abschlag Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="97ac2-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="97ac2-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendering der Karte kann sich geringfügig zwischen dem Desktop und den Clients für Mobile Teams sowie Microsoft Teams im Desktop Browser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="97ac2-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="97ac2-110">Sie können ein Inlinebild mit einer beliebigen Teams-Karte einfügen.</span><span class="sxs-lookup"><span data-stu-id="97ac2-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="97ac2-111">Bilder werden als `.png` , `.jpg` oder `.gif` Dateien formatiert und dürfen nicht mehr als 1024 × 1024 px oder 1 MB betragen.</span><span class="sxs-lookup"><span data-stu-id="97ac2-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="97ac2-112">Animierte GIF-Zeichen werden nicht offiziell unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="97ac2-113">*Siehe* [Karten Referenz](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="97ac2-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="97ac2-114">Formatieren von Karten mit Abschlag</span><span class="sxs-lookup"><span data-stu-id="97ac2-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="97ac2-115">Es gibt zwei Kartentypen, die das Abschlag in Microsoft Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="97ac2-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="97ac2-116">**Adaptive Karten**: das Abschlag wird sowohl im Feld Adaptive Karten `Textblock` als auch unterstützt `Fact.Title` `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="97ac2-116">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="97ac2-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-117">HTML is not supported in adaptive cards.</span></span>
> * <span data-ttu-id="97ac2-118">**O365-connectorkarten**: Abschlag und limitierter HTML-Code werden in Office 365-connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="97ac2-119">**Abschlag Formatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="97ac2-119">**Markdown formatting: Adaptive Cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="97ac2-120">Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="97ac2-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="97ac2-121">Format</span><span class="sxs-lookup"><span data-stu-id="97ac2-121">Style</span></span> | <span data-ttu-id="97ac2-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="97ac2-122">Example</span></span> | <span data-ttu-id="97ac2-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="97ac2-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="97ac2-124">bold</span><span class="sxs-lookup"><span data-stu-id="97ac2-124">bold</span></span> | <span data-ttu-id="97ac2-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="97ac2-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="97ac2-126">italic</span><span class="sxs-lookup"><span data-stu-id="97ac2-126">italic</span></span> | <span data-ttu-id="97ac2-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="97ac2-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="97ac2-128">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-128">unordered list</span></span> | <ul><li><span data-ttu-id="97ac2-129">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-129">text</span></span></li><li><span data-ttu-id="97ac2-130">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="97ac2-131">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-131">ordered list</span></span> | <ol><li><span data-ttu-id="97ac2-132">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-132">text</span></span></li><li><span data-ttu-id="97ac2-133">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="97ac2-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="97ac2-134">Hyperlinks</span></span> |[<span data-ttu-id="97ac2-135">Bing</span><span class="sxs-lookup"><span data-stu-id="97ac2-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="97ac2-136">Die folgenden Abschlag Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="97ac2-137">Header</span><span class="sxs-lookup"><span data-stu-id="97ac2-137">Headers</span></span>
* <span data-ttu-id="97ac2-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="97ac2-138">Tables</span></span>
* <span data-ttu-id="97ac2-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="97ac2-139">Images</span></span>
* <span data-ttu-id="97ac2-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="97ac2-140">Preformatted text</span></span>
* <span data-ttu-id="97ac2-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="97ac2-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97ac2-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="97ac2-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="97ac2-143">Neugliederungen für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-143">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="97ac2-144">In Listen können Sie die `\r` oder `\n` Escape-Sequenzen für "reinlines" verwenden.</span><span class="sxs-lookup"><span data-stu-id="97ac2-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="97ac2-145">`\n\n`Die Verwendung in einer Liste bewirkt, dass das nächste Element in der Liste eingerückt wird.</span><span class="sxs-lookup"><span data-stu-id="97ac2-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="97ac2-146">Wenn Sie an einer anderen Stelle im TextBlock eine Umrisse benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="97ac2-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="97ac2-147">Unterschiede zwischen Mobilgeräten und Desktops für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-147">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="97ac2-148">Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="97ac2-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="97ac2-149">Auf dem Desktop wird die Formatierung für das Abgleichen von adaptiven Karten in beiden Webbrowsern und in der Microsoft Teams-Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-149">On the desktop, Adaptive Card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatieren von adaptiven Karten Abschlägen im Desktop Client](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="97ac2-151">Auf IOS wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-151">On iOS, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in ios](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="97ac2-153">Auf Android wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="97ac2-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-155">More information on Adaptive Cards</span></span>

<span data-ttu-id="97ac2-156">[Text Features in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums-und Lokalisierungsfeatures werden in Microsoft Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="97ac2-157">Formatierungs Beispiel für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="97ac2-158">Erwähnung der Unterstützung in Adaptive Cards v 1.2</span><span class="sxs-lookup"><span data-stu-id="97ac2-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="97ac2-159">Kartenbasierte Erwähnungen werden in den Netz-, Desktop-und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="97ac2-160">Sie können @ Mentions in einem adaptiven Kartentext für Bots und Messaging-Erweiterungs Antworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="97ac2-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="97ac2-161">Um @ Mentions in Cards hinzuzufügen, befolgten Sie die gleiche Benachrichtigungslogik und die gleiche Darstellung wie die nachrichtenbasierte [Erwähnungen in Kanal-und Gruppenchat Unterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span><span class="sxs-lookup"><span data-stu-id="97ac2-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="97ac2-162">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet](https://adaptivecards.io/explorer/FactSet.html) -Elementen enthalten.</span><span class="sxs-lookup"><span data-stu-id="97ac2-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="97ac2-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in Adaptive Cards v 1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="97ac2-164">Kanal & Team Erwähnungen werden in bot-Nachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-164">Channel & Team mentions are not supported in bot messages.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="97ac2-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="97ac2-165">Constructing mentions</span></span>

<span data-ttu-id="97ac2-166">Um eine Erwähnung in eine Adaptive Karte aufzunehmen, muss Ihre APP die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="97ac2-166">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="97ac2-167">`<at>username</at>`in den unterstützten Adaptive Card-Elementen</span><span class="sxs-lookup"><span data-stu-id="97ac2-167">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="97ac2-168">Das `mention` Objekt innerhalb einer `msteams` Eigenschaft im Karteninhalt, das die Teams-Benutzer-ID des erwähnten Benutzers enthält</span><span class="sxs-lookup"><span data-stu-id="97ac2-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="97ac2-169">Beispiel Adaptive Karte mit Erwähnung</span><span class="sxs-lookup"><span data-stu-id="97ac2-169">Sample Adaptive card with a mention</span></span>

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

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="97ac2-170">**Abschlag Formatierung: O365-Verbindungskarten**</span><span class="sxs-lookup"><span data-stu-id="97ac2-170">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="97ac2-171">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="97ac2-171">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="97ac2-172">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="97ac2-172">HTML support is described in the last section.</span></span>

| <span data-ttu-id="97ac2-173">Format</span><span class="sxs-lookup"><span data-stu-id="97ac2-173">Style</span></span> | <span data-ttu-id="97ac2-174">Beispiel</span><span class="sxs-lookup"><span data-stu-id="97ac2-174">Example</span></span> | <span data-ttu-id="97ac2-175">Markdown</span><span class="sxs-lookup"><span data-stu-id="97ac2-175">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="97ac2-176">bold</span><span class="sxs-lookup"><span data-stu-id="97ac2-176">bold</span></span> | <span data-ttu-id="97ac2-177">**text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-177">**text**</span></span> | `**text**` |
| <span data-ttu-id="97ac2-178">italic</span><span class="sxs-lookup"><span data-stu-id="97ac2-178">italic</span></span> | <span data-ttu-id="97ac2-179">*text*</span><span class="sxs-lookup"><span data-stu-id="97ac2-179">*text*</span></span> | `*text*` |
| <span data-ttu-id="97ac2-180">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="97ac2-180">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="97ac2-181">**Text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-181">**Text**</span></span> | `### Text`|
| <span data-ttu-id="97ac2-182">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="97ac2-182">strikethrough</span></span> | <span data-ttu-id="97ac2-183">~~text~~</span><span class="sxs-lookup"><span data-stu-id="97ac2-183">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="97ac2-184">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-184">unordered list</span></span> | <ul><li><span data-ttu-id="97ac2-185">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-185">text</span></span></li><li><span data-ttu-id="97ac2-186">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-186">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="97ac2-187">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-187">ordered list</span></span> | <ol><li><span data-ttu-id="97ac2-188">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-188">text</span></span></li><li><span data-ttu-id="97ac2-189">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-189">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="97ac2-190">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="97ac2-190">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="97ac2-191">blockquote</span><span class="sxs-lookup"><span data-stu-id="97ac2-191">blockquote</span></span> | <span data-ttu-id="97ac2-192">>blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="97ac2-192">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="97ac2-193">Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-193">hyperlink</span></span> | [<span data-ttu-id="97ac2-194">Bing</span><span class="sxs-lookup"><span data-stu-id="97ac2-194">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="97ac2-195">Bild Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-195">image link</span></span> |![Duck on a Rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="97ac2-197">In connectorkarten werden für die neureihen für `\n\n` , jedoch nicht für `\n` oder gerendert `\r` .</span><span class="sxs-lookup"><span data-stu-id="97ac2-197">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="97ac2-198">Unterschiede bei Mobiltelefonen und Desktops für connectorkarten mit Abschlag</span><span class="sxs-lookup"><span data-stu-id="97ac2-198">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="97ac2-199">Auf dem Desktop sieht die Abschlag Formatierung für connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-199">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im Desktop Client](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="97ac2-201">Auf IOS sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-201">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im IOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="97ac2-203">Probleme:</span><span class="sxs-lookup"><span data-stu-id="97ac2-203">Issues:</span></span>

* <span data-ttu-id="97ac2-204">Der IOS-Client für Microsoft Teams rendert keine Abschlag-oder HTML-Inline Bilder in Steckkarten.</span><span class="sxs-lookup"><span data-stu-id="97ac2-204">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="97ac2-205">Block Zitate werden als Einzüge, jedoch ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="97ac2-205">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="97ac2-206">Auf Android sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-206">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Abschlag Formatierung für connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="97ac2-208">Formatierungs Beispiel für Abschlag-konnektorkarten</span><span class="sxs-lookup"><span data-stu-id="97ac2-208">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="97ac2-209">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="97ac2-209">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="97ac2-210">**HTML-Formatierung: O365-Verbindungskarten**</span><span class="sxs-lookup"><span data-stu-id="97ac2-210">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="97ac2-211">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="97ac2-211">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="97ac2-212">Das Abschlag wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="97ac2-212">Markdown is described in the next section.</span></span>

| <span data-ttu-id="97ac2-213">Format</span><span class="sxs-lookup"><span data-stu-id="97ac2-213">Style</span></span> | <span data-ttu-id="97ac2-214">Beispiel</span><span class="sxs-lookup"><span data-stu-id="97ac2-214">Example</span></span> | <span data-ttu-id="97ac2-215">HTML</span><span class="sxs-lookup"><span data-stu-id="97ac2-215">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="97ac2-216">bold</span><span class="sxs-lookup"><span data-stu-id="97ac2-216">bold</span></span> | <span data-ttu-id="97ac2-217">**text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-217">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="97ac2-218">italic</span><span class="sxs-lookup"><span data-stu-id="97ac2-218">italic</span></span> | <span data-ttu-id="97ac2-219">*text*</span><span class="sxs-lookup"><span data-stu-id="97ac2-219">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="97ac2-220">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="97ac2-220">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="97ac2-221">**Text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-221">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="97ac2-222">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="97ac2-222">strikethrough</span></span> | <span data-ttu-id="97ac2-223">~~text~~</span><span class="sxs-lookup"><span data-stu-id="97ac2-223">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="97ac2-224">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-224">unordered list</span></span> | <ul><li><span data-ttu-id="97ac2-225">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-225">text</span></span></li><li><span data-ttu-id="97ac2-226">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-226">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="97ac2-227">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-227">ordered list</span></span> | <ol><li><span data-ttu-id="97ac2-228">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-228">text</span></span></li><li><span data-ttu-id="97ac2-229">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-229">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="97ac2-230">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="97ac2-230">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="97ac2-231">blockquote</span><span class="sxs-lookup"><span data-stu-id="97ac2-231">blockquote</span></span> | <blockquote><span data-ttu-id="97ac2-232">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-232">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="97ac2-233">Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-233">hyperlink</span></span> | [<span data-ttu-id="97ac2-234">Bing</span><span class="sxs-lookup"><span data-stu-id="97ac2-234">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="97ac2-235">Bild Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-235">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="97ac2-236">In connectorkarten werden die Neubuchungen in HTML mithilfe des- `<p>` Tags gerendert.</span><span class="sxs-lookup"><span data-stu-id="97ac2-236">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="97ac2-237">Unterschiede zwischen Mobiltelefonen und Desktops für connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="97ac2-237">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="97ac2-238">Auf dem Desktop sieht die HTML-Formatierung für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-238">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Desktop Client](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="97ac2-240">Auf IOS sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-240">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im IOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="97ac2-242">Probleme:</span><span class="sxs-lookup"><span data-stu-id="97ac2-242">Issues:</span></span>

* <span data-ttu-id="97ac2-243">Inline Bilder werden nicht in ios unter Verwendung von "Abschlag" oder "HTML in"-Steckkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="97ac2-243">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="97ac2-244">Vorformatierter Text wird gerendert, weist jedoch keinen grauen Hintergrund auf.</span><span class="sxs-lookup"><span data-stu-id="97ac2-244">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="97ac2-245">Auf Android sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="97ac2-245">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="97ac2-247">Formatierungs Beispiel für HTML-Verbindungskarten</span><span class="sxs-lookup"><span data-stu-id="97ac2-247">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="97ac2-248">**HTML-Formatierung: Hero-und Miniatur Ansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="97ac2-248">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="97ac2-249">HTML-Tags werden für einfache Karten wie die Hero-und die Thumbnail-Karte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-249">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="97ac2-250">Abschläge werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-250">Markdown is not supported.</span></span>

| <span data-ttu-id="97ac2-251">Format</span><span class="sxs-lookup"><span data-stu-id="97ac2-251">Style</span></span> | <span data-ttu-id="97ac2-252">Beispiel</span><span class="sxs-lookup"><span data-stu-id="97ac2-252">Example</span></span> | <span data-ttu-id="97ac2-253">HTML</span><span class="sxs-lookup"><span data-stu-id="97ac2-253">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="97ac2-254">bold</span><span class="sxs-lookup"><span data-stu-id="97ac2-254">bold</span></span> | <span data-ttu-id="97ac2-255">**text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-255">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="97ac2-256">italic</span><span class="sxs-lookup"><span data-stu-id="97ac2-256">italic</span></span> | <span data-ttu-id="97ac2-257">*text*</span><span class="sxs-lookup"><span data-stu-id="97ac2-257">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="97ac2-258">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="97ac2-258">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="97ac2-259">**Text**</span><span class="sxs-lookup"><span data-stu-id="97ac2-259">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="97ac2-260">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="97ac2-260">strikethrough</span></span> | <span data-ttu-id="97ac2-261">~~text~~</span><span class="sxs-lookup"><span data-stu-id="97ac2-261">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="97ac2-262">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-262">unordered list</span></span> | <ul><li><span data-ttu-id="97ac2-263">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-263">text</span></span></li><li><span data-ttu-id="97ac2-264">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-264">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="97ac2-265">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="97ac2-265">ordered list</span></span> | <ol><li><span data-ttu-id="97ac2-266">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-266">text</span></span></li><li><span data-ttu-id="97ac2-267">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-267">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="97ac2-268">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="97ac2-268">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="97ac2-269">blockquote</span><span class="sxs-lookup"><span data-stu-id="97ac2-269">blockquote</span></span> | <blockquote><span data-ttu-id="97ac2-270">text</span><span class="sxs-lookup"><span data-stu-id="97ac2-270">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="97ac2-271">Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-271">hyperlink</span></span> | [<span data-ttu-id="97ac2-272">Bing</span><span class="sxs-lookup"><span data-stu-id="97ac2-272">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="97ac2-273">Bild Link</span><span class="sxs-lookup"><span data-stu-id="97ac2-273">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="97ac2-274">Unterschiede zwischen Mobilgeräten und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-274">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="97ac2-275">Aufgrund der Unterschiede zwischen Desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="97ac2-275">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="97ac2-276">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-276">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktop Client](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="97ac2-278">Auf IOS wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-278">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im IOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="97ac2-280">Probleme:</span><span class="sxs-lookup"><span data-stu-id="97ac2-280">Issues:</span></span>

* <span data-ttu-id="97ac2-281">Zeichenformatierungen wie Fett und kursiv werden auf IOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="97ac2-281">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="97ac2-282">Auf Android wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="97ac2-282">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="97ac2-284">Zeichenformatierungen wie Fett und kursiv werden auf Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="97ac2-284">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="97ac2-285">Formatierungs Beispiel für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="97ac2-285">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="97ac2-286">Diese Screenshots wurden mit Microsoft Teams AppStudio erstellt, wobei die Text-Eigenschaft einer Hero Card auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="97ac2-286">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="97ac2-287">Sie können die Formatierung in ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="97ac2-287">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
