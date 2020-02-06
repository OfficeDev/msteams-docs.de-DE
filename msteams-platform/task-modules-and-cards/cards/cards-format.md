---
title: Text Formatierung in Karten
description: Beschreibt die Formatierung von Karten Texten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: eb8aa13b9e75d08dadd5e615029a9d418c6c7892
ms.sourcegitcommit: 44ac886c0ca34a16222d3991a61606f8483b8481
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "41783969"
---
# <a name="card-formatting"></a><span data-ttu-id="8eea4-104">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="8eea4-104">Card formatting</span></span>

<span data-ttu-id="8eea4-105">Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie entweder "Abschlag" oder "HTML" verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eea4-105">You can add rich text formatting to your cards using either markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="8eea4-106">Karten unterstützen die Formatierung nur in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle.</span><span class="sxs-lookup"><span data-stu-id="8eea4-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="8eea4-107">Die Formatierung kann anhand einer Teilmenge der XML-Formatierung (HTML) oder eines Abschlags je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8eea4-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="8eea4-108">Für die aktuelle AMD-Zukunftsentwicklung werden Adaptive Karten mit Abschlag Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8eea4-108">For current amd future development Adaptive cards using markdown formatting is recommended.</span></span>

<span data-ttu-id="8eea4-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendering der Karte kann sich geringfügig zwischen dem Desktop und den Clients für Mobile Teams sowie Microsoft Teams im Desktop Browser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="8eea4-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

## <a name="card-types"></a><span data-ttu-id="8eea4-110">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="8eea4-110">Card types</span></span>

<span data-ttu-id="8eea4-111">Es gibt drei Arten von Karten, die das Abschlag in Microsoft Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="8eea4-111">There are three types of cards that support Markdown in Teams:</span></span>

* <span data-ttu-id="8eea4-112">**Adaptive Karten**: das Abschlag wird sowohl im `Textblock` Feld Adaptive Karten als `Fact.Title` auch `Fact.Value`unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-112">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="8eea4-113">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-113">HTML is not supported in adaptive cards.</span></span>
* <span data-ttu-id="8eea4-114">**O365-connectorkarten**: Abschlag und limitierter HTML-Code werden in Office 365-connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-114">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>
* <span data-ttu-id="8eea4-115">**Einfache Karten**: der beschränkte HTML-Code wird unterstützt, aber in einfachen Karten wird kein Abschlag unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-115">**Simple Cards**: Limited HTML is supported, but markdown is not supported in simple cards.</span></span>

## <a name="markdown-formatting-for-adaptive-cards"></a><span data-ttu-id="8eea4-116">Abschlag Formatierung für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-116">Markdown formatting for Adaptive Cards</span></span>

 <span data-ttu-id="8eea4-117">Die unterstützten `Textblock`Format `Fact.Title` Vorlagen `Fact.Value` für und sind:</span><span class="sxs-lookup"><span data-stu-id="8eea4-117">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="8eea4-118">Format</span><span class="sxs-lookup"><span data-stu-id="8eea4-118">Style</span></span> | <span data-ttu-id="8eea4-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8eea4-119">Example</span></span> | <span data-ttu-id="8eea4-120">Markdown</span><span class="sxs-lookup"><span data-stu-id="8eea4-120">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8eea4-121">bold</span><span class="sxs-lookup"><span data-stu-id="8eea4-121">bold</span></span> | <span data-ttu-id="8eea4-122">**Bold**</span><span class="sxs-lookup"><span data-stu-id="8eea4-122">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="8eea4-123">italic</span><span class="sxs-lookup"><span data-stu-id="8eea4-123">italic</span></span> | <span data-ttu-id="8eea4-124">_Italic_</span><span class="sxs-lookup"><span data-stu-id="8eea4-124">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="8eea4-125">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-125">unordered list</span></span> | <ul><li><span data-ttu-id="8eea4-126">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-126">text</span></span></li><li><span data-ttu-id="8eea4-127">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-127">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="8eea4-128">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-128">ordered list</span></span> | <ol><li><span data-ttu-id="8eea4-129">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-129">text</span></span></li><li><span data-ttu-id="8eea4-130">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-130">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="8eea4-131">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="8eea4-131">Hyperlinks</span></span> |[<span data-ttu-id="8eea4-132">Bing</span><span class="sxs-lookup"><span data-stu-id="8eea4-132">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="8eea4-133">Die folgenden Abschlag Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-133">The following markdown tags are not supported:</span></span>

* <span data-ttu-id="8eea4-134">Header</span><span class="sxs-lookup"><span data-stu-id="8eea4-134">Headers</span></span>
* <span data-ttu-id="8eea4-135">Tabellen</span><span class="sxs-lookup"><span data-stu-id="8eea4-135">Tables</span></span>
* <span data-ttu-id="8eea4-136">Bilder</span><span class="sxs-lookup"><span data-stu-id="8eea4-136">Images</span></span>
* <span data-ttu-id="8eea4-137">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8eea4-137">Preformatted text</span></span>
* <span data-ttu-id="8eea4-138">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="8eea4-138">Blockquotes</span></span>

<span data-ttu-id="8eea4-139">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8eea4-139">Adaptive cards do not support any HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="8eea4-140">Neugliederungen für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-140">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="8eea4-141">In Listen können Sie die oder `\r` `\n` Escape-Sequenzen für "reinlines" verwenden.</span><span class="sxs-lookup"><span data-stu-id="8eea4-141">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="8eea4-142">Die `\n\n` Verwendung in einer Liste bewirkt, dass das nächste Element in der Liste eingerückt wird.</span><span class="sxs-lookup"><span data-stu-id="8eea4-142">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="8eea4-143">Wenn Sie an einer anderen Stelle im TextBlock eine Umrisse `\n\n`benötigen, verwenden Sie.</span><span class="sxs-lookup"><span data-stu-id="8eea4-143">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="8eea4-144">Unterschiede zwischen Mobilgeräten und Desktops für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-144">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="8eea4-145">Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8eea4-145">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="8eea4-146">Auf dem Desktop wird die Formatierung für das Abgleichen von adaptiven Karten in beiden Webbrowsern und in der Microsoft Teams-Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-146">On the desktop, Adaptive Card markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatieren von adaptiven Karten Abschlägen im Desktop Client](~/assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="8eea4-148">Auf IOS wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-148">On iOS, Adaptive Card markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in ios](~/assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="8eea4-150">Auf Android wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-150">On Android, Adaptive Card markdown formatting appears like this:</span></span>

![Formatierung von adaptiven Karten Abschriften in Android](~/assets/images/cards/Adaptive-markdown-Android.png)

### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="8eea4-152">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-152">For more information on Adaptive Cards</span></span>

<span data-ttu-id="8eea4-153">[Text Features in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums-und Lokalisierungsfeatures werden in Microsoft Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-153">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="8eea4-154">Formatierungs Beispiel für Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-154">Formatting sample for Adaptive cards</span></span>

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

## <a name="mention-support-within-adaptive-cards"></a><span data-ttu-id="8eea4-155">Erwähnung von Unterstützung in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-155">Mention support within Adaptive cards</span></span> 

> [!NOTE]
> <span data-ttu-id="8eea4-156">Die Erwähnung der Unterstützung in Cards wird derzeit nur in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-156">Mention support in cards is currently supported in [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="8eea4-157">Bots und Messaging-Erweiterungen können jetzt Erwähnungen innerhalb des Karteninhalts in Text Block-und FactSet-Elementen enthalten.</span><span class="sxs-lookup"><span data-stu-id="8eea4-157">Bots and Messaging extensions can now include mentions within the card content in Text Block and FactSet elements.</span></span> 

### <a name="constructing-mentions"></a><span data-ttu-id="8eea4-158">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="8eea4-158">Constructing mentions</span></span>

<span data-ttu-id="8eea4-159">Um eine Erwähnung in eine Adaptive Karte aufzunehmen, muss Ihre APP die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="8eea4-159">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="8eea4-160">`<at>username</at>`in den unterstützten Adaptive Card-Elementen</span><span class="sxs-lookup"><span data-stu-id="8eea4-160">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="8eea4-161">Das `mention` Objekt innerhalb einer `msteams` Eigenschaft im Karteninhalt, das die Teams-Benutzer-ID des erwähnten Benutzers enthält</span><span class="sxs-lookup"><span data-stu-id="8eea4-161">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

<span data-ttu-id="8eea4-162">Beachten Sie, dass derzeit keine Karten mit Erwähnungen auf mobilen Clients unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="8eea4-162">Note that cards with mentions aren't supported on mobile clients at the moment.</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="8eea4-163">Beispiel Adaptive Karte mit Erwähnung</span><span class="sxs-lookup"><span data-stu-id="8eea4-163">Sample Adaptive card with a mention</span></span>

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

## <a name="html-formatting-for-connector-cards"></a><span data-ttu-id="8eea4-164">HTML-Formatierung für Verbindungskarten</span><span class="sxs-lookup"><span data-stu-id="8eea4-164">HTML formatting for Connector Cards</span></span>

<span data-ttu-id="8eea4-165">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8eea4-165">Connector cards support limited markdown and HTML formatting.</span></span> <span data-ttu-id="8eea4-166">Das Abschlag wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8eea4-166">Markdown is described in the next section.</span></span>

| <span data-ttu-id="8eea4-167">Format</span><span class="sxs-lookup"><span data-stu-id="8eea4-167">Style</span></span> | <span data-ttu-id="8eea4-168">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8eea4-168">Example</span></span> | <span data-ttu-id="8eea4-169">HTML</span><span class="sxs-lookup"><span data-stu-id="8eea4-169">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8eea4-170">bold</span><span class="sxs-lookup"><span data-stu-id="8eea4-170">bold</span></span> | <span data-ttu-id="8eea4-171">**text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-171">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="8eea4-172">italic</span><span class="sxs-lookup"><span data-stu-id="8eea4-172">italic</span></span> | <span data-ttu-id="8eea4-173">*text*</span><span class="sxs-lookup"><span data-stu-id="8eea4-173">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="8eea4-174">Kopfzeile (Ebenen 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="8eea4-174">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8eea4-175">**Text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-175">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="8eea4-176">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="8eea4-176">strikethrough</span></span> | <span data-ttu-id="8eea4-177">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8eea4-177">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="8eea4-178">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-178">unordered list</span></span> | <ul><li><span data-ttu-id="8eea4-179">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-179">text</span></span></li><li><span data-ttu-id="8eea4-180">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-180">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="8eea4-181">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-181">ordered list</span></span> | <ol><li><span data-ttu-id="8eea4-182">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-182">text</span></span></li><li><span data-ttu-id="8eea4-183">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-183">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="8eea4-184">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8eea4-184">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="8eea4-185">blockquote</span><span class="sxs-lookup"><span data-stu-id="8eea4-185">blockquote</span></span> | <blockquote><span data-ttu-id="8eea4-186">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-186">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="8eea4-187">Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-187">hyperlink</span></span> | [<span data-ttu-id="8eea4-188">Bing</span><span class="sxs-lookup"><span data-stu-id="8eea4-188">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="8eea4-189">Bild Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-189">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="8eea4-190">In connectorkarten werden die Neubuchungen in HTML mithilfe des `<p>` -Tags gerendert.</span><span class="sxs-lookup"><span data-stu-id="8eea4-190">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="8eea4-191">Unterschiede zwischen Mobiltelefonen und Desktops für connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="8eea4-191">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="8eea4-192">Auf dem Desktop sieht die HTML-Formatierung für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-192">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Desktop Client](~/assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="8eea4-194">Auf IOS sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-194">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im IOS-Client](~/assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="8eea4-196">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8eea4-196">Issues:</span></span>

* <span data-ttu-id="8eea4-197">Inline Bilder werden nicht in ios unter Verwendung von "Abschlag" oder "HTML in"-Steckkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="8eea4-197">Inline images are not rendered on iOS using either markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="8eea4-198">Vorformatierter Text wird gerendert, weist jedoch keinen grauen Hintergrund auf.</span><span class="sxs-lookup"><span data-stu-id="8eea4-198">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="8eea4-199">Auf Android sieht HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-199">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Android-Client](~/assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="8eea4-201">Formatierungs Beispiel für HTML-Verbindungskarten</span><span class="sxs-lookup"><span data-stu-id="8eea4-201">Formatting sample for HTML Connector Cards</span></span>

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

## <a name="markdown-formatting-for-connector-cards"></a><span data-ttu-id="8eea4-202">Abschlag Formatierung für connectorkarten</span><span class="sxs-lookup"><span data-stu-id="8eea4-202">Markdown formatting for Connector Cards</span></span>

<span data-ttu-id="8eea4-203">Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8eea4-203">Connector cards support limited markdown and HTML formatting.</span></span> <span data-ttu-id="8eea4-204">HTML wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8eea4-204">HTML is described in the last section.</span></span>

| <span data-ttu-id="8eea4-205">Format</span><span class="sxs-lookup"><span data-stu-id="8eea4-205">Style</span></span> | <span data-ttu-id="8eea4-206">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8eea4-206">Example</span></span> | <span data-ttu-id="8eea4-207">Markdown</span><span class="sxs-lookup"><span data-stu-id="8eea4-207">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8eea4-208">bold</span><span class="sxs-lookup"><span data-stu-id="8eea4-208">bold</span></span> | <span data-ttu-id="8eea4-209">**text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-209">**text**</span></span> | `**text**` |
| <span data-ttu-id="8eea4-210">italic</span><span class="sxs-lookup"><span data-stu-id="8eea4-210">italic</span></span> | <span data-ttu-id="8eea4-211">*text*</span><span class="sxs-lookup"><span data-stu-id="8eea4-211">*text*</span></span> | `*text*` |
| <span data-ttu-id="8eea4-212">Kopfzeile (Ebenen 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="8eea4-212">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8eea4-213">**Text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-213">**Text**</span></span> | `### Text`|
| <span data-ttu-id="8eea4-214">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="8eea4-214">strikethrough</span></span> | <span data-ttu-id="8eea4-215">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8eea4-215">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="8eea4-216">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-216">unordered list</span></span> | <ul><li><span data-ttu-id="8eea4-217">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-217">text</span></span></li><li><span data-ttu-id="8eea4-218">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-218">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="8eea4-219">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-219">ordered list</span></span> | <ol><li><span data-ttu-id="8eea4-220">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-220">text</span></span></li><li><span data-ttu-id="8eea4-221">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-221">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="8eea4-222">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8eea4-222">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="8eea4-223">blockquote</span><span class="sxs-lookup"><span data-stu-id="8eea4-223">blockquote</span></span> | <span data-ttu-id="8eea4-224">>blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="8eea4-224">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="8eea4-225">Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-225">hyperlink</span></span> | [<span data-ttu-id="8eea4-226">Bing</span><span class="sxs-lookup"><span data-stu-id="8eea4-226">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="8eea4-227">Bild Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-227">image link</span></span> |![Duck on a Rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="8eea4-229">In connectorkarten werden für die neureihen für `\n\n`, jedoch nicht für `\n` oder `\r`gerendert.</span><span class="sxs-lookup"><span data-stu-id="8eea4-229">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="8eea4-230">Unterschiede bei Mobiltelefonen und Desktops für connectorkarten mit Abschlag</span><span class="sxs-lookup"><span data-stu-id="8eea4-230">Mobile and desktop differences for connector cards using markdown</span></span>

<span data-ttu-id="8eea4-231">Auf dem Desktop sieht die Abschlag Formatierung für connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-231">On the desktop, markdown formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Desktop Client](~/assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="8eea4-233">Auf IOS sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-233">On iOS, markdown formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im IOS-Client](~/assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="8eea4-235">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8eea4-235">Issues:</span></span>

* <span data-ttu-id="8eea4-236">Der IOS-Client für Microsoft Teams rendert keine Abschlag-oder HTML-Inline Bilder in Steckkarten.</span><span class="sxs-lookup"><span data-stu-id="8eea4-236">The iOS client for Teams does not render markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="8eea4-237">Block Zitate werden als Einzüge, jedoch ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="8eea4-237">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="8eea4-238">Auf Android sieht die Abschläge für Verbindungskarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="8eea4-238">On Android, markdown formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Verbindungskarten im Android-Client](~/assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="8eea4-240">Formatierungs Beispiel für Abschlag-konnektorkarten</span><span class="sxs-lookup"><span data-stu-id="8eea4-240">Formatting example for markdown Connector Cards</span></span>

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

## <a name="html-formatting-for-simple-cards"></a><span data-ttu-id="8eea4-241">HTML-Formatierung für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-241">HTML Formatting for simple cards</span></span>

<span data-ttu-id="8eea4-242">Diese HTML-Tags werden für einfache Karten wie die Hero-und die Thumbnail-Karte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-242">These HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="8eea4-243">Abschläge werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-243">Markdown is not supported.</span></span>

| <span data-ttu-id="8eea4-244">Format</span><span class="sxs-lookup"><span data-stu-id="8eea4-244">Style</span></span> | <span data-ttu-id="8eea4-245">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8eea4-245">Example</span></span> | <span data-ttu-id="8eea4-246">HTML</span><span class="sxs-lookup"><span data-stu-id="8eea4-246">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8eea4-247">bold</span><span class="sxs-lookup"><span data-stu-id="8eea4-247">bold</span></span> | <span data-ttu-id="8eea4-248">**text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-248">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="8eea4-249">italic</span><span class="sxs-lookup"><span data-stu-id="8eea4-249">italic</span></span> | <span data-ttu-id="8eea4-250">*text*</span><span class="sxs-lookup"><span data-stu-id="8eea4-250">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="8eea4-251">Kopfzeile (Ebenen 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="8eea4-251">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8eea4-252">**Text**</span><span class="sxs-lookup"><span data-stu-id="8eea4-252">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="8eea4-253">durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="8eea4-253">strikethrough</span></span> | <span data-ttu-id="8eea4-254">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8eea4-254">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="8eea4-255">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-255">unordered list</span></span> | <ul><li><span data-ttu-id="8eea4-256">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-256">text</span></span></li><li><span data-ttu-id="8eea4-257">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-257">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="8eea4-258">sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="8eea4-258">ordered list</span></span> | <ol><li><span data-ttu-id="8eea4-259">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-259">text</span></span></li><li><span data-ttu-id="8eea4-260">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-260">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="8eea4-261">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8eea4-261">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="8eea4-262">blockquote</span><span class="sxs-lookup"><span data-stu-id="8eea4-262">blockquote</span></span> | <blockquote><span data-ttu-id="8eea4-263">text</span><span class="sxs-lookup"><span data-stu-id="8eea4-263">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="8eea4-264">Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-264">hyperlink</span></span> | [<span data-ttu-id="8eea4-265">Bing</span><span class="sxs-lookup"><span data-stu-id="8eea4-265">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="8eea4-266">Bild Link</span><span class="sxs-lookup"><span data-stu-id="8eea4-266">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="8eea4-267">Unterschiede zwischen Mobilgeräten und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-267">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="8eea4-268">Aufgrund der Unterschiede zwischen Desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8eea4-268">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="8eea4-269">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-269">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktop Client](~/assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="8eea4-271">Auf IOS wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-271">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im IOS-Client](~/assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="8eea4-273">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8eea4-273">Issues:</span></span>

* <span data-ttu-id="8eea4-274">Zeichenformatierungen wie Fett und kursiv werden auf IOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="8eea4-274">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="8eea4-275">Auf Android wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8eea4-275">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](~/assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="8eea4-277">Zeichenformatierungen wie Fett und kursiv werden auf Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8eea4-277">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="8eea4-278">Formatierungs Beispiel für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="8eea4-278">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="8eea4-279">Diese Screenshots wurden mit Microsoft Teams AppStudio erstellt, wobei die Text-Eigenschaft einer Hero Card auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="8eea4-279">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="8eea4-280">Sie können die Formatierung in ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="8eea4-280">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`
