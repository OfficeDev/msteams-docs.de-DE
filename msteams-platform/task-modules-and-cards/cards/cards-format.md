---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentext in Microsoft Teams
keywords: Teams-Bots- Kartenformat
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: eead38b7f28ca740473a1df029e35b9ac624391d
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994168"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="3393e-104">Formatieren von Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="3393e-104">Format cards in Teams</span></span>

<span data-ttu-id="3393e-105">Je nach Kartentyp können Sie Rich-Text-Formatierungen entweder mit Markdown oder HTML zu Ihren Karten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3393e-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="3393e-106">Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="3393e-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="3393e-107">Die Formatierung kann mithilfe einer Teilmenge der XML-Formatierung (HTML) oder markdown abhängig vom Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3393e-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="3393e-108">Für aktuelle und zukünftige Entwicklungskarten wird adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="3393e-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="3393e-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann sich geringfügig zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="3393e-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="3393e-110">Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen.</span><span class="sxs-lookup"><span data-stu-id="3393e-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="3393e-111">Bilder, die als , oder Dateien formatiert werden  `.png` `.jpg` und `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten dürfen.</span><span class="sxs-lookup"><span data-stu-id="3393e-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="3393e-112">Animierte GIF-Dateien werden offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="3393e-113">Weitere Informationen finden Sie unter [Kartenreferenz.](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="3393e-113">For more information, see [Cards reference](./cards-reference.md#inline-card-images).</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="3393e-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="3393e-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="3393e-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="3393e-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3393e-116">**Adaptive Karten:** Markdown wird im Feld für adaptive Karten `Textblock` sowie und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="3393e-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="3393e-118">**O365-Connectorkarten:** Markdown und beschränkter HTML-Code werden in Office 365 Connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="3393e-119">**Markdownformatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="3393e-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="3393e-120">Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="3393e-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="3393e-121">Format</span><span class="sxs-lookup"><span data-stu-id="3393e-121">Style</span></span> | <span data-ttu-id="3393e-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3393e-122">Example</span></span> | <span data-ttu-id="3393e-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="3393e-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3393e-124">bold</span><span class="sxs-lookup"><span data-stu-id="3393e-124">bold</span></span> | <span data-ttu-id="3393e-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="3393e-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="3393e-126">italic</span><span class="sxs-lookup"><span data-stu-id="3393e-126">italic</span></span> | <span data-ttu-id="3393e-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="3393e-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="3393e-128">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-128">unordered list</span></span> | <ul><li><span data-ttu-id="3393e-129">text</span><span class="sxs-lookup"><span data-stu-id="3393e-129">text</span></span></li><li><span data-ttu-id="3393e-130">text</span><span class="sxs-lookup"><span data-stu-id="3393e-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="3393e-131">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-131">ordered list</span></span> | <ol><li><span data-ttu-id="3393e-132">text</span><span class="sxs-lookup"><span data-stu-id="3393e-132">text</span></span></li><li><span data-ttu-id="3393e-133">text</span><span class="sxs-lookup"><span data-stu-id="3393e-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="3393e-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="3393e-134">Hyperlinks</span></span> |[<span data-ttu-id="3393e-135">Bing</span><span class="sxs-lookup"><span data-stu-id="3393e-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="3393e-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="3393e-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="3393e-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="3393e-137">Headers</span></span>
* <span data-ttu-id="3393e-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="3393e-138">Tables</span></span>
* <span data-ttu-id="3393e-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="3393e-139">Images</span></span>
* <span data-ttu-id="3393e-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="3393e-140">Preformatted text</span></span>
* <span data-ttu-id="3393e-141">Blockzitaten</span><span class="sxs-lookup"><span data-stu-id="3393e-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3393e-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="3393e-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="3393e-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="3393e-144">In Listen können Sie die `\r` `\n` Oder Escapesequenzen für Newlines verwenden.</span><span class="sxs-lookup"><span data-stu-id="3393e-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="3393e-145">Die Verwendung `\n\n` in einer Liste bewirkt, dass das nächste Element in der Liste eingezogen wird.</span><span class="sxs-lookup"><span data-stu-id="3393e-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="3393e-146">Wenn Sie newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="3393e-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="3393e-147">Unterschiede zwischen Mobilgeräten und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="3393e-148">Die Formatierung unterscheidet sich geringfügig zwischen der Desktopversion und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="3393e-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="3393e-149">Auf dem Desktop wird die Markdown-Formatierung für adaptive Karten sowohl in Webbrowsern als auch in der Teams Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3393e-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Markdown-Formatierung für adaptive Karten im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="3393e-151">Unter iOS wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3393e-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Markdown-Formatierung adaptiver Karten in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="3393e-153">Unter Android wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3393e-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Markdown-Formatierung für adaptive Karten in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="3393e-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-155">More information on Adaptive cards</span></span>

<span data-ttu-id="3393e-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="3393e-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="3393e-158">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="3393e-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="3393e-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="3393e-160">Sie können @Erwähnungen in einem adaptiven Kartentext für Bots und Antworten auf Messaging-Erweiterungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3393e-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="3393e-161">Um @Erwähnungen in Karten hinzuzufügen, befolgen Sie die gleiche Benachrichtigungslogik und dasselbe Rendering wie nachrichtenbasierte [Erwähnungen in Kanal- und Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="3393e-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="3393e-162">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="3393e-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="3393e-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="3393e-164">Kanal- & Teamerwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="3393e-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="3393e-165">Constructing mentions</span></span>

<span data-ttu-id="3393e-166">Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="3393e-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="3393e-167">`<at>username</at>` in den unterstützten adaptiven Kartenelementen.</span><span class="sxs-lookup"><span data-stu-id="3393e-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="3393e-168">Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt, das die Teams Benutzer-ID des erwähnten Benutzers enthält.</span><span class="sxs-lookup"><span data-stu-id="3393e-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="3393e-169">Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="3393e-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="3393e-170">Es kann verwendet werden, um einen bestimmten Benutzer zu @mention.</span><span class="sxs-lookup"><span data-stu-id="3393e-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="3393e-171">Die `userId` kann mithilfe einer der im [Abrufen der Benutzer-ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)erwähnten Optionen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="3393e-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="3393e-172">Beispiel für eine adaptive Karte mit einer Erwähnung</span><span class="sxs-lookup"><span data-stu-id="3393e-172">Sample Adaptive card with a mention</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="3393e-173">Informationsformatierung in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="3393e-174">Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karten.</span><span class="sxs-lookup"><span data-stu-id="3393e-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="3393e-175">Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md)angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="3393e-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md).</span></span> 

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="3393e-176">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="3393e-176">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

<span data-ttu-id="3393e-177">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="3393e-177">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskierungsinformationsbild](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="3393e-179">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="3393e-179">Full width Adaptive card</span></span>
<span data-ttu-id="3393e-180">Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Platz zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="3393e-180">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="3393e-181">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3393e-181">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="3393e-182">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="3393e-182">Constructing full width cards</span></span>
<span data-ttu-id="3393e-183">Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf . `Full`</span><span class="sxs-lookup"><span data-stu-id="3393e-183">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="3393e-184">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="3393e-184">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="3393e-185">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="3393e-185">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="3393e-186">Eine adaptive Karte mit voller Breite wird wie folgt angezeigt: ![ Ansicht "Adaptive Karte mit voller Breite"](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="3393e-186">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="3393e-187">Wenn Sie die Eigenschaft nicht `width` auf *"Vollständig"* festgelegt haben, wird die Standardansicht der adaptiven Karte wie folgt angezeigt: Ansicht für ![ adaptive Karten mit geringer Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="3393e-187">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card appears as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="3393e-188">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3393e-188">Typeahead support</span></span>

<span data-ttu-id="3393e-189">Innerhalb des Schemaelements kann das Abfragen von [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Benutzern zum Filtern und Auswählen durch eine große Anzahl von Auswahlmöglichkeiten den Abschluss der Aufgabe erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="3393e-189">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="3393e-190">Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingegrenzt oder gefiltert wird, während ein Benutzer die Eingabe eintippt.</span><span class="sxs-lookup"><span data-stu-id="3393e-190">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="3393e-191">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-191">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="3393e-192">So aktivieren Sie Typeahead innerhalb des `Input.Choiceset` `style` Satzes, und stellen Sie `filtered` sicher, dass er auf festgelegt `isMultiSelect` `false` ist.</span><span class="sxs-lookup"><span data-stu-id="3393e-192">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="3393e-193">Beispiel für adaptive Karte mit Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="3393e-193">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="3393e-194">Phasenansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-194">Stage view for images in Adaptive Cards</span></span>

<span data-ttu-id="3393e-195">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="3393e-195">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="3393e-196">Wenn Benutzer mit dem Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="3393e-196">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="3393e-197">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3393e-197">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="3393e-198">Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke des Bilds ein Erweiterungssymbol angezeigt: ![ adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="3393e-198">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="3393e-199">Das Bild wird in der Phasenansicht angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: ![ Bild in Phasenansicht erweitert](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="3393e-199">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="3393e-200">In der Phasenansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="3393e-200">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="3393e-201">Sie können auswählen, welche Bilder in Ihrer adaptiven Karte für diese Funktion benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="3393e-201">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="3393e-202">Die Funktion zum Vergrößern und Verkleinern gilt nur für die Bildelemente (Bildtyp) auf einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="3393e-202">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="3393e-203">Für Teams mobile Apps sind standardmäßig Funktionen für die Phasenansicht für Bilder in adaptiven Karten verfügbar, und Benutzer können adaptive Kartenbilder in der Phasenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="3393e-203">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="3393e-204">**Markdownformatierung: O365-Connectorkarten**</span><span class="sxs-lookup"><span data-stu-id="3393e-204">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="3393e-205">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="3393e-205">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="3393e-206">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3393e-206">HTML support is described in the last section.</span></span>

| <span data-ttu-id="3393e-207">Format</span><span class="sxs-lookup"><span data-stu-id="3393e-207">Style</span></span> | <span data-ttu-id="3393e-208">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3393e-208">Example</span></span> | <span data-ttu-id="3393e-209">Markdown</span><span class="sxs-lookup"><span data-stu-id="3393e-209">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3393e-210">bold</span><span class="sxs-lookup"><span data-stu-id="3393e-210">bold</span></span> | <span data-ttu-id="3393e-211">**text**</span><span class="sxs-lookup"><span data-stu-id="3393e-211">**text**</span></span> | `**text**` |
| <span data-ttu-id="3393e-212">italic</span><span class="sxs-lookup"><span data-stu-id="3393e-212">italic</span></span> | <span data-ttu-id="3393e-213">*text*</span><span class="sxs-lookup"><span data-stu-id="3393e-213">*text*</span></span> | `*text*` |
| <span data-ttu-id="3393e-214">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3393e-214">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3393e-215">**Text**</span><span class="sxs-lookup"><span data-stu-id="3393e-215">**Text**</span></span> | `### Text`|
| <span data-ttu-id="3393e-216">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="3393e-216">strikethrough</span></span> | <span data-ttu-id="3393e-217">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3393e-217">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="3393e-218">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-218">unordered list</span></span> | <ul><li><span data-ttu-id="3393e-219">text</span><span class="sxs-lookup"><span data-stu-id="3393e-219">text</span></span></li><li><span data-ttu-id="3393e-220">text</span><span class="sxs-lookup"><span data-stu-id="3393e-220">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="3393e-221">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-221">ordered list</span></span> | <ol><li><span data-ttu-id="3393e-222">text</span><span class="sxs-lookup"><span data-stu-id="3393e-222">text</span></span></li><li><span data-ttu-id="3393e-223">text</span><span class="sxs-lookup"><span data-stu-id="3393e-223">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="3393e-224">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="3393e-224">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="3393e-225">blockquote</span><span class="sxs-lookup"><span data-stu-id="3393e-225">blockquote</span></span> | <span data-ttu-id="3393e-226">>Blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="3393e-226">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="3393e-227">Link</span><span class="sxs-lookup"><span data-stu-id="3393e-227">hyperlink</span></span> | [<span data-ttu-id="3393e-228">Bing</span><span class="sxs-lookup"><span data-stu-id="3393e-228">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="3393e-229">Bildlink</span><span class="sxs-lookup"><span data-stu-id="3393e-229">image link</span></span> |![Ente auf einem Brocken](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="3393e-231">In Konnektorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="3393e-231">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="3393e-232">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="3393e-232">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="3393e-233">Auf dem Desktop sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-233">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="3393e-235">Unter iOS sieht die Markdownformatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-235">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="3393e-237">Probleme:</span><span class="sxs-lookup"><span data-stu-id="3393e-237">Issues:</span></span>

* <span data-ttu-id="3393e-238">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="3393e-238">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="3393e-239">Blockquotes werden als eingezogen, aber ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="3393e-239">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="3393e-240">Unter Android sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-240">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="3393e-242">Formatierungsbeispiel für Markdown-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="3393e-242">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="3393e-243">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="3393e-243">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="3393e-244">**HTML-Formatierung: O365-Connectorkarten**</span><span class="sxs-lookup"><span data-stu-id="3393e-244">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="3393e-245">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="3393e-245">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="3393e-246">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3393e-246">Markdown is described in the next section.</span></span>

| <span data-ttu-id="3393e-247">Format</span><span class="sxs-lookup"><span data-stu-id="3393e-247">Style</span></span> | <span data-ttu-id="3393e-248">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3393e-248">Example</span></span> | <span data-ttu-id="3393e-249">HTML</span><span class="sxs-lookup"><span data-stu-id="3393e-249">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3393e-250">bold</span><span class="sxs-lookup"><span data-stu-id="3393e-250">bold</span></span> | <span data-ttu-id="3393e-251">**text**</span><span class="sxs-lookup"><span data-stu-id="3393e-251">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="3393e-252">italic</span><span class="sxs-lookup"><span data-stu-id="3393e-252">italic</span></span> | <span data-ttu-id="3393e-253">*text*</span><span class="sxs-lookup"><span data-stu-id="3393e-253">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="3393e-254">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3393e-254">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3393e-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="3393e-255">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="3393e-256">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="3393e-256">strikethrough</span></span> | <span data-ttu-id="3393e-257">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3393e-257">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="3393e-258">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-258">unordered list</span></span> | <ul><li><span data-ttu-id="3393e-259">text</span><span class="sxs-lookup"><span data-stu-id="3393e-259">text</span></span></li><li><span data-ttu-id="3393e-260">text</span><span class="sxs-lookup"><span data-stu-id="3393e-260">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="3393e-261">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-261">ordered list</span></span> | <ol><li><span data-ttu-id="3393e-262">text</span><span class="sxs-lookup"><span data-stu-id="3393e-262">text</span></span></li><li><span data-ttu-id="3393e-263">text</span><span class="sxs-lookup"><span data-stu-id="3393e-263">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="3393e-264">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="3393e-264">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="3393e-265">blockquote</span><span class="sxs-lookup"><span data-stu-id="3393e-265">blockquote</span></span> | <blockquote><span data-ttu-id="3393e-266">text</span><span class="sxs-lookup"><span data-stu-id="3393e-266">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="3393e-267">Link</span><span class="sxs-lookup"><span data-stu-id="3393e-267">hyperlink</span></span> | [<span data-ttu-id="3393e-268">Bing</span><span class="sxs-lookup"><span data-stu-id="3393e-268">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="3393e-269">Bildlink</span><span class="sxs-lookup"><span data-stu-id="3393e-269">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="3393e-270">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="3393e-270">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="3393e-271">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit HTML</span><span class="sxs-lookup"><span data-stu-id="3393e-271">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="3393e-272">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-272">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="3393e-274">Unter iOS sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-274">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="3393e-276">Probleme:</span><span class="sxs-lookup"><span data-stu-id="3393e-276">Issues:</span></span>

* <span data-ttu-id="3393e-277">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in Connectorkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="3393e-277">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="3393e-278">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="3393e-278">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="3393e-279">Unter Android sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-279">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="3393e-281">Formatierungsbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="3393e-281">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="3393e-282">**HTML-Formatierung: Favoriten- und Miniaturansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="3393e-282">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="3393e-283">HTML-Tags werden für einfache Karten wie die Hero- und Miniaturansichtskarte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-283">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="3393e-284">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3393e-284">Markdown is not supported.</span></span>

| <span data-ttu-id="3393e-285">Format</span><span class="sxs-lookup"><span data-stu-id="3393e-285">Style</span></span> | <span data-ttu-id="3393e-286">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3393e-286">Example</span></span> | <span data-ttu-id="3393e-287">HTML</span><span class="sxs-lookup"><span data-stu-id="3393e-287">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3393e-288">bold</span><span class="sxs-lookup"><span data-stu-id="3393e-288">bold</span></span> | <span data-ttu-id="3393e-289">**text**</span><span class="sxs-lookup"><span data-stu-id="3393e-289">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="3393e-290">italic</span><span class="sxs-lookup"><span data-stu-id="3393e-290">italic</span></span> | <span data-ttu-id="3393e-291">*text*</span><span class="sxs-lookup"><span data-stu-id="3393e-291">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="3393e-292">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3393e-292">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3393e-293">**Text**</span><span class="sxs-lookup"><span data-stu-id="3393e-293">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="3393e-294">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="3393e-294">strikethrough</span></span> | <span data-ttu-id="3393e-295">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3393e-295">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="3393e-296">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-296">unordered list</span></span> | <ul><li><span data-ttu-id="3393e-297">text</span><span class="sxs-lookup"><span data-stu-id="3393e-297">text</span></span></li><li><span data-ttu-id="3393e-298">text</span><span class="sxs-lookup"><span data-stu-id="3393e-298">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="3393e-299">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="3393e-299">ordered list</span></span> | <ol><li><span data-ttu-id="3393e-300">text</span><span class="sxs-lookup"><span data-stu-id="3393e-300">text</span></span></li><li><span data-ttu-id="3393e-301">text</span><span class="sxs-lookup"><span data-stu-id="3393e-301">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="3393e-302">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="3393e-302">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="3393e-303">blockquote</span><span class="sxs-lookup"><span data-stu-id="3393e-303">blockquote</span></span> | <blockquote><span data-ttu-id="3393e-304">text</span><span class="sxs-lookup"><span data-stu-id="3393e-304">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="3393e-305">Link</span><span class="sxs-lookup"><span data-stu-id="3393e-305">hyperlink</span></span> | [<span data-ttu-id="3393e-306">Bing</span><span class="sxs-lookup"><span data-stu-id="3393e-306">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="3393e-307">Bildlink</span><span class="sxs-lookup"><span data-stu-id="3393e-307">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="3393e-308">Unterschiede zwischen Mobilgeräten und Desktops bei einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-308">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="3393e-309">Aufgrund von Auflösungsunterschieden zwischen desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="3393e-309">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="3393e-310">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3393e-310">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="3393e-312">Unter iOS wird html-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3393e-312">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="3393e-314">Probleme:</span><span class="sxs-lookup"><span data-stu-id="3393e-314">Issues:</span></span>

* <span data-ttu-id="3393e-315">Zeichenformatierungen wie Fett und Kursiv werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="3393e-315">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="3393e-316">Unter Android sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3393e-316">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="3393e-318">Zeichenformatierungen wie fett und kursiv werden unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3393e-318">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="3393e-319">Formatierungsbeispiel für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="3393e-319">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="3393e-320">Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="3393e-320">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="3393e-321">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="3393e-321">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
