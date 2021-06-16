---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentext in Microsoft Teams
keywords: Teams-Bots- Kartenformat
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 6a420ca549cd5131afc50813b5c8267f28073e5b
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949763"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="88ed8-104">Formatieren von Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="88ed8-104">Format cards in Teams</span></span>

<span data-ttu-id="88ed8-105">Je nach Kartentyp können Sie Rich-Text-Formatierungen entweder mit Markdown oder HTML zu Ihren Karten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="88ed8-106">Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="88ed8-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="88ed8-107">Die Formatierung kann mithilfe einer Teilmenge der XML-Formatierung (HTML) oder markdown abhängig vom Kartentyp angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="88ed8-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="88ed8-108">Für aktuelle und zukünftige Entwicklungskarten wird adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="88ed8-109">Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann sich geringfügig zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="88ed8-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="88ed8-110">Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="88ed8-111">Bilder, die als , oder Dateien formatiert werden  `.png` `.jpg` und `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten dürfen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="88ed8-112">Animierte GIF-Dateien werden offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="88ed8-113">Weitere Informationen finden Sie unter [Kartenreferenz.](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="88ed8-113">For more information, see [Cards reference](./cards-reference.md#inline-card-images).</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="88ed8-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="88ed8-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="88ed8-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="88ed8-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="88ed8-116">**Adaptive Karten:** Markdown wird im Feld für adaptive Karten `Textblock` sowie und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="88ed8-117">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="88ed8-118">**O365-Connectorkarten:** Markdown und beschränkter HTML-Code werden in Office 365 Connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="88ed8-119">**Markdownformatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="88ed8-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="88ed8-120">Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="88ed8-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="88ed8-121">Format</span><span class="sxs-lookup"><span data-stu-id="88ed8-121">Style</span></span> | <span data-ttu-id="88ed8-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="88ed8-122">Example</span></span> | <span data-ttu-id="88ed8-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="88ed8-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="88ed8-124">bold</span><span class="sxs-lookup"><span data-stu-id="88ed8-124">bold</span></span> | <span data-ttu-id="88ed8-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="88ed8-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="88ed8-126">italic</span><span class="sxs-lookup"><span data-stu-id="88ed8-126">italic</span></span> | <span data-ttu-id="88ed8-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="88ed8-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="88ed8-128">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-128">unordered list</span></span> | <ul><li><span data-ttu-id="88ed8-129">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-129">text</span></span></li><li><span data-ttu-id="88ed8-130">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="88ed8-131">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-131">ordered list</span></span> | <ol><li><span data-ttu-id="88ed8-132">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-132">text</span></span></li><li><span data-ttu-id="88ed8-133">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="88ed8-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="88ed8-134">Hyperlinks</span></span> |[<span data-ttu-id="88ed8-135">Bing</span><span class="sxs-lookup"><span data-stu-id="88ed8-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="88ed8-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="88ed8-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="88ed8-137">Headers</span></span>
* <span data-ttu-id="88ed8-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="88ed8-138">Tables</span></span>
* <span data-ttu-id="88ed8-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="88ed8-139">Images</span></span>
* <span data-ttu-id="88ed8-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="88ed8-140">Preformatted text</span></span>
* <span data-ttu-id="88ed8-141">Blockzitaten</span><span class="sxs-lookup"><span data-stu-id="88ed8-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88ed8-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="88ed8-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="88ed8-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="88ed8-144">In Listen können Sie die `\r` `\n` Oder Escapesequenzen für Newlines verwenden.</span><span class="sxs-lookup"><span data-stu-id="88ed8-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="88ed8-145">Die Verwendung `\n\n` in einer Liste bewirkt, dass das nächste Element in der Liste eingezogen wird.</span><span class="sxs-lookup"><span data-stu-id="88ed8-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="88ed8-146">Wenn Sie newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="88ed8-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="88ed8-147">Unterschiede zwischen Mobilgeräten und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="88ed8-148">Die Formatierung unterscheidet sich geringfügig zwischen der Desktopversion und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="88ed8-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="88ed8-149">Auf dem Desktop wird die Markdown-Formatierung für adaptive Karten sowohl in Webbrowsern als auch in der Teams Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Markdown-Formatierung für adaptive Karten im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="88ed8-151">Unter iOS wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Markdown-Formatierung adaptiver Karten in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="88ed8-153">Unter Android wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Markdown-Formatierung für adaptive Karten in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="88ed8-155">Weitere Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-155">More information on Adaptive cards</span></span>

<span data-ttu-id="88ed8-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="88ed8-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="88ed8-158">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="88ed8-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="88ed8-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="88ed8-160">Sie können @Erwähnungen in einem adaptiven Kartentext für Bots und Antworten auf Messaging-Erweiterungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="88ed8-161">Um @Erwähnungen in Karten hinzuzufügen, befolgen Sie die gleiche Benachrichtigungslogik und dasselbe Rendering wie nachrichtenbasierte [Erwähnungen in Kanal- und Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="88ed8-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="88ed8-162">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="88ed8-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="88ed8-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="88ed8-164">Kanal- & Teamerwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="88ed8-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="88ed8-165">Constructing mentions</span></span>

<span data-ttu-id="88ed8-166">Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="88ed8-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="88ed8-167">`<at>username</at>` in den unterstützten adaptiven Kartenelementen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="88ed8-168">Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt, das die Teams Benutzer-ID des erwähnten Benutzers enthält.</span><span class="sxs-lookup"><span data-stu-id="88ed8-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="88ed8-169">Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="88ed8-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="88ed8-170">Es kann verwendet werden, um einen bestimmten Benutzer zu @mention.</span><span class="sxs-lookup"><span data-stu-id="88ed8-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="88ed8-171">Die `userId` kann mithilfe einer der im [Abrufen der Benutzer-ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)erwähnten Optionen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="88ed8-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="88ed8-172">Beispiel für eine adaptive Karte mit einer Erwähnung</span><span class="sxs-lookup"><span data-stu-id="88ed8-172">Sample Adaptive card with a mention</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="88ed8-173">Informationsformatierung in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="88ed8-174">Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karten.</span><span class="sxs-lookup"><span data-stu-id="88ed8-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="88ed8-175">Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md)angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="88ed8-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="88ed8-176">Die Eigenschaft zum Maskieren von Informationen ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="88ed8-176">The information masking property is currently available in the developer preview only.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="88ed8-177">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="88ed8-177">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

<span data-ttu-id="88ed8-178">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="88ed8-178">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskierungsinformationsbild](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="88ed8-180">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="88ed8-180">Full width Adaptive card</span></span>
<span data-ttu-id="88ed8-181">Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Platz zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-181">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="88ed8-182">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="88ed8-182">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="88ed8-183">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="88ed8-183">Constructing full width cards</span></span>
<span data-ttu-id="88ed8-184">Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf . `Full`</span><span class="sxs-lookup"><span data-stu-id="88ed8-184">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="88ed8-185">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="88ed8-185">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="88ed8-186">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="88ed8-186">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="88ed8-187">Eine adaptive Karte mit voller Breite wird wie folgt angezeigt: ![ Ansicht "Adaptive Karte mit voller Breite"](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="88ed8-187">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="88ed8-188">Wenn Sie die Eigenschaft nicht `width` auf *"Vollständig"* festgelegt haben, wird die Standardansicht der adaptiven Karte wie folgt angezeigt: Ansicht für ![ adaptive Karten mit geringer Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="88ed8-188">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card appears as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="88ed8-189">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="88ed8-189">Typeahead support</span></span>

<span data-ttu-id="88ed8-190">Innerhalb des Schemaelements kann das Abfragen von [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Benutzern zum Filtern und Auswählen durch eine große Anzahl von Auswahlmöglichkeiten den Abschluss der Aufgabe erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-190">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="88ed8-191">Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingegrenzt oder gefiltert wird, während ein Benutzer die Eingabe eintippt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-191">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="88ed8-192">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-192">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="88ed8-193">So aktivieren Sie Typeahead innerhalb des `Input.Choiceset` `style` Satzes, und stellen Sie `filtered` sicher, dass er auf festgelegt `isMultiSelect` `false` ist.</span><span class="sxs-lookup"><span data-stu-id="88ed8-193">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="88ed8-194">Beispiel für adaptive Karte mit Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="88ed8-194">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="88ed8-195">Phasenansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-195">Stage view for images in Adaptive Cards</span></span>

<span data-ttu-id="88ed8-196">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-196">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="88ed8-197">Wenn Benutzer mit dem Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="88ed8-197">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="88ed8-198">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="88ed8-198">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="88ed8-199">Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke des Bilds ein Erweiterungssymbol angezeigt: ![ adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="88ed8-199">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="88ed8-200">Das Bild wird in der Phasenansicht angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: ![ Bild in Phasenansicht erweitert](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="88ed8-200">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="88ed8-201">In der Phasenansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="88ed8-201">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="88ed8-202">Sie können auswählen, welche Bilder in Ihrer adaptiven Karte für diese Funktion benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="88ed8-202">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="88ed8-203">Die Funktion zum Vergrößern und Verkleinern gilt nur für die Bildelemente (Bildtyp) auf einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="88ed8-203">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="88ed8-204">Für Teams mobile Apps sind standardmäßig Funktionen für die Phasenansicht für Bilder in adaptiven Karten verfügbar, und Benutzer können adaptive Kartenbilder in der Phasenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="88ed8-204">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="88ed8-205">**Markdownformatierung: O365-Connectorkarten**</span><span class="sxs-lookup"><span data-stu-id="88ed8-205">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="88ed8-206">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-206">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="88ed8-207">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="88ed8-207">HTML support is described in the last section.</span></span>

| <span data-ttu-id="88ed8-208">Format</span><span class="sxs-lookup"><span data-stu-id="88ed8-208">Style</span></span> | <span data-ttu-id="88ed8-209">Beispiel</span><span class="sxs-lookup"><span data-stu-id="88ed8-209">Example</span></span> | <span data-ttu-id="88ed8-210">Markdown</span><span class="sxs-lookup"><span data-stu-id="88ed8-210">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="88ed8-211">bold</span><span class="sxs-lookup"><span data-stu-id="88ed8-211">bold</span></span> | <span data-ttu-id="88ed8-212">**text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-212">**text**</span></span> | `**text**` |
| <span data-ttu-id="88ed8-213">italic</span><span class="sxs-lookup"><span data-stu-id="88ed8-213">italic</span></span> | <span data-ttu-id="88ed8-214">*text*</span><span class="sxs-lookup"><span data-stu-id="88ed8-214">*text*</span></span> | `*text*` |
| <span data-ttu-id="88ed8-215">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="88ed8-215">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="88ed8-216">**Text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-216">**Text**</span></span> | `### Text`|
| <span data-ttu-id="88ed8-217">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="88ed8-217">strikethrough</span></span> | <span data-ttu-id="88ed8-218">~~text~~</span><span class="sxs-lookup"><span data-stu-id="88ed8-218">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="88ed8-219">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-219">unordered list</span></span> | <ul><li><span data-ttu-id="88ed8-220">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-220">text</span></span></li><li><span data-ttu-id="88ed8-221">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-221">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="88ed8-222">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-222">ordered list</span></span> | <ol><li><span data-ttu-id="88ed8-223">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-223">text</span></span></li><li><span data-ttu-id="88ed8-224">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-224">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="88ed8-225">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="88ed8-225">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="88ed8-226">blockquote</span><span class="sxs-lookup"><span data-stu-id="88ed8-226">blockquote</span></span> | <span data-ttu-id="88ed8-227">>Blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="88ed8-227">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="88ed8-228">Link</span><span class="sxs-lookup"><span data-stu-id="88ed8-228">hyperlink</span></span> | [<span data-ttu-id="88ed8-229">Bing</span><span class="sxs-lookup"><span data-stu-id="88ed8-229">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="88ed8-230">Bildlink</span><span class="sxs-lookup"><span data-stu-id="88ed8-230">image link</span></span> |![Ente auf einem Brocken](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="88ed8-232">In Konnektorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="88ed8-232">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="88ed8-233">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="88ed8-233">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="88ed8-234">Auf dem Desktop sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-234">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="88ed8-236">Unter iOS sieht die Markdownformatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-236">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="88ed8-238">Probleme:</span><span class="sxs-lookup"><span data-stu-id="88ed8-238">Issues:</span></span>

* <span data-ttu-id="88ed8-239">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="88ed8-239">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="88ed8-240">Blockquotes werden als eingezogen, aber ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="88ed8-240">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="88ed8-241">Unter Android sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-241">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="88ed8-243">Formatierungsbeispiel für Markdown-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="88ed8-243">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="88ed8-244">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="88ed8-244">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="88ed8-245">**HTML-Formatierung: O365-Connectorkarten**</span><span class="sxs-lookup"><span data-stu-id="88ed8-245">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="88ed8-246">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="88ed8-246">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="88ed8-247">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="88ed8-247">Markdown is described in the next section.</span></span>

| <span data-ttu-id="88ed8-248">Format</span><span class="sxs-lookup"><span data-stu-id="88ed8-248">Style</span></span> | <span data-ttu-id="88ed8-249">Beispiel</span><span class="sxs-lookup"><span data-stu-id="88ed8-249">Example</span></span> | <span data-ttu-id="88ed8-250">HTML</span><span class="sxs-lookup"><span data-stu-id="88ed8-250">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="88ed8-251">bold</span><span class="sxs-lookup"><span data-stu-id="88ed8-251">bold</span></span> | <span data-ttu-id="88ed8-252">**text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-252">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="88ed8-253">italic</span><span class="sxs-lookup"><span data-stu-id="88ed8-253">italic</span></span> | <span data-ttu-id="88ed8-254">*text*</span><span class="sxs-lookup"><span data-stu-id="88ed8-254">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="88ed8-255">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="88ed8-255">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="88ed8-256">**Text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-256">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="88ed8-257">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="88ed8-257">strikethrough</span></span> | <span data-ttu-id="88ed8-258">~~text~~</span><span class="sxs-lookup"><span data-stu-id="88ed8-258">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="88ed8-259">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-259">unordered list</span></span> | <ul><li><span data-ttu-id="88ed8-260">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-260">text</span></span></li><li><span data-ttu-id="88ed8-261">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-261">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="88ed8-262">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-262">ordered list</span></span> | <ol><li><span data-ttu-id="88ed8-263">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-263">text</span></span></li><li><span data-ttu-id="88ed8-264">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-264">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="88ed8-265">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="88ed8-265">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="88ed8-266">blockquote</span><span class="sxs-lookup"><span data-stu-id="88ed8-266">blockquote</span></span> | <blockquote><span data-ttu-id="88ed8-267">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-267">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="88ed8-268">Link</span><span class="sxs-lookup"><span data-stu-id="88ed8-268">hyperlink</span></span> | [<span data-ttu-id="88ed8-269">Bing</span><span class="sxs-lookup"><span data-stu-id="88ed8-269">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="88ed8-270">Bildlink</span><span class="sxs-lookup"><span data-stu-id="88ed8-270">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="88ed8-271">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="88ed8-271">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="88ed8-272">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit HTML</span><span class="sxs-lookup"><span data-stu-id="88ed8-272">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="88ed8-273">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-273">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="88ed8-275">Unter iOS sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-275">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="88ed8-277">Probleme:</span><span class="sxs-lookup"><span data-stu-id="88ed8-277">Issues:</span></span>

* <span data-ttu-id="88ed8-278">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in Connectorkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="88ed8-278">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="88ed8-279">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="88ed8-279">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="88ed8-280">Unter Android sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-280">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="88ed8-282">Formatierungsbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="88ed8-282">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="88ed8-283">**HTML-Formatierung: Favoriten- und Miniaturansichtskarten**</span><span class="sxs-lookup"><span data-stu-id="88ed8-283">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="88ed8-284">HTML-Tags werden für einfache Karten wie die Hero- und Miniaturansichtskarte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-284">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="88ed8-285">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-285">Markdown is not supported.</span></span>

| <span data-ttu-id="88ed8-286">Format</span><span class="sxs-lookup"><span data-stu-id="88ed8-286">Style</span></span> | <span data-ttu-id="88ed8-287">Beispiel</span><span class="sxs-lookup"><span data-stu-id="88ed8-287">Example</span></span> | <span data-ttu-id="88ed8-288">HTML</span><span class="sxs-lookup"><span data-stu-id="88ed8-288">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="88ed8-289">bold</span><span class="sxs-lookup"><span data-stu-id="88ed8-289">bold</span></span> | <span data-ttu-id="88ed8-290">**text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-290">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="88ed8-291">italic</span><span class="sxs-lookup"><span data-stu-id="88ed8-291">italic</span></span> | <span data-ttu-id="88ed8-292">*text*</span><span class="sxs-lookup"><span data-stu-id="88ed8-292">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="88ed8-293">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="88ed8-293">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="88ed8-294">**Text**</span><span class="sxs-lookup"><span data-stu-id="88ed8-294">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="88ed8-295">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="88ed8-295">strikethrough</span></span> | <span data-ttu-id="88ed8-296">~~text~~</span><span class="sxs-lookup"><span data-stu-id="88ed8-296">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="88ed8-297">Ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-297">unordered list</span></span> | <ul><li><span data-ttu-id="88ed8-298">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-298">text</span></span></li><li><span data-ttu-id="88ed8-299">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-299">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="88ed8-300">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="88ed8-300">ordered list</span></span> | <ol><li><span data-ttu-id="88ed8-301">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-301">text</span></span></li><li><span data-ttu-id="88ed8-302">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-302">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="88ed8-303">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="88ed8-303">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="88ed8-304">blockquote</span><span class="sxs-lookup"><span data-stu-id="88ed8-304">blockquote</span></span> | <blockquote><span data-ttu-id="88ed8-305">text</span><span class="sxs-lookup"><span data-stu-id="88ed8-305">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="88ed8-306">Link</span><span class="sxs-lookup"><span data-stu-id="88ed8-306">hyperlink</span></span> | [<span data-ttu-id="88ed8-307">Bing</span><span class="sxs-lookup"><span data-stu-id="88ed8-307">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="88ed8-308">Bildlink</span><span class="sxs-lookup"><span data-stu-id="88ed8-308">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="88ed8-309">Unterschiede zwischen Mobilgeräten und Desktops bei einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-309">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="88ed8-310">Aufgrund von Auflösungsunterschieden zwischen desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="88ed8-310">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="88ed8-311">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-311">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="88ed8-313">Unter iOS wird html-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="88ed8-313">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="88ed8-315">Probleme:</span><span class="sxs-lookup"><span data-stu-id="88ed8-315">Issues:</span></span>

* <span data-ttu-id="88ed8-316">Zeichenformatierungen wie Fett und Kursiv werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="88ed8-316">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="88ed8-317">Unter Android sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88ed8-317">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="88ed8-319">Zeichenformatierungen wie fett und kursiv werden unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88ed8-319">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="88ed8-320">Formatierungsbeispiel für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="88ed8-320">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="88ed8-321">Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="88ed8-321">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="88ed8-322">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="88ed8-322">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
