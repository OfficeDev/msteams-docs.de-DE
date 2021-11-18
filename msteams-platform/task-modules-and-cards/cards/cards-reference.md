---
title: Kartentypen
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
ms.localizationpriority: medium
keywords: Referenz zu Bots-Karten
ms.topic: reference
ms.openlocfilehash: 47e87ea28a1e003838152cd7f535a23d6861ac6f
ms.sourcegitcommit: e45742fd2aa2ff5e5c15e8f7c20cc14fbef6d441
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2021
ms.locfileid: "61075590"
---
# <a name="types-of-cards"></a>Kartentypen

Adaptive, Hero-, List-, Office 365 Connector-, Beleg-, Anmelde- und Miniaturansichtskarten und Kartensammlungen werden in Bots für Microsoft Teams unterstützt. Sie basieren auf Vom Bot Framework definierten Karten, aber Teams unterstützt nicht alle Bot Framework-Karten und hat einige eigene hinzugefügt.

Bevor Sie die verschiedenen Kartentypen identifizieren, sollten Sie wissen, wie Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte erstellen.

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a>Erstellen einer Favoritenkarte, Miniaturansichtskarte oder adaptiven Karte

**So erstellen Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte aus App Studio**

1. Wechseln Sie von Teams zu **App Studio.**
1. Wählen Sie **den Karten-Editor** aus.
1. Wählen Sie **"Neue Karte erstellen"** aus.
1. Wählen Sie **"Erstellen"** für eine der Karten aus **Hero-Karte,** **Miniaturansichtskarte** oder **adaptiver Karte** aus. Die Metadatendetails, Schaltflächen und JSON-, Csharp- und Knotencodebeispiele werden für diese Karte gezeigt.

    ![Favoritenkartendetails](~/assets/images/Cards/Herocarddetails.png)

1. Wählen Sie **"Diese Karte senden" aus.** Die Karte wird als Chatnachricht an Sie gesendet.

## <a name="card-examples"></a>Kartenbeispiele

Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3. Codebeispiele sind auch im **Microsoft/BotBuilder-Samples-Repository** auf GitHub verfügbar. Es folgen einige Kartenbeispiele:

* .NET
  * [Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).

* Node.js
  * [Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).

## <a name="card-types"></a>Kartentypen

Sie können unterschiedliche Kartentypen basierend auf Ihren Anwendungsanforderungen identifizieren und verwenden. In der folgenden Tabelle sind die Kartentypen aufgeführt, die Ihnen zur Verfügung stehen:

| Kartentyp | Beschreibung |
| --- | --- |
| [Adaptive Karte](#adaptive-card) | Diese Karte ist in hohem Maße anpassbar und kann eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten. |
| [Hero-Karte](#hero-card) | Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge. |
| [Karte auflisten](#list-card) | Diese Karte enthält eine Bildlaufliste von Elementen. |
| [Office 365-Connectorkarte](#office-365-connector-card) | Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. |
| [Belegkarte](#receipt-card) | Diese Karte stellt dem Benutzer einen Beleg bereit. |
| [Anmeldekarte](#signin-card) | Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer anmeldet. |
| [Miniaturansichtskarte](#thumbnail-card) | Diese Karte enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen. |
| [Kartensammlungen](#card-collections) | Diese Kartensammlung wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben. |

## <a name="features-that-support-different-card-types"></a>Features, die unterschiedliche Kartentypen unterstützen

| Kartentyp | Bots | Vorschau der Nachrichtenerweiterung | Ergebnisse der Nachrichtenerweiterung | Aufgabenmodule | Ausgehende Webhooks | Eingehende Webhooks | Office 365-Connectors |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Adaptive Karte | ✔ | ✖ | ✔ | ✔ | ✔ | ✔ | ✖ |
| Office 365-Connectorkarte | ✔ | ✖ | ✔ | ✖ | ✔ | ✔ | ✔ |
| Hero-Karte | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Miniaturansichtskarte | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Karte auflisten | ✔ | ✖ | ✖ | ✖ | ✔ | ✔ | ✖ |
| Belegkarte | ✔ | ✖ | ✖ | ✖ | ✖ | ✔ | ✖ |
| Anmeldekarte | ✔ | ✖ | ✖ | ✖ | ✖ | ✖ | ✖ |

> [!NOTE]
> Bei adaptiven Karten in eingehenden Webhooks werden alle systemeigenen Schemaelemente adaptiver Karten, mit Ausnahme `Action.Submit` von , vollständig unterstützt. Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)und [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

## <a name="common-properties-for-all-cards"></a>Allgemeine Eigenschaften für alle Karten

Sie können einige allgemeine Eigenschaften durchgehen, die für alle Karten gelten.

> [!NOTE]
> Favoriten- und Miniaturansichtskarten mit mehreren Aktionen werden automatisch in mehrere Karten in einem Karusselllayout aufgeteilt.

### <a name="inline-card-images"></a>Inlinekartenbilder

Die Karte kann ein Inlinebild enthalten, indem ein Link zum öffentlich verfügbaren Bild eingeschlossen wird. Aus Leistungsgründen wird dringend empfohlen, das Image auf einem öffentlichen Content Delivery Network (CDN) zu hosten.

Bilder werden in der Größe nach oben oder unten skaliert, um das Seitenverhältnis für die Abdeckung des Bildbereichs beizubehalten. Bilder werden dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.

Bilder müssen höchstens 1024×1024 und im PNG-, JPEG- oder GIF-Format vorliegen. Animierte GIF-Dateien werden nicht unterstützt.

Die folgende Tabelle enthält die Eigenschaften von Inlinekartenbildern:

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| url | URL | HTTPS-URL zum Bild. |
| alt | Zeichenfolge | Beschreibung des Bilds, auf das zugegriffen werden kann. |

> [!NOTE]
> Wenn eine Karte eine Bild-URL enthält, die vor dem endgültigen Bild umgeleitet wird, wird die Umleitung in der Bild-URL nicht unterstützt. Dies geschieht für Bilder, die in der öffentlichen Cloud freigegeben sind.

### <a name="buttons"></a>Schaltflächen

Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt. Schaltflächentext befindet sich immer in einer zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet. Zusätzliche Schaltflächen, die über die von der Karte maximal unterstützte Anzahl hinausgehen, werden nicht angezeigt.

Weitere Informationen finden Sie unter [Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

### <a name="card-formatting"></a>Kartenformatierung

Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)

Nachdem Sie die allgemeinen Eigenschaften für alle Karten identifiziert haben, können Sie jetzt mit adaptiven Karten arbeiten, die Ihnen helfen, das Engagement und die Effizienz zu steigern, indem Sie Ihre Aktionen erfordernden Inhalte direkt zu den von Ihnen verwendeten Apps hinzufügen.

## <a name="adaptive-card"></a>Adaptive Karte

Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. Weitere Informationen finden Sie unter [Adaptive Karten.](https://github.com/microsoft/AdaptiveCards/releases/tag/2020.07)

### <a name="support-for-adaptive-cards"></a>Unterstützung für adaptive Karten

Die folgende Tabelle enthält die Features, die adaptive Karten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * Teams Plattform unterstützt v1.4 oder frühere Adaptive Kartenfeatures für vom Bot gesendete Karten und aktionsbasierte Messaging-Erweiterungen.
> * Teams Plattform unterstützt v1.3 oder eine frühere Version von Features für adaptive Karten für andere Funktionen, z. B. von Benutzern gesendete Karten (suchbasierte Messagingerweiterungen und Verbreitung von Links), Registerkarten und Aufgabenmodule.
> * Das Formatieren positiver oder destruktiver Aktionen wird in adaptiven Karten auf der Teams Plattform nicht unterstützt.
> * Medienelemente werden derzeit in adaptiver Karte auf der Teams Plattform nicht unterstützt.

### <a name="example-of-adaptive-card"></a>Beispiel für adaptive Karte

![Beispiel für eine adaptive Karte](~/assets/images/cards/adaptivecard.png)

Der folgende Code zeigt ein Beispiel für eine adaptive Karte:

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

#### <a name="additional-information-on-adaptive-cards"></a>Zusätzliche Informationen zu adaptiven Karten

Bot Framework-Referenz:

* [Knoten "Adaptive Karten"](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [Adaptive Karte C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

Sie können jetzt mit einer Hero-Karte arbeiten, bei der es sich um eine Mehrzweckkarte handelt, die verwendet wird, um eine potenzielle Benutzerauswahl visuell hervorzuheben.

## <a name="hero-card"></a>Hero-Karte

Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-hero-cards"></a>Unterstützung für Favoritenkarten

Die folgende Tabelle enthält die Features, die Hero-Karten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Eigenschaften einer Favoritenkarte

Die folgende Tabelle enthält die Eigenschaften einer Hero-Karte:

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal zwei Zeilen. |
| Untertitel | Rich-Text  | Untertitel der Karte. Maximal zwei Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md) |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 16:9. |
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der für die aktuelle Karte gilt. Maximal sechs. |
| Tippen | Action-Objekt | Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

### <a name="example-of-a-hero-card"></a>Beispiel für eine Hero-Karte

![Beispiel für eine Hero-Karte](~/assets/images/cards/hero.png)

Der folgende Code zeigt ein Beispiel für eine Hero-Karte:

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

### <a name="additional-information-on-hero-cards"></a>Zusätzliche Informationen zu Favoritenkarten

Bot Framework-Referenz:

* [Hero-Karte Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [Hero-Karte C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Karte auflisten

Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgeht, was die Listensammlung bereitstellen kann. Die Listenkarte enthält eine Bildlaufliste mit Elementen.

### <a name="support-for-list-cards"></a>Unterstützung für Listenkarten

Die folgende Tabelle enthält die Features, die Listenkarten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Eigenschaften einer Listenkarte

Die folgende Tabelle enthält die Eigenschaften einer Listenkarte:

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| items | Array von Listenelementen | Satz von Elementen, die auf die Karte anwendbar sind.|
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der für die aktuelle Karte gilt. Maximal 6. |

### <a name="example-of-a-list-card"></a>Beispiel für eine Listenkarte

Der folgende Code zeigt ein Beispiel für eine Listenkarte:

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

## <a name="office-365-connector-card"></a>Office 365 Connectorkarte

Sie können mit einer Office 365 Connectorkarte arbeiten, die ein flexibles Layout bietet und eine hervorragende Möglichkeit darstellt, nützliche Informationen zu erhalten. Die Office 365 Connectorkarte wird in Teams unterstützt, nicht in Bot Framework. Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. Diese Karte enthält eine Connectorkarte, sodass sie von Bots verwendet werden kann. Informationen zu Unterschieden zwischen Connectorkarten und der Office 365 Connectorkarte finden Sie unter [zusätzliche Informationen auf der Office 365 Connector-Karte.](#additional-information-on-the-office-365-connector-card)

### <a name="support-for-office-365-connector-cards"></a>Unterstützung für Office 365 Connectorkarten

Die folgende Tabelle enthält die Features, die Office 365 Connectorkarten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Eigenschaften der Office 365-Connectorkarte

Die folgende Tabelle enthält die Eigenschaften der Office 365-Connectorkarte:

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal zwei Zeilen. |
| Zusammenfassung | Rich-Text  | Zusammenfassung der Karte. Maximal zwei Zeilen. |
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md) |
| themeColor | HEX-Zeichenfolge | Farbe, die die `accentColor` aus dem Anwendungsmanifest bereitgestellte Überschreibung überschreibt. |

### <a name="additional-information-on-the-office-365-connector-card"></a>Zusätzliche Informationen auf der Office 365 Connectorkarte

Office 365 Connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ `ActionCard` Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)

Der wichtige Unterschied zwischen der Verwendung von Connectorkarten aus einem Connector und der Verwendung von Connectorkarten in Ihrem Bot besteht in der Behandlung von Kartenaktionen. In der folgenden Tabelle sind die Unterschiede aufgeführt:

| Connector | Bot |
| --- | --- |
| Der Endpunkt empfängt die Kartennutzlast über HTTP POST. | Die `HttpPOST` Aktion löst eine Aktivität `invoke` aus, die nur die Aktions-ID und den Textkörper an den Bot sendet.|

Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.

> [!NOTE]
> Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.

Alle Textfelder unterstützen Markdown und HTML. Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen. Standardmäßig `markdown` ist auf `true` . Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` dies auf `false` fest.

Wenn Sie die `themeColor` Eigenschaft angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.

Um den Renderingstil für `activityImage` anzugeben, können Sie `activityImageType` wie in der folgenden Tabelle dargestellt festlegen:

| Wert | Beschreibung |
| --- | --- |
| `avatar` | Standard, `activityImage` wird als Kreis zugeschnitten. |
| `article` | `activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei. |

Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Referenz zu Nachrichtenkarten](/outlook/actionable-messages/card-reference)mit Aktionen. Die einzigen Connectorkarteneigenschaften, die Teams derzeit nicht unterstützt, sind:

* `heroImage`
* `hideOriginalBody`
* `startGroup`immer wie in Teams behandelt `true`
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Beispiel für eine Office 365-Connectorkarte

Der folgende Code zeigt ein Beispiel für eine Office 365 Connectorkarte:

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

## <a name="receipt-card"></a>Belegkarte

Teams unterstützt die Belegkarte. Es handelt sich um eine Karte, die es einem Bot ermöglicht, dem Benutzer einen Beleg bereitzustellen. Es enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.

### <a name="support-for-receipt-cards"></a>Unterstützung für Belegkarten

Die folgende Tabelle enthält die Features, die Belegkarten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Beispiel für eine Belegkarte

![Beispiel für eine Belegkarte](~/assets/images/cards/receipt.png)

Der folgende Code zeigt ein Beispiel für eine Belegkarte:

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a>Zusätzliche Informationen zu Belegkarten

Bot Framework-Referenz:

* [Belegkarte Node.js](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Belegkarte C #](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Anmeldekarte

Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` und `openUrl` unterstützt.

Die Anmeldeaktion kann von einer beliebigen Karte in Teams verwendet werden, nicht nur von der Anmeldekarte. Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Bots.](~/bots/how-to/authentication/auth-flow-bot.md)

### <a name="support-for-signin-cards"></a>Unterstützung für Anmeldekarten

Die folgende Tabelle enthält die Features, die Anmeldekarten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Zusätzliche Informationen zu Anmeldekarten

Bot Framework-Referenz:

* [Anmeldekarten-Node.js](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Anmeldekarte C #](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Miniaturansichtskarte

Sie können mit einer Miniaturansichtskarte arbeiten, die zum Senden einer einfachen Nachricht mit Aktionen verwendet wird. Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-thumbnail-cards"></a>Unterstützung für Miniaturansichtskarten

Die folgende Tabelle enthält die Features, die Miniaturansichtskarten unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Eigenschaften einer Miniaturansichtskarte

Die folgende Tabelle enthält die Eigenschaften einer Miniaturansichtskarte:

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| Untertitel | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md) |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 1:1 Quadrat. |
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der für die aktuelle Karte gilt. Maximal 6. |
| Tippen | Action-Objekt | Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

### <a name="example-of-a-thumbnail-card"></a>Beispiel für eine Miniaturansichtskarte

Der folgende Code zeigt ein Beispiel für eine Miniaturansichtskarte:

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

### <a name="additional-information"></a>Weitere Informationen

Bot Framework-Referenz:

* [Miniaturansichtskarte Node.js](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Miniaturansichtskarte C #](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Kartensammlungen

Sie können mit Kartensammlungen arbeiten, die Karussell- und Listensammlungen enthalten. Teams unterstützt Kartensammlungen. Kartensammlungen enthalten `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` . Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.

### <a name="carousel-collection"></a>Karussellsammlung

Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugehörigen Aktionsschaltflächen.

#### <a name="support-for-carousel-collections"></a>Unterstützung für Karussellsammlungen

Die folgende Tabelle enthält die Features, die Karussellsammlungen unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.

#### <a name="properties-of-a-carousel-card"></a>Eigenschaften einer Karussellkarte

Die Eigenschaften einer Karussellkarte sind identisch mit den Favoriten- und Miniaturansichtskarten.

#### <a name="example-of-a-carousel-collection"></a>Beispiel für eine Karussellsammlung

![Beispiel für ein Karussell von Karten](~/assets/images/cards/carousel.png)

Der folgende Code zeigt ein Beispiel für eine Karussellsammlung:

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

#### <a name="syntax-for-carousel-collections"></a>Syntax für Karussellsammlungen

`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.

### <a name="list-collection"></a>Sammlung auflisten

Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugehörigen Aktionsschaltflächen.

#### <a name="support-for-list-collections"></a>Unterstützung für Listensammlungen

Die folgende Tabelle enthält die Features, die Listensammlungen unterstützen:

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

#### <a name="example-of-a-list-collection"></a>Beispiel für eine Listensammlung

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

Die Eigenschaften von Listensammlungen sind identisch mit den Favoriten- oder Miniaturansichtskarten.

Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.

> [!NOTE]
> Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.

#### <a name="syntax-for-list-collections"></a>Syntax für Listensammlungen

`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.

## <a name="cards-not-supported-in-teams"></a>Karten werden in Teams nicht unterstützt

Die folgenden Karten werden vom Bot Framework implementiert, aber nicht von Teams unterstützt:

* Animationskarten
* Audiokarten
* Grafikkarten

## <a name="see-also"></a>Weitere Informationen

* [Aufgabenmodule](~/task-modules-and-cards/what-are-task-modules.md)
* [Formatieren von Karten](~/task-modules-and-cards/cards/cards-format.md)
* [Aktuelle Karten](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/work-with-universal-actions-for-adaptive-cards.md)
