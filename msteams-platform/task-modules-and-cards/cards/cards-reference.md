---
title: Karten Referenz
description: Beschreibt alle Karten-und Karten Aktionen, die Bots in Microsoft Teams zur Verfügung stehen.
keywords: Referenz zu Bots-Karten
ms.openlocfilehash: 0bcc905f3d5b678700a396ff3e5b8b5f0232046f
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452610"
---
# <a name="cards-reference"></a>Karten Referenz

Die in diesem Abschnitt aufgelisteten Karten werden in Bots für Teams unterstützt. Sie basieren auf Karten, die durch das bot-Framework definiert wurden, aber Teams unterstützen nicht alle bot-Framework-Karten und haben eigene hinzugefügt. Unterschiede werden in den nachstehenden verweisen aufgerufen.

## <a name="card-examples"></a>Kartenbeispiele

Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das bot Builder SDK (v3). Im Microsoft/BotBuilder-Samples-Repository auf GitHub sind auch Codebeispiele verfügbar.

* .NET
  * [Hinzufügen von Karten als Anlagen zu Nachrichten](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [Kartenbeispiel Code (bot Builder v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* Node.js
  * [Hinzufügen von Karten als Anlagen zu Nachrichten](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [Kartenbeispiel Code (bot Builder v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a>Kartentypen

In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt.

| Kartentyp | Beschreibung |
| --- | --- |
| [Adaptive Karte](#adaptive-card) | Hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. |
| [Hero Card](#hero-card) | Enthält normalerweise ein einzelnes großes Bild, eine oder mehrere Schaltflächen und einen kleinen Textumfang. |
| [Karte auflisten](#list-card) | Eine Bildlaufliste mit Elementen. |
| [Office 365-Anschluss Karte](#office-365-connector-card) | Flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. |
| [Bestätigungs Karte](#receipt-card) | Stellt dem Benutzer eine Quittung zur Verfügung. |
| [SignIn-Karte](#signin-card) | Ermöglicht einem bot, das Anmelden eines Benutzers anzufordern. |
| [Miniatur Ansichtskarte](#thumbnail-card) | Enthält normalerweise ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen. |
| [Kartensammlungen](#card-collections) | Wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben. |

## <a name="common-properties-for-all-cards"></a>Allgemeine Eigenschaften für alle Karten

### <a name="inline-card-images"></a>Inline Karten Bilder

Ihre Karte kann ein Inlinebild enthalten, indem Sie einen Link zu Ihrem öffentlich verfügbaren Bild hinzufügen. Aus Leistungsgründen wird dringend empfohlen, dass Sie Ihr Image in einem öffentlichen Content-Delivery-Netzwerk (CDN) hosten.

Bilder werden in der Größe nach oben oder unten skaliert, wobei das Seitenverhältnis zum Abdecken des Bildbereichs beibehalten und dann vom Center abgeschnitten wurde, um das entsprechende Seitenverhältnis für die Karte zu erreichen.

Bilder müssen im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht offiziell unterstützt.

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| url | URL | HTTPS-URL zum Bild |
| alt | Zeichenfolge | Barrierefreie Beschreibung des Bilds |

### <a name="buttons"></a>Schaltflächen

Die Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt. Der Schaltflächentext befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Schaltflächenbreite überschreitet. Alle zusätzlichen Schaltflächen jenseits der von der Karte unterstützten Maximalzahl werden nicht angezeigt.

Weitere Informationen finden Sie unter [Karten Aktionen](~/task-modules-and-cards/cards/cards-actions.md) .

### <a name="card-formatting"></a>Kartenformatierung

Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) .

## <a name="adaptive-card"></a>Adaptive Karte

Eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. *Siehe* [Adaptive Cards v 1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).

### <a name="support-for-adaptive-cards"></a>Unterstützung für Adaptive Karten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

> [!NOTE]
> Medienelemente werden derzeit in Adaptive Cards v 1.2 auf der Teams-Plattform nicht unterstützt.

### <a name="example-adaptive-card"></a>Beispiel für eine Adaptive Karte

![Beispiel für eine Adaptive Karten Karte](~/assets/images/cards/adaptivecard.png)

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="for-more-information-on-adaptive-cards"></a>Weitere Informationen zu adaptiven Karten

* [Adaptive Karten – Übersicht](/adaptive-cards/)
* [Adaptive Karten Aktionen in Microsoft Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a>Hero Card

Eine Karte, die normalerweise ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-hero-cards"></a>Unterstützung für Hero Cards

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="properties-of-a-hero-card"></a>Eigenschaften einer Heldenkarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen. |
| unter | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) . |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 16:9 |
| Schaltflächen | Array von Action-Objekten | Eine Gruppe von Aktionen, die für die aktuelle Karte gelten. Maximal 6 |
| Tippen | Action-Objekt | Diese Aktion wird aktiviert, wenn der Benutzer die Karte selbst anzapft. |
|

### <a name="example-hero-card"></a>Beispiel für Hero Card

![Beispiel für eine Hero Card](~/assets/images/cards/hero.png)

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="for-more-information-on-hero-cards"></a>Weitere Informationen zu Hero Cards

Bot-Framework-Referenz:

* [Held-Karten Knoten](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [Hero Card C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a>Karte auflisten

Die Listen Karte wurde von Microsoft Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgehen, was die Listen Sammlung bieten kann. Die Listen Karte enthält eine Liste mit Elementen im Bildlauf.

### <a name="support-for-list-cards"></a>Unterstützung für Listen Karten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |
|

### <a name="properties-of-a-list-card"></a>Eigenschaften einer Listen Karte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| Elemente | Array von Listenelementen  ||
| Schaltflächen | Array von Action-Objekten | Eine Gruppe von Aktionen, die für die aktuelle Karte gelten. Maximal 6. |

### <a name="example-list-card"></a>Beispiel Listen Karte

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a>Office 365-Anschluss Karte

Unterstützt in Microsoft Teams, nicht im bot-Framework.

Die Office 365-Anschluss Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. Diese Karte kapselt eine connectorkarte ein, damit Sie von Bots verwendet werden kann. Im Abschnitt Hinweise finden Sie Informationen zu den Unterschieden zwischen connectorkarten und der O365-Karte.

### <a name="support-for-office-365-connector-cards"></a>Unterstützung für Office 365-Anschlusskarten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |
|

### <a name="properties-of-the-office-365-connector-card"></a>Eigenschaften der Office 365-Verbindungskarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen. |
| Zusammenfassung | Rich-Text  | Zusammenfassung der Karte. Maximal 2 Zeilen. |
| text | Rich-Text  | Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) . |
| themeColor | Hex-Zeichenfolge | Farbe, die die vom Anwendungsmanifest bereitgestellte accentColor überschreibt |

### <a name="notes-on-the-office-365-connector-card"></a>Hinweise auf der Office 365-Anschluss Karte

Office 365-connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [Action Card-Aktionen](/outlook/actionable-messages/card-reference#actioncard-action).

Ein wichtiger Unterschied zwischen der Verwendung von connectorkarten aus einem Konnektor und der Verwendung von Steckkarten in Ihrem bot ist die Handhabung von Karten Aktionen.

* Für einen Connector erhält der Endpunkt die Karten Nutzlast per HTTP-Post.
* Für einen bot löst die `HttpPOST` Aktion eine `invoke` Aktivität aus, die nur die Aktions-ID und den Textkörper an den bot sendet.

Jede Verbindungskarte kann maximal 10 Abschnitte anzeigen, und jeder Abschnitt kann maximal 5 Bilder und 5 Aktionen enthalten.

> [!NOTE]
> Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.

Alle Textfelder unterstützen Abschlag und HTML. Sie können steuern, welche Abschnitte "Abschlag" oder "HTML" verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen. Standardmäßig `markdown` ist auf festgelegt `true` ; Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` auf fest `false` .

Wenn Sie die `themeColor` Eigenschaft angeben, wird die `accentColor` Eigenschaft im App-Manifest überschrieben.

Um das Renderingformat für festzulegen `activityImage` , können Sie `activityImageType` Folgendes festlegen.

| Wert | Beschreibung |
| --- | --- |
| `avatar` | Standard `activityImage` wird als Kreis abgeschnitten |
| `article` | `activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei. |

Weitere Details zu den Eigenschaften von Verbindungskarten finden Sie in der [Referenz zur Nachrichten Karte mit Aktionen](/outlook/actionable-messages/card-reference). Die einzigen Verbindungskarten Eigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind folgende:

* `heroImage`
* `hideOriginalBody`
* `startGroup` (immer wie `true` in Teams behandelt)
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a>Beispiel Office 365 Connector-Karte

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a>Bestätigungs Karte

In Microsoft Teams unterstützt.

Eine Karte, mit der ein bot dem Benutzer eine Quittung zur Verfügung stellen kann. Sie enthält normalerweise die Liste der Elemente, die in die Empfangs-, Steuer-und Gesamtinformationen sowie anderen Text eingeschlossen werden sollen.

### <a name="support-for-receipts-cards"></a>Unterstützung für Empfangs Karten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="for-more-information-on-receipt-cards"></a>Weitere Informationen zu Empfangs Karten

Bot-Framework-Referenz:

* [Zugangskarten Knoten](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Quittungs Karte C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a>SignIn-Karte

Eine Karte, mit der ein bot die Anmeldung eines Benutzers anfordern kann. Wird in Microsoft Teams in einer etwas anderen Form als im bot-Framework unterstützt. Die SignIn-Karte in Microsoft Teams ähnelt der SignIn-Karte im bot-Framework mit der Ausnahme, dass die SignIn-Karte in Microsoft Teams nur zwei Aktionen unterstützt: `signin` und `openUrl` .

Die *SignIn-Aktion* kann von jeder beliebigen Karte in Microsoft Teams und nicht nur von der SignIn-Karte verwendet werden. Weitere Informationen zur Authentifizierung finden Sie im Thema [Microsoft Teams-Authentifizierungs Fluss für Bots](~/bots/how-to/authentication/auth-flow-bot.md) .

### <a name="support-for-signin-cards"></a>Unterstützung für SignIn-Karten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |
|

### <a name="for-more-information-on-signin-cards"></a>Weitere Informationen zu SignIn-Karten

Bot-Framework-Referenz:

* [SignIn-Karten Knoten](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [SignIn-Karte C #](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a>Miniatur Ansichtskarte

Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-thumbnail-cards"></a>Unterstützung für Miniatur Ansichtskarten

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

![Beispiel für eine Miniatur Ansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Eigenschaften einer Miniatur Ansichtskarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| unter | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird direkt unterhalb des Untertitels angezeigt; Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) . |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 1:1 (quadratisch) |
| Schaltflächen | Array von Action-Objekten | Eine Gruppe von Aktionen, die für die aktuelle Karte gelten. Maximal 6 |
| Tippen | Action-Objekt | Diese Aktion wird aktiviert, wenn der Benutzer die Karte selbst anzapft. |
|

### <a name="example-thumbnail-card"></a>Beispiel-Miniatur Ansichtskarte

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="for-more-information"></a>Weitere Informationen

Bot-Framework-Referenz:

* [Miniatur Ansichtskarten Knoten](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Miniatur Ansichtskarte C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a>Kartensammlungen

Kartensammlungen werden in Microsoft Teams unterstützt.

Kartensammlungen werden durch das bot-Framework bereitgestellt: `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` . Diese Sammlungen können Adaptive, Hero oder Thumbnail-Karten enthalten.

## <a name="carousel-collection"></a>Carousel-Sammlung

Das [Karussell-Layout](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) zeigt ein Karussell von Karten, optional mit zugeordneten Aktionsschaltflächen.

### <a name="support-for-carousel-collections"></a>Unterstützung für Karussell Sammlungen

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |
|

> [!NOTE]
> Ein Karussell kann maximal 10 Karten pro Nachricht anzeigen.

### <a name="example-carousel-collection"></a>Beispiel für eine Karussell Sammlung

![Beispiel für ein Karten Karussell](~/assets/images/cards/carousel.png)

Eigenschaften entsprechen denen für die Hero-oder Thumbnail-Karte.

### <a name="syntax-for-carousel-collections"></a>Syntax für Karussell Sammlungen

`builder.AttachmentLayout.carousel`

## <a name="list-collection"></a>List-Auflistung

### <a name="support-for-list-collections"></a>Unterstützung für Listen Auflistungen

Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.

| Bots in Microsoft Teams | Messaging-Erweiterungen  | Connectors | Bot-Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="example-list-collection"></a>Beispiel Listen Sammlung

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

Eigenschaften entsprechen denen für die Hero-oder Thumbnail-Karte.

In einer Liste können maximal 10 Karten pro Nachricht angezeigt werden.

> [!NOTE]
> Einige Kombinationen aus Listen Karten werden auf IOS und Android noch nicht unterstützt.

### <a name="syntax-for-list-collections"></a>Syntax für Listen Auflistungen

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a>In Microsoft Teams nicht unterstützte Karten

Die folgenden Karten werden vom bot-Framework implementiert, werden jedoch von Microsoft Teams nicht unterstützt.

* Animations Karten
* Audio-Karten
* Grafikkarten
