---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentexten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: d7016f8b954e885221c55bd6c29309fd90a1dcfc
ms.sourcegitcommit: d41da0b608327829b902aded6bc85c0d0016d068
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "51474999"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="c606f-104">Formatieren von Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="c606f-104">Format cards in Teams</span></span>

<span data-ttu-id="c606f-105">Je nach Kartentyp können Sie Ihren Karten mithilfe von Markdown oder HTML Rich-Text-Formatierungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c606f-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="c606f-106">Karten unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln.</span><span class="sxs-lookup"><span data-stu-id="c606f-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="c606f-107">Die Formatierung kann mit einer Teilmenge der XML-Formatierung (HTML) oder Markdown je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c606f-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="c606f-108">Für die aktuelle und zukünftige Entwicklung wird adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="c606f-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="c606f-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser geringfügig variieren.</span><span class="sxs-lookup"><span data-stu-id="c606f-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="c606f-110">Sie können ein Inlinebild mit einer beliebigen Teams-Karte verwenden.</span><span class="sxs-lookup"><span data-stu-id="c606f-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="c606f-111">Bilder, die als , oder Dateien formatiert werden und  `.png` `.jpg` dürfen `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="c606f-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="c606f-112">Animierte GIF wird offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="c606f-113">*Siehe Kartenreferenz* [](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="c606f-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="c606f-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="c606f-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="c606f-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="c606f-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c606f-116">**Adaptive Karten:** Markdown wird im Feld Adaptive Karte sowie `Textblock` und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="c606f-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="c606f-118">**O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="c606f-119">**Markdownformatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="c606f-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="c606f-120">Die unterstützten Formatvorlagen für `Textblock` und `Fact.Title` `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="c606f-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="c606f-121">Format</span><span class="sxs-lookup"><span data-stu-id="c606f-121">Style</span></span> | <span data-ttu-id="c606f-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c606f-122">Example</span></span> | <span data-ttu-id="c606f-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="c606f-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="c606f-124">bold</span><span class="sxs-lookup"><span data-stu-id="c606f-124">bold</span></span> | <span data-ttu-id="c606f-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="c606f-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="c606f-126">italic</span><span class="sxs-lookup"><span data-stu-id="c606f-126">italic</span></span> | <span data-ttu-id="c606f-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="c606f-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="c606f-128">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-128">unordered list</span></span> | <ul><li><span data-ttu-id="c606f-129">text</span><span class="sxs-lookup"><span data-stu-id="c606f-129">text</span></span></li><li><span data-ttu-id="c606f-130">text</span><span class="sxs-lookup"><span data-stu-id="c606f-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="c606f-131">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-131">ordered list</span></span> | <ol><li><span data-ttu-id="c606f-132">text</span><span class="sxs-lookup"><span data-stu-id="c606f-132">text</span></span></li><li><span data-ttu-id="c606f-133">text</span><span class="sxs-lookup"><span data-stu-id="c606f-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="c606f-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="c606f-134">Hyperlinks</span></span> |[<span data-ttu-id="c606f-135">Bing</span><span class="sxs-lookup"><span data-stu-id="c606f-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="c606f-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="c606f-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="c606f-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="c606f-137">Headers</span></span>
* <span data-ttu-id="c606f-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="c606f-138">Tables</span></span>
* <span data-ttu-id="c606f-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="c606f-139">Images</span></span>
* <span data-ttu-id="c606f-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="c606f-140">Preformatted text</span></span>
* <span data-ttu-id="c606f-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="c606f-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c606f-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="c606f-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="c606f-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="c606f-144">In Listen können Sie die `\r` Escapesequenzen für `\n` Newlines verwenden.</span><span class="sxs-lookup"><span data-stu-id="c606f-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="c606f-145">Wenn Sie in einer Liste verwenden, wird das nächste Element in der Liste `\n\n` eingezogen.</span><span class="sxs-lookup"><span data-stu-id="c606f-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="c606f-146">Wenn Sie Newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="c606f-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="c606f-147">Unterschiede zwischen Mobilen und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="c606f-148">Die Formatierung ist zwischen dem Desktop und den mobilen Versionen von Teams geringfügig unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="c606f-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="c606f-149">Auf dem Desktop wird die Formatierung der adaptiven Karten-Markdown in webbrowsern und in der Teams-Clientanwendung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c606f-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatierung der adaptiven Karte Markdown im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="c606f-151">Unter iOS sieht die Formatierung der adaptiven Karten-Markdown wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Formatierung der adaptiven Karte Markdown in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="c606f-153">Unter Android wird die Formatierung der adaptiven Karten-Markdown wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c606f-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Adaptive Karten-Markdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="c606f-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-155">More information on Adaptive cards</span></span>

<span data-ttu-id="c606f-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="c606f-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-157">Formatting sample for Adaptive cards</span></span>

``` json
{
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
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
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="c606f-158">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="c606f-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="c606f-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="c606f-160">Sie können @-Erwähnungen in einem adaptiven Kartentext für Bots und Nachrichtenerweiterungsantworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c606f-160">You can add @ mentions within an Adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="c606f-161">Um @-Erwähnungen in Karten hinzuzufügen, folgen Sie derselben Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte Erwähnungen in Kanal- und [Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions )</span><span class="sxs-lookup"><span data-stu-id="c606f-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="c606f-162">Bots und Messagingerweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="c606f-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="c606f-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="c606f-164">Channel & Team erwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="c606f-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="c606f-165">Constructing mentions</span></span>

<span data-ttu-id="c606f-166">Um eine Erwähnung in einer adaptiven Karte zu verwenden, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="c606f-166">To include a mention in an Adaptive card your app needs to include the following elements</span></span>

* <span data-ttu-id="c606f-167">`<at>username</at>` in den unterstützten adaptiven Kartenelementen</span><span class="sxs-lookup"><span data-stu-id="c606f-167">`<at>username</at>` in the supported Adaptive card elements</span></span>
* <span data-ttu-id="c606f-168">Das Objekt innerhalb einer Eigenschaft im Karteninhalt, die die `mention` `msteams` Teams-Benutzer-ID des erwähnten Benutzers enthält</span><span class="sxs-lookup"><span data-stu-id="c606f-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="c606f-169">Beispiel für adaptive Karte mit erwähnung</span><span class="sxs-lookup"><span data-stu-id="c606f-169">Sample Adaptive card with a mention</span></span>

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
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
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


### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="c606f-170">Informationsmasken in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-170">Information masking in Adaptive cards</span></span>
<span data-ttu-id="c606f-171">Verwenden Sie die Informationsmaskeneigenschaft, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) adaptiver Karten.</span><span class="sxs-lookup"><span data-stu-id="c606f-171">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="c606f-172">Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration angegeben wurde.](../../build-your-first-app/build-bot.md#4-configure-your-bot)</span><span class="sxs-lookup"><span data-stu-id="c606f-172">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md#4-configure-your-bot).</span></span> 

> [!NOTE]
> <span data-ttu-id="c606f-173">Die Informationsmaskeneigenschaft ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c606f-173">The information masking property is currently available in the developer preview only.</span></span>

<span data-ttu-id="c606f-174">Um Informationen in adaptiven Karten zu maskieren, fügen Sie die Eigenschaft zum Eingeben `isMasked`  `Input.Text` hinzu, und legen Sie den Wert auf *true .*</span><span class="sxs-lookup"><span data-stu-id="c606f-174">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="c606f-175">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="c606f-175">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="c606f-176">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="c606f-176">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskieren eines Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="c606f-178">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="c606f-178">Full width Adaptive card</span></span>
<span data-ttu-id="c606f-179">Sie können die Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und `msteams` zusätzlichen Canvasbereich zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="c606f-179">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="c606f-180">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c606f-180">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="c606f-181">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="c606f-181">Constructing full width cards</span></span>
<span data-ttu-id="c606f-182">Um eine adaptive Karte mit voller Breite zu erstellen, muss das Objekt in der Eigenschaft im Karteninhalt `width` `msteams` auf festgelegt `Full` werden.</span><span class="sxs-lookup"><span data-stu-id="c606f-182">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="c606f-183">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="c606f-183">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="c606f-184">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="c606f-184">Sample adaptive card with full width</span></span>

``` json
{
    "type": "AdaptiveCard",
    "body": [{
        "type": "Container",
        "items": [{
            "type": "TextBlock",
            "text": "Digest card",
            "size": "Large",
            "weight": "Bolder"
        }]
    }],

    "msteams": {
        "width": "Full"
    },
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

<span data-ttu-id="c606f-185">Eine adaptive Karte mit voller Breite wird wie folgt ![ angezeigt: Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="c606f-185">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="c606f-186">Wenn Sie die Eigenschaft nicht auf Vollständig festgelegt haben, lautet die Standardansicht der adaptiven Karte wie folgt: Adaptive Kartenansicht mit geringer `width`  ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="c606f-186">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="c606f-187">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="c606f-187">Typeahead support</span></span>

<span data-ttu-id="c606f-188">Innerhalb des Schemaelements kann das Durchfiltern und Auswählen durch eine ansehnliche Anzahl von Auswahlmöglichkeiten den [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Aufgabenabschluss erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="c606f-188">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="c606f-189">Die Typaheadunterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl beim Eingeben durch einen Benutzer ein- oder gefiltert wird.</span><span class="sxs-lookup"><span data-stu-id="c606f-189">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="c606f-190">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-190">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="c606f-191">So aktivieren Sie typeahead innerhalb der `Input.Choiceset` Gruppe `style` `filtered` auf, und stellen Sie sicher, `isMultiSelect` dass auf festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="c606f-191">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="c606f-192">Beispiel für adaptive Karte mit Typaheadunterstützung</span><span class="sxs-lookup"><span data-stu-id="c606f-192">Sample adaptive card with typeahead support</span></span>

``` json
{
   "type": "Input.ChoiceSet",
   "label": "Select a user",
   "isMultiSelect": false,
   "choices":  [
      { "title": "User 1", "value": "User1" },
      { "title": "User 2", "value": "User2" }
    ],
   "style": "filtered"
}
``` 

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="c606f-193">Schrittansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-193">Stage view for images in Adaptive Cards</span></span>

> [!NOTE]
> <span data-ttu-id="c606f-194">Dieses Feature ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c606f-194">This feature is currently available in developer preview only.</span></span>
 
<span data-ttu-id="c606f-195">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von Bildern `msteams` in der Ansicht der Stufe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c606f-195">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="c606f-196">Wenn Benutzer den Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="c606f-196">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="c606f-197">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c606f-197">For information on how to use the property, see the following example:</span></span>

``` json
{
    "type": "AdaptiveCard",
     "body": [
          {
            "type": "Image",
            "url": "https://picsum.photos/200/200?image=110",
            "msTeams": {
              "allowExpand": true
            }
          },
     ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

<span data-ttu-id="c606f-198">Wenn Benutzer auf das Bild zeigen, wird oben rechts im Bild ein Erweiterungssymbol ![ angezeigt: Adaptive Karte mit erweiterbaren Bildern](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="c606f-198">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="c606f-199">Das Bild wird in der Ansicht "Stage" angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: Bild wird in ![ die Ansicht "Stage" erweitert.](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="c606f-199">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="c606f-200">In der Abschnittsansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="c606f-200">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="c606f-201">Sie können auswählen, welche Bilder auf Ihrer adaptiven Karte über diese Funktion verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="c606f-201">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="c606f-202">Die Zoom- und Zoom-Out-Funktion gilt nur für die Bildelemente (Bildtyp) in einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="c606f-202">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="c606f-203">Für mobile Teams-Apps sind die Funktionen für die Stage View für Bilder in adaptiven Karten standardmäßig verfügbar, und Benutzer können adaptive Kartenbilder in der Ansicht der Stufe anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das Attribut vorhanden ist `allowExpand` oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c606f-203">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="c606f-204">**Markdownformatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="c606f-204">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="c606f-205">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="c606f-205">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="c606f-206">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c606f-206">HTML support is described in the last section.</span></span>

| <span data-ttu-id="c606f-207">Format</span><span class="sxs-lookup"><span data-stu-id="c606f-207">Style</span></span> | <span data-ttu-id="c606f-208">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c606f-208">Example</span></span> | <span data-ttu-id="c606f-209">Markdown</span><span class="sxs-lookup"><span data-stu-id="c606f-209">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="c606f-210">bold</span><span class="sxs-lookup"><span data-stu-id="c606f-210">bold</span></span> | <span data-ttu-id="c606f-211">**text**</span><span class="sxs-lookup"><span data-stu-id="c606f-211">**text**</span></span> | `**text**` |
| <span data-ttu-id="c606f-212">italic</span><span class="sxs-lookup"><span data-stu-id="c606f-212">italic</span></span> | <span data-ttu-id="c606f-213">*text*</span><span class="sxs-lookup"><span data-stu-id="c606f-213">*text*</span></span> | `*text*` |
| <span data-ttu-id="c606f-214">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="c606f-214">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="c606f-215">**Text**</span><span class="sxs-lookup"><span data-stu-id="c606f-215">**Text**</span></span> | `### Text`|
| <span data-ttu-id="c606f-216">strikethrough</span><span class="sxs-lookup"><span data-stu-id="c606f-216">strikethrough</span></span> | <span data-ttu-id="c606f-217">~~text~~</span><span class="sxs-lookup"><span data-stu-id="c606f-217">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="c606f-218">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-218">unordered list</span></span> | <ul><li><span data-ttu-id="c606f-219">text</span><span class="sxs-lookup"><span data-stu-id="c606f-219">text</span></span></li><li><span data-ttu-id="c606f-220">text</span><span class="sxs-lookup"><span data-stu-id="c606f-220">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="c606f-221">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-221">ordered list</span></span> | <ol><li><span data-ttu-id="c606f-222">text</span><span class="sxs-lookup"><span data-stu-id="c606f-222">text</span></span></li><li><span data-ttu-id="c606f-223">text</span><span class="sxs-lookup"><span data-stu-id="c606f-223">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="c606f-224">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="c606f-224">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="c606f-225">blockquote</span><span class="sxs-lookup"><span data-stu-id="c606f-225">blockquote</span></span> | <span data-ttu-id="c606f-226">>blockquote text</span><span class="sxs-lookup"><span data-stu-id="c606f-226">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="c606f-227">Link</span><span class="sxs-lookup"><span data-stu-id="c606f-227">hyperlink</span></span> | [<span data-ttu-id="c606f-228">Bing</span><span class="sxs-lookup"><span data-stu-id="c606f-228">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="c606f-229">Bildlink</span><span class="sxs-lookup"><span data-stu-id="c606f-229">image link</span></span> |![Ente auf einem Felchen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="c606f-231">In Connectorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="c606f-231">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="c606f-232">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von Markdown</span><span class="sxs-lookup"><span data-stu-id="c606f-232">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="c606f-233">Auf dem Desktop sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-233">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="c606f-235">Unter iOS sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-235">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="c606f-237">Probleme:</span><span class="sxs-lookup"><span data-stu-id="c606f-237">Issues:</span></span>

* <span data-ttu-id="c606f-238">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="c606f-238">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="c606f-239">Blockquotes werden als eingezogen gerendert, aber ohne grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="c606f-239">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="c606f-240">Unter Android sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-240">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="c606f-242">Formatierungsbeispiel für Markdown Connector Cards</span><span class="sxs-lookup"><span data-stu-id="c606f-242">Formatting example for Markdown Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
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
            "text": "embedded image link: ![Duck on a rock](https://aka.ms/Fo983c)"
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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="c606f-243">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="c606f-243">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="c606f-244">**HTML-Formatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="c606f-244">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="c606f-245">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="c606f-245">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="c606f-246">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c606f-246">Markdown is described in the next section.</span></span>

| <span data-ttu-id="c606f-247">Format</span><span class="sxs-lookup"><span data-stu-id="c606f-247">Style</span></span> | <span data-ttu-id="c606f-248">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c606f-248">Example</span></span> | <span data-ttu-id="c606f-249">HTML</span><span class="sxs-lookup"><span data-stu-id="c606f-249">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="c606f-250">bold</span><span class="sxs-lookup"><span data-stu-id="c606f-250">bold</span></span> | <span data-ttu-id="c606f-251">**text**</span><span class="sxs-lookup"><span data-stu-id="c606f-251">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="c606f-252">italic</span><span class="sxs-lookup"><span data-stu-id="c606f-252">italic</span></span> | <span data-ttu-id="c606f-253">*text*</span><span class="sxs-lookup"><span data-stu-id="c606f-253">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="c606f-254">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="c606f-254">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="c606f-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="c606f-255">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="c606f-256">strikethrough</span><span class="sxs-lookup"><span data-stu-id="c606f-256">strikethrough</span></span> | <span data-ttu-id="c606f-257">~~text~~</span><span class="sxs-lookup"><span data-stu-id="c606f-257">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="c606f-258">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-258">unordered list</span></span> | <ul><li><span data-ttu-id="c606f-259">text</span><span class="sxs-lookup"><span data-stu-id="c606f-259">text</span></span></li><li><span data-ttu-id="c606f-260">text</span><span class="sxs-lookup"><span data-stu-id="c606f-260">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="c606f-261">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-261">ordered list</span></span> | <ol><li><span data-ttu-id="c606f-262">text</span><span class="sxs-lookup"><span data-stu-id="c606f-262">text</span></span></li><li><span data-ttu-id="c606f-263">text</span><span class="sxs-lookup"><span data-stu-id="c606f-263">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="c606f-264">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="c606f-264">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="c606f-265">blockquote</span><span class="sxs-lookup"><span data-stu-id="c606f-265">blockquote</span></span> | <blockquote><span data-ttu-id="c606f-266">text</span><span class="sxs-lookup"><span data-stu-id="c606f-266">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="c606f-267">Link</span><span class="sxs-lookup"><span data-stu-id="c606f-267">hyperlink</span></span> | [<span data-ttu-id="c606f-268">Bing</span><span class="sxs-lookup"><span data-stu-id="c606f-268">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="c606f-269">Bildlink</span><span class="sxs-lookup"><span data-stu-id="c606f-269">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="c606f-270">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="c606f-270">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="c606f-271">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="c606f-271">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="c606f-272">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-272">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="c606f-274">Unter iOS sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-274">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="c606f-276">Probleme:</span><span class="sxs-lookup"><span data-stu-id="c606f-276">Issues:</span></span>

* <span data-ttu-id="c606f-277">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in ConnectorKarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="c606f-277">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="c606f-278">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="c606f-278">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="c606f-279">Unter Android sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="c606f-279">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="c606f-281">Formatierungsbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="c606f-281">Formatting sample for HTML Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
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
            "text": "embedded image <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="c606f-282">**HTML-Formatierung: Hero- und Miniaturansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="c606f-282">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="c606f-283">HTML-Tags werden für einfache Karten wie die Held- und Miniaturansichtskarte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-283">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="c606f-284">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c606f-284">Markdown is not supported.</span></span>

| <span data-ttu-id="c606f-285">Format</span><span class="sxs-lookup"><span data-stu-id="c606f-285">Style</span></span> | <span data-ttu-id="c606f-286">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c606f-286">Example</span></span> | <span data-ttu-id="c606f-287">HTML</span><span class="sxs-lookup"><span data-stu-id="c606f-287">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="c606f-288">bold</span><span class="sxs-lookup"><span data-stu-id="c606f-288">bold</span></span> | <span data-ttu-id="c606f-289">**text**</span><span class="sxs-lookup"><span data-stu-id="c606f-289">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="c606f-290">italic</span><span class="sxs-lookup"><span data-stu-id="c606f-290">italic</span></span> | <span data-ttu-id="c606f-291">*text*</span><span class="sxs-lookup"><span data-stu-id="c606f-291">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="c606f-292">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="c606f-292">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="c606f-293">**Text**</span><span class="sxs-lookup"><span data-stu-id="c606f-293">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="c606f-294">strikethrough</span><span class="sxs-lookup"><span data-stu-id="c606f-294">strikethrough</span></span> | <span data-ttu-id="c606f-295">~~text~~</span><span class="sxs-lookup"><span data-stu-id="c606f-295">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="c606f-296">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-296">unordered list</span></span> | <ul><li><span data-ttu-id="c606f-297">text</span><span class="sxs-lookup"><span data-stu-id="c606f-297">text</span></span></li><li><span data-ttu-id="c606f-298">text</span><span class="sxs-lookup"><span data-stu-id="c606f-298">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="c606f-299">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="c606f-299">ordered list</span></span> | <ol><li><span data-ttu-id="c606f-300">text</span><span class="sxs-lookup"><span data-stu-id="c606f-300">text</span></span></li><li><span data-ttu-id="c606f-301">text</span><span class="sxs-lookup"><span data-stu-id="c606f-301">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="c606f-302">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="c606f-302">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="c606f-303">blockquote</span><span class="sxs-lookup"><span data-stu-id="c606f-303">blockquote</span></span> | <blockquote><span data-ttu-id="c606f-304">text</span><span class="sxs-lookup"><span data-stu-id="c606f-304">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="c606f-305">Link</span><span class="sxs-lookup"><span data-stu-id="c606f-305">hyperlink</span></span> | [<span data-ttu-id="c606f-306">Bing</span><span class="sxs-lookup"><span data-stu-id="c606f-306">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="c606f-307">Bildlink</span><span class="sxs-lookup"><span data-stu-id="c606f-307">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="c606f-308">Unterschiede zwischen Mobilen und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-308">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="c606f-309">Aufgrund von Auflösungsunterschieden zwischen dem Desktop und der mobilen Plattform unterscheiden sich die Formatierungen zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="c606f-309">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="c606f-310">Auf dem Desktop wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c606f-310">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="c606f-312">Unter iOS wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c606f-312">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="c606f-314">Probleme:</span><span class="sxs-lookup"><span data-stu-id="c606f-314">Issues:</span></span>

* <span data-ttu-id="c606f-315">Zeichenformatierungen wie fett und italisch werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="c606f-315">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="c606f-316">Unter Android wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c606f-316">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="c606f-318">Zeichenformatierung wie fett und italisch wird unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c606f-318">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="c606f-319">Formatierungsbeispiel für die HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="c606f-319">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="c606f-320">Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="c606f-320">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="c606f-321">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="c606f-321">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
