---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentexten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: b50109ad664bda2fc130e08c53dd7fca2a3d54ef
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922517"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="8a553-104">Formatieren von Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="8a553-104">Format cards in Teams</span></span>

<span data-ttu-id="8a553-105">Je nach Kartentyp können Sie Ihren Karten mithilfe von Markdown oder HTML Rich-Text-Formatierungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a553-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="8a553-106">Karten unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln.</span><span class="sxs-lookup"><span data-stu-id="8a553-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="8a553-107">Die Formatierung kann mit einer Teilmenge der XML-Formatierung (HTML) oder Markdown je nach Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8a553-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="8a553-108">Für die aktuelle und zukünftige Entwicklung wird adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8a553-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="8a553-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser geringfügig variieren.</span><span class="sxs-lookup"><span data-stu-id="8a553-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="8a553-110">Sie können ein Inlinebild mit einer beliebigen Teams-Karte verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a553-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="8a553-111">Bilder, die als , oder Dateien formatiert werden und  `.png` `.jpg` dürfen `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="8a553-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="8a553-112">Animierte GIF wird offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="8a553-113">*Siehe Kartenreferenz* [](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="8a553-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="8a553-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="8a553-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="8a553-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="8a553-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8a553-116">**Adaptive Karten:** Markdown wird im Feld Adaptive Karte sowie `Textblock` und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="8a553-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="8a553-118">**O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="8a553-119">**Markdownformatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="8a553-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="8a553-120">Die unterstützten Formatvorlagen für `Textblock` und `Fact.Title` `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="8a553-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="8a553-121">Format</span><span class="sxs-lookup"><span data-stu-id="8a553-121">Style</span></span> | <span data-ttu-id="8a553-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a553-122">Example</span></span> | <span data-ttu-id="8a553-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="8a553-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8a553-124">bold</span><span class="sxs-lookup"><span data-stu-id="8a553-124">bold</span></span> | <span data-ttu-id="8a553-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="8a553-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="8a553-126">italic</span><span class="sxs-lookup"><span data-stu-id="8a553-126">italic</span></span> | <span data-ttu-id="8a553-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="8a553-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="8a553-128">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-128">unordered list</span></span> | <ul><li><span data-ttu-id="8a553-129">text</span><span class="sxs-lookup"><span data-stu-id="8a553-129">text</span></span></li><li><span data-ttu-id="8a553-130">text</span><span class="sxs-lookup"><span data-stu-id="8a553-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="8a553-131">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-131">ordered list</span></span> | <ol><li><span data-ttu-id="8a553-132">text</span><span class="sxs-lookup"><span data-stu-id="8a553-132">text</span></span></li><li><span data-ttu-id="8a553-133">text</span><span class="sxs-lookup"><span data-stu-id="8a553-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="8a553-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="8a553-134">Hyperlinks</span></span> |[<span data-ttu-id="8a553-135">Bing</span><span class="sxs-lookup"><span data-stu-id="8a553-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="8a553-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8a553-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="8a553-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="8a553-137">Headers</span></span>
* <span data-ttu-id="8a553-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="8a553-138">Tables</span></span>
* <span data-ttu-id="8a553-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="8a553-139">Images</span></span>
* <span data-ttu-id="8a553-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8a553-140">Preformatted text</span></span>
* <span data-ttu-id="8a553-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="8a553-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a553-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8a553-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="8a553-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="8a553-144">In Listen können Sie die `\r` Escapesequenzen für `\n` Newlines verwenden.</span><span class="sxs-lookup"><span data-stu-id="8a553-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="8a553-145">Wenn Sie in einer Liste verwenden, wird das nächste Element in der Liste `\n\n` eingezogen.</span><span class="sxs-lookup"><span data-stu-id="8a553-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="8a553-146">Wenn Sie Newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="8a553-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="8a553-147">Unterschiede zwischen Mobilen und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="8a553-148">Die Formatierung ist zwischen dem Desktop und den mobilen Versionen von Teams geringfügig unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="8a553-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="8a553-149">Auf dem Desktop wird die Formatierung der adaptiven Karten-Markdown in webbrowsern und in der Teams-Clientanwendung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a553-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatierung der adaptiven Karte Markdown im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="8a553-151">Unter iOS sieht die Formatierung der adaptiven Karten-Markdown wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Formatierung der adaptiven Karte Markdown in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="8a553-153">Unter Android wird die Formatierung der adaptiven Karten-Markdown wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a553-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Adaptive Karten-Markdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="8a553-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-155">More information on Adaptive cards</span></span>

<span data-ttu-id="8a553-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="8a553-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="8a553-158">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="8a553-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="8a553-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="8a553-160">Sie können @-Erwähnungen in einem adaptiven Kartentext für Bots und Nachrichtenerweiterungsantworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a553-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="8a553-161">Um @-Erwähnungen in Karten hinzuzufügen, folgen Sie derselben Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte Erwähnungen in Kanal- und [Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="8a553-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="8a553-162">Bots und Messagingerweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="8a553-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="8a553-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="8a553-164">Channel & Team erwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="8a553-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="8a553-165">Constructing mentions</span></span>

<span data-ttu-id="8a553-166">Um eine Erwähnung in einer adaptiven Karte zu erhalten, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="8a553-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="8a553-167">`<at>username</at>` in den unterstützten adaptiven Kartenelementen.</span><span class="sxs-lookup"><span data-stu-id="8a553-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="8a553-168">Das Objekt innerhalb einer Eigenschaft im Karteninhalt, die `mention` `msteams` die Teams-Benutzer-ID des erwähnten Benutzers enthält.</span><span class="sxs-lookup"><span data-stu-id="8a553-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="8a553-169">Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="8a553-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="8a553-170">Es kann zum @mention eines bestimmten Benutzers verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8a553-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="8a553-171">Der kann mithilfe einer der unter Abrufen der Benutzer-ID genannten `userId` [Optionen abgerufen werden.](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)</span><span class="sxs-lookup"><span data-stu-id="8a553-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="8a553-172">Beispiel für adaptive Karte mit erwähnung</span><span class="sxs-lookup"><span data-stu-id="8a553-172">Sample Adaptive card with a mention</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="8a553-173">Informationsmasken in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="8a553-174">Verwenden Sie die Informationsmaskeneigenschaft, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) adaptiver Karten.</span><span class="sxs-lookup"><span data-stu-id="8a553-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="8a553-175">Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration angegeben wurde.](../../build-your-first-app/build-bot.md#4-configure-your-bot)</span><span class="sxs-lookup"><span data-stu-id="8a553-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md#4-configure-your-bot).</span></span> 

> [!NOTE]
> <span data-ttu-id="8a553-176">Die Informationsmaskeneigenschaft ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a553-176">The information masking property is currently available in the developer preview only.</span></span>

<span data-ttu-id="8a553-177">Um Informationen in adaptiven Karten zu maskieren, fügen Sie die Eigenschaft zum Eingeben `isMasked`  `Input.Text` hinzu, und legen Sie den Wert auf *true .*</span><span class="sxs-lookup"><span data-stu-id="8a553-177">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="8a553-178">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="8a553-178">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="8a553-179">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="8a553-179">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskieren eines Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="8a553-181">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="8a553-181">Full width Adaptive card</span></span>
<span data-ttu-id="8a553-182">Sie können die Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und `msteams` zusätzlichen Canvasbereich zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="8a553-182">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="8a553-183">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8a553-183">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="8a553-184">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="8a553-184">Constructing full width cards</span></span>
<span data-ttu-id="8a553-185">Um eine adaptive Karte mit voller Breite zu erstellen, muss das Objekt in der Eigenschaft im Karteninhalt `width` `msteams` auf festgelegt `Full` werden.</span><span class="sxs-lookup"><span data-stu-id="8a553-185">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="8a553-186">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="8a553-186">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="8a553-187">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="8a553-187">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="8a553-188">Eine adaptive Karte mit voller Breite wird wie folgt ![ angezeigt: Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="8a553-188">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="8a553-189">Wenn Sie die Eigenschaft nicht auf Vollständig festgelegt haben, lautet die Standardansicht der adaptiven Karte wie folgt: Adaptive Kartenansicht mit geringer `width`  ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="8a553-189">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="8a553-190">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="8a553-190">Typeahead support</span></span>

<span data-ttu-id="8a553-191">Innerhalb des Schemaelements kann das Durchfiltern und Auswählen durch eine ansehnliche Anzahl von Auswahlmöglichkeiten den [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Aufgabenabschluss erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="8a553-191">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="8a553-192">Die Typaheadunterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl beim Eingeben durch einen Benutzer ein- oder gefiltert wird.</span><span class="sxs-lookup"><span data-stu-id="8a553-192">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="8a553-193">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-193">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="8a553-194">So aktivieren Sie typeahead innerhalb der `Input.Choiceset` Gruppe `style` `filtered` auf, und stellen Sie sicher, `isMultiSelect` dass auf festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="8a553-194">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="8a553-195">Beispiel für adaptive Karte mit Typaheadunterstützung</span><span class="sxs-lookup"><span data-stu-id="8a553-195">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="8a553-196">Schrittansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-196">Stage view for images in Adaptive Cards</span></span>

> [!NOTE]
> <span data-ttu-id="8a553-197">Dieses Feature ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8a553-197">This feature is currently available in developer preview only.</span></span>
 
<span data-ttu-id="8a553-198">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von Bildern `msteams` in der Ansicht der Stufe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a553-198">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="8a553-199">Wenn Benutzer den Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="8a553-199">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="8a553-200">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8a553-200">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="8a553-201">Wenn Benutzer auf das Bild zeigen, wird oben rechts im Bild ein Erweiterungssymbol ![ angezeigt: Adaptive Karte mit erweiterbaren Bildern](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="8a553-201">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="8a553-202">Das Bild wird in der Ansicht "Stage" angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: Bild wird in ![ die Ansicht "Stage" erweitert.](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="8a553-202">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="8a553-203">In der Abschnittsansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="8a553-203">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="8a553-204">Sie können auswählen, welche Bilder auf Ihrer adaptiven Karte über diese Funktion verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="8a553-204">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="8a553-205">Die Zoom- und Zoom-Out-Funktion gilt nur für die Bildelemente (Bildtyp) in einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="8a553-205">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="8a553-206">Für mobile Teams-Apps sind die Funktionen für die Stage View für Bilder in adaptiven Karten standardmäßig verfügbar, und Benutzer können adaptive Kartenbilder in der Ansicht der Stufe anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das Attribut vorhanden ist `allowExpand` oder nicht.</span><span class="sxs-lookup"><span data-stu-id="8a553-206">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="8a553-207">**Markdownformatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="8a553-207">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="8a553-208">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8a553-208">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="8a553-209">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8a553-209">HTML support is described in the last section.</span></span>

| <span data-ttu-id="8a553-210">Format</span><span class="sxs-lookup"><span data-stu-id="8a553-210">Style</span></span> | <span data-ttu-id="8a553-211">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a553-211">Example</span></span> | <span data-ttu-id="8a553-212">Markdown</span><span class="sxs-lookup"><span data-stu-id="8a553-212">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8a553-213">bold</span><span class="sxs-lookup"><span data-stu-id="8a553-213">bold</span></span> | <span data-ttu-id="8a553-214">**text**</span><span class="sxs-lookup"><span data-stu-id="8a553-214">**text**</span></span> | `**text**` |
| <span data-ttu-id="8a553-215">italic</span><span class="sxs-lookup"><span data-stu-id="8a553-215">italic</span></span> | <span data-ttu-id="8a553-216">*text*</span><span class="sxs-lookup"><span data-stu-id="8a553-216">*text*</span></span> | `*text*` |
| <span data-ttu-id="8a553-217">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="8a553-217">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8a553-218">**Text**</span><span class="sxs-lookup"><span data-stu-id="8a553-218">**Text**</span></span> | `### Text`|
| <span data-ttu-id="8a553-219">strikethrough</span><span class="sxs-lookup"><span data-stu-id="8a553-219">strikethrough</span></span> | <span data-ttu-id="8a553-220">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8a553-220">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="8a553-221">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-221">unordered list</span></span> | <ul><li><span data-ttu-id="8a553-222">text</span><span class="sxs-lookup"><span data-stu-id="8a553-222">text</span></span></li><li><span data-ttu-id="8a553-223">text</span><span class="sxs-lookup"><span data-stu-id="8a553-223">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="8a553-224">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-224">ordered list</span></span> | <ol><li><span data-ttu-id="8a553-225">text</span><span class="sxs-lookup"><span data-stu-id="8a553-225">text</span></span></li><li><span data-ttu-id="8a553-226">text</span><span class="sxs-lookup"><span data-stu-id="8a553-226">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="8a553-227">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8a553-227">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="8a553-228">blockquote</span><span class="sxs-lookup"><span data-stu-id="8a553-228">blockquote</span></span> | <span data-ttu-id="8a553-229">>blockquote text</span><span class="sxs-lookup"><span data-stu-id="8a553-229">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="8a553-230">Link</span><span class="sxs-lookup"><span data-stu-id="8a553-230">hyperlink</span></span> | [<span data-ttu-id="8a553-231">Bing</span><span class="sxs-lookup"><span data-stu-id="8a553-231">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="8a553-232">Bildlink</span><span class="sxs-lookup"><span data-stu-id="8a553-232">image link</span></span> |![Ente auf einem Felchen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="8a553-234">In Connectorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="8a553-234">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="8a553-235">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von Markdown</span><span class="sxs-lookup"><span data-stu-id="8a553-235">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="8a553-236">Auf dem Desktop sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-236">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="8a553-238">Unter iOS sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-238">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="8a553-240">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8a553-240">Issues:</span></span>

* <span data-ttu-id="8a553-241">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="8a553-241">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="8a553-242">Blockquotes werden als eingezogen gerendert, aber ohne grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="8a553-242">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="8a553-243">Unter Android sieht die Markdownformatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-243">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="8a553-245">Formatierungsbeispiel für Markdown Connector Cards</span><span class="sxs-lookup"><span data-stu-id="8a553-245">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="8a553-246">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="8a553-246">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="8a553-247">**HTML-Formatierung: O365 Connector Cards**</span><span class="sxs-lookup"><span data-stu-id="8a553-247">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="8a553-248">Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="8a553-248">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="8a553-249">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8a553-249">Markdown is described in the next section.</span></span>

| <span data-ttu-id="8a553-250">Format</span><span class="sxs-lookup"><span data-stu-id="8a553-250">Style</span></span> | <span data-ttu-id="8a553-251">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a553-251">Example</span></span> | <span data-ttu-id="8a553-252">HTML</span><span class="sxs-lookup"><span data-stu-id="8a553-252">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8a553-253">bold</span><span class="sxs-lookup"><span data-stu-id="8a553-253">bold</span></span> | <span data-ttu-id="8a553-254">**text**</span><span class="sxs-lookup"><span data-stu-id="8a553-254">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="8a553-255">italic</span><span class="sxs-lookup"><span data-stu-id="8a553-255">italic</span></span> | <span data-ttu-id="8a553-256">*text*</span><span class="sxs-lookup"><span data-stu-id="8a553-256">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="8a553-257">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="8a553-257">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8a553-258">**Text**</span><span class="sxs-lookup"><span data-stu-id="8a553-258">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="8a553-259">strikethrough</span><span class="sxs-lookup"><span data-stu-id="8a553-259">strikethrough</span></span> | <span data-ttu-id="8a553-260">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8a553-260">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="8a553-261">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-261">unordered list</span></span> | <ul><li><span data-ttu-id="8a553-262">text</span><span class="sxs-lookup"><span data-stu-id="8a553-262">text</span></span></li><li><span data-ttu-id="8a553-263">text</span><span class="sxs-lookup"><span data-stu-id="8a553-263">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="8a553-264">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-264">ordered list</span></span> | <ol><li><span data-ttu-id="8a553-265">text</span><span class="sxs-lookup"><span data-stu-id="8a553-265">text</span></span></li><li><span data-ttu-id="8a553-266">text</span><span class="sxs-lookup"><span data-stu-id="8a553-266">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="8a553-267">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8a553-267">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="8a553-268">blockquote</span><span class="sxs-lookup"><span data-stu-id="8a553-268">blockquote</span></span> | <blockquote><span data-ttu-id="8a553-269">text</span><span class="sxs-lookup"><span data-stu-id="8a553-269">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="8a553-270">Link</span><span class="sxs-lookup"><span data-stu-id="8a553-270">hyperlink</span></span> | [<span data-ttu-id="8a553-271">Bing</span><span class="sxs-lookup"><span data-stu-id="8a553-271">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="8a553-272">Bildlink</span><span class="sxs-lookup"><span data-stu-id="8a553-272">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="8a553-273">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="8a553-273">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="8a553-274">Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von HTML</span><span class="sxs-lookup"><span data-stu-id="8a553-274">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="8a553-275">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-275">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="8a553-277">Unter iOS sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-277">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="8a553-279">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8a553-279">Issues:</span></span>

* <span data-ttu-id="8a553-280">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in ConnectorKarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="8a553-280">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="8a553-281">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="8a553-281">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="8a553-282">Unter Android sieht die HTML-Formatierung wie dies aus:</span><span class="sxs-lookup"><span data-stu-id="8a553-282">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="8a553-284">Formatierungsbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="8a553-284">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="8a553-285">**HTML-Formatierung: Hero- und Miniaturansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="8a553-285">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="8a553-286">HTML-Tags werden für einfache Karten wie die Held- und Miniaturansichtskarte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-286">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="8a553-287">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a553-287">Markdown is not supported.</span></span>

| <span data-ttu-id="8a553-288">Format</span><span class="sxs-lookup"><span data-stu-id="8a553-288">Style</span></span> | <span data-ttu-id="8a553-289">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a553-289">Example</span></span> | <span data-ttu-id="8a553-290">HTML</span><span class="sxs-lookup"><span data-stu-id="8a553-290">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8a553-291">bold</span><span class="sxs-lookup"><span data-stu-id="8a553-291">bold</span></span> | <span data-ttu-id="8a553-292">**text**</span><span class="sxs-lookup"><span data-stu-id="8a553-292">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="8a553-293">italic</span><span class="sxs-lookup"><span data-stu-id="8a553-293">italic</span></span> | <span data-ttu-id="8a553-294">*text*</span><span class="sxs-lookup"><span data-stu-id="8a553-294">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="8a553-295">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="8a553-295">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="8a553-296">**Text**</span><span class="sxs-lookup"><span data-stu-id="8a553-296">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="8a553-297">strikethrough</span><span class="sxs-lookup"><span data-stu-id="8a553-297">strikethrough</span></span> | <span data-ttu-id="8a553-298">~~text~~</span><span class="sxs-lookup"><span data-stu-id="8a553-298">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="8a553-299">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-299">unordered list</span></span> | <ul><li><span data-ttu-id="8a553-300">text</span><span class="sxs-lookup"><span data-stu-id="8a553-300">text</span></span></li><li><span data-ttu-id="8a553-301">text</span><span class="sxs-lookup"><span data-stu-id="8a553-301">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="8a553-302">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="8a553-302">ordered list</span></span> | <ol><li><span data-ttu-id="8a553-303">text</span><span class="sxs-lookup"><span data-stu-id="8a553-303">text</span></span></li><li><span data-ttu-id="8a553-304">text</span><span class="sxs-lookup"><span data-stu-id="8a553-304">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="8a553-305">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="8a553-305">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="8a553-306">blockquote</span><span class="sxs-lookup"><span data-stu-id="8a553-306">blockquote</span></span> | <blockquote><span data-ttu-id="8a553-307">text</span><span class="sxs-lookup"><span data-stu-id="8a553-307">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="8a553-308">Link</span><span class="sxs-lookup"><span data-stu-id="8a553-308">hyperlink</span></span> | [<span data-ttu-id="8a553-309">Bing</span><span class="sxs-lookup"><span data-stu-id="8a553-309">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="8a553-310">Bildlink</span><span class="sxs-lookup"><span data-stu-id="8a553-310">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="8a553-311">Unterschiede zwischen Mobilen und Desktops für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-311">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="8a553-312">Aufgrund von Auflösungsunterschieden zwischen dem Desktop und der mobilen Plattform unterscheiden sich die Formatierungen zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="8a553-312">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="8a553-313">Auf dem Desktop wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a553-313">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="8a553-315">Unter iOS wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a553-315">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="8a553-317">Probleme:</span><span class="sxs-lookup"><span data-stu-id="8a553-317">Issues:</span></span>

* <span data-ttu-id="8a553-318">Zeichenformatierungen wie fett und italisch werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="8a553-318">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="8a553-319">Unter Android wird die HTML-Formatierung wie dies angezeigt:</span><span class="sxs-lookup"><span data-stu-id="8a553-319">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="8a553-321">Zeichenformatierung wie fett und italisch wird unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a553-321">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="8a553-322">Formatierungsbeispiel für die HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="8a553-322">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="8a553-323">Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="8a553-323">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="8a553-324">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="8a553-324">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
