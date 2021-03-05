---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentexten in Microsoft Teams
keywords: Teams-Bots-Kartenformat
ms.date: 03/29/2018
ms.openlocfilehash: 1221693ab9ae002ee982ef34a05ead1feb8b1f27
ms.sourcegitcommit: 47cf0d05e15e5c23616b18ae4e815fd871bbf827
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50455396"
---
# <a name="format-cards-in-teams"></a>Formatieren von Karten in Teams

Je nach Kartentyp können Sie Ihren Karten mithilfe von Markdown oder HTML Rich-Text-Formatierungen hinzufügen.

Karten unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln. Die Formatierung kann mit einer Teilmenge der XML-Formatierung (HTML) oder Markdown je nach Kartentyp angegeben werden. Für die aktuelle und zukünftige Entwicklung wird adaptive Karten mit Markdown-Formatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser geringfügig variieren.

Sie können ein Inlinebild mit einer beliebigen Teams-Karte verwenden. Bilder, die als , oder Dateien formatiert werden und  `.png` `.jpg` dürfen `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten. Animierte GIF wird offiziell nicht unterstützt. *Siehe Kartenreferenz* [](./cards-reference.md#inline-card-images)

## <a name="formatting-cards-with-markdown"></a>Formatieren von Karten mit Markdown

Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:

> [!div class="checklist"]
> * **Adaptive Karten:** Markdown wird im Feld Adaptive Karte sowie `Textblock` und `Fact.Title` `Fact.Value` unterstützt. HTML wird in adaptiven Karten nicht unterstützt.
> * **O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.

# <a name="markdown-formatting-adaptive-cards"></a>[**Markdownformatierung: Adaptive Karten**](#tab/adaptive-md)

 Die unterstützten Formatvorlagen für `Textblock` und `Fact.Title` `Fact.Value` sind:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **Bold** | ```**Bold**``` |
| italic | _Italic_ | ```_Italic_``` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hyperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Die folgenden Markdown-Tags werden nicht unterstützt:

* Überschriften
* Tabellen
* Bilder
* Vorformatierter Text
* Blockquotes

> [!IMPORTANT]
> Adaptive Karten unterstützen keine HTML-Formatierung.

### <a name="newlines-for-adaptive-cards"></a>Newlines für adaptive Karten

In Listen können Sie die `\r` Escapesequenzen für `\n` Newlines verwenden. Wenn Sie in einer Liste verwenden, wird das nächste Element in der Liste `\n\n` eingezogen. Wenn Sie Newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Unterschiede zwischen Mobilen und Desktops für adaptive Karten

Die Formatierung ist zwischen dem Desktop und den mobilen Versionen von Teams geringfügig unterschiedlich.

Auf dem Desktop wird die Formatierung der adaptiven Karten-Markdown in webbrowsern und in der Teams-Clientanwendung wie dies angezeigt:

![Formatierung der adaptiven Karte Markdown im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

Unter iOS sieht die Formatierung der adaptiven Karten-Markdown wie dies aus:

![Formatierung der adaptiven Karte Markdown in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

Unter Android wird die Formatierung der adaptiven Karten-Markdown wie dies angezeigt:

![Adaptive Karten-Markdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Weitere Informationen zu adaptiven Karten

[Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures) Die in diesem Thema erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.

### <a name="formatting-sample-for-adaptive-cards"></a>Formatierungsbeispiel für adaptive Karten

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Erwähnen der Unterstützung in adaptiven Karten v1.2

Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt. Sie können @-Erwähnungen in einem adaptiven Kartentext für Bots und Nachrichtenerweiterungsantworten hinzufügen.  Um @-Erwähnungen in Karten hinzuzufügen, folgen Sie derselben Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte Erwähnungen in Kanal- und [Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions )

Bots und Messagingerweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.

> [!NOTE]
> * [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams-Plattform nicht unterstützt.
> * Channel & Team erwähnungen werden in Botnachrichten nicht unterstützt.

#### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Um eine Erwähnung in einer adaptiven Karte zu verwenden, muss Ihre App die folgenden Elemente enthalten:

* `<at>username</at>` in den unterstützten adaptiven Kartenelementen
* Das Objekt innerhalb einer Eigenschaft im Karteninhalt, die die `mention` `msteams` Teams-Benutzer-ID des erwähnten Benutzers enthält

#### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel für adaptive Karte mit erwähnung

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


### <a name="information-masking-in-adaptive-cards"></a>Informationsmasken in adaptiven Karten
Verwenden Sie die Informationsmaskeneigenschaft, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern.

> [!NOTE]
> Die Informationsmaskeneigenschaft ist derzeit nur in der Entwicklervorschau verfügbar.

#### <a name="mask-information"></a>Maskeninformationen
Um Informationen in adaptiven Karten zu maskieren, fügen Sie die Eigenschaft zum Eingeben `isMasked`  `Input.Text` hinzu, und legen Sie den Wert auf *true .*

#### <a name="sample-adaptive-card-with-masking-property"></a>Beispiel für adaptive Karte mit Maskierungseigenschaft

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:

![Maskieren eines Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Adaptive Karte mit voller Breite
Sie können die Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und `msteams` zusätzlichen Canvasbereich zu nutzen. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

#### <a name="constructing-full-width-cards"></a>Erstellen von Karten mit voller Breite
Um eine adaptive Karte mit voller Breite zu erstellen, muss das Objekt in der Eigenschaft im Karteninhalt `width` `msteams` auf festgelegt `Full` werden.
Darüber hinaus muss Ihre App die folgenden Elemente enthalten:

#### <a name="sample-adaptive-card-with-full-width"></a>Beispiel für adaptive Karte mit voller Breite

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

Eine adaptive Karte mit voller Breite wird wie folgt ![ angezeigt: Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)

Wenn Sie die Eigenschaft nicht auf Vollständig festgelegt haben, lautet die Standardansicht der adaptiven Karte wie folgt: Adaptive Kartenansicht mit geringer `width`  ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)



# <a name="markdown-formatting-o365-connector-cards"></a>[**Markdownformatierung: O365 Connector Cards**](#tab/connector-md)

Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung. Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text`|
| strikethrough | ~~text~~ | `~~text~~` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| vorformatierter Text | `text` | ``preformatted text`` |
| blockquote | >blockquote text | `>blockquote text` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bildlink |![Ente auf einem Felchen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In Connectorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von Markdown

Auf dem Desktop sieht die Markdownformatierung für Connectorkarten wie dies aus:

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

Unter iOS sieht die Markdownformatierung für Connectorkarten wie dies aus:

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Probleme:

* Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.
* Blockquotes werden als eingezogen gerendert, aber ohne grauen Hintergrund.

Unter Android sieht die Markdownformatierung für Connectorkarten wie dies aus:

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Formatierungsbeispiel für Markdown Connector Cards

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

## <a name="formatting-cards-with-html"></a>Formatieren von Karten mit HTML

# <a name="html-formatting-o365-connector-cards"></a>[**HTML-Formatierung: O365 Connector Cards**](#tab/connector-html)

Connectorkarten unterstützen eine eingeschränkte Markdown- und HTML-Formatierung. Markdown wird im nächsten Abschnitt beschrieben.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Unterschiede zwischen Mobilen und Desktops für Connectorkarten mithilfe von HTML

Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie dies aus:

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

Unter iOS sieht die HTML-Formatierung wie dies aus:

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

Probleme:

* Inlinebilder werden unter iOS nicht mit Markdown oder HTML in ConnectorKarten gerendert.
* Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.

Unter Android sieht die HTML-Formatierung wie dies aus:

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Formatierungsbeispiel für HTML-Connectorkarten

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**HTML-Formatierung: Hero- und Miniaturansichtskarten**](#tab/simple-html)

HTML-Tags werden für einfache Karten wie die Held- und Miniaturansichtskarte unterstützt. Markdown wird nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Unterschiede zwischen Mobilen und Desktops für einfache Karten

Aufgrund von Auflösungsunterschieden zwischen dem Desktop und der mobilen Plattform unterscheiden sich die Formatierungen zwischen dem Desktop und der mobilen Version von Teams.

Auf dem Desktop wird die HTML-Formatierung wie dies angezeigt:

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

Unter iOS wird die HTML-Formatierung wie dies angezeigt:

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Probleme:

* Zeichenformatierungen wie fett und italisch werden unter iOS nicht gerendert.

Unter Android wird die HTML-Formatierung wie dies angezeigt:

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

Zeichenformatierung wie fett und italisch wird unter Android korrekt angezeigt.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Formatierungsbeispiel für die HTML-Formatierung in einfachen Karten

Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde. Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
