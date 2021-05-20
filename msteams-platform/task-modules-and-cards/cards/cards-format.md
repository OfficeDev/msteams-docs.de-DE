---
title: Textformatierung in Karten
description: Beschreibt die Kartentextformatierung in Microsoft Teams
keywords: Teams Bots Karten Format
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 848656097f2c865705cc0d91dece93049d8c6790
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566582"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="b6ff2-104">Formatkarten in Teams</span><span class="sxs-lookup"><span data-stu-id="b6ff2-104">Format cards in Teams</span></span>

<span data-ttu-id="b6ff2-105">Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie Markdown oder HTML verwenden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="b6ff2-106">Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="b6ff2-107">Die Formatierung kann je nach Kartentyp mithilfe einer Teilmenge der XML-Formatierung (HTML) oder Markdown angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="b6ff2-108">Für die aktuelle und zukünftige Entwicklung werden Adaptive Karten mit Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="b6ff2-109">Die Formatierungsunterstützung unterscheidet sich zwischen den verschiedenen Kartentypen, und das Rendern der Karte kann sich geringfügig zwischen dem Desktop und dem mobilen Teams-Clients sowie Teams im Desktopbrowser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="b6ff2-110">Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="b6ff2-111">Bilder eine als , oder Dateien formatiert werden  `.png` `.jpg` und darf `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="b6ff2-112">Animiertes GIF wird offiziell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="b6ff2-113">Weitere Informationen finden Sie unter [Kartenreferenz](./cards-reference.md#inline-card-images).</span><span class="sxs-lookup"><span data-stu-id="b6ff2-113">For more information, see [Cards reference](./cards-reference.md#inline-card-images).</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="b6ff2-114">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="b6ff2-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="b6ff2-115">Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b6ff2-116">**Adaptive Karten**: Markdown wird im Feld Adaptive Karte `Textblock` sowie und `Fact.Title` `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="b6ff2-117">HTML wird in Adaptive-Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="b6ff2-118">**O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="b6ff2-119">**Markdown-Formatierung: Adaptive Karten**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="b6ff2-120">Die unterstützten Stile für `Textblock` `Fact.Title` und `Fact.Value` sind:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="b6ff2-121">Format</span><span class="sxs-lookup"><span data-stu-id="b6ff2-121">Style</span></span> | <span data-ttu-id="b6ff2-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b6ff2-122">Example</span></span> | <span data-ttu-id="b6ff2-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="b6ff2-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b6ff2-124">bold</span><span class="sxs-lookup"><span data-stu-id="b6ff2-124">bold</span></span> | <span data-ttu-id="b6ff2-125">**Bold**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="b6ff2-126">italic</span><span class="sxs-lookup"><span data-stu-id="b6ff2-126">italic</span></span> | <span data-ttu-id="b6ff2-127">_Italic_</span><span class="sxs-lookup"><span data-stu-id="b6ff2-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="b6ff2-128">ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-128">unordered list</span></span> | <ul><li><span data-ttu-id="b6ff2-129">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-129">text</span></span></li><li><span data-ttu-id="b6ff2-130">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="b6ff2-131">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-131">ordered list</span></span> | <ol><li><span data-ttu-id="b6ff2-132">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-132">text</span></span></li><li><span data-ttu-id="b6ff2-133">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="b6ff2-134">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="b6ff2-134">Hyperlinks</span></span> |[<span data-ttu-id="b6ff2-135">Bing</span><span class="sxs-lookup"><span data-stu-id="b6ff2-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="b6ff2-136">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="b6ff2-137">Überschriften</span><span class="sxs-lookup"><span data-stu-id="b6ff2-137">Headers</span></span>
* <span data-ttu-id="b6ff2-138">Tabellen</span><span class="sxs-lookup"><span data-stu-id="b6ff2-138">Tables</span></span>
* <span data-ttu-id="b6ff2-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="b6ff2-139">Images</span></span>
* <span data-ttu-id="b6ff2-140">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-140">Preformatted text</span></span>
* <span data-ttu-id="b6ff2-141">Blockzitaten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6ff2-142">Adaptive Karten unterstützen keine HTML-Formatierung.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="b6ff2-143">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="b6ff2-144">In Listen können Sie die `\r` oder `\n` Escape-Sequenzen für Zeilenumleinen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="b6ff2-145">Wenn Sie `\n\n` in einer Liste verwenden, wird das nächste Element in der Liste eingerückt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="b6ff2-146">Wenn Sie an anderer Stelle im Textblock Zeilenumleitungen benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="b6ff2-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="b6ff2-147">Mobilfunk- und Desktop-Unterschiede bei Adaptive-Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="b6ff2-148">Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Teams.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="b6ff2-149">Auf dem Desktop wird die Adaptive Card Markdown-Formatierung sowohl in Webbrowsern als auch in der Teams-Clientanwendung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Adaptive Kartenmarkierungsformatierung im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="b6ff2-151">Unter iOS wird die adaptive Kartenmarkierungsformatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Adaptive Kartenmarkierungsformatierung in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="b6ff2-153">Unter Android wird die Adaptive Card Markdown-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Adaptive Kartenmarkdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="b6ff2-155">Weitere Informationen zu Adaptive Cards</span><span class="sxs-lookup"><span data-stu-id="b6ff2-155">More information on Adaptive cards</span></span>

<span data-ttu-id="b6ff2-156">[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="b6ff2-157">Formatierungsbeispiel für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="b6ff2-158">Erwähnen Sie die Unterstützung in Adaptive Cards v1.2</span><span class="sxs-lookup"><span data-stu-id="b6ff2-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="b6ff2-159">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-159">Card based mentions are supported in web, desktop and mobile clients.</span></span> <span data-ttu-id="b6ff2-160">Sie können in einem adaptiven Kartenkörper für Bots und Messaging-Erweiterungsantworten .</span><span class="sxs-lookup"><span data-stu-id="b6ff2-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span> <span data-ttu-id="b6ff2-161">Um in Karten die Erwähnungen von - hinzuzufügen, folgen Sie der gleichen Benachrichtigungslogik und dem gleichen Rendering wie die von nachrichtenbasierten [Erwähnungen in Kanal- und Gruppenchatunterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span><span class="sxs-lookup"><span data-stu-id="b6ff2-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="b6ff2-162">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="b6ff2-163">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in Adaptive Cards v1.2 auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="b6ff2-164">Channel & Team-Erwähnungen werden in Bot-Nachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="b6ff2-165">Konstruktionserwähnungen</span><span class="sxs-lookup"><span data-stu-id="b6ff2-165">Constructing mentions</span></span>

<span data-ttu-id="b6ff2-166">Um eine Erwähnung in eine Adaptive Card aufzunehmen, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-166">To include a mention in an Adaptive Card your app needs to include the following elements:</span></span>

* <span data-ttu-id="b6ff2-167">`<at>username</at>` in den unterstützten Adaptive-Kartenelementen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-167">`<at>username</at>` in the supported Adaptive card elements.</span></span>
* <span data-ttu-id="b6ff2-168">Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt, das die Teams Benutzer-ID des genannten Benutzers enthält.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned.</span></span>
* <span data-ttu-id="b6ff2-169">Der `userId` ist einzigartig für Ihre Bot-ID und einen bestimmten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-169">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="b6ff2-170">Es kann verwendet werden, um einen bestimmten Benutzer zu @mention.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-170">It can be used to @mention a particular user.</span></span> <span data-ttu-id="b6ff2-171">Der `userId` kann mit einer der in get the user [ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)genannten Optionen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-171">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="b6ff2-172">Beispiel Adaptive Karte mit Erwähnung</span><span class="sxs-lookup"><span data-stu-id="b6ff2-172">Sample Adaptive card with a mention</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="b6ff2-173">Informationsmaskierung in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-173">Information masking in Adaptive cards</span></span>
<span data-ttu-id="b6ff2-174">Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort- oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements Adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karte.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-174">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span> 

> [!NOTE]
> <span data-ttu-id="b6ff2-175">Die Funktion unterstützt nur die Client-seitige Informationsmaskierung, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md)angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-175">The feature only supports client side information masking, the masked input text is sent as clear text to the https endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md).</span></span> 

> [!NOTE]
> <span data-ttu-id="b6ff2-176">Die Eigenschaft zum Maskieren von Informationen ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-176">The information masking property is currently available in the developer preview only.</span></span>

<span data-ttu-id="b6ff2-177">Um Informationen in adaptiven Karten zu maskieren, fügen Sie die `isMasked` Eigenschaft **dem Typ** `Input.Text` hinzu, und legen Sie den Wert auf *true* fest.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-177">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="b6ff2-178">Beispiel Adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="b6ff2-178">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="b6ff2-179">Das folgende Bild ist ein Beispiel für das Maskieren von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-179">The following image is an example of masking information in Adaptive cards:</span></span>

![Maskierung des Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="b6ff2-181">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="b6ff2-181">Full width Adaptive card</span></span>
<span data-ttu-id="b6ff2-182">Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Bereich zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-182">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="b6ff2-183">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-183">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="b6ff2-184">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="b6ff2-184">Constructing full width cards</span></span>
<span data-ttu-id="b6ff2-185">Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf festgelegt `Full` werden.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-185">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="b6ff2-186">Darüber hinaus muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-186">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="b6ff2-187">Muster-Adaptive-Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="b6ff2-187">Sample adaptive card with full width</span></span>

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

<span data-ttu-id="b6ff2-188">Eine adaptive Karte mit voller Breite wird wie folgt angezeigt: ![ Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-188">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="b6ff2-189">Wenn Sie die Eigenschaft nicht auf Voll festgelegt `width` haben, lautet die Standardansicht der Adaptive Card wie folgt: Adaptive Kartenansicht mit kleiner ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-189">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>

### <a name="typeahead-support"></a><span data-ttu-id="b6ff2-190">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="b6ff2-190">Typeahead support</span></span>

<span data-ttu-id="b6ff2-191">Innerhalb des [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Schemaelements kann das Filtern und Auswählen von Benutzern durch eine beträchtliche Anzahl von Auswahlmöglichkeiten die Aufgabenvervollständigung erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-191">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter through and select through a sizable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="b6ff2-192">Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingeschränkt oder gefiltert wird, während ein Benutzer die Eingabe eingibt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-192">Typeahead support within Adaptive cards can simplify input selection by narrowing or filtering the set of input choices as a user is typing the input.</span></span> 

#### <a name="enable-typeahead-in-adaptive-cards"></a><span data-ttu-id="b6ff2-193">Aktivieren von Typeahead in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-193">Enable typeahead in Adaptive cards</span></span>

<span data-ttu-id="b6ff2-194">So aktivieren Sie typeahead innerhalb des `Input.Choiceset` Satzes `style` auf und stellen `filtered` sie `isMultiSelect` sicher, dass auf festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-194">To enable typeahead within the `Input.Choiceset` set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span> 

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="b6ff2-195">Beispiel für adaptive Karte mit Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="b6ff2-195">Sample adaptive card with typeahead support</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="b6ff2-196">Bühnenansicht für Bilder in Adaptive Cards</span><span class="sxs-lookup"><span data-stu-id="b6ff2-196">Stage view for images in Adaptive Cards</span></span>

> [!NOTE]
> <span data-ttu-id="b6ff2-197">Diese Funktion ist derzeit nur in der Entwicklervorschau verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-197">This feature is currently available in developer preview only.</span></span>
 
<span data-ttu-id="b6ff2-198">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit hinzuzufügen, Bilder in der `msteams` Bühnenansicht selektiv anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-198">In an Adaptive card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="b6ff2-199">Wenn Benutzer den Mauszeiger über die Bilder bewegen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-199">When users hover over the images, they would see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="b6ff2-200">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-200">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="b6ff2-201">Wenn Benutzer den Mauszeiger über das Bild bewegen, wird oben rechts im Bild ein Erweiterungssymbol angezeigt: ![ Adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-201">When users hover over the image, an expand icon appears at top right corner of the image: ![Adaptive card with expandable image](../../assets/images/cards/adaptivecard-hover-expand-icon.png)</span></span>

<span data-ttu-id="b6ff2-202">Das Bild wird in der Bühnenansicht angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: ![ Bild zur Bühnenansicht erweitert](../../assets/images/cards/adaptivecard-expand-image.png)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-202">The image appears in stage view when the user selects the expand button: ![Image expanded to stage view](../../assets/images/cards/adaptivecard-expand-image.png)</span></span>

<span data-ttu-id="b6ff2-203">In der Bühnenansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-203">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="b6ff2-204">Sie können auswählen, welche Bilder in Ihrer Adaptive-Karte diese Funktion benötigen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-204">You can select which images in your Adaptive card needs to have this capability.</span></span>

> [!NOTE]
> <span data-ttu-id="b6ff2-205">Die Zoom-In- und Verkleinerungsfunktion gilt nur für die Bildelemente (Bildtyp) auf einer adaptiven Karte.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-205">Zoom in and zoom out capability applies only to the image elements (Image type) in an Adaptive card.</span></span>

> [!NOTE]
> <span data-ttu-id="b6ff2-206">Für Teams mobilen Apps sind die Bühnenansichtsfunktionen für Bilder in Adaptive Cards standardmäßig verfügbar, und Benutzer können adaptive Kartenbilder in der Bühnenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-206">For Teams mobile apps, stage view functionality for images in Adaptive Cards are available by default and users will be able to view Adaptive card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="b6ff2-207">**Markdown-Formatierung: O365 Connector-Karten**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-207">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="b6ff2-208">Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-208">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="b6ff2-209">Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-209">HTML support is described in the last section.</span></span>

| <span data-ttu-id="b6ff2-210">Format</span><span class="sxs-lookup"><span data-stu-id="b6ff2-210">Style</span></span> | <span data-ttu-id="b6ff2-211">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b6ff2-211">Example</span></span> | <span data-ttu-id="b6ff2-212">Markdown</span><span class="sxs-lookup"><span data-stu-id="b6ff2-212">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b6ff2-213">bold</span><span class="sxs-lookup"><span data-stu-id="b6ff2-213">bold</span></span> | <span data-ttu-id="b6ff2-214">**text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-214">**text**</span></span> | `**text**` |
| <span data-ttu-id="b6ff2-215">italic</span><span class="sxs-lookup"><span data-stu-id="b6ff2-215">italic</span></span> | <span data-ttu-id="b6ff2-216">*text*</span><span class="sxs-lookup"><span data-stu-id="b6ff2-216">*text*</span></span> | `*text*` |
| <span data-ttu-id="b6ff2-217">Header (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-217">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="b6ff2-218">**Text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-218">**Text**</span></span> | `### Text`|
| <span data-ttu-id="b6ff2-219">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="b6ff2-219">strikethrough</span></span> | <span data-ttu-id="b6ff2-220">~~text~~</span><span class="sxs-lookup"><span data-stu-id="b6ff2-220">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="b6ff2-221">ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-221">unordered list</span></span> | <ul><li><span data-ttu-id="b6ff2-222">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-222">text</span></span></li><li><span data-ttu-id="b6ff2-223">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-223">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="b6ff2-224">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-224">ordered list</span></span> | <ol><li><span data-ttu-id="b6ff2-225">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-225">text</span></span></li><li><span data-ttu-id="b6ff2-226">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-226">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="b6ff2-227">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-227">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="b6ff2-228">blockquote</span><span class="sxs-lookup"><span data-stu-id="b6ff2-228">blockquote</span></span> | <span data-ttu-id="b6ff2-229">>Blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-229">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="b6ff2-230">Link</span><span class="sxs-lookup"><span data-stu-id="b6ff2-230">hyperlink</span></span> | [<span data-ttu-id="b6ff2-231">Bing</span><span class="sxs-lookup"><span data-stu-id="b6ff2-231">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="b6ff2-232">Bildlink</span><span class="sxs-lookup"><span data-stu-id="b6ff2-232">image link</span></span> |![Ente auf einem Felsen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="b6ff2-234">In Verbindungskarten werden Zeilenlinien für gerendert, `\n\n` jedoch nicht für oder `\n` `\r` .</span><span class="sxs-lookup"><span data-stu-id="b6ff2-234">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="b6ff2-235">Mobile und Desktop-Unterschiede für Connectorkarten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="b6ff2-235">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="b6ff2-236">Auf dem Desktop sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-236">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="b6ff2-238">Unter iOS sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-238">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="b6ff2-240">Probleme:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-240">Issues:</span></span>

* <span data-ttu-id="b6ff2-241">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inline-Images in Connector Cards.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-241">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="b6ff2-242">Blockquotes werden als eingerückt, aber ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-242">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="b6ff2-243">Unter Android sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-243">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="b6ff2-245">Formatieren von Beispiel für Markdown Connector Cards</span><span class="sxs-lookup"><span data-stu-id="b6ff2-245">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="b6ff2-246">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="b6ff2-246">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="b6ff2-247">**HTML-Formatierung: O365 Connector-Karten**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-247">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="b6ff2-248">Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-248">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="b6ff2-249">Markdown wird im nächsten Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-249">Markdown is described in the next section.</span></span>

| <span data-ttu-id="b6ff2-250">Format</span><span class="sxs-lookup"><span data-stu-id="b6ff2-250">Style</span></span> | <span data-ttu-id="b6ff2-251">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b6ff2-251">Example</span></span> | <span data-ttu-id="b6ff2-252">HTML</span><span class="sxs-lookup"><span data-stu-id="b6ff2-252">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b6ff2-253">bold</span><span class="sxs-lookup"><span data-stu-id="b6ff2-253">bold</span></span> | <span data-ttu-id="b6ff2-254">**text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-254">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="b6ff2-255">italic</span><span class="sxs-lookup"><span data-stu-id="b6ff2-255">italic</span></span> | <span data-ttu-id="b6ff2-256">*text*</span><span class="sxs-lookup"><span data-stu-id="b6ff2-256">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="b6ff2-257">Header (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-257">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="b6ff2-258">**Text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-258">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="b6ff2-259">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="b6ff2-259">strikethrough</span></span> | <span data-ttu-id="b6ff2-260">~~text~~</span><span class="sxs-lookup"><span data-stu-id="b6ff2-260">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="b6ff2-261">ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-261">unordered list</span></span> | <ul><li><span data-ttu-id="b6ff2-262">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-262">text</span></span></li><li><span data-ttu-id="b6ff2-263">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-263">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="b6ff2-264">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-264">ordered list</span></span> | <ol><li><span data-ttu-id="b6ff2-265">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-265">text</span></span></li><li><span data-ttu-id="b6ff2-266">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-266">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="b6ff2-267">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-267">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="b6ff2-268">blockquote</span><span class="sxs-lookup"><span data-stu-id="b6ff2-268">blockquote</span></span> | <blockquote><span data-ttu-id="b6ff2-269">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-269">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="b6ff2-270">Link</span><span class="sxs-lookup"><span data-stu-id="b6ff2-270">hyperlink</span></span> | [<span data-ttu-id="b6ff2-271">Bing</span><span class="sxs-lookup"><span data-stu-id="b6ff2-271">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="b6ff2-272">Bildlink</span><span class="sxs-lookup"><span data-stu-id="b6ff2-272">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="b6ff2-273">In Connectorkarten werden Zeilenlinien in HTML mit dem Tag gerendert. `<p>`</span><span class="sxs-lookup"><span data-stu-id="b6ff2-273">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="b6ff2-274">Mobile und Desktop-Unterschiede für Connectorkarten mit HTML</span><span class="sxs-lookup"><span data-stu-id="b6ff2-274">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="b6ff2-275">Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-275">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="b6ff2-277">Unter iOS sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-277">On iOS, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="b6ff2-279">Probleme:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-279">Issues:</span></span>

* <span data-ttu-id="b6ff2-280">Inlinebilder werden unter iOS weder mit Markdown noch html in Connector Cards gerendert.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-280">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="b6ff2-281">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-281">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="b6ff2-282">Unter Android sieht die HTML-Formatierung wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-282">On Android, HTML formatting looks like this:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="b6ff2-284">Formatierungsbeispiel für HTML Connector Cards</span><span class="sxs-lookup"><span data-stu-id="b6ff2-284">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="b6ff2-285">**HTML-Formatierung: Helden- und Miniaturkarten**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-285">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="b6ff2-286">HTML-Tags werden für einfache Karten wie Helden- und Miniaturkarten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-286">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="b6ff2-287">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-287">Markdown is not supported.</span></span>

| <span data-ttu-id="b6ff2-288">Format</span><span class="sxs-lookup"><span data-stu-id="b6ff2-288">Style</span></span> | <span data-ttu-id="b6ff2-289">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b6ff2-289">Example</span></span> | <span data-ttu-id="b6ff2-290">HTML</span><span class="sxs-lookup"><span data-stu-id="b6ff2-290">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="b6ff2-291">bold</span><span class="sxs-lookup"><span data-stu-id="b6ff2-291">bold</span></span> | <span data-ttu-id="b6ff2-292">**text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-292">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="b6ff2-293">italic</span><span class="sxs-lookup"><span data-stu-id="b6ff2-293">italic</span></span> | <span data-ttu-id="b6ff2-294">*text*</span><span class="sxs-lookup"><span data-stu-id="b6ff2-294">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="b6ff2-295">Header (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="b6ff2-295">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="b6ff2-296">**Text**</span><span class="sxs-lookup"><span data-stu-id="b6ff2-296">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="b6ff2-297">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="b6ff2-297">strikethrough</span></span> | <span data-ttu-id="b6ff2-298">~~text~~</span><span class="sxs-lookup"><span data-stu-id="b6ff2-298">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="b6ff2-299">ungeordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-299">unordered list</span></span> | <ul><li><span data-ttu-id="b6ff2-300">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-300">text</span></span></li><li><span data-ttu-id="b6ff2-301">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-301">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="b6ff2-302">geordnete Liste</span><span class="sxs-lookup"><span data-stu-id="b6ff2-302">ordered list</span></span> | <ol><li><span data-ttu-id="b6ff2-303">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-303">text</span></span></li><li><span data-ttu-id="b6ff2-304">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-304">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="b6ff2-305">vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-305">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="b6ff2-306">blockquote</span><span class="sxs-lookup"><span data-stu-id="b6ff2-306">blockquote</span></span> | <blockquote><span data-ttu-id="b6ff2-307">text</span><span class="sxs-lookup"><span data-stu-id="b6ff2-307">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="b6ff2-308">Link</span><span class="sxs-lookup"><span data-stu-id="b6ff2-308">hyperlink</span></span> | [<span data-ttu-id="b6ff2-309">Bing</span><span class="sxs-lookup"><span data-stu-id="b6ff2-309">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="b6ff2-310">Bildlink</span><span class="sxs-lookup"><span data-stu-id="b6ff2-310">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="b6ff2-311">Mobilfunk- und Desktop-Unterschiede für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-311">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="b6ff2-312">Aufgrund von Auflösungsunterschieden zwischen desktop- und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-312">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="b6ff2-313">Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-313">On the desktop, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="b6ff2-315">Unter iOS wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-315">On iOS, HTML formatting appears like this:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="b6ff2-317">Probleme:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-317">Issues:</span></span>

* <span data-ttu-id="b6ff2-318">Zeichenformatierungen wie fett und kursiv werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-318">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="b6ff2-319">Unter Android wird die HTML-Formatierung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b6ff2-319">On Android, HTML formatting appears like this:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="b6ff2-321">Zeichenformatierung wie fett und kursiv anzeiget korrekt auf Android.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-321">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="b6ff2-322">Formatieren von Beispielen für HTML-Formatierung in einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="b6ff2-322">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="b6ff2-323">Diese Screenshots wurden mit Teams AppStudio erstellt, wo die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-323">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="b6ff2-324">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="b6ff2-324">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
