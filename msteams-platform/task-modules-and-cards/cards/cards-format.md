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
# <a name="format-cards-in-teams"></a>Formatieren von Karten in Microsoft Teams

Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie entweder "Abschlag" oder "HTML" verwenden.

Karten unterstützen die Formatierung nur in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle. Die Formatierung kann anhand einer Teilmenge der XML-Formatierung (HTML) oder eines Abschlags je nach Kartentyp angegeben werden. Für die aktuelle und zukünftige Entwicklung werden Adaptive Karten mit Abschlag Formatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendering der Karte kann sich geringfügig zwischen dem Desktop und den Clients für Mobile Teams sowie Microsoft Teams im Desktop Browser unterscheiden.

Sie können ein Inlinebild mit einer beliebigen Teams-Karte einfügen. Bilder werden als `.png` , `.jpg` oder `.gif` Dateien formatiert und dürfen nicht mehr als 1024 × 1024 px oder 1 MB betragen. Animierte GIF-Zeichen werden nicht offiziell unterstützt. *Siehe* [Karten Referenz](./cards-reference.md#inline-card-images)

## <a name="formatting-cards-with-markdown"></a>Formatieren von Karten mit Abschlag

Es gibt zwei Kartentypen, die das Abschlag in Microsoft Teams unterstützen:

> [!div class="checklist"]
> * **Adaptive Karten**: das Abschlag wird sowohl im Feld Adaptive Karten `Textblock` als auch unterstützt `Fact.Title` `Fact.Value` . HTML wird in adaptiven Karten nicht unterstützt.
> * **O365-connectorkarten**: Abschlag und limitierter HTML-Code werden in Office 365-connectorkarten in den Textfeldern unterstützt.

# <a name="markdown-formatting-adaptive-cards"></a>[**Abschlag Formatierung: Adaptive Karten**](#tab/adaptive-md)

 Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **Bold** | ```**Bold**``` |
| italic | _Italic_ | ```_Italic_``` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hyperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Die folgenden Abschlag Tags werden nicht unterstützt:

* Header
* Tabellen
* Bilder
* Vorformatierter Text
* Blockquotes

> [!IMPORTANT]
> Adaptive Karten unterstützen keine HTML-Formatierung.

### <a name="newlines-for-adaptive-cards"></a>Neugliederungen für Adaptive Karten

In Listen können Sie die `\r` oder `\n` Escape-Sequenzen für "reinlines" verwenden. `\n\n`Die Verwendung in einer Liste bewirkt, dass das nächste Element in der Liste eingerückt wird. Wenn Sie an einer anderen Stelle im TextBlock eine Umrisse benötigen, verwenden Sie `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für Adaptive Karten

Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Microsoft Teams.

Auf dem Desktop wird die Formatierung für das Abgleichen von adaptiven Karten in beiden Webbrowsern und in der Microsoft Teams-Clientanwendung wie folgt angezeigt:

![Formatieren von adaptiven Karten Abschlägen im Desktop Client](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

Auf IOS wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:

![Formatierung von adaptiven Karten Abschriften in ios](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

Auf Android wird die Formatierung für Adaptive Karten Abschriften wie folgt angezeigt:

![Formatierung von adaptiven Karten Abschriften in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Weitere Informationen zu adaptiven Karten

[Text Features in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums-und Lokalisierungsfeatures werden in Microsoft Teams nicht unterstützt.

### <a name="formatting-sample-for-adaptive-cards"></a>Formatierungs Beispiel für Adaptive Karten

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Erwähnung der Unterstützung in Adaptive Cards v 1.2

Kartenbasierte Erwähnungen werden in den Netz-, Desktop-und mobilen Clients unterstützt. Sie können @ Mentions in einem adaptiven Kartentext für Bots und Messaging-Erweiterungs Antworten hinzufügen.  Um @ Mentions in Cards hinzuzufügen, befolgten Sie die gleiche Benachrichtigungslogik und die gleiche Darstellung wie die nachrichtenbasierte [Erwähnungen in Kanal-und Gruppenchat Unterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).

Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet](https://adaptivecards.io/explorer/FactSet.html) -Elementen enthalten.

> [!NOTE]
>[Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in Adaptive Cards v 1.2 auf der Teams-Plattform nicht unterstützt.

### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Um eine Erwähnung in eine Adaptive Karte aufzunehmen, muss Ihre APP die folgenden Elemente enthalten:

* `<at>username</at>`in den unterstützten Adaptive Card-Elementen
* Das `mention` Objekt innerhalb einer `msteams` Eigenschaft im Karteninhalt, das die Teams-Benutzer-ID des erwähnten Benutzers enthält

### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel Adaptive Karte mit Erwähnung

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

# <a name="markdown-formatting-o365-connector-cards"></a>[**Abschlag Formatierung: O365-Verbindungskarten**](#tab/connector-md)

Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung. Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text`|
| durchgestrichen | ~~text~~ | `~~text~~` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Vorformatierter Text | `text` | ``preformatted text`` |
| blockquote | >blockquote-Text | `>blockquote text` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bild Link |![Duck on a Rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In connectorkarten werden für die neureihen für `\n\n` , jedoch nicht für `\n` oder gerendert `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Unterschiede bei Mobiltelefonen und Desktops für connectorkarten mit Abschlag

Auf dem Desktop sieht die Abschlag Formatierung für connectorkarten wie folgt aus:

![Abschlag Formatierung für connectorkarten im Desktop Client](../../assets/images/cards/connector-desktop-markdown-combined.png)

Auf IOS sieht die Abschläge für Verbindungskarten wie folgt aus:

![Abschlag Formatierung für connectorkarten im IOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Probleme:

* Der IOS-Client für Microsoft Teams rendert keine Abschlag-oder HTML-Inline Bilder in Steckkarten.
* Block Zitate werden als Einzüge, jedoch ohne grauen Hintergrund gerendert.

Auf Android sieht die Abschläge für Verbindungskarten wie folgt aus:

![Abschlag Formatierung für connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Formatierungs Beispiel für Abschlag-konnektorkarten

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

## <a name="formatting-cards-with-html"></a>Formatieren von Karten mit HTML

# <a name="html-formatting-o365-connector-cards"></a>[**HTML-Formatierung: O365-Verbindungskarten**](#tab/connector-html)

Connectorkarten unterstützen beschränkte Abschlag-und HTML-Formatierung. Das Abschlag wird im nächsten Abschnitt beschrieben.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bild Link | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In connectorkarten werden die Neubuchungen in HTML mithilfe des- `<p>` Tags gerendert.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Unterschiede zwischen Mobiltelefonen und Desktops für connectorkarten mithilfe von HTML

Auf dem Desktop sieht die HTML-Formatierung für Verbindungskarten wie folgt aus:

![HTML-Formatierung für Verbindungskarten im Desktop Client](../../assets/images/cards/Connector-desktop-html-combined.png)

Auf IOS sieht HTML-Formatierung wie folgt aus:

![HTML-Formatierung für Verbindungskarten im IOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

Probleme:

* Inline Bilder werden nicht in ios unter Verwendung von "Abschlag" oder "HTML in"-Steckkarten gerendert.
* Vorformatierter Text wird gerendert, weist jedoch keinen grauen Hintergrund auf.

Auf Android sieht HTML-Formatierung wie folgt aus:

![HTML-Formatierung für Verbindungskarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Formatierungs Beispiel für HTML-Verbindungskarten

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**HTML-Formatierung: Hero-und Miniatur Ansichtskarten**](#tab/simple-html)

HTML-Tags werden für einfache Karten wie die Hero-und die Thumbnail-Karte unterstützt. Abschläge werden nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bild Link |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für einfache Karten

Aufgrund der Unterschiede zwischen Desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Microsoft Teams.

Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im Desktop Client](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

Auf IOS wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im IOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Probleme:

* Zeichenformatierungen wie Fett und kursiv werden auf IOS nicht gerendert.

Auf Android wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

Zeichenformatierungen wie Fett und kursiv werden auf Android korrekt angezeigt.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Formatierungs Beispiel für HTML-Formatierung in einfachen Karten

Diese Screenshots wurden mit Microsoft Teams AppStudio erstellt, wobei die Text-Eigenschaft einer Hero Card auf die folgende Zeichenfolge festgelegt wurde. Sie können die Formatierung in ihren eigenen Karten testen, indem Sie diesen Code ändern.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
