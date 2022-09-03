---
title: Textformatierung in Karten
description: In diesem Modul erfahren Sie, was Kartentextformatierung in Microsoft Teams ist, und Sie formatieren Karten mit Markdown.
ms.localizationpriority: high
ms.topic: reference
ms.date: 06/25/2021
ms.openlocfilehash: e6cbccdb436b8d84f5d139b6a082765f22f373c6
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586959"
---
# <a name="format-cards-in-microsoft-teams"></a>Formatieren von Karten in Microsoft Teams

Im Folgenden werden die beiden Möglichkeiten zum Hinzufügen von Rich-Text-Formatierungen für Ihre Karten beschrieben:

* [Markdown](#format-cards-with-markdown)
* [HTML](#format-cards-with-html)

Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften. Die Formatierung kann je nach Kartentyp mithilfe einer Teilmenge von XML- oder HTML-Formatierung oder mit Markdown angegeben werden. Für die aktuelle und zukünftige Entwicklung von adaptiven Karten wird die Markdownformatierung empfohlen.

Die Formatierungsunterstützung unterscheidet sich zwischen Kartentypen. Das Rendern der Karte kann sich geringfügig zwischen dem Desktopclient und den mobilen Microsoft Teams-Clients sowie Teams im Desktopbrowser unterscheiden.

Sie können ein Inlinebild mit einer beliebigen Teams-Karte einschließen. Unterstützte Bildformate sind PNG-, JPG- oder GIF-Formate. Halten Sie die Abmessungen innerhalb von 1024 x 1024 Pixel und die Dateigröße kleiner als 1 MB. Animierte GIF-Bilder werden nicht unterstützt. Weitere Informationen finden Sie unter [Typen von Karten](./cards-reference.md#inline-card-images).

Sie können adaptive Karten und Office 365-Connector-Karten mit Markdown formatieren, die bestimmte unterstützte Formatvorlagen enthalten.

## <a name="format-cards-with-markdown"></a>Formatieren von Karten mit Markdown

Die folgenden Kartentypen unterstützen Markdownformatierung in Teams:

* Adaptive Karten: Markdown wird in der adaptiven Karte im `Textblock`-Feld sowie in `Fact.Title` und `Fact.Value` unterstützt. HTML wird in adaptiven Karten nicht unterstützt.
* Office 365-Connector-Karten: Markdown und eingeschränkter HTML-Code werden in Office 365-Connector-Karten in den Textfeldern unterstützt.

Sie können Zeilenumbrüche für adaptive Karten verwenden, indem Sie die Escape-Sequenzen `\r` oder `\n` für Zeilenumbrüche in Listen verwenden. Die Formatierung unterscheidet sich für adaptive Karten zwischen der Desktopversion und den mobilen Versionen von Teams. Kartenbasierte Erwähnungen werden in Web-, Desktop- und mobilen Clients unterstützt. Sie können die Eigenschaft für die Informationsmaskierung verwenden, um bestimmte Informationen zu maskieren, beispielsweise das Kennwort oder vertrauliche Informationen von Benutzern innerhalb des `Input.Text`-Eingabeelements der adaptiven Karte. Sie können die Breite einer adaptiven Karte mithilfe des `width`-Objekts erweitern. Sie können die Typeahead-Unterstützung innerhalb adaptiver Karten aktivieren und den Satz von Eingabeoptionen filtern, während der Benutzer Text eingibt. Sie können die `msteams`-Eigenschaft verwenden, um die Möglichkeit hinzuzufügen, Bilder selektiv in der Bühnenansicht anzuzeigen.

Die Formatierung unterscheidet sich für adaptive Karten und Connector-Karten zwischen der Desktopversion und den mobilen Versionen von Teams. In diesem Abschnitt können Sie das Beispiel für das Markdownformat für adaptive Karten und Connector-Karten durchgehen.

# <a name="markdown-format-for-adaptive-cards"></a>[Markdownformat für adaptive Karten](#tab/adaptive-md)

 Die folgende Tabelle enthält die unterstützten Formatvorlagen für `Textblock`, `Fact.Title` und `Fact.Value`:

| Format | Beispiel | Markdown |
| --- | --- | --- |
| Fett | **Bold** | ```**Bold**``` |
| Kursiv | _Italic_ | ```_Italic_``` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hyperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Die folgenden Markdowntags werden nicht unterstützt:

* Überschriften
* Tabellen
* Bilder
* Vorformatierter Text
* Blockzitate

### <a name="newlines-for-adaptive-cards"></a>Zeilenumbrüche für adaptive Karten

Sie können die Escape-Sequenzen `\r` oder `\n` für Zeilenumbrüche in Listen verwenden. Die Verwendung von `\n\n` in Listen bewirkt, dass das nächste Element in der Liste eingezogen wird. Wenn Sie Zeilenumbrüche an anderer Stelle im TextBlock benötigen, verwenden Sie `\n\n`.

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Unterschiede für adaptive Karten zwischen Mobilgeräten und Desktops

Auf dem Desktop erscheint die Markdownformatierung für adaptive Karten wie in der folgenden Abbildung dargestellt, sowohl in Webbrowsern als auch in der Teams-Clientanwendung:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-desktop-client.png" alt-text="Adaptiver Markdown-Desktopclient":::

Unter iOS erscheint die Markdownformatierung für adaptive Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-iOS-75.png" alt-text="Markdownformatierung adaptiver Karten in iOS":::

Unter Android erscheint die Markdownformatierung für adaptive Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/Adaptive-markdown-Android.png" alt-text="Markdownformatierung adaptiver Karten in Android":::

Weitere Informationen finden Sie unter [Textfeatures in adaptiven Karten](/adaptive-cards/create/textfeatures).

> [!NOTE]
> Die in diesem Abschnitt erwähnten Datums- und Lokalisierungsfeatures werden in Teams nicht unterstützt.

### <a name="adaptive-cards-format-sample"></a>Formatbeispiel für adaptive Karten

Der folgende Code zeigt ein Beispiel der Formatierung für adaptive Karten:

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

Adaptive Karten unterstützen Emoji. Der folgende Code zeigt ein Beispiel für Adaptive Karten mit einem Emoji:

``` json
{ "$schema": "http://adaptivecards.io/schemas/adaptive-card.json", "type": "AdaptiveCard", "version": "1.0", "body": [ { "type": "Container", "items": [ { "type": "TextBlock", "text": "Publish Adaptive Card with emojis 🥰 ", "weight": "bolder", "size": "medium" }, ] }, ], }
```

:::image type="content" source="../../assets/images/Cards/adaptive-card-emoji.png" alt-text="Adaptive Karte mit einem Emoji":::

### <a name="mention-support-within-adaptive-cards"></a>Unterstützung von Erwähnungen innerhalb adaptiver Karten

Sie können @erwähnen in einem Textblock einer adaptiven Karte für Bots und Nachrichtenerweiterungsantworten hinzufügen. Um @erwähnen in Karten hinzuzufügen, folgen Sie der gleichen Benachrichtigungslogik und demselben Rendering wie bei nachrichtenbasierten [Erwähnungen in Kanal- und Gruppenchatunterhaltungen](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).

Bots und Nachrichtenerweiterungen können Erwähnungen innerhalb des Karteninhalts in den Elementen [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) und [FactSet](https://adaptivecards.io/explorer/FactSet.html) enthalten.

> [!NOTE]
>
> * [Medienelemente](https://adaptivecards.io/explorer/Media.html) werden in adaptiven Karten auf der Teams-Plattform derzeit nicht unterstützt.
> * Kanal- und Teamerwähnungen werden in Botnachrichten nicht unterstützt.

Um eine Erwähnung in eine adaptive Karte aufzunehmen, muss Ihre App die folgenden Elemente enthalten:

* `<at>username</at>` in den unterstützten Elementen der adaptiven Karte.
* Das `mention`-Objekt innerhalb einer `msteams`-Eigenschaft im Karteninhalt enthält die Teams-Benutzer-ID des erwähnten Benutzers.
* Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie kann verwendet werden, um einen bestimmten Benutzer zu @erwähnen. Die `userId` kann mithilfe einer der in [Benutzer-ID abrufen](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id) erwähnten Optionen abgerufen werden.

#### <a name="sample-adaptive-card-with-a-mention"></a>Beispiel einer adaptiven Karte mit einer Erwähnung

Der folgende Code zeigt ein Beispiel einer adaptiven Karte mit einer Erwähnung:

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

### <a name="microsoft-azure-active-directory-azure-ad-object-id-and-upn-in-user-mention"></a>Microsoft Azure Active Directory(Azure AD)-Objekt-ID und UPN in Benutzererwähnung

Die Teams-Plattform ermöglicht es, Benutzer mit ihrer Azure AD-Objekt-ID und dem Benutzerprinzipalnamen (User Principle Name, UPN) zu erwähnen, zusätzlich zu den bestehenden Erwähnungs-IDs. Bots mit adaptiven Karten und Connectors mit eingehenden Webhooks unterstützen die zwei Benutzererwähnungs-IDs.

In der folgenden Tabelle werden die neu unterstützten Benutzererwähnungs-IDs beschrieben:

|IDs  | Unterstützende Funktionen | Beschreibung | Beispiel |
|----------|--------|---------------|---------|
| Azure AD-Objekt-ID | Bot, Connector |  Objekt-ID des Azure AD-Benutzers | 49c4641c-ab91-4248-aebb-6a7de286397b |
| UPN | Bot, Connector | UPN des Azure AD-Benutzers | john.smith@microsoft.com |

#### <a name="user-mention-in-bots-with-adaptive-cards"></a>Benutzererwähnung in Bots mit adaptiven Karten

Bots unterstützen die Benutzererwähnung mit der Azure AD-Objekt-ID und dem UPN, zusätzlich zu den vorhandenen IDs. Die Unterstützung für zwei neue IDs ist in Bots für Textnachrichten, adaptiven Kartentext und die Nachrichtenerweiterungsantwort verfügbar. Bots unterstützen die Erwähnungs-IDs in Unterhaltungen und `invoke`-Szenarien. Der Benutzer erhält eine Aktivitätsfeedbenachrichtigung, wenn er mit den IDs @erwähnt wird.

> [!NOTE]
> Schemaupdates und Änderungen der Benutzeroberfläche/-erfahrung sind für Benutzererwähnungen mit adaptiven Karten im Bot nicht erforderlich.

##### <a name="example"></a>Beispiel

Beispiel für die Benutzererwähnung in Bots mit adaptiven Karten wie folgt:

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.0",
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Hi <at>Adele UPN</at>, <at>Adele Azure AD</at>"
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
        "text": "<at>Adele Azure AD</at>",
        "mentioned": {
          "id": "87d349ed-44d7-43e1-9a83-5f2406dee5bd",
          "name": "Adele Vance"
        }
      }
    ]
  }
}
```

Die folgende Abbildung veranschaulicht die Benutzererwähnung mit adaptiver Karte im Bot:

:::image type="content" source="../../assets/images/authentication/user-mention-in-bot.png" alt-text="Benutzererwähnung im Bot mit adaptiver Karte":::

#### <a name="user-mention-in-incoming-webhook-with-adaptive-cards"></a>Benutzererwähnung im eingehenden Webhook mit adaptiven Karten

Eingehende Webhooks beginnen mit der Unterstützung der Benutzererwähnung in adaptiven Karten mit der Azure AD-Objekt-ID und dem UPN.

> [!NOTE]
>
> * Aktivieren Sie die Benutzererwähnung im Schema für eingehende Webhooks, um die Azure AD-Objekt-ID und den UPN zu unterstützen.
> * Änderungen der Benutzeroberfläche/-erfahrung sind für Benutzererwähnungen mittels Azure AD-Objekt-ID und UPN nicht erforderlich.

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
                    "text": "Hi <at>Adele UPN</at>, <at>Adele Azure AD</at>"
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
                        "text": "<at>Adele Azure AD</at>",
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

Die folgende Abbildung veranschaulicht die Benutzererwähnung im eingehenden Webhook:

:::image type="content" source="../../assets/images/authentication/user-mention-in-incoming-webhook.png" alt-text="Benutzererwähnung im eingehenden Webhook":::

### <a name="information-masking-in-adaptive-cards"></a>Maskieren von Information in adaptiven Karten

Verwenden Sie die Eigenschaft zur Informationsmaskierung, um bestimmte Informationen zu maskieren, z. B. das Kennwort oder vertrauliche Informationen von Benutzern innerhalb des [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html)Eingabeelements der adaptiven Karte.

> [!NOTE]
> Das Feature unterstützt nur die clientseitige Informationsmaskierung. Der maskierte Eingabetext wird als Klartext an die HTTPS-Endpunktadresse gesendet, die während der [Bot-Konfiguration](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint) angegeben wurde.

Um Informationen in adaptiven Karten zu maskieren, fügen Sie die `style`-Eigenschaft an den **Typ** `input.text` hinzu, und legen Sie den Wert auf **Kennwort** fest.

#### <a name="sample-adaptive-card-with-masking-property"></a>Beispiel für adaptive Karte mit Maskierungseigenschaft

Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Maskierungseigenschaft:

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

Die folgende Abbildung zeigt ein Beispiel für die Maskierung von Informationen in adaptiven Karten:

:::image type="content" source="../../assets/images/Cards/masking-information-view.png" alt-text="Maskieren der Informationsansicht":::

### <a name="full-width-adaptive-card"></a>Adaptive Karte in ganzer Breite

Sie können die `msteams`-Eigenschaft verwenden, um die Breite einer adaptiven Karte zu erweitern und zusätzlichen Canvas-Raum zu verwenden. Der nächste Abschnitt enthält Informationen zur Verwendung der Eigenschaft.

> [!NOTE]
> Testen Sie Die adaptive Karte mit voller Breite in schmalen Formfaktoren wie mobilen und Besprechungsseitenbereichen, um sicherzustellen, dass Inhalte nicht abgeschnitten werden.

#### <a name="construct-full-width-cards"></a>Erstellen von Karten in ganzer Breite

Um eine adaptive Karte in ganzer Breite zu erstellen, muss das `width`-Objekt der `msteams`-Eigenschaft im Karteninhalt auf `Full` festgelegt werden.

#### <a name="sample-adaptive-card-with-full-width"></a>Beispiel einer adaptiven Karte in ganzer Breite

Um eine adaptive Karte in ganzer Breite zu erstellen, muss Ihre App die Elemente aus dem folgenden Codebeispiel enthalten:

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

Die folgende Abbildung zeigt eine adaptive Karte in ganzer Breite:

:::image type="content" source="../../assets/images/Cards/full-width-adaptive-card.png" alt-text="Adaptive Kartenansicht in ganzer Breite":::

Die folgende Abbildung zeigt die Standardansicht der adaptiven Karte, wenn Sie die `width`-Eigenschaft nicht auf **Ganz** festgelegt haben:

:::image type="content" source="../../assets/images/Cards/small-width-adaptive-card.png" alt-text="Adaptive Kartenansicht mit geringer Breite":::

### <a name="typeahead-support"></a>Typeahead-Unterstützung

Wenn Benutzer innerhalb des [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html)-Schemaelements zum Filtern und Auswählen einer beträchtlichen Anzahl von Auswahlmöglichkeiten auffordert werden, kann die Aufgabenvervollständigung erheblich verlangsamt werden. Die Unterstützung von Typeahead innerhalb adaptiver Karten kann die Eingabeauswahl vereinfachen, indem der Satz von Eingabeoptionen eingegrenzt oder gefiltert wird, während der Benutzer Text eingibt.

Um Typeahead in `Input.Choiceset` zu aktivieren, legen Sie `style` auf `filtered` fest, und stellen Sie sicher, dass `isMultiSelect` auf `false` festgelegt ist.

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Beispiel für eine adaptive Karte mit Typeahead-Unterstützung

Der folgende Code zeigt ein Beispiel für eine adaptive Karte mit Typeahead-Unterstützung:

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

### <a name="stage-view-for-images-in-adaptive-cards"></a>Bühnenansicht für Bilder in adaptiven Karten

In einer adaptiven Karte können Sie die Eigenschaft `msteams` verwenden, um die Möglichkeit zum selektiven Anzeigen von Bildern in der Bühnenansicht hinzuzufügen. Wenn Benutzer mit dem Mauszeiger auf die Bilder zeigen, wird ein Erweiterungssymbol angezeigt, für welches das `allowExpand`-Attribut auf `true` festgelegt ist. Informationen zur Verwendung der Eigenschaft finden Sie im folgenden Beispiel:

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
          }
     ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

Wenn Benutzer mit dem Mauszeiger auf das Bild zeigen, wird in der oberen rechten Ecke ein Erweiterungssymbol angezeigt, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/adaptivecard-hover-expand-icon.png" alt-text="Adaptive Karte mit erweiterbarem Bild":::

Das Bild wird in der Bühnenansicht angezeigt, wenn der Benutzer das Erweiterungssymbol auswählt, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/adaptivecard-expand-image.png" alt-text="Bild in Bühnenansicht erweitert":::

In der Bühnenansicht können Benutzer das Bild vergrößern und verkleinern. Sie können die Bilder auf Ihrer adaptiven Karte auswählen, die über diese Funktion verfügen muss.

> [!NOTE]
>
> * Die Funktion zum Vergrößern und Verkleinern gilt nur für Bildelemente, die in einer adaptiven Karte den Typ „Bild“ aufweisen.
> * Für mobile Teams-Apps ist die Funktionen der Bühnenansicht für Bilder in adaptiven Karten standardmäßig verfügbar. Benutzer können adaptive Kartenbilder in der Bühnenansicht anzeigen, indem sie einfach auf das Bild tippen, unabhängig davon, ob das `allowExpand`-Attribut vorhanden ist oder nicht.

# <a name="markdown-format-for-office-365-connector-cards"></a>[Markdownformat für Office 365-Connector-Karten](#tab/connector-md)

Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierung.

| Format | Beispiel | Markdown |
| --- | --- | --- |
| Fett | **text** | `**text**` |
| Kursiv | _text_ | `*text*` |
| Header (Stufe 1&ndash;3) | **Text** | `### Text`|
| Durchgestrichen | ~~text~~ | `~~text~~` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Vorformatierter Text | `text` | ``preformatted text`` |
| Blockzitat | >Blockzitat-Text | `>blockquote text` |
| Hyperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Bildverknüpfung |![Ente auf einem Stein](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

In Connector-Karten werden Zeilenumbrüche für `\n\n` gerendert, jedoch nicht für `\n` oder `\r`.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für Connector-Karten 

Auf dem Desktop erscheint die Markdownformatierung für Connector-Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/connector-desktop-markdown-combined.png" alt-text="Markdownformatierung für Connector-Karten":::

Unter iOS erscheint die Markdownformatierung für Connector-Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/connector-iphone-html-combined-80.png" alt-text="Markdownformatierung für Connector-Karten im iOS-Client":::

Connector-Karten, die Markdown für iOS verwenden, weisen die folgenden Probleme auf:

* Der iOS-Client für Teams rendert keine Markdown- oder HTML-Inlinebilder in Connector-Karten.
* Blockzitate werden als eingezogen gerendert, aber ohne grauen Hintergrund.

Unter Android erscheint die Markdownformatierung für Connector-Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/connector-android-markdown-combined.png" alt-text="Markdownformatierung für Connector-Karten im Android-Client":::

### <a name="format-example-for-markdown-connector-cards"></a>Formatbeispiel für Markdown-Connector-Karten

Der folgende Code zeigt ein Beispiel für die Formatierung von Markdown-Connector-Karten:

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

Die folgenden Kartentypen unterstützen die HTML-Formatierung in Teams:

* Office 365-Connector-Karten: Eingeschränkte Markdown- und HTML-Formatierung wird in Office 365-Connector-Karten unterstützt.
* Hero- und Miniaturansichtskarten: HTML-Tags werden für einfache Karten unterstützt, z. B. Hero- und Miniaturansichtskarten.

Die Formatierung unterscheidet sich für Office 365 Connector-Karten und einfachen Karten zwischen Desktop- und mobilen Versionen von Teams. In diesem Abschnitt können Sie das HTML-Formatbeispiel für Connector-Karten und einfache Karten durchgehen.

# <a name="html-format-for-office-365-connector-cards"></a>[HTML-Format für Office 365-Connector-Karten](#tab/connector-html)

Connector-Karten unterstützen eingeschränkte Markdown- und HTML-Formatierung.

| Format | Beispiel | HTML |
| --- | --- | --- |
| Fett | **text** | `<strong>text</strong>` |
| Kursiv | _text_ | `<em>text</em>` |
| Header (Stufe 1&ndash;3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| Blockzitat | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildverknüpfung | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

In Connector-Karten werden Zeilenumbrüche in HTML mit dem `<p>`-Tag gerendert.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für Connector-Karten 

Auf dem Desktop erscheint die HTML-Formatierung für Connector-Karten wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/Connector-desktop-html-combined.png" alt-text="HTML-Formatierung für Connector-Karten im Desktopclient":::

Unter iOS erscheint die HTML-Formatierung wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/connector-iphone-html-combined-80.png" alt-text="HTML-Formatierung für Connector-Karten im iOS-Client":::

Connector-Karten, die HTML für iOS verwenden, weisen die folgenden Probleme auf:

* Inlinebilder in Connector-Karten werden unter iOS weder mit Markdown noch mit HTML gerendert.
* Vorformatierter Text wird gerendert, hat aber keinen grauen Hintergrund.

Unter Android erscheint die HTML-Formatierung wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/connector-android-html-combined.png" alt-text="HTML-Formatierung für Connector-Karten im Android-Client":::

### <a name="format-sample-for-html-connector-cards"></a>Formatbeispiel für HTML-Connector-Karten

Der folgende Code zeigt ein Beispiel für die Formatierung von HTML-Connector-Karten:

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

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[HTML-Format für Hero- und Miniaturansichtskarten](#tab/simple-html)

HTML-Tags werden für einfache Karten unterstützt, z. B. Hero- und Miniaturansichtskarten. Markdown wird nicht unterstützt.

| Format | Beispiel | HTML |
| --- | --- | --- |
| Fett | **text** | `<strong>text</strong>` |
| Kursiv | _text_ | `<em>text</em>` |
| Header (Stufe 1&ndash;3) | **Text** | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `<pre>text</pre>` |
| Blockzitat | <blockquote>text</blockquote> | `<blockquote>text</blockquote>` |
| Hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Bildverknüpfung |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Unterschiede zwischen Mobilgeräten und Desktops für einfache Karten

Da es Auflösungsunterschiede zwischen der Desktop- und der mobilen Plattform gibt, unterscheidet sich die Formatierung zwischen der Desktopversion und der mobilen Version von Teams.

Auf dem Desktop erscheint die HTML-Formatierung wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-desktop-v2.png" alt-text="HTML-Formatierung im Desktopclient":::

Unter iOS erscheint die HTML-Formatierung wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-mobile-v2.png" alt-text="HTML-Formatierung im iOS-Client":::

Zeichenformatierungen wie „Fett“ und „Kursiv“ werden unter iOS nicht gerendert.

Unter Android erscheint die HTML-Formatierung wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../../assets/images/Cards/card-formatting-xml-android-60.png" alt-text="HTML-Formatierung im Android-Client":::

Zeichenformatierung wie „Fett“ und „Kursiv“ werden unter Android korrekt angezeigt.

### <a name="format-example-for-simple-cards"></a>Formatbeispiel für einfache Karten

Die Bilder im vorherigen Abschnitt wurden mithilfe des **App-Studios** von Teams erstellt, wobei die Texteigenschaft einer Hero-Karte auf die folgende Zeichenfolge festgelegt ist:

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

Sie können die Formatierung auf Ihren eigenen Karten testen, indem Sie diesen Code ändern.

---

## <a name="see-also"></a>Siehe auch

* [Kartenaktionen](./cards-actions.md)
* [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* [Aufgabenmodule](~/task-modules-and-cards/cards/cards-format.md)
* [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)
* [Schemaexplorer für Adaptive Karten](https://adaptivecards.io/explorer/TextBlock.html)
