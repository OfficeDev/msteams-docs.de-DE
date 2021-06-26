---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentext in Microsoft Teams
keywords: Teams-Bots- Kartenformat
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 877a16f884e91138dc656434438a5fe1dd2ffd6e
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140641"
---
# <a name="format-cards-in-microsoft-teams"></a><span data-ttu-id="5121f-104">Formatieren von Karten in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5121f-104">Format cards in Microsoft Teams</span></span>

<span data-ttu-id="5121f-105">Es folgen die beiden Möglichkeiten zum Hinzufügen von Rich-Text-Formatierungen zu Ihren Karten:</span><span class="sxs-lookup"><span data-stu-id="5121f-105">Following are the two ways to add rich text formatting to your cards:</span></span>
* [<span data-ttu-id="5121f-106">Markdown</span><span class="sxs-lookup"><span data-stu-id="5121f-106">Markdown</span></span>](#format-cards-with-markdown)
* [<span data-ttu-id="5121f-107">HTML</span><span class="sxs-lookup"><span data-stu-id="5121f-107">HTML</span></span>](#format-cards-with-html)

<span data-ttu-id="5121f-108">Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.</span><span class="sxs-lookup"><span data-stu-id="5121f-108">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="5121f-109">Die Formatierung kann je nach Kartentyp mithilfe einer Teilmenge von XML- oder HTML-Formatierungen oder Markdown angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5121f-109">Formatting can be specified using a subset of XML or HTML formatting or Markdown, depending on the card type.</span></span> <span data-ttu-id="5121f-110">Für die aktuelle und zukünftige Entwicklung adaptiver Karten wird die Markdown-Formatierung empfohlen.</span><span class="sxs-lookup"><span data-stu-id="5121f-110">For current and future development of Adaptive Cards, Markdown formatting is recommended.</span></span>

<span data-ttu-id="5121f-111">Die Formatierungsunterstützung unterscheidet sich zwischen Kartentypen.</span><span class="sxs-lookup"><span data-stu-id="5121f-111">Formatting support differs between card types.</span></span> <span data-ttu-id="5121f-112">Das Rendern der Karte kann sich geringfügig zwischen dem Desktop- und dem mobilen Microsoft Teams-Clients sowie Teams im Desktopbrowser unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5121f-112">Rendering of the card can differ slightly between the desktop and the mobile Microsoft Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="5121f-113">Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen.</span><span class="sxs-lookup"><span data-stu-id="5121f-113">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="5121f-114">Bilder können als , oder Dateien formatiert werden `.png` `.jpg` und `.gif` dürfen 1024 ×1024 px oder 1 MB nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="5121f-114">Images can be formatted as `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="5121f-115">Animierte GIF-Dateien werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-115">Animated GIF is not supported.</span></span> <span data-ttu-id="5121f-116">Weitere Informationen finden Sie unter [Kartentypen.](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="5121f-116">For more information, see [types of cards](./cards-reference.md#inline-card-images).</span></span>

<span data-ttu-id="5121f-117">Sie können adaptive Karten und Office 365 Connectorkarten mit Markdown formatieren, die bestimmte unterstützte Formatvorlagen enthalten.</span><span class="sxs-lookup"><span data-stu-id="5121f-117">You can format Adaptive Cards and Office 365 Connector cards with Markdown that include certain supported styles.</span></span>

## <a name="format-cards-with-markdown"></a><span data-ttu-id="5121f-118">Formatieren von Karten mit Markdown</span><span class="sxs-lookup"><span data-stu-id="5121f-118">Format cards with Markdown</span></span>

<span data-ttu-id="5121f-119">Die folgenden Kartentypen unterstützen Markdown-Formatierung in Teams:</span><span class="sxs-lookup"><span data-stu-id="5121f-119">The following card types support Markdown formatting in Teams:</span></span>

* <span data-ttu-id="5121f-120">Adaptive Karten: Markdown wird im Feld für adaptive Karten `Textblock` sowie `Fact.Title` und `Fact.Value` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-120">Adaptive Cards: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="5121f-121">HTML wird in adaptiven Karten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-121">HTML is not supported in Adaptive Cards.</span></span>
* <span data-ttu-id="5121f-122">O365-Connectorkarten: Markdown und beschränkter HTML-Code werden in O365-Connectorkarten in den Textfeldern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-122">O365 Connector cards: Markdown and limited HTML is supported in O365 Connector cards in the text fields.</span></span>

<span data-ttu-id="5121f-123">Sie können Newlines für adaptive Karten verwenden `\r` oder `\n` Escapesequenzen für Newlines in Listen verwenden.</span><span class="sxs-lookup"><span data-stu-id="5121f-123">You can use newlines for Adaptive Cards using `\r` or `\n` escape sequences for newlines in lists.</span></span> <span data-ttu-id="5121f-124">Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="5121f-124">Formatting is different between the desktop and the mobile versions of Teams for Adaptive Cards.</span></span> <span data-ttu-id="5121f-125">Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-125">Card-based mentions are supported in web, desktop, and mobile clients.</span></span> <span data-ttu-id="5121f-126">Sie können die Eigenschaft zum Maskieren von Informationen verwenden, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive `Input.Text` Karten.</span><span class="sxs-lookup"><span data-stu-id="5121f-126">You can use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive Card `Input.Text` input element.</span></span> <span data-ttu-id="5121f-127">Sie können die Breite einer adaptiven Karte mithilfe des `width` Objekts erweitern.</span><span class="sxs-lookup"><span data-stu-id="5121f-127">You can expand the width of an Adaptive Card using the `width` object.</span></span> <span data-ttu-id="5121f-128">Sie können die Typaheadunterstützung in adaptiven Karten aktivieren und die Eingabeauswahl filtern, während der Benutzer die Eingabe eingibt.</span><span class="sxs-lookup"><span data-stu-id="5121f-128">You can enable typeahead support within Adaptive Cards and filter the set of input choices as the user types the input.</span></span> <span data-ttu-id="5121f-129">Mit der Eigenschaft können Sie die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5121f-129">You can use the `msteams` property to add the ability to display images in stage view selectively.</span></span>

<span data-ttu-id="5121f-130">Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für adaptive Karten und Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="5121f-130">Formatting is different between the desktop and the mobile versions of Teams for Adaptive Cards and connector cards.</span></span> <span data-ttu-id="5121f-131">In diesem Abschnitt können Sie das Beispiel für das Markdown-Format für adaptive Karten und Connectorkarten durchgehen.</span><span class="sxs-lookup"><span data-stu-id="5121f-131">In this section, you can go through the Markdown format example for Adaptive Cards and connector cards.</span></span>

# <a name="markdown-format-for-adaptive-cards"></a>[<span data-ttu-id="5121f-132">Markdown-Format für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-132">Markdown format for Adaptive Cards</span></span>](#tab/adaptive-md)

 <span data-ttu-id="5121f-133">Die folgende Tabelle enthält die unterstützten Formatvorlagen für `Textblock` `Fact.Title` , `Fact.Value` und:</span><span class="sxs-lookup"><span data-stu-id="5121f-133">The following table provides the supported styles for `Textblock`, `Fact.Title`, and `Fact.Value`:</span></span>

| <span data-ttu-id="5121f-134">Format</span><span class="sxs-lookup"><span data-stu-id="5121f-134">Style</span></span> | <span data-ttu-id="5121f-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5121f-135">Example</span></span> | <span data-ttu-id="5121f-136">Markdown</span><span class="sxs-lookup"><span data-stu-id="5121f-136">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5121f-137">Fett</span><span class="sxs-lookup"><span data-stu-id="5121f-137">Bold</span></span> | <span data-ttu-id="5121f-138">**Bold**</span><span class="sxs-lookup"><span data-stu-id="5121f-138">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="5121f-139">Kursiv</span><span class="sxs-lookup"><span data-stu-id="5121f-139">Italic</span></span> | <span data-ttu-id="5121f-140">_Italic_</span><span class="sxs-lookup"><span data-stu-id="5121f-140">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="5121f-141">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-141">Unordered list</span></span> | <ul><li><span data-ttu-id="5121f-142">text</span><span class="sxs-lookup"><span data-stu-id="5121f-142">text</span></span></li><li><span data-ttu-id="5121f-143">text</span><span class="sxs-lookup"><span data-stu-id="5121f-143">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="5121f-144">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-144">Ordered list</span></span> | <ol><li><span data-ttu-id="5121f-145">text</span><span class="sxs-lookup"><span data-stu-id="5121f-145">text</span></span></li><li><span data-ttu-id="5121f-146">text</span><span class="sxs-lookup"><span data-stu-id="5121f-146">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="5121f-147">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="5121f-147">Hyperlinks</span></span> |[<span data-ttu-id="5121f-148">Bing</span><span class="sxs-lookup"><span data-stu-id="5121f-148">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="5121f-149">Die folgenden Markdown-Tags werden nicht unterstützt:</span><span class="sxs-lookup"><span data-stu-id="5121f-149">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="5121f-150">Überschriften</span><span class="sxs-lookup"><span data-stu-id="5121f-150">Headers</span></span>
* <span data-ttu-id="5121f-151">Tabellen</span><span class="sxs-lookup"><span data-stu-id="5121f-151">Tables</span></span>
* <span data-ttu-id="5121f-152">Bilder</span><span class="sxs-lookup"><span data-stu-id="5121f-152">Images</span></span>
* <span data-ttu-id="5121f-153">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="5121f-153">Preformatted text</span></span>
* <span data-ttu-id="5121f-154">Blockzitaten</span><span class="sxs-lookup"><span data-stu-id="5121f-154">Blockquotes</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="5121f-155">Newlines für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-155">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="5121f-156">Sie können die `\r` `\n` Oder Escapesequenzen für Newlines in Listen verwenden.</span><span class="sxs-lookup"><span data-stu-id="5121f-156">You can use the `\r` or `\n` escape sequences for newlines in lists.</span></span> <span data-ttu-id="5121f-157">Die Verwendung `\n\n` in Listen bewirkt, dass das nächste Element in der Liste eingezogen wird.</span><span class="sxs-lookup"><span data-stu-id="5121f-157">Using `\n\n` in lists causes the next element in the list to be indented.</span></span> <span data-ttu-id="5121f-158">Wenn Sie newlines an anderer Stelle im TextBlock benötigen, verwenden Sie `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="5121f-158">If you require newlines elsewhere in the TextBlock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="5121f-159">Unterschiede zwischen Mobilgeräten und Desktops für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-159">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="5121f-160">Auf dem Desktop wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung in Webbrowsern und in der Teams Clientanwendung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-160">On the desktop, Adaptive Card Markdown formatting appears as shown in the following image in both web browsers and in the Teams client application:</span></span>

![Markdown-Formatierung für adaptive Karten im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="5121f-162">Unter iOS wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-162">On iOS, Adaptive Card Markdown formatting appears as shown in the following image:</span></span>

![Markdown-Formatierung adaptiver Karten in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="5121f-164">Unter Android wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-164">On Android, Adaptive Card Markdown formatting appears as shown in the following image:</span></span>

![Markdown-Formatierung für adaptive Karten in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

<span data-ttu-id="5121f-166">Weitere Informationen finden Sie unter [Textfeatures in adaptiven Karten.](/adaptive-cards/create/textfeatures)</span><span class="sxs-lookup"><span data-stu-id="5121f-166">For more information, see [text features in Adaptive Cards](/adaptive-cards/create/textfeatures).</span></span>

> [!NOTE]
> <span data-ttu-id="5121f-167">Die in diesem Abschnitt erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-167">The date and localization features mentioned in this section are not supported in Teams.</span></span>

### <a name="adaptive-cards-format-sample"></a><span data-ttu-id="5121f-168">Beispiel für adaptive Kartenformat</span><span class="sxs-lookup"><span data-stu-id="5121f-168">Adaptive Cards format sample</span></span>

<span data-ttu-id="5121f-169">Der folgende Code zeigt ein Beispiel für die Formatierung adaptiver Karten:</span><span class="sxs-lookup"><span data-stu-id="5121f-169">The following code shows an example of Adaptive Cards formatting:</span></span>

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

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="5121f-170">Erwähnen der Unterstützung in adaptiven Karten v1.2</span><span class="sxs-lookup"><span data-stu-id="5121f-170">Mention support within Adaptive Cards v1.2</span></span>

<span data-ttu-id="5121f-171">Sie können @mentions in einem Textkörper für adaptive Karten für Bots und Messaging-Erweiterungsantworten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5121f-171">You can add @mentions within an Adaptive Card body for bots and messaging extension responses.</span></span> <span data-ttu-id="5121f-172">Um @mentions in Karten hinzuzufügen, folgen Sie der gleichen Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte [Erwähnungen in Kanal- und Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)</span><span class="sxs-lookup"><span data-stu-id="5121f-172">To add @mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).</span></span>

<span data-ttu-id="5121f-173">Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.</span><span class="sxs-lookup"><span data-stu-id="5121f-173">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="5121f-174">[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-174">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive Cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="5121f-175">Kanal- und Teamerwähnungen werden in Botnachrichten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-175">Channel and team mentions are not supported in bot messages.</span></span>

<span data-ttu-id="5121f-176">Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="5121f-176">To include a mention in an Adaptive Card, your app needs to include the following elements:</span></span>

* <span data-ttu-id="5121f-177">`<at>username</at>` in den unterstützten adaptiven Kartenelementen.</span><span class="sxs-lookup"><span data-stu-id="5121f-177">`<at>username</at>` in the supported Adaptive Card elements.</span></span>
* <span data-ttu-id="5121f-178">Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt enthält die Teams Benutzer-ID des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="5121f-178">The `mention` object inside of an `msteams` property in the card content includes the Teams user ID of the user being mentioned.</span></span>
* <span data-ttu-id="5121f-179">Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="5121f-179">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="5121f-180">Es kann verwendet werden, um einen bestimmten Benutzer zu @mention.</span><span class="sxs-lookup"><span data-stu-id="5121f-180">It can be used to @mention a particular user.</span></span> <span data-ttu-id="5121f-181">Die `userId` kann mithilfe einer der im [Abrufen der Benutzer-ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)erwähnten Optionen abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="5121f-181">The `userId` can be retrieved using one of the options mentioned in [get the user ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="5121f-182">Beispiel für eine adaptive Karte mit einer Erwähnung</span><span class="sxs-lookup"><span data-stu-id="5121f-182">Sample Adaptive Card with a mention</span></span>

<span data-ttu-id="5121f-183">Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit einer Erwähnung:</span><span class="sxs-lookup"><span data-stu-id="5121f-183">The following code shows an example of Adaptive Card with a mention:</span></span>

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

### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="5121f-184">Informationsformatierung in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-184">Information masking in Adaptive Cards</span></span>

<span data-ttu-id="5121f-185">Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karten.</span><span class="sxs-lookup"><span data-stu-id="5121f-185">Use the information masking property to mask specific information, such as password or sensitive information from users within the Adaptive Card [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) input element.</span></span>

> [!NOTE]
> <span data-ttu-id="5121f-186">Das Feature unterstützt nur die clientseitige Informationsmaske.</span><span class="sxs-lookup"><span data-stu-id="5121f-186">The feature only supports client side information masking.</span></span> <span data-ttu-id="5121f-187">Der maskierte Eingabetext wird als Klartext an die HTTPS-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint)angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="5121f-187">The masked input text is sent as clear text to the HTTPS endpoint address that was specified during [bot configuration](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint).</span></span>

<span data-ttu-id="5121f-188">Um Informationen in adaptiven Karten zu maskieren, fügen Sie die `isMasked` Eigenschaft zum **Eingeben** `Input.Text` hinzu, und legen Sie ihren Wert auf **"true"** fest.</span><span class="sxs-lookup"><span data-stu-id="5121f-188">To mask information in Adaptive Cards, add the `isMasked` property to **type** `Input.Text`, and set its value to **true**.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="5121f-189">Beispiel für adaptive Karte mit Maskierungseigenschaft</span><span class="sxs-lookup"><span data-stu-id="5121f-189">Sample Adaptive Card with masking property</span></span>

<span data-ttu-id="5121f-190">Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Maskierungseigenschaft:</span><span class="sxs-lookup"><span data-stu-id="5121f-190">The following code shows an example of Adaptive Card with masking property:</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

<span data-ttu-id="5121f-191">Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:</span><span class="sxs-lookup"><span data-stu-id="5121f-191">The following image is an example of masking information in Adaptive Cards:</span></span>

![Maskierungsinformationsbild](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="5121f-193">Adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="5121f-193">Full width Adaptive Card</span></span>

<span data-ttu-id="5121f-194">Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Platz zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="5121f-194">You can use the `msteams` property to expand the width of an Adaptive Card and make use of additional canvas space.</span></span> <span data-ttu-id="5121f-195">Der nächste Abschnitt enthält Informationen zur Verwendung der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5121f-195">The next section provides information on how to use the property.</span></span>

#### <a name="construct-full-width-cards"></a><span data-ttu-id="5121f-196">Erstellen von Karten mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="5121f-196">Construct full width cards</span></span>

<span data-ttu-id="5121f-197">Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf festgelegt `Full` werden.</span><span class="sxs-lookup"><span data-stu-id="5121f-197">To make a full width Adaptive Card, the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="5121f-198">Beispiel für adaptive Karte mit voller Breite</span><span class="sxs-lookup"><span data-stu-id="5121f-198">Sample Adaptive Card with full width</span></span>

<span data-ttu-id="5121f-199">Um eine adaptive Karte mit voller Breite zu erstellen, muss Ihre App die Elemente aus dem folgenden Codebeispiel enthalten:</span><span class="sxs-lookup"><span data-stu-id="5121f-199">To make a full width Adaptive Card, your app must include the elements from the following code sample:</span></span>

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

<span data-ttu-id="5121f-200">Die folgende Abbildung zeigt eine adaptive Karte mit voller Breite:</span><span class="sxs-lookup"><span data-stu-id="5121f-200">The following image shows a full width Adaptive Card:</span></span>

![Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)

<span data-ttu-id="5121f-202">Die folgende Abbildung zeigt die Standardansicht der adaptiven Karte, wenn Sie die Eigenschaft nicht `width` auf **"Vollständig"** festgelegt haben:</span><span class="sxs-lookup"><span data-stu-id="5121f-202">The following image shows the default view of the Adaptive Card when you have not set the `width` property to **Full**:</span></span>

![Ansicht für adaptive Karten mit geringer Breite](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a><span data-ttu-id="5121f-204">Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="5121f-204">Typeahead support</span></span>

<span data-ttu-id="5121f-205">Innerhalb des Schemaelements kann das Abfragen von [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Benutzern zum Filtern und Auswählen einer großen Anzahl von Auswahlmöglichkeiten den Abschluss der Aufgabe erheblich verlangsamen.</span><span class="sxs-lookup"><span data-stu-id="5121f-205">Within the [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) schema element, asking users to filter and select a sizeable number of choices can significantly slow down task completion.</span></span> <span data-ttu-id="5121f-206">Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingegrenzt oder gefiltert wird, während der Benutzer die Eingabe eingibt.</span><span class="sxs-lookup"><span data-stu-id="5121f-206">Typeahead support within Adaptive Cards can simplify input selection by narrowing or filtering the set of input choices as the user types the input.</span></span>

<span data-ttu-id="5121f-207">So aktivieren Sie Typeahead in der `Input.Choiceset` , legen Sie `style` `filtered` fest, und stellen Sie sicher, dass `isMultiSelect` sie auf festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="5121f-207">To enable typeahead within the `Input.Choiceset`, set `style` to `filtered` and ensure `isMultiSelect` is set to `false`.</span></span>

#### <a name="sample-adaptive-card-with-typeahead-support"></a><span data-ttu-id="5121f-208">Beispiel für adaptive Karte mit Typeahead-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="5121f-208">Sample Adaptive Card with typeahead support</span></span>

<span data-ttu-id="5121f-209">Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Typahead-Unterstützung:</span><span class="sxs-lookup"><span data-stu-id="5121f-209">The following code shows an example of Adaptive Card with typeahead support:</span></span>

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

### <a name="stage-view-for-images-in-adaptive-cards"></a><span data-ttu-id="5121f-210">Phasenansicht für Bilder in adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-210">Stage view for images in Adaptive Cards</span></span>

<span data-ttu-id="5121f-211">In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5121f-211">In an Adaptive Card, you can use the `msteams` property to add the ability to display images in stage view selectively.</span></span> <span data-ttu-id="5121f-212">Wenn Benutzer mit dem Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist.</span><span class="sxs-lookup"><span data-stu-id="5121f-212">When users hover over the images, they can see an expand icon, for which the `allowExpand` attribute is set to `true`.</span></span> <span data-ttu-id="5121f-213">Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5121f-213">For information on how to use the property, see the following example:</span></span>

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

<span data-ttu-id="5121f-214">Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke ein Erweiterungssymbol angezeigt, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="5121f-214">When users hover over the image, an expand icon appears at the top right corner as shown in the following image:</span></span>

![Adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

<span data-ttu-id="5121f-216">Das Bild wird in der Phasenansicht angezeigt, wenn der Benutzer das Erweiterungssymbol wie in der folgenden Abbildung dargestellt auswählt:</span><span class="sxs-lookup"><span data-stu-id="5121f-216">The image appears in stage view when the user selects the expand icon as shown in the following image:</span></span>

![Bild, erweitert auf Phasenansicht](../../assets/images/cards/adaptivecard-expand-image.png)

<span data-ttu-id="5121f-218">In der Phasenansicht können Benutzer das Bild vergrößern und verkleinern.</span><span class="sxs-lookup"><span data-stu-id="5121f-218">In the stage view, users can zoom in and zoom out of the image.</span></span> <span data-ttu-id="5121f-219">Sie können die Bilder in Ihrer adaptiven Karte auswählen, die über diese Funktion verfügen müssen.</span><span class="sxs-lookup"><span data-stu-id="5121f-219">You can select the images in your Adaptive Card that must have this capability.</span></span>

> [!NOTE]
> * <span data-ttu-id="5121f-220">Die Funktion zum Vergrößern und Verkleinern gilt nur für die Bildelemente, bei denen es sich um Bildtypen in einer adaptiven Karte handelt.</span><span class="sxs-lookup"><span data-stu-id="5121f-220">Zoom in and zoom out capability applies only to the image elements that is image type in an Adaptive Card.</span></span>
> * <span data-ttu-id="5121f-221">Für Teams mobile Apps ist standardmäßig die Phasenansichtsfunktion für Bilder in adaptiven Karten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5121f-221">For Teams mobile apps, stage view functionality for images in Adaptive Cards is available by default.</span></span> <span data-ttu-id="5121f-222">Benutzer können Adaptive Kartenbilder in der Phasenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="5121f-222">Users can view Adaptive Card images in stage view by simply tapping on the image, irrespective of whether the `allowExpand` attribute is present or not.</span></span>

# <a name="markdown-format-for-o365-connector-cards"></a>[<span data-ttu-id="5121f-223">Markdownformat für O365-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-223">Markdown format for O365 Connector cards</span></span>](#tab/connector-md)

<span data-ttu-id="5121f-224">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="5121f-224">Connector cards support limited Markdown and HTML formatting.</span></span>

| <span data-ttu-id="5121f-225">Format</span><span class="sxs-lookup"><span data-stu-id="5121f-225">Style</span></span> | <span data-ttu-id="5121f-226">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5121f-226">Example</span></span> | <span data-ttu-id="5121f-227">Markdown</span><span class="sxs-lookup"><span data-stu-id="5121f-227">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5121f-228">Fett</span><span class="sxs-lookup"><span data-stu-id="5121f-228">Bold</span></span> | <span data-ttu-id="5121f-229">**text**</span><span class="sxs-lookup"><span data-stu-id="5121f-229">**text**</span></span> | `**text**` |
| <span data-ttu-id="5121f-230">Kursiv</span><span class="sxs-lookup"><span data-stu-id="5121f-230">Italic</span></span> | <span data-ttu-id="5121f-231">*text*</span><span class="sxs-lookup"><span data-stu-id="5121f-231">*text*</span></span> | `*text*` |
| <span data-ttu-id="5121f-232">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="5121f-232">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="5121f-233">**Text**</span><span class="sxs-lookup"><span data-stu-id="5121f-233">**Text**</span></span> | `### Text`|
| <span data-ttu-id="5121f-234">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="5121f-234">Strikethrough</span></span> | <span data-ttu-id="5121f-235">~~text~~</span><span class="sxs-lookup"><span data-stu-id="5121f-235">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="5121f-236">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-236">Unordered list</span></span> | <ul><li><span data-ttu-id="5121f-237">text</span><span class="sxs-lookup"><span data-stu-id="5121f-237">text</span></span></li><li><span data-ttu-id="5121f-238">text</span><span class="sxs-lookup"><span data-stu-id="5121f-238">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="5121f-239">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-239">Ordered list</span></span> | <ol><li><span data-ttu-id="5121f-240">text</span><span class="sxs-lookup"><span data-stu-id="5121f-240">text</span></span></li><li><span data-ttu-id="5121f-241">text</span><span class="sxs-lookup"><span data-stu-id="5121f-241">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="5121f-242">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="5121f-242">Preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="5121f-243">Blockquote</span><span class="sxs-lookup"><span data-stu-id="5121f-243">Blockquote</span></span> | <span data-ttu-id="5121f-244">>Blockquote-Text</span><span class="sxs-lookup"><span data-stu-id="5121f-244">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="5121f-245">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="5121f-245">Hyperlink</span></span> | [<span data-ttu-id="5121f-246">Bing</span><span class="sxs-lookup"><span data-stu-id="5121f-246">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="5121f-247">Bildlink</span><span class="sxs-lookup"><span data-stu-id="5121f-247">Image link</span></span> |![Ente auf einem Brocken](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="5121f-249">In Konnektorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .</span><span class="sxs-lookup"><span data-stu-id="5121f-249">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards"></a><span data-ttu-id="5121f-250">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-250">Mobile and desktop differences for connector cards</span></span>

<span data-ttu-id="5121f-251">Auf dem Desktop wird die Markdown-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-251">On the desktop, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="5121f-253">Unter iOS wird die Markdownformatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-253">On iOS, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="5121f-255">Bei Connectorkarten, die Markdown für iOS verwenden, gibt es folgende Probleme:</span><span class="sxs-lookup"><span data-stu-id="5121f-255">Connector cards using Markdown for iOS include the following issues:</span></span>

* <span data-ttu-id="5121f-256">Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.</span><span class="sxs-lookup"><span data-stu-id="5121f-256">The iOS client for Teams does not render Markdown or HTML inline images in connector cards.</span></span>
* <span data-ttu-id="5121f-257">Blockquotes werden als eingezogen, aber ohne grauen Hintergrund gerendert.</span><span class="sxs-lookup"><span data-stu-id="5121f-257">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="5121f-258">Unter Android wird die Markdown-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-258">On Android, Markdown formatting for connector cards appears as shown in the following image:</span></span>

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="format-example-for-markdown-connector-cards"></a><span data-ttu-id="5121f-260">Formatbeispiel für Markdown-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-260">Format example for Markdown connector cards</span></span>

<span data-ttu-id="5121f-261">Der folgende Code zeigt ein Beispiel für die Formatierung von Markdown-Connectorkarten:</span><span class="sxs-lookup"><span data-stu-id="5121f-261">The following code shows an example of formatting for Markdown connector cards:</span></span>

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

## <a name="format-cards-with-html"></a><span data-ttu-id="5121f-262">Formatieren von Karten mit HTML</span><span class="sxs-lookup"><span data-stu-id="5121f-262">Format cards with HTML</span></span>

<span data-ttu-id="5121f-263">Die folgenden Kartentypen unterstützen HTML-Formatierung in Teams:</span><span class="sxs-lookup"><span data-stu-id="5121f-263">The following card types support HTML formatting in Teams:</span></span>

* <span data-ttu-id="5121f-264">O365-Connectorkarten: Eingeschränkte Markdown- und HTML-Formatierung wird in Office 365 Connector-Karten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-264">O365 Connector cards: Limited Markdown and HTML formatting is supported in Office 365 Connector cards.</span></span>
* <span data-ttu-id="5121f-265">Favoriten- und Miniaturansichtskarten: HTML-Tags werden für einfache Karten unterstützt, z. B. die Favoriten- und Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="5121f-265">Hero and thumbnail cards: HTML tags are supported for simple cards, such as the hero and thumbnail cards.</span></span>

<span data-ttu-id="5121f-266">Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für O365-Connectorkarten und einfache Karten.</span><span class="sxs-lookup"><span data-stu-id="5121f-266">Formatting is different between the desktop and the mobile versions of Teams for O365 Connector cards and simple cards.</span></span> <span data-ttu-id="5121f-267">In diesem Abschnitt können Sie das HTML-Formatbeispiel für Konnektorkarten und einfache Karten durchgehen.</span><span class="sxs-lookup"><span data-stu-id="5121f-267">In this section, you can go through the HTML format example for connector cards and simple cards.</span></span>

# <a name="html-format-for-o365-connector-cards"></a>[<span data-ttu-id="5121f-268">HTML-Format für O365-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-268">HTML format for O365 Connector cards</span></span>](#tab/connector-html)

<span data-ttu-id="5121f-269">Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.</span><span class="sxs-lookup"><span data-stu-id="5121f-269">Connector cards support limited Markdown and HTML formatting.</span></span>

| <span data-ttu-id="5121f-270">Format</span><span class="sxs-lookup"><span data-stu-id="5121f-270">Style</span></span> | <span data-ttu-id="5121f-271">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5121f-271">Example</span></span> | <span data-ttu-id="5121f-272">HTML</span><span class="sxs-lookup"><span data-stu-id="5121f-272">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5121f-273">Fett</span><span class="sxs-lookup"><span data-stu-id="5121f-273">Bold</span></span> | <span data-ttu-id="5121f-274">**text**</span><span class="sxs-lookup"><span data-stu-id="5121f-274">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="5121f-275">Kursiv</span><span class="sxs-lookup"><span data-stu-id="5121f-275">Italic</span></span> | <span data-ttu-id="5121f-276">*text*</span><span class="sxs-lookup"><span data-stu-id="5121f-276">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="5121f-277">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="5121f-277">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="5121f-278">**Text**</span><span class="sxs-lookup"><span data-stu-id="5121f-278">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="5121f-279">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="5121f-279">Strikethrough</span></span> | <span data-ttu-id="5121f-280">~~text~~</span><span class="sxs-lookup"><span data-stu-id="5121f-280">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="5121f-281">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-281">Unordered list</span></span> | <ul><li><span data-ttu-id="5121f-282">text</span><span class="sxs-lookup"><span data-stu-id="5121f-282">text</span></span></li><li><span data-ttu-id="5121f-283">text</span><span class="sxs-lookup"><span data-stu-id="5121f-283">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="5121f-284">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-284">Ordered list</span></span> | <ol><li><span data-ttu-id="5121f-285">text</span><span class="sxs-lookup"><span data-stu-id="5121f-285">text</span></span></li><li><span data-ttu-id="5121f-286">text</span><span class="sxs-lookup"><span data-stu-id="5121f-286">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="5121f-287">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="5121f-287">Preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="5121f-288">Blockquote</span><span class="sxs-lookup"><span data-stu-id="5121f-288">Blockquote</span></span> | <blockquote><span data-ttu-id="5121f-289">text</span><span class="sxs-lookup"><span data-stu-id="5121f-289">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="5121f-290">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="5121f-290">Hyperlink</span></span> | [<span data-ttu-id="5121f-291">Bing</span><span class="sxs-lookup"><span data-stu-id="5121f-291">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="5121f-292">Bildlink</span><span class="sxs-lookup"><span data-stu-id="5121f-292">Image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="5121f-293">In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.</span><span class="sxs-lookup"><span data-stu-id="5121f-293">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards"></a><span data-ttu-id="5121f-294">Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-294">Mobile and desktop differences for connector cards</span></span>

<span data-ttu-id="5121f-295">Auf dem Desktop wird die HTML-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-295">On the desktop, HTML formatting for connector cards appears as shown in the following image:</span></span>

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="5121f-297">Unter iOS wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-297">On iOS, HTML formatting appears as shown in the following image:</span></span>

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="5121f-299">Konnektorkarten, die HTML für iOS verwenden, umfassen die folgenden Probleme:</span><span class="sxs-lookup"><span data-stu-id="5121f-299">Connector cards using HTML for iOS include the following issues:</span></span>

* <span data-ttu-id="5121f-300">Inlinebilder werden unter iOS nicht mit Markdown oder HTML in Connectorkarten gerendert.</span><span class="sxs-lookup"><span data-stu-id="5121f-300">Inline images are not rendered on iOS using either Markdown or HTML in connector cards.</span></span>
* <span data-ttu-id="5121f-301">Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="5121f-301">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="5121f-302">Unter Android wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-302">On Android, HTML formatting appears as shown in the following image:</span></span>

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="format-sample-for-html-connector-cards"></a><span data-ttu-id="5121f-304">Formatbeispiel für HTML-Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="5121f-304">Format sample for HTML connector cards</span></span>

<span data-ttu-id="5121f-305">Der folgende Code zeigt ein Beispiel für die Formatierung für HTML-Connectorkarten:</span><span class="sxs-lookup"><span data-stu-id="5121f-305">The following code shows an example of formatting for HTML connector cards:</span></span>

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

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[<span data-ttu-id="5121f-306">HTML-Format für Favoriten- und Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="5121f-306">HTML format for hero and thumbnail cards</span></span>](#tab/simple-html)

<span data-ttu-id="5121f-307">HTML-Tags werden für einfache Karten unterstützt, z. B. die Favoriten- und Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="5121f-307">HTML tags are supported for simple cards, such as the hero and thumbnail cards.</span></span> <span data-ttu-id="5121f-308">Markdown wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5121f-308">Markdown is not supported.</span></span>

| <span data-ttu-id="5121f-309">Format</span><span class="sxs-lookup"><span data-stu-id="5121f-309">Style</span></span> | <span data-ttu-id="5121f-310">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5121f-310">Example</span></span> | <span data-ttu-id="5121f-311">HTML</span><span class="sxs-lookup"><span data-stu-id="5121f-311">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="5121f-312">Fett</span><span class="sxs-lookup"><span data-stu-id="5121f-312">Bold</span></span> | <span data-ttu-id="5121f-313">**text**</span><span class="sxs-lookup"><span data-stu-id="5121f-313">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="5121f-314">Kursiv</span><span class="sxs-lookup"><span data-stu-id="5121f-314">Italic</span></span> | <span data-ttu-id="5121f-315">*text*</span><span class="sxs-lookup"><span data-stu-id="5121f-315">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="5121f-316">Kopfzeile (Ebenen 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="5121f-316">Header (levels 1&ndash;3)</span></span> | <span data-ttu-id="5121f-317">**Text**</span><span class="sxs-lookup"><span data-stu-id="5121f-317">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="5121f-318">Durchgestrichen</span><span class="sxs-lookup"><span data-stu-id="5121f-318">Strikethrough</span></span> | <span data-ttu-id="5121f-319">~~text~~</span><span class="sxs-lookup"><span data-stu-id="5121f-319">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="5121f-320">Unsortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-320">Unordered list</span></span> | <ul><li><span data-ttu-id="5121f-321">text</span><span class="sxs-lookup"><span data-stu-id="5121f-321">text</span></span></li><li><span data-ttu-id="5121f-322">text</span><span class="sxs-lookup"><span data-stu-id="5121f-322">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="5121f-323">Sortierte Liste</span><span class="sxs-lookup"><span data-stu-id="5121f-323">Ordered list</span></span> | <ol><li><span data-ttu-id="5121f-324">text</span><span class="sxs-lookup"><span data-stu-id="5121f-324">text</span></span></li><li><span data-ttu-id="5121f-325">text</span><span class="sxs-lookup"><span data-stu-id="5121f-325">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="5121f-326">Vorformatierter Text</span><span class="sxs-lookup"><span data-stu-id="5121f-326">Preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="5121f-327">Blockquote</span><span class="sxs-lookup"><span data-stu-id="5121f-327">Blockquote</span></span> | <blockquote><span data-ttu-id="5121f-328">text</span><span class="sxs-lookup"><span data-stu-id="5121f-328">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="5121f-329">Hyperlink</span><span class="sxs-lookup"><span data-stu-id="5121f-329">Hyperlink</span></span> | [<span data-ttu-id="5121f-330">Bing</span><span class="sxs-lookup"><span data-stu-id="5121f-330">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="5121f-331">Bildlink</span><span class="sxs-lookup"><span data-stu-id="5121f-331">Image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="5121f-332">Unterschiede zwischen Mobilgeräten und Desktops bei einfachen Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-332">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="5121f-333">Da es Auflösungsunterschiede zwischen dem Desktop und der mobilen Plattform gibt, unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.</span><span class="sxs-lookup"><span data-stu-id="5121f-333">As there are resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="5121f-334">Auf dem Desktop wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-334">On the desktop, HTML formatting appears as shown in the following image:</span></span>

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="5121f-336">Unter iOS wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-336">On iOS, HTML formatting appears as shown in the following image:</span></span>

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="5121f-338">Zeichenformatierungen wie Fett und Kursiv werden unter iOS nicht gerendert.</span><span class="sxs-lookup"><span data-stu-id="5121f-338">Character formatting, such as bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="5121f-339">Unter Android wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="5121f-339">On Android, HTML formatting appears as shown in the following image:</span></span>

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="5121f-341">Zeichenformatierung, z. B. fett und kursiv, wird unter Android korrekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5121f-341">Character formatting, such as bold and italic display correctly on Android.</span></span>

### <a name="format-example-for-simple-cards"></a><span data-ttu-id="5121f-342">Formatbeispiel für einfache Karten</span><span class="sxs-lookup"><span data-stu-id="5121f-342">Format example for simple cards</span></span>

<span data-ttu-id="5121f-343">Die Bilder im vorherigen Abschnitt wurden mit Teams **App Studio** erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="5121f-343">The images in the previous section were created using Teams **App Studio**, where the text property of a hero card is set to the following string:</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

<span data-ttu-id="5121f-344">Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.</span><span class="sxs-lookup"><span data-stu-id="5121f-344">You can test formatting in your own cards by modifying this code.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="5121f-345">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5121f-345">See also</span></span>

* [<span data-ttu-id="5121f-346">Kartenaktionen</span><span class="sxs-lookup"><span data-stu-id="5121f-346">Card actions</span></span>](./cards-actions.md)
* [<span data-ttu-id="5121f-347">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="5121f-347">Task modules</span></span>](~/task-modules-and-cards/cards/cards-format.md)
