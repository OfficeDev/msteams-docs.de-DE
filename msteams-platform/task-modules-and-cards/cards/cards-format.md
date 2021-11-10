---
title: Textformatierung in Karten
description: Beschreibt die Formatierung von Kartentext in Microsoft Teams
keywords: Teams-Bots- Kartenformat
ms.localizationpriority: medium
ms.topic: reference
ms.date: 06/25/2021
ms.openlocfilehash: 526b20146c81ba10ef026412adc111fe33a01814
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887609"
---
# <a name="format-cards-in-microsoft-teams"></a>Formatieren von Karten in Microsoft Teams

Es folgen die beiden Möglichkeiten zum Hinzufügen von Rich-Text-Formatierungen zu Ihren Karten:
* [Markdown](#format-cards-with-markdown)
* [HTML](#format-cards-with-html)

Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften. Die Formatierung kann je nach Kartentyp mithilfe einer Teilmenge von XML- oder HTML-Formatierungen oder Markdown angegeben werden. Für die aktuelle und zukünftige Entwicklung adaptiver Karten wird die Markdown-Formatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen Kartentypen. Das Rendern der Karte kann sich geringfügig zwischen dem Desktop und den mobilen Microsoft Teams-Clients sowie Teams im Desktopbrowser unterscheiden.

Sie können ein Inlinebild mit einer beliebigen Teams Karte einfügen. Bilder können als , oder Dateien formatiert werden `.png` `.jpg` und `.gif` dürfen 1024 ×1024 px oder 1 MB nicht überschreiten. Animierte GIF-Dateien werden nicht unterstützt. Weitere Informationen finden Sie unter [Kartentypen.](./cards-reference.md#inline-card-images)

Sie können adaptive Karten und Office 365 Connectorkarten mit Markdown formatieren, die bestimmte unterstützte Formatvorlagen enthalten.

## <a name="format-cards-with-markdown"></a>Formatieren von Karten mit Markdown

Die folgenden Kartentypen unterstützen Markdown-Formatierung in Teams:

* Adaptive Karten: Markdown wird im Feld für adaptive Karten `Textblock` sowie `Fact.Title` und `Fact.Value` unterstützt. HTML wird in adaptiven Karten nicht unterstützt.
* Office 365 Connectorkarten: Markdown und beschränkter HTML-Code werden in Office 365 Connectorkarten in den Textfeldern unterstützt.

Sie können Newlines für adaptive Karten verwenden `\r` oder `\n` Escapesequenzen für Newlines in Listen verwenden. Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für adaptive Karten. Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt. Sie können die Eigenschaft zum Maskieren von Informationen verwenden, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive `Input.Text` Karten. Sie können die Breite einer adaptiven Karte mithilfe des `width` Objekts erweitern. Sie können die Typaheadunterstützung in adaptiven Karten aktivieren und die Eingabeauswahl filtern, während der Benutzer die Eingabe eingibt. Mit der Eigenschaft können Sie die Möglichkeit zum selektiven Anzeigen von `msteams` Bildern in der Phasenansicht hinzufügen.

Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für adaptive Karten und Connectorkarten. In diesem Abschnitt können Sie das Beispiel für das Markdown-Format für adaptive Karten und Connectorkarten durchgehen.

# <a name="markdown-format-for-adaptive-cards"></a>[Markdown-Format für adaptive Karten](#tab/adaptive-md)

 Die folgende Tabelle enthält die unterstützten Formatvorlagen für `Textblock` `Fact.Title` , `Fact.Value` und:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| Fett | **Bold** | ```**Bold**``` |
| Kursiv | _Italic_ | ```_Italic_``` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hyperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Die folgenden Markdown-Tags werden nicht unterstützt:

* Überschriften
* Tabellen
* Bilder
* Vorformatierter Text
* Blockzitaten

### <a name="newlines-for-adaptive-cards"></a>Newlines für adaptive Karten

Sie können die `\r` `\n` Oder Escapesequenzen für Newlines in Listen verwenden. Die Verwendung `\n\n` in Listen bewirkt, dass das nächste Element in der Liste eingezogen wird. Wenn Sie newlines an anderer Stelle im TextBlock benötigen, verwenden Sie `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für adaptive Karten

Auf dem Desktop wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung in Webbrowsern und in der Teams Clientanwendung angezeigt:

![Markdown-Formatierung für adaptive Karten im Desktopclient](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

Unter iOS wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung dargestellt angezeigt:

![Markdown-Formatierung adaptiver Karten in iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

Unter Android wird die Markdown-Formatierung für adaptive Karten wie in der folgenden Abbildung dargestellt angezeigt:

![Markdown-Formatierung für adaptive Karten in Android](../../assets/images/cards/Adaptive-markdown-Android.png)

Weitere Informationen finden Sie unter [Textfeatures in adaptiven Karten.](/adaptive-cards/create/textfeatures)

> [!NOTE]
> Die in diesem Abschnitt erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.

### <a name="adaptive-cards-format-sample"></a>Beispiel für adaptive Kartenformat

Der folgende Code zeigt ein Beispiel für die Formatierung adaptiver Karten:

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

### <a name="mention-support-within-adaptive-cards"></a>Erwähnen der Unterstützung in adaptiven Karten 

Sie können @mentions in einem Textkörper für adaptive Karten für Bots und Nachrichtenerweiterungsantworten hinzufügen. Um @mentions in Karten hinzuzufügen, folgen Sie der gleichen Benachrichtigungslogik und dem Rendern wie nachrichtenbasierte [Erwähnungen in Kanal- und Gruppenchatunterhaltungen.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)

Bots und Messaging-Erweiterungen können Erwähnungen innerhalb des Karteninhalts in [TextBlock-](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet-Elementen](https://adaptivecards.io/explorer/FactSet.html) enthalten.

> [!NOTE]
> * [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden derzeit in adaptiven Karten auf Teams Plattform nicht unterstützt.
> * Kanal- und Teamerwähnungen werden in Botnachrichten nicht unterstützt.

Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:

* `<at>username</at>` in den unterstützten adaptiven Kartenelementen.
* Das `mention` Objekt innerhalb einer Eigenschaft im `msteams` Karteninhalt enthält die Teams Benutzer-ID des erwähnten Benutzers.
* Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Es kann verwendet werden, um einen bestimmten Benutzer zu @mention. Die `userId` kann mithilfe einer der im [Abrufen der Benutzer-ID](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id)erwähnten Optionen abgerufen werden.

#### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel für eine adaptive Karte mit einer Erwähnung

Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit einer Erwähnung:

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

### <a name="aad-object-id-and-upn-in-user-mention"></a>AAD Objekt-ID und UPN in Benutzererwähnung 

Teams Plattform ermöglicht es, Benutzer zusätzlich zu den vorhandenen Erwähnungs-IDs mit ihrer AAD Objekt-ID und dem Benutzerprinzipalnamen (User Principle Name, UPN) zu erwähnen. Bots mit adaptiven Karten und Connectors mit eingehenden Webhooks unterstützen die beiden Benutzererwähnungs-IDs. 

In der folgenden Tabelle werden die neu unterstützten Benutzererwähnungs-IDs beschrieben:

|Ids  | Unterstützende Funktionen |   Beschreibung | Beispiel |
|----------|--------|---------------|---------|
| AAD-Objekt-ID | Bot, Connector |  AAD Objekt-ID des Benutzers |  49c4641c-ab91-4248-aebb-6a7de286397b |
| UPN | Bot, Connector | UPN AAD Benutzers | john.smith@microsoft.com |

#### <a name="user-mention-in-bots-with-adaptive-cards"></a>Benutzererwähnung in Bots mit adaptiven Karten 

Bots unterstützen die Benutzererwähnung mit der AAD-Objekt-ID und upn zusätzlich zu den vorhandenen IDs. Die Unterstützung für zwei neue IDs ist in Bots für Textnachrichten, den Textkörper adaptiver Karten und die Antwort auf Messaging-Erweiterungen verfügbar. Bots unterstützen die Erwähnungs-IDs in Unterhaltungen und `invoke` Szenarien. Der Benutzer erhält eine Aktivitätsfeedbenachrichtigung, wenn er mit den IDs @mentioned wird. 

> [!NOTE]
> Schemaupdates und Ui/UX-Änderungen sind für Benutzererwähnungen mit adaptiven Karten in Bot nicht erforderlich.

##### <a name="example"></a>Beispiel 

Beispiel für eine Benutzererwähnung in Bots mit adaptiven Karten wie folgt:

```json 
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.0",
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Hi <at>Adele UPN</at>, <at>Adele AAD</at>"
    }
  ],
  "msteams": {
    "entities": [
      {
        "type": "mention",
        "text": "<at>Adele UPN</at>",
        "mentioned": {
          "id": "AdeleV@contoso.onmicrosoft.com",
          "name": "Adele Vance"
        }
      },
      {
        "type": "mention",
        "text": "<at>Adele AAD</at>",
        "mentioned": {
          "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
          "name": "Adele Vance"
        }
      }
    ]
  }
}
```

Die folgende Abbildung zeigt die Benutzererwähnung mit adaptiver Karte in Bot:

![Benutzererwähnung im Bot mit adaptiver Karte](~/assets/images/authentication/user-mention-in-bot.png)

#### <a name="user-mention-in-incoming-webhook-with-adaptive-cards"></a>Benutzererwähnung im eingehenden Webhook mit adaptiven Karten 

Eingehende Webhooks unterstützen die Erwähnung von Benutzern in adaptiven Karten mit der AAD-Objekt-ID und dem UPN.

> [!NOTE]    
> * Aktivieren Sie die Benutzererwähnung im Schema für eingehende Webhooks, um AAD Objekt-ID und UPN zu unterstützen. 
> * Benutzeroberflächen-/UX-Änderungen sind für Benutzererwähnungen mit AAD Objekt-ID und UPN nicht erforderlich.      
> * Die Aktivitätsfeedbenachrichtigung für eingehenden Webhook mit Benutzererwähnung wird in der zukünftigen Version verfügbar sein.

##### <a name="example"></a>Beispiel 

Beispiel für die Benutzererwähnung im eingehenden Webhook wie folgt:

```json
{
    "type": "message",
    "attachments": [
        {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
            "type": "AdaptiveCard",
            "body": [
                {
                    "type": "TextBlock",
                    "size": "Medium",
                    "weight": "Bolder",
                    "text": "Sample Adaptive Card with User Mention"
                },
                {
                    "type": "TextBlock",
                    "text": "Hi <at>Adele UPN</at>, <at>Adele AAD</at>"
                }
            ],
            "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
            "version": "1.0",
            "msteams": {
                "entities": [
                    {
                        "type": "mention",
                        "text": "<at>Adele UPN</at>",
                        "mentioned": {
                          "id": "AdeleV@contoso.onmicrosoft.com",
                          "name": "Adele Vance"
                        }
                      },
                      {
                        "type": "mention",
                        "text": "<at>Adele AAD</at>",
                        "mentioned": {
                          "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
                          "name": "Adele Vance"
                        }
                      }
                ]
            }
        }
    }]
}
```

Die folgende Abbildung veranschaulicht die Erwähnung von Benutzern im eingehenden Webhook:

![Benutzererwähnung im eingehenden Webhook](~/assets/images/authentication/user-mention-in-incoming-webhook.png)

### <a name="information-masking-in-adaptive-cards"></a>Informationsformatierung in adaptiven Karten

Verwenden Sie die Eigenschaft zum Maskieren von Informationen, um bestimmte Informationen zu maskieren, z. B. Kennwort oder vertrauliche Informationen von Benutzern innerhalb des Eingabeelements für adaptive [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Karten.

> [!NOTE]
> Das Feature unterstützt nur die clientseitige Informationsmaske. Der maskierte Eingabetext wird als Klartext an die HTTPS-Endpunktadresse gesendet, die während der [Botkonfiguration](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint)angegeben wurde.

Um Informationen in adaptiven Karten zu maskieren, fügen Sie die `isMasked` Eigenschaft zum **Eingeben** `Input.Text` hinzu, und legen Sie ihren Wert auf **"true"** fest.

#### <a name="sample-adaptive-card-with-masking-property"></a>Beispiel für adaptive Karte mit Maskierungseigenschaft

Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Maskierungseigenschaft:

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

Sie können die `msteams` Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Platz zu nutzen. Der nächste Abschnitt enthält Informationen zur Verwendung der Eigenschaft.

#### <a name="construct-full-width-cards"></a>Erstellen von Karten mit voller Breite

Um eine adaptive Karte mit voller Breite zu erstellen, muss das `width` Objekt in der Eigenschaft im `msteams` Karteninhalt auf festgelegt `Full` werden.

#### <a name="sample-adaptive-card-with-full-width"></a>Beispiel für adaptive Karte mit voller Breite

Um eine adaptive Karte mit voller Breite zu erstellen, muss Ihre App die Elemente aus dem folgenden Codebeispiel enthalten:

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

Die folgende Abbildung zeigt eine adaptive Karte mit voller Breite:

![Adaptive Kartenansicht mit voller Breite](../../assets/images/cards/full-width-adaptive-card.png)

Die folgende Abbildung zeigt die Standardansicht der adaptiven Karte, wenn Sie die Eigenschaft nicht `width` auf **"Vollständig"** festgelegt haben:

![Ansicht für adaptive Karten mit geringer Breite](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a>Typeahead-Unterstützung

Innerhalb des Schemaelements kann das Abfragen von [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Benutzern zum Filtern und Auswählen einer großen Anzahl von Auswahlmöglichkeiten den Abschluss der Aufgabe erheblich verlangsamen. Die Typeahead-Unterstützung in adaptiven Karten kann die Eingabeauswahl vereinfachen, indem die Eingabeauswahl eingegrenzt oder gefiltert wird, während der Benutzer die Eingabe eingibt.

So aktivieren Sie Typeahead in der `Input.Choiceset` , legen Sie `style` `filtered` fest, und stellen Sie sicher, dass `isMultiSelect` sie auf festgelegt `false` ist.

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Beispiel für adaptive Karte mit Typeahead-Unterstützung

Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Typahead-Unterstützung:

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

Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke ein Erweiterungssymbol angezeigt, wie in der folgenden Abbildung dargestellt:

![Adaptive Karte mit erweiterbarem Bild](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

Das Bild wird in der Phasenansicht angezeigt, wenn der Benutzer das Erweiterungssymbol wie in der folgenden Abbildung dargestellt auswählt:

![Bild, erweitert auf Phasenansicht](../../assets/images/cards/adaptivecard-expand-image.png)

In der Phasenansicht können Benutzer das Bild vergrößern und verkleinern. Sie können die Bilder in Ihrer adaptiven Karte auswählen, die über diese Funktion verfügen müssen.

> [!NOTE]
> * Die Funktion zum Vergrößern und Verkleinern gilt nur für die Bildelemente, bei denen es sich um Bildtypen in einer adaptiven Karte handelt.
> * Für Teams mobile Apps ist standardmäßig die Phasenansichtsfunktion für Bilder in adaptiven Karten verfügbar. Benutzer können Adaptive Kartenbilder in der Phasenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand` Attribut vorhanden ist oder nicht.

# <a name="markdown-format-for-office-365-connector-cards"></a>[Markdownformat für Office 365 Connectorkarten](#tab/connector-md)

Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| Fett | **text** | `**text**` |
| Kursiv | *text* | `*text*` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text`|
| Durchgestrichen | ~~text~~ | `~~text~~` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Vorformatierter Text | `text` | ``preformatted text`` |
| Blockquote | >Blockquote-Text | `>blockquote text` |
| Hyperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bildlink |![Ente auf einem Brocken](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In Konnektorkarten werden Newlines für `\n\n` gerendert, aber nicht für `\n` oder `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für Connectorkarten

Auf dem Desktop wird die Markdown-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:

![Markdownformatierung für Connectorkarten im Desktopclient](../../assets/images/cards/connector-desktop-markdown-combined.png)

Unter iOS wird die Markdownformatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:

![Markdownformatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Bei Connectorkarten, die Markdown für iOS verwenden, gibt es folgende Probleme:

* Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connectorkarten.
* Blockquotes werden als eingezogen, aber ohne grauen Hintergrund gerendert.

Unter Android wird die Markdown-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:

![Markdownformatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="format-example-for-markdown-connector-cards"></a>Formatbeispiel für Markdown-Connectorkarten

Der folgende Code zeigt ein Beispiel für die Formatierung von Markdown-Connectorkarten:

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

## <a name="format-cards-with-html"></a>Formatieren von Karten mit HTML

Die folgenden Kartentypen unterstützen HTML-Formatierung in Teams:

* Office 365 Connectorkarten: Eingeschränkte Markdown- und HTML-Formatierung wird in Office 365 Connectorkarten unterstützt.
* Favoriten- und Miniaturansichtskarten: HTML-Tags werden für einfache Karten unterstützt, z. B. die Favoriten- und Miniaturansichtskarten.

Die Formatierung unterscheidet sich zwischen der Desktopversion und der mobilen Version von Teams für Office 365 Connectorkarten und einfache Karten. In diesem Abschnitt können Sie das HTML-Formatbeispiel für Konnektorkarten und einfache Karten durchgehen.

# <a name="html-format-for-office-365-connector-cards"></a>[HTML-Format für Office 365 Connectorkarten](#tab/connector-html)

Connectorkarten unterstützen eingeschränkte Markdown- und HTML-Formatierungen.

| Format | Beispiel | HTML |
| --- | --- | --- |
| Fett | **text** | `<strong>text</strong>` |
| Kursiv | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In Connectorkarten werden Newlines mithilfe des Tags in HTML `<p>` gerendert.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops bei Connectorkarten

Auf dem Desktop wird die HTML-Formatierung für Connectorkarten wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung für Connectorkarten im Desktopclient](../../assets/images/cards/Connector-desktop-html-combined.png)

Unter iOS wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung für Connectorkarten im iOS-Client](../../assets/images/cards/connector-iphone-html-combined-80.png)

Konnektorkarten, die HTML für iOS verwenden, umfassen die folgenden Probleme:

* Inlinebilder werden unter iOS nicht mit Markdown oder HTML in Connectorkarten gerendert.
* Vorformatierter Text wird gerendert, hat jedoch keinen grauen Hintergrund.

Unter Android wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung für Connectorkarten im Android-Client](../../assets/images/cards/connector-android-html-combined.png)

### <a name="format-sample-for-html-connector-cards"></a>Formatbeispiel für HTML-Connectorkarten

Der folgende Code zeigt ein Beispiel für die Formatierung für HTML-Connectorkarten:

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

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[HTML-Format für Favoriten- und Miniaturansichtskarten](#tab/simple-html)

HTML-Tags werden für einfache Karten unterstützt, z. B. die Favoriten- und Miniaturansichtskarten. Markdown wird nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| Fett | **text** | `<strong>text</strong>` |
| Kursiv | *text* | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops bei einfachen Karten

Da es Auflösungsunterschiede zwischen dem Desktop und der mobilen Plattform gibt, unterscheidet sich die Formatierung zwischen dem Desktop und der mobilen Version von Teams.

Auf dem Desktop wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung im Desktopclient](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

Unter iOS wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung im iOS-Client](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Zeichenformatierungen wie Fett und Kursiv werden unter iOS nicht gerendert.

Unter Android wird die HTML-Formatierung wie in der folgenden Abbildung dargestellt angezeigt:

![HTML-Formatierung im Android-Client](../../assets/images/cards/card-formatting-xml-android-60.png)

Zeichenformatierung, z. B. fett und kursiv, wird unter Android korrekt angezeigt.

### <a name="format-example-for-simple-cards"></a>Formatbeispiel für einfache Karten

Die Bilder im vorherigen Abschnitt wurden mit Teams **App Studio** erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt ist:

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

Sie können die Formatierung in Ihren eigenen Karten testen, indem Sie diesen Code ändern.

---

## <a name="see-also"></a>Siehe auch

* [Kartenaktionen](./cards-actions.md)
* [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* [Aufgabenmodule](~/task-modules-and-cards/cards/cards-format.md)
* [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)
