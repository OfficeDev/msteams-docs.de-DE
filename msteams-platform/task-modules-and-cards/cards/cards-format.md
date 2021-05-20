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
# <a name="format-cards-in-teams"></a>Formatkarten in Teams

Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierungen hinzufügen, indem Sie Markdown oder HTML verwenden.

Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften. Die Formatierung kann je nach Kartentyp mithilfe einer Teilmenge der XML-Formatierung (HTML) oder Markdown angegeben werden. Für die aktuelle und zukünftige Entwicklung werden Adaptive Karten mit Markdown-Formatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen den verschiedenen Kartentypen, und das Rendern der Karte kann sich geringfügig zwischen dem Desktop und dem mobilen Teams-Clients sowie Teams im Desktopbrowser unterscheiden.

Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen. Bilder eine als , oder Dateien formatiert werden  `.png` `.jpg` und darf `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten. Animiertes GIF wird offiziell nicht unterstützt. Weitere Informationen finden Sie unter [Kartenreferenz](./cards-reference.md#inline-card-images).

## <a name="formatting-cards-with-markdown"></a>Formatieren von Karten mit Markdown

Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:

> [!div class="checklist"]
> * **Adaptive Karten**: Markdown wird im Feld Adaptive Karte `Textblock` sowie und `Fact.Title` `Fact.Value` unterstützt. HTML wird in Adaptive-Karten nicht unterstützt.
> * **O365 Connector Cards**: Markdown und eingeschränkter HTML-Code werden in Office 365 Connector-Karten in den Textfeldern unterstützt.

# <a name="markdown-formatting-adaptive-cards"></a>[**Markdown-Formatierung: Adaptive Karten**](#tab/adaptive-md)

 Die unterstützten Stile für `Textblock` `Fact.Title` und `Fact.Value` sind:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **Bold** | ```**Bold**``` |
| italic | _Italic_ | ```_Italic_``` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hyperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Die folgenden Markdown-Tags werden nicht unterstützt:

* Überschriften
* Tabellen
* Bilder
* Vorformatierter Text
* Blockzitaten

> [!IMPORTANT]
> Adaptive Karten unterstützen keine HTML-Formatierung.

### <a name="newlines-for-adaptive-cards"></a>Newlines für adaptive Karten

In Listen können Sie die `\r` oder `\n` Escape-Sequenzen für Zeilenumleinen verwenden. Wenn Sie `\n\n` in einer Liste verwenden, wird das nächste Element in der Liste eingerückt. Wenn Sie an anderer Stelle im Textblock Zeilenumleitungen benötigen, verwenden Sie `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Mobilfunk- und Desktop-Unterschiede bei Adaptive-Karten

Die Formatierung unterscheidet sich geringfügig zwischen dem Desktop und den mobilen Versionen von Teams.

Auf dem Desktop wird die Adaptive Card Markdown-Formatierung sowohl in Webbrowsern als auch in der Teams-Clientanwendung wie folgt angezeigt:

![Adaptive Kartenmarkierungsformatierung im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

Unter iOS wird die adaptive Kartenmarkierungsformatierung wie folgt angezeigt:

![Adaptive Kartenmarkierungsformatierung in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

Unter Android wird die Adaptive Card Markdown-Formatierung wie folgt angezeigt:

![Adaptive Kartenmarkdown-Formatierung in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Weitere Informationen zu Adaptive Cards

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Erwähnen Sie die Unterstützung in Adaptive Cards v1.2

Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt. Sie können in einem adaptiven Kartenkörper für Bots und Messaging-Erweiterungsantworten . Um in Karten die Erwähnungen von - hinzuzufügen, folgen Sie der gleichen Benachrichtigungslogik und dem gleichen Rendering wie die von nachrichtenbasierten [Erwähnungen in Kanal- und Gruppenchatunterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).

Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.

> [!NOTE]
> * [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in Adaptive Cards v1.2 auf der Teams Plattform nicht unterstützt.
> * Channel & Team-Erwähnungen werden in Bot-Nachrichten nicht unterstützt.

#### <a name="constructing-mentions"></a>Konstruktionserwähnungen

Um eine Erwähnung in eine Adaptive Card aufzunehmen, muss Ihre App die folgenden Elemente enthalten:

* `<at>username</at>` in den unterstützten Adaptive-Kartenelementen.
* Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt, das die Teams Benutzer-ID des genannten Benutzers enthält.
* Der `userId` ist einzigartig für Ihre Bot-ID und einen bestimmten Benutzer. Es kann verwendet werden, um einen bestimmten Benutzer zu @mention. Der `userId` kann mit einer der in get the user [ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)genannten Optionen abgerufen werden.

#### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel Adaptive Karte mit Erwähnung

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

### <a name="information-masking-in-adaptive-cards"></a>Informationsmaskierung in adaptiven Karten
Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort- oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements Adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karte. 

> [!NOTE]
> Die Funktion unterstützt nur die Client-seitige Informationsmaskierung, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md)angegeben wurde. 

> [!NOTE]
> Die Eigenschaft zum Maskieren von Informationen ist derzeit nur in der Entwicklervorschau verfügbar.

Um Informationen in adaptiven Karten zu maskieren, fügen Sie die `isMasked` Eigenschaft **dem Typ** `Input.Text` hinzu, und legen Sie den Wert auf *true* fest.

#### <a name="sample-adaptive-card-with-masking-property"></a>Beispiel Adaptive Karte mit Maskierungseigenschaft

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

Das folgende Bild ist ein Beispiel für das Maskieren von Informationen in adaptiven Karten:

![Maskierung des Informationsbilds](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Adaptive Karte mit voller Breite
Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Bereich zu nutzen. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

#### <a name="constructing-full-width-cards"></a>Erstellen von Karten mit voller Breite
Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf festgelegt `Full` werden.
Darüber hinaus muss Ihre App die folgenden Elemente enthalten:

#### <a name="sample-adaptive-card-with-full-width"></a>Muster-Adaptive-Karte mit voller Breite

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

Eine adaptive Karte mit voller Breite wird wie folgt angezeigt: ![ Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)

Wenn Sie die Eigenschaft nicht auf Voll festgelegt `width` haben, lautet die Standardansicht der Adaptive Card wie folgt: Adaptive Kartenansicht mit kleiner ![ Breite](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a>Typeahead-Unterstützung

Innerhalb des [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Schemaelements kann das Filtern und Auswählen von Benutzern durch eine beträchtliche Anzahl von Auswahlmöglichkeiten die Aufgabenvervollständigung erheblich verlangsamen. Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingeschränkt oder gefiltert wird, während ein Benutzer die Eingabe eingibt. 

#### <a name="enable-typeahead-in-adaptive-cards"></a>Aktivieren von Typeahead in adaptiven Karten

So aktivieren Sie typeahead innerhalb des `Input.Choiceset` Satzes `style` auf und stellen `filtered` sie `isMultiSelect` sicher, dass auf festgelegt `false` ist. 

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Beispiel für adaptive Karte mit Typeahead-Unterstützung

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

### <a name="stage-view-for-images-in-adaptive-cards"></a>Bühnenansicht für Bilder in Adaptive Cards

> [!NOTE]
> Diese Funktion ist derzeit nur in der Entwicklervorschau verfügbar.
 
In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit hinzuzufügen, Bilder in der `msteams` Bühnenansicht selektiv anzuzeigen. Wenn Benutzer den Mauszeiger über die Bilder bewegen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

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

Wenn Benutzer den Mauszeiger über das Bild bewegen, wird oben rechts im Bild ein Erweiterungssymbol angezeigt: ![ Adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

Das Bild wird in der Bühnenansicht angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: ![ Bild zur Bühnenansicht erweitert](../../assets/images/cards/adaptivecard-expand-image.png)

In der Bühnenansicht können Benutzer das Bild vergrößern und verkleinern. Sie können auswählen, welche Bilder in Ihrer Adaptive-Karte diese Funktion benötigen.

> [!NOTE]
> Die Zoom-In- und Verkleinerungsfunktion gilt nur für die Bildelemente (Bildtyp) auf einer adaptiven Karte.

> [!NOTE]
> Für Teams mobilen Apps sind die Bühnenansichtsfunktionen für Bilder in Adaptive Cards standardmäßig verfügbar, und Benutzer können adaptive Kartenbilder in der Bühnenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.

# <a name="markdown-formatting-o365-connector-cards"></a>[**Markdown-Formatierung: O365 Connector-Karten**](#tab/connector-md)

Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierungen. Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| Header (Ebenen 1 &ndash; 3) | **Text** | `### Text`|
| Durchgestrichen | ~~text~~ | `~~text~~` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| vorformatierter Text | `text` | ``preformatted text`` |
| blockquote | >Blockquote-Text | `>blockquote text` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bildlink |![Ente auf einem Felsen](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In Verbindungskarten werden Zeilenlinien für gerendert, `\n\n` jedoch nicht für oder `\n` `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Mobile und Desktop-Unterschiede für Connectorkarten mit Markdown

Auf dem Desktop sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

Unter iOS sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Probleme:

* Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inline-Images in Connector Cards.
* Blockquotes werden als eingerückt, aber ohne grauen Hintergrund gerendert.

Unter Android sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Formatieren von Beispiel für Markdown Connector Cards

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

# <a name="html-formatting-o365-connector-cards"></a>[**HTML-Formatierung: O365 Connector-Karten**](#tab/connector-html)

Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierungen. Markdown wird im nächsten Abschnitt beschrieben.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Header (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In Connectorkarten werden Zeilenlinien in HTML mit dem Tag gerendert. `<p>`

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Mobile und Desktop-Unterschiede für Connectorkarten mit HTML

Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie folgt aus:

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

Unter iOS sieht die HTML-Formatierung wie folgt aus:

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

Probleme:

* Inlinebilder werden unter iOS weder mit Markdown noch html in Connector Cards gerendert.
* Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.

Unter Android sieht die HTML-Formatierung wie folgt aus:

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Formatierungsbeispiel für HTML Connector Cards

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**HTML-Formatierung: Helden- und Miniaturkarten**](#tab/simple-html)

HTML-Tags werden für einfache Karten wie Helden- und Miniaturkarten unterstützt. Markdown wird nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Header (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Mobilfunk- und Desktop-Unterschiede für einfache Karten

Aufgrund von Auflösungsunterschieden zwischen desktop- und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.

Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

Unter iOS wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Probleme:

* Zeichenformatierungen wie fett und kursiv werden unter iOS nicht gerendert.

Unter Android wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

Zeichenformatierung wie fett und kursiv anzeiget korrekt auf Android.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Formatieren von Beispielen für HTML-Formatierung in einfachen Karten

Diese Screenshots wurden mit Teams AppStudio erstellt, wo die Texteigenschaft einer Heldenkarte auf die folgende Zeichenfolge festgelegt wurde. Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
