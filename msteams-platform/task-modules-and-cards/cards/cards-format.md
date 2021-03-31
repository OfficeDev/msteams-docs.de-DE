---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentexten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: 240481f6deaa9246692ca297712bd311fbd9405d
ms.sourcegitcommit: 2bf651dfbaf5dbab6d466788f668e7a6c5d69c36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "51421622"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="145d9-104">Formatieren von Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="145d9-104">Format cards in Teams</span></span>

<span data-ttu-id="145d9-105">Je nach Kartentyp können Sie Ihren Karten mithilfe von Markdown oder HTML Rich-Text-Formatierungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="145d9-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="145d9-106">Karten unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln.</span><span class="sxs-lookup"><span data-stu-id="145d9-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="145d9-107">Die Formatierung kann mit einer Teilmenge der XML-Formatierung (HTML) oder Markdown je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="145d9-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="145d9-108">Für die aktuelle und zukünftige Entwicklung wird adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="145d9-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="145d9-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser geringfügig variieren.</span><span class="sxs-lookup"><span data-stu-id="145d9-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="145d9-110">Sie können ein Inlinebild mit einer beliebigen Teams-Karte verwenden.</span><span class="sxs-lookup"><span data-stu-id="145d9-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="145d9-111">Bilder, die als , oder Dateien formatiert werden und  `.png` `.jpg` dürfen `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="145d9-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="145d9-112">Animierte GIF wird offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="145d9-113">*Siehe Kartenreferenz* [](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="145d9-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="145d9-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="145d9-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="145d9-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="145d9-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="145d9-116">**Adaptive Karten:** Markdown wird im Feld Adaptive Karte sowie `Textblock` und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="145d9-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="145d9-118">**O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="145d9-119">**Markdownformatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="145d9-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="145d9-120">Die unterstützten Formatvorlagen für `Textblock` und `Fact.Title` `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="145d9-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="145d9-121">Format</span><span class="sxs-lookup"><span data-stu-id="145d9-121">Style</span></span> | <span data-ttu-id="145d9-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="145d9-122">Example</span></span> | <span data-ttu-id="145d9-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="145d9-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="145d9-124">bold</span><span class="sxs-lookup"><span data-stu-id="145d9-124">bold</span></span> | <span data-ttu-id="145d9-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="145d9-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="145d9-126">italic</span><span class="sxs-lookup"><span data-stu-id="145d9-126">italic</span></span> | <span data-ttu-id="145d9-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="145d9-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="145d9-128">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-128">unordered list</span></span> | <ul><li><span data-ttu-id="145d9-129">text</span><span class="sxs-lookup"><span data-stu-id="145d9-129">text</span></span></li><li><span data-ttu-id="145d9-130">text</span><span class="sxs-lookup"><span data-stu-id="145d9-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="145d9-131">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-131">ordered list</span></span> | <ol><li><span data-ttu-id="145d9-132">text</span><span class="sxs-lookup"><span data-stu-id="145d9-132">text</span></span></li><li><span data-ttu-id="145d9-133">text</span><span class="sxs-lookup"><span data-stu-id="145d9-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="145d9-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="145d9-134">Hyperlinks</span></span> |[<span data-ttu-id="145d9-135">Bing</span><span class="sxs-lookup"><span data-stu-id="145d9-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="145d9-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="145d9-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="145d9-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="145d9-137">Headers</span></span>
* <span data-ttu-id="145d9-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="145d9-138">Tables</span></span>
* <span data-ttu-id="145d9-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="145d9-139">Images</span></span>
* <span data-ttu-id="145d9-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="145d9-140">Preformatted text</span></span>
* <span data-ttu-id="145d9-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="145d9-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="145d9-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="145d9-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="145d9-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="145d9-144">In Listen können Sie die `\r` Escapesequenzen für `\n` Newlines verwenden.</span><span class="sxs-lookup"><span data-stu-id="145d9-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="145d9-145">Wenn Sie in einer Liste verwenden, wird das nächste Element in der Liste `\n\n` eingezogen.</span><span class="sxs-lookup"><span data-stu-id="145d9-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="145d9-146">Wenn Sie Newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="145d9-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="145d9-147">Unterschiede zwischen Mobilen und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="145d9-148">Die Formatierung ist zwischen dem Desktop und den mobilen Versionen von Teams geringfügig unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="145d9-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="145d9-149">Auf dem Desktop wird die Formatierung der adaptiven Karten-Markdown in webbrowsern und in der Teams-Clientanwendung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="145d9-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatierung der adaptiven Karte Markdown im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="145d9-151">Unter iOS sieht die Formatierung der adaptiven Karten-Markdown wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Formatierung der adaptiven Karte Markdown in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="145d9-153">Unter Android wird die Formatierung der adaptiven Karten-Markdown wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="145d9-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Adaptive Karten-Markdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="145d9-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-155">More information on Adaptive cards</span></span>

<span data-ttu-id="145d9-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="145d9-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="145d9-158">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="145d9-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="145d9-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="145d9-160">Sie können @-Erwähnungen in einem adaptiven Kartentext für Bots und Nachrichtenerweiterungsantworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="145d9-160">You can add @ mentions within an Adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="145d9-161">Um @-Erwähnungen in Karten hinzuzufügen, folgen Sie derselben Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte Erwähnungen in Kanal- und [Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions )</span><span class="sxs-lookup"><span data-stu-id="145d9-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="145d9-162">Bots und Messagingerweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="145d9-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="145d9-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="145d9-164">Channel & Team erwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="145d9-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="145d9-165">Constructing mentions</span></span>

<span data-ttu-id="145d9-166">Um eine Erwähnung in einer adaptiven Karte zu verwenden, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="145d9-166">To include a mention in an Adaptive card your app needs to include the following elements</span></span>

* <span data-ttu-id="145d9-167">`<at>username</at>` in den unterstützten adaptiven Kartenelementen</span><span class="sxs-lookup"><span data-stu-id="145d9-167">`<at>username</at>` in the supported Adaptive card elements</span></span>
* <span data-ttu-id="145d9-168">Das Objekt innerhalb einer Eigenschaft im Karteninhalt, die die `mention` `msteams` Teams-Benutzer-ID des erwähnten Benutzers enthält</span><span class="sxs-lookup"><span data-stu-id="145d9-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="145d9-169">Beispiel für adaptive Karte mit erwähnung</span><span class="sxs-lookup"><span data-stu-id="145d9-169">Sample Adaptive card with a mention</span></span>

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


### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="145d9-170">Informationsmasken in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-170">Information masking in Adaptive cards</span></span>
<span data-ttu-id="145d9-171">Verwenden Sie die Informationsmaskeneigenschaft, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) adaptiver Karten.</span><span class="sxs-lookup"><span data-stu-id="145d9-171">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="145d9-172">Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration angegeben wurde.](../../build-your-first-app/build-bot.md#4-configure-your-bot)</span><span class="sxs-lookup"><span data-stu-id="145d9-172">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md#4-configure-your-bot).</span></span> 

> [!NOTE]
> <span data-ttu-id="145d9-173">Die Informationsmaskeneigenschaft ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="145d9-173">The information masking property is currently available in the developer preview only.</span></span>

<span data-ttu-id="145d9-174">Um Informationen in adaptiven Karten zu maskieren, fügen Sie die Eigenschaft zum Eingeben `isMasked`  `Input.Text` hinzu, und legen Sie den Wert auf *true .*</span><span class="sxs-lookup"><span data-stu-id="145d9-174">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="145d9-175">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="145d9-175">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="145d9-176">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="145d9-176">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskieren eines Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="145d9-178">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="145d9-178">Full width Adaptive card</span></span>
<span data-ttu-id="145d9-179">Sie können die Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und `msteams` zusätzlichen Canvasbereich zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="145d9-179">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="145d9-180">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="145d9-180">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="145d9-181">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="145d9-181">Constructing full width cards</span></span>
<span data-ttu-id="145d9-182">Um eine adaptive Karte mit voller Breite zu erstellen, muss das Objekt in der Eigenschaft im Karteninhalt `width` `msteams` auf festgelegt `Full` werden.</span><span class="sxs-lookup"><span data-stu-id="145d9-182">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="145d9-183">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="145d9-183">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="145d9-184">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="145d9-184">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="145d9-185">Eine adaptive Karte mit voller Breite wird wie folgt ![ angezeigt: Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="145d9-185">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="145d9-186">Wenn Sie die Eigenschaft nicht auf Vollständig festgelegt haben, lautet die Standardansicht der adaptiven Karte wie folgt: Adaptive Kartenansicht mit geringer `width`  ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="145d9-186">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="145d9-187">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="145d9-187">Typeahead support</span></span>

<span data-ttu-id="145d9-188">Innerhalb des Schemaelements kann das Durchfiltern und Auswählen durch eine ansehnliche Anzahl von Auswahlmöglichkeiten den [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Aufgabenabschluss erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="145d9-188">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="145d9-189">Die Typaheadunterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl beim Eingeben durch einen Benutzer ein- oder gefiltert wird.</span><span class="sxs-lookup"><span data-stu-id="145d9-189">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="145d9-190">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-190">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="145d9-191">So aktivieren Sie typeahead innerhalb der `Input.Choiceset` Gruppe `style` `filtered` auf, und stellen Sie sicher, `isMultiSelect` dass auf festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="145d9-191">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="145d9-192">Beispiel für adaptive Karte mit Typaheadunterstützung</span><span class="sxs-lookup"><span data-stu-id="145d9-192">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="145d9-193">Schrittansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-193">Stage view for images in Adaptive Cards</span></span>
<span data-ttu-id="145d9-194">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von Bildern `msteams` in der Ansicht der Stufe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="145d9-194">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="145d9-195">Wenn Benutzer den Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="145d9-195">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="145d9-196">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="145d9-196">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="145d9-197">Wenn Benutzer auf das Bild zeigen, wird oben rechts im Bild ein Erweiterungssymbol ![ angezeigt: Adaptive Karte mit erweiterbaren Bildern](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="145d9-197">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="145d9-198">Das Bild wird in der Ansicht "Stage" angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: Bild wird in ![ die Ansicht "Stage" erweitert.](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="145d9-198">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="145d9-199">In der Abschnittsansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="145d9-199">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="145d9-200">Sie können auswählen, welche Bilder auf Ihrer adaptiven Karte über diese Funktion verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="145d9-200">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="145d9-201">Die Zoom- und Zoom-Out-Funktion gilt nur für die Bildelemente (Bildtyp) in einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="145d9-201">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="145d9-202">Für mobile Teams-Apps sind die Funktionen für die Stage View für Bilder in adaptiven Karten standardmäßig verfügbar, und Benutzer können adaptive Kartenbilder in der Ansicht der Stufe anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das Attribut vorhanden ist `allowExpand` oder nicht.</span><span class="sxs-lookup"><span data-stu-id="145d9-202">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="145d9-203">**Markdownformatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="145d9-203">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="145d9-204">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="145d9-204">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="145d9-205">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="145d9-205">HTML support is described in the last section.</span></span>

| <span data-ttu-id="145d9-206">Format</span><span class="sxs-lookup"><span data-stu-id="145d9-206">Style</span></span> | <span data-ttu-id="145d9-207">Beispiel</span><span class="sxs-lookup"><span data-stu-id="145d9-207">Example</span></span> | <span data-ttu-id="145d9-208">Markdown</span><span class="sxs-lookup"><span data-stu-id="145d9-208">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="145d9-209">bold</span><span class="sxs-lookup"><span data-stu-id="145d9-209">bold</span></span> | <span data-ttu-id="145d9-210">**text**</span><span class="sxs-lookup"><span data-stu-id="145d9-210">**text**</span></span> | `**text**` |
| <span data-ttu-id="145d9-211">italic</span><span class="sxs-lookup"><span data-stu-id="145d9-211">italic</span></span> | <span data-ttu-id="145d9-212">*text*</span><span class="sxs-lookup"><span data-stu-id="145d9-212">*text*</span></span> | `*text*` |
| <span data-ttu-id="145d9-213">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="145d9-213">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="145d9-214">**Text**</span><span class="sxs-lookup"><span data-stu-id="145d9-214">**Text**</span></span> | `### Text`|
| <span data-ttu-id="145d9-215">strikethrough</span><span class="sxs-lookup"><span data-stu-id="145d9-215">strikethrough</span></span> | <span data-ttu-id="145d9-216">~~text~~</span><span class="sxs-lookup"><span data-stu-id="145d9-216">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="145d9-217">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-217">unordered list</span></span> | <ul><li><span data-ttu-id="145d9-218">text</span><span class="sxs-lookup"><span data-stu-id="145d9-218">text</span></span></li><li><span data-ttu-id="145d9-219">text</span><span class="sxs-lookup"><span data-stu-id="145d9-219">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="145d9-220">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-220">ordered list</span></span> | <ol><li><span data-ttu-id="145d9-221">text</span><span class="sxs-lookup"><span data-stu-id="145d9-221">text</span></span></li><li><span data-ttu-id="145d9-222">text</span><span class="sxs-lookup"><span data-stu-id="145d9-222">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="145d9-223">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="145d9-223">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="145d9-224">blockquote</span><span class="sxs-lookup"><span data-stu-id="145d9-224">blockquote</span></span> | <span data-ttu-id="145d9-225">>blockquote text</span><span class="sxs-lookup"><span data-stu-id="145d9-225">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="145d9-226">Link</span><span class="sxs-lookup"><span data-stu-id="145d9-226">hyperlink</span></span> | [<span data-ttu-id="145d9-227">Bing</span><span class="sxs-lookup"><span data-stu-id="145d9-227">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="145d9-228">Bildlink</span><span class="sxs-lookup"><span data-stu-id="145d9-228">image link</span></span> |![Ente auf einem Felchen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="145d9-230">In Connectorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="145d9-230">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="145d9-231">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von Markdown</span><span class="sxs-lookup"><span data-stu-id="145d9-231">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="145d9-232">Auf dem Desktop sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-232">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="145d9-234">Unter iOS sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-234">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="145d9-236">Probleme:</span><span class="sxs-lookup"><span data-stu-id="145d9-236">Issues:</span></span>

* <span data-ttu-id="145d9-237">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="145d9-237">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="145d9-238">Blockquotes werden als eingezogen gerendert, aber ohne grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="145d9-238">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="145d9-239">Unter Android sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-239">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="145d9-241">Formatierungsbeispiel für Markdown Connector Cards</span><span class="sxs-lookup"><span data-stu-id="145d9-241">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="145d9-242">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="145d9-242">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="145d9-243">**HTML-Formatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="145d9-243">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="145d9-244">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="145d9-244">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="145d9-245">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="145d9-245">Markdown is described in the next section.</span></span>

| <span data-ttu-id="145d9-246">Format</span><span class="sxs-lookup"><span data-stu-id="145d9-246">Style</span></span> | <span data-ttu-id="145d9-247">Beispiel</span><span class="sxs-lookup"><span data-stu-id="145d9-247">Example</span></span> | <span data-ttu-id="145d9-248">HTML</span><span class="sxs-lookup"><span data-stu-id="145d9-248">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="145d9-249">bold</span><span class="sxs-lookup"><span data-stu-id="145d9-249">bold</span></span> | <span data-ttu-id="145d9-250">**text**</span><span class="sxs-lookup"><span data-stu-id="145d9-250">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="145d9-251">italic</span><span class="sxs-lookup"><span data-stu-id="145d9-251">italic</span></span> | <span data-ttu-id="145d9-252">*text*</span><span class="sxs-lookup"><span data-stu-id="145d9-252">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="145d9-253">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="145d9-253">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="145d9-254">**Text**</span><span class="sxs-lookup"><span data-stu-id="145d9-254">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="145d9-255">strikethrough</span><span class="sxs-lookup"><span data-stu-id="145d9-255">strikethrough</span></span> | <span data-ttu-id="145d9-256">~~text~~</span><span class="sxs-lookup"><span data-stu-id="145d9-256">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="145d9-257">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-257">unordered list</span></span> | <ul><li><span data-ttu-id="145d9-258">text</span><span class="sxs-lookup"><span data-stu-id="145d9-258">text</span></span></li><li><span data-ttu-id="145d9-259">text</span><span class="sxs-lookup"><span data-stu-id="145d9-259">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="145d9-260">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-260">ordered list</span></span> | <ol><li><span data-ttu-id="145d9-261">text</span><span class="sxs-lookup"><span data-stu-id="145d9-261">text</span></span></li><li><span data-ttu-id="145d9-262">text</span><span class="sxs-lookup"><span data-stu-id="145d9-262">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="145d9-263">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="145d9-263">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="145d9-264">blockquote</span><span class="sxs-lookup"><span data-stu-id="145d9-264">blockquote</span></span> | <blockquote><span data-ttu-id="145d9-265">text</span><span class="sxs-lookup"><span data-stu-id="145d9-265">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="145d9-266">Link</span><span class="sxs-lookup"><span data-stu-id="145d9-266">hyperlink</span></span> | [<span data-ttu-id="145d9-267">Bing</span><span class="sxs-lookup"><span data-stu-id="145d9-267">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="145d9-268">Bildlink</span><span class="sxs-lookup"><span data-stu-id="145d9-268">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="145d9-269">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="145d9-269">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="145d9-270">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="145d9-270">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="145d9-271">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-271">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="145d9-273">Unter iOS sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-273">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="145d9-275">Probleme:</span><span class="sxs-lookup"><span data-stu-id="145d9-275">Issues:</span></span>

* <span data-ttu-id="145d9-276">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in ConnectorKarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="145d9-276">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="145d9-277">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="145d9-277">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="145d9-278">Unter Android sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="145d9-278">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="145d9-280">Formatierungsbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="145d9-280">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="145d9-281">**HTML-Formatierung: Hero- und Miniaturansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="145d9-281">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="145d9-282">HTML-Tags werden für einfache Karten wie die Held- und Miniaturansichtskarte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-282">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="145d9-283">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="145d9-283">Markdown is not supported.</span></span>

| <span data-ttu-id="145d9-284">Format</span><span class="sxs-lookup"><span data-stu-id="145d9-284">Style</span></span> | <span data-ttu-id="145d9-285">Beispiel</span><span class="sxs-lookup"><span data-stu-id="145d9-285">Example</span></span> | <span data-ttu-id="145d9-286">HTML</span><span class="sxs-lookup"><span data-stu-id="145d9-286">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="145d9-287">bold</span><span class="sxs-lookup"><span data-stu-id="145d9-287">bold</span></span> | <span data-ttu-id="145d9-288">**text**</span><span class="sxs-lookup"><span data-stu-id="145d9-288">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="145d9-289">italic</span><span class="sxs-lookup"><span data-stu-id="145d9-289">italic</span></span> | <span data-ttu-id="145d9-290">*text*</span><span class="sxs-lookup"><span data-stu-id="145d9-290">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="145d9-291">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="145d9-291">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="145d9-292">**Text**</span><span class="sxs-lookup"><span data-stu-id="145d9-292">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="145d9-293">strikethrough</span><span class="sxs-lookup"><span data-stu-id="145d9-293">strikethrough</span></span> | <span data-ttu-id="145d9-294">~~text~~</span><span class="sxs-lookup"><span data-stu-id="145d9-294">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="145d9-295">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-295">unordered list</span></span> | <ul><li><span data-ttu-id="145d9-296">text</span><span class="sxs-lookup"><span data-stu-id="145d9-296">text</span></span></li><li><span data-ttu-id="145d9-297">text</span><span class="sxs-lookup"><span data-stu-id="145d9-297">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="145d9-298">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="145d9-298">ordered list</span></span> | <ol><li><span data-ttu-id="145d9-299">text</span><span class="sxs-lookup"><span data-stu-id="145d9-299">text</span></span></li><li><span data-ttu-id="145d9-300">text</span><span class="sxs-lookup"><span data-stu-id="145d9-300">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="145d9-301">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="145d9-301">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="145d9-302">blockquote</span><span class="sxs-lookup"><span data-stu-id="145d9-302">blockquote</span></span> | <blockquote><span data-ttu-id="145d9-303">text</span><span class="sxs-lookup"><span data-stu-id="145d9-303">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="145d9-304">Link</span><span class="sxs-lookup"><span data-stu-id="145d9-304">hyperlink</span></span> | [<span data-ttu-id="145d9-305">Bing</span><span class="sxs-lookup"><span data-stu-id="145d9-305">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="145d9-306">Bildlink</span><span class="sxs-lookup"><span data-stu-id="145d9-306">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="145d9-307">Unterschiede zwischen Mobilen und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-307">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="145d9-308">Aufgrund von Auflösungsunterschieden zwischen dem Desktop und der mobilen Plattform unterscheiden sich die Formatierungen zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="145d9-308">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="145d9-309">Auf dem Desktop wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="145d9-309">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="145d9-311">Unter iOS wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="145d9-311">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="145d9-313">Probleme:</span><span class="sxs-lookup"><span data-stu-id="145d9-313">Issues:</span></span>

* <span data-ttu-id="145d9-314">Zeichenformatierungen wie fett und italisch werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="145d9-314">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="145d9-315">Unter Android wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="145d9-315">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="145d9-317">Zeichenformatierung wie fett und italisch wird unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="145d9-317">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="145d9-318">Formatierungsbeispiel für die HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="145d9-318">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="145d9-319">Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="145d9-319">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="145d9-320">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="145d9-320">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
