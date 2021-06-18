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
# <a name="format-cards-in-teams"></a>Formatieren von Karten in Teams

Je nach Kartentyp können Sie Rich-Text-Formatierungen entweder mit Markdown oder HTML zu Ihren Karten hinzufügen.

Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften. Die Formatierung kann mithilfe einer Teilmenge der XML-Formatierung (HTML) oder markdown abhängig vom Kartentyp angegeben werden. Für aktuelle und zukünftige Entwicklungskarten wird adaptive Karten mit Markdown-Formatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen verschiedenen Kartentypen, und das Rendern der Karte kann sich geringfügig zwischen dem Desktop und den mobilen Teams-Clients sowie Teams im Desktopbrowser unterscheiden.

Sie können ein Inlinebild mit einer beliebigen Teams Karte einschließen. Bilder, die als , oder Dateien formatiert werden  `.png` `.jpg` und `.gif` 1024 ×1024 px oder 1 MB nicht überschreiten dürfen. Animierte GIF-Dateien werden offiziell nicht unterstützt. Weitere Informationen finden Sie unter [Kartenreferenz.](./cards-reference.md#inline-card-images)

## <a name="formatting-cards-with-markdown"></a>Formatieren von Karten mit Markdown

Es gibt zwei Kartentypen, die Markdown in Teams unterstützen:

> [!div class="checklist"]
> * **Adaptive Karten:** Markdown wird im Feld für adaptive Karten `Textblock` sowie und `Fact.Title` `Fact.Value` unterstützt. HTML wird in adaptiven Karten nicht unterstützt.
> * **O365-Connectorkarten:** Markdown und beschränkter HTML-Code werden in Office 365 Connectorkarten in den Textfeldern unterstützt.

# <a name="markdown-formatting-adaptive-cards"></a>[**Markdownformatierung: Adaptive Karten**](#tab/adaptive-md)

 Die unterstützten Formatvorlagen für `Textblock` `Fact.Title` und `Fact.Value` sind:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **Bold** | ```**Bold**``` |
| italic | _Italic_ | ```_Italic_``` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
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

In Listen können Sie die `\r` `\n` Oder Escapesequenzen für Newlines verwenden. Die Verwendung `\n\n` in einer Liste bewirkt, dass das nächste Element in der Liste eingezogen wird. Wenn Sie newlines an anderer Stelle im Textblock benötigen, verwenden Sie `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für adaptive Karten

Die Formatierung unterscheidet sich geringfügig zwischen der Desktopversion und der mobilen Version von Teams.

Auf dem Desktop wird die Markdown-Formatierung für adaptive Karten sowohl in Webbrowsern als auch in der Teams Clientanwendung wie folgt angezeigt:

![Markdown-Formatierung für adaptive Karten im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

Unter iOS wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:

![Markdown-Formatierung adaptiver Karten in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

Unter Android wird die Markdown-Formatierung für adaptive Karten wie folgt angezeigt:

![Markdown-Formatierung für adaptive Karten in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

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

Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt. Sie können @Erwähnungen in einem adaptiven Kartentext für Bots und Antworten auf Messaging-Erweiterungen hinzufügen. Um @Erwähnungen in Karten hinzuzufügen, befolgen Sie die gleiche Benachrichtigungslogik und dasselbe Rendering wie nachrichtenbasierte [Erwähnungen in Kanal- und Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)

Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.

> [!NOTE]
> * [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten v1.2 auf der Teams Plattform nicht unterstützt.
> * Kanal- & Teamerwähnungen werden in Botnachrichten nicht unterstützt.

#### <a name="constructing-mentions"></a>Erstellen von Erwähnungen

Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:

* `<at>username</at>` in den unterstützten adaptiven Kartenelementen.
* Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt, das die Teams Benutzer-ID des erwähnten Benutzers enthält.
* Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Es kann verwendet werden, um einen bestimmten Benutzer zu @mention. Die `userId` kann mithilfe einer der im [Abrufen der Benutzer-ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)erwähnten Optionen abgerufen werden.

#### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel für eine adaptive Karte mit einer Erwähnung

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

### <a name="information-masking-in-adaptive-cards"></a>Informationsformatierung in adaptiven Karten
Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karten. 

> [!NOTE]
> Das Feature unterstützt nur die clientseitige Informationsmaske, der maskierte Eingabetext wird als Klartext an die https-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md)angegeben wurde. 

#### <a name="sample-adaptive-card-with-masking-property"></a>Beispiel für adaptive Karte mit Maskierungseigenschaft

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

Die folgende Abbildung ist ein Beispiel für die Maskierung von Informationen in adaptiven Karten:

![Maskierungsinformationsbild](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Adaptive Karte mit voller Breite
Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Platz zu nutzen. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

#### <a name="constructing-full-width-cards"></a>Erstellen von Karten mit voller Breite
Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf . `Full`
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

Eine adaptive Karte mit voller Breite wird wie folgt angezeigt: ![ Ansicht "Adaptive Karte mit voller Breite"](../../assets/images/cards/full-width-adaptive-card.png)

Wenn Sie die Eigenschaft nicht `width` auf *"Vollständig"* festgelegt haben, wird die Standardansicht der adaptiven Karte wie folgt angezeigt: Ansicht für ![ adaptive Karten mit geringer Breite](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a>Typeahead-Unterstützung

Innerhalb des Schemaelements kann das Abfragen von [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Benutzern zum Filtern und Auswählen durch eine große Anzahl von Auswahlmöglichkeiten den Abschluss der Aufgabe erheblich verlangsamen. Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingegrenzt oder gefiltert wird, während ein Benutzer die Eingabe eintippt. 

#### <a name="enable-typeahead-in-adaptive-cards"></a>Aktivieren von Typeahead in adaptiven Karten

So aktivieren Sie Typeahead innerhalb des `Input.Choiceset` `style` Satzes, und stellen Sie `filtered` sicher, dass er auf festgelegt `isMultiSelect` `false` ist. 

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

### <a name="stage-view-for-images-in-adaptive-cards"></a>Phasenansicht für Bilder in adaptiven Karten

In einer adaptiven Karte können Sie die Eigenschaft verwenden, um die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzuzufügen. Wenn Benutzer mit dem Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für das das `allowExpand` Attribut auf festgelegt `true` ist. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

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

Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke des Bilds ein Erweiterungssymbol angezeigt: ![ adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

Das Bild wird in der Phasenansicht angezeigt, wenn der Benutzer die Schaltfläche "Erweitern" auswählt: ![ Bild in Phasenansicht erweitert](../../assets/images/cards/adaptivecard-expand-image.png)

In der Phasenansicht können Benutzer das Bild vergrößern und verkleinern. Sie können auswählen, welche Bilder in Ihrer adaptiven Karte für diese Funktion benötigt werden.

> [!NOTE]
> Die Funktion zum Vergrößern und Verkleinern gilt nur für die Bildelemente (Bildtyp) auf einer adaptiven Karte.

> [!NOTE]
> Für Teams mobile Apps sind standardmäßig Funktionen für die Phasenansicht für Bilder in adaptiven Karten verfügbar, und Benutzer können adaptive Kartenbilder in der Phasenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.

# <a name="markdown-formatting-o365-connector-cards"></a>[**Markdownformatierung: O365-Connectorkarten**](#tab/connector-md)

Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen. Die HTML-Unterstützung wird im letzten Abschnitt beschrieben.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text`|
| Durchgestrichen | ~~text~~ | `~~text~~` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Vorformatierter Text | `text` | ``preformatted text`` |
| blockquote | >Blockquote-Text | `>blockquote text` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bildlink |![Ente auf einem Brocken](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In Konnektorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit Markdown

Auf dem Desktop sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

Unter iOS sieht die Markdownformatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Probleme:

* Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.
* Blockquotes werden als eingezogen, aber ohne grauen Hintergrund gerendert.

Unter Android sieht die Markdown-Formatierung für Connectorkarten wie folgt aus:

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Formatierungsbeispiel für Markdown-Connectorkarten

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

# <a name="html-formatting-o365-connector-cards"></a>[**HTML-Formatierung: O365-Connectorkarten**](#tab/connector-html)

Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen. Markdown wird im nächsten Abschnitt beschrieben.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten mit HTML

Auf dem Desktop sieht die HTML-Formatierung für Connectorkarten wie folgt aus:

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

Unter iOS sieht die HTML-Formatierung wie folgt aus:

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

Probleme:

* Inlinebilder werden unter iOS nicht mit Markdown oder HTML in Connectorkarten gerendert.
* Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.

Unter Android sieht die HTML-Formatierung wie folgt aus:

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**HTML-Formatierung: Favoriten- und Miniaturansichtskarten**](#tab/simple-html)

HTML-Tags werden für einfache Karten wie die Hero- und Miniaturansichtskarte unterstützt. Markdown wird nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops bei einfachen Karten

Aufgrund von Auflösungsunterschieden zwischen desktop und mobiler Plattform unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.

Auf dem Desktop wird die HTML-Formatierung wie folgt angezeigt:

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

Unter iOS wird html-Formatierung wie folgt angezeigt:

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Probleme:

* Zeichenformatierungen wie Fett und Kursiv werden unter iOS nicht gerendert.

Unter Android sieht die HTML-Formatierung wie folgt aus:

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

Zeichenformatierungen wie fett und kursiv werden unter Android korrekt angezeigt.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Formatierungsbeispiel für HTML-Formatierung in einfachen Karten

Diese Screenshots wurden mit Teams AppStudio erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt wurde. Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
