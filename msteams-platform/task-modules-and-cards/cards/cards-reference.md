---
title: Karten-Referenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams zur Verfügung stehen
keywords: Bots-Kartenreferenz
ms.topic: reference
ms.openlocfilehash: b9e11a6a6cb6de370323a3b07e2451a3abc41f12
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634537"
---
# <a name="cards-reference"></a>Karten-Referenz

Die in diesem Dokument aufgeführten Karten werden in Bots für Microsoft Teams unterstützt. Sie basieren auf Karten, die vom Bot Framework definiert wurden, aber Teams unterstützt nicht alle Bot Framework-Karten, und stattdessen wurden einige Teams-Karten hinzugefügt. Unterschiede werden in den Verweisen in diesem Dokument aufgerufen.

## <a name="card-examples"></a>Kartenbeispiele

Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3. Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.

* .NET
  * [Hinzufügen von Karten als Anlagen zu Nachrichten](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [Kartenbeispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards)

* Node.js
  * [Hinzufügen von Karten als Anlagen zu Nachrichten](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [Kartenbeispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards)

## <a name="types-of-cards"></a>Kartentypen

In dieser Tabelle sind die verfügbaren Kartentypen aufgeführt:

| Kartentyp | Beschreibung |
| --- | --- |
| [Adaptive Karte](#adaptive-card) | Diese Karte ist eine hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. |
| [Heldenkarte](#hero-card) | Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge. |
| [Listenkarte](#list-card) | Diese Karte ist eine Bildlaufliste mit Elementen. |
| [Office 365-Connectorkarte](#office-365-connector-card) | Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. |
| [Belegkarte](#receipt-card) | Diese Karte bietet dem Benutzer eine Quittung. |
| [Signin-Karte](#signin-card) | Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer meldet. |
| [Miniaturansichtskarte](#thumbnail-card) | Diese Karte enthält in der Regel ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen. |
| [Kartensammlungen](#card-collections) | Diese Karten werden verwendet, um mehrere Elemente in einer einzigen Antwort zurück zu geben. |

## <a name="common-properties-for-all-cards"></a>Allgemeine Eigenschaften für alle Karten

### <a name="inline-card-images"></a>Inlinekartenbilder

Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich verfügbaren Bild enthält. Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Netzwerk für die Inhaltszustellung (Public Content Delivery Network, CDN) zu hosten.

Bilder werden in der Größe nach oben oder unten skaliert, wobei das Seitenverhältnis beibehalten wird, um den Bildbereich zu abdecken. Bilder werden dann aus der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erreichen.

Bilder müssen mindestens 1024×1024 im PNG-, JPEG- oder GIF-Format vorliegen und keine animierte GIF unterstützen.

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| url | URL | HTTPS-URL zum Bild. |
| alt | String | Barrierefreie Beschreibung des Bilds. |

> [!NOTE]
> Wenn eine Karte eine Bild-URL enthält, die eine Umleitung vor dem endgültigen Bild durchgeht, wird die Umleitung in der Bild-URL nicht unterstützt. Dies tritt für Bilder auf, die in der öffentlichen Cloud freigegeben werden.

### <a name="buttons"></a>Schaltflächen

Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt. Der Text der Schaltfläche befindet sich immer in einer einzigen Zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet. Alle zusätzlichen Schaltflächen, die über die maximale Anzahl hinausgehen, die von der Karte unterstützt wird, werden nicht angezeigt.

Weitere Informationen finden Sie unter [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

### <a name="card-formatting"></a>Kartenformatierung

Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="adaptive-card"></a>Adaptive Karte

Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. Siehe [adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).

### <a name="support-for-adaptive-cards"></a>Unterstützung für adaptive Karten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * Die Teams-Plattform unterstützt Version 1.2 oder früher von adaptiven Kartenfeatures.
> * Medienelemente werden derzeit in adaptiver Karte v1.2 auf der Teams-Plattform nicht unterstützt.

### <a name="example-of-an-adaptive-card"></a>Beispiel für eine adaptive Karte

![Beispiel für eine adaptive Karte](~/assets/images/cards/adaptivecard.png)

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

* [Adaptive Karten Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [Adaptive Karte C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a>Heldenkarte

Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-hero-cards"></a>Unterstützung für Heldenkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Eigenschaften einer Heldenkarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen. |
| subtitle | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 16:9. |
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der auf die aktuelle Karte anwendbar ist. Maximal 6. |
| tippen | Action-Objekt | Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

### <a name="example-of-a-hero-card"></a>Beispiel für eine Heldenkarte

![Beispiel für eine Heldenkarte](~/assets/images/cards/hero.png)

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

### <a name="additional-information-on-hero-cards"></a>Zusätzliche Informationen zu Heldenkarten

Bot Framework-Referenz:

* [Hero card Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [Heldenkarte C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Listenkarte

Die Listenkarte wurde von Teams hinzugefügt, um Funktionen zu bieten, die über das hinaus gehen, was die Listensammlung bereitstellen kann. Die Listenkarte enthält eine Bildlaufliste mit Elementen.

### <a name="support-for-list-cards"></a>Unterstützung für Listenkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Eigenschaften einer Listenkarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| items | Array von Listenelementen ||
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der auf die aktuelle Karte anwendbar ist. Maximal 6. |

### <a name="example-of-a-list-card"></a>Beispiel für eine Listenkarte

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

## <a name="office-365-connector-card"></a>Office 365-Connectorkarte

Die Office 365-Connectorkarte wird in Teams und nicht in Bot Framework unterstützt. Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. Diese Karte kapselt eine Connectorkarte, sodass sie von Bots verwendet werden kann. Unterschiede zwischen Connectorkarten und der O365-Karte finden Sie unter [Hinweise auf der Office 365-Connectorkarte](#notes-on-the-office-365-connector-card).

### <a name="support-for-office-365-connector-cards"></a>Unterstützung für Office 365-Connectorkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Eigenschaften der Office 365-Connectorkarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen. |
| Zusammenfassung | Rich-Text  | Zusammenfassung der Karte. Maximal 2 Zeilen. |
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| themeColor | HEX-Zeichenfolge | Farbe, die die im Anwendungsmanifest bereitgestellte accentColor überschreibt. |

### <a name="notes-on-the-office-365-connector-card"></a>Hinweise auf der Office 365-Connectorkarte

Office 365-Connectorkarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)

Ein wichtiger Unterschied zwischen der Verwendung von Connectorkarten von einem Connector und der Verwendung von Connectorkarten in Ihrem Bot ist die Behandlung von Kartenaktionen.

* Für einen Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.
* Bei einem Bot löst die Aktion eine Aktivität aus, die nur die `HttpPOST` `invoke` Aktions-ID und den Textkörper an den Bot sendet.

Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.

> [!NOTE]
> Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.

Alle Textfelder unterstützen Markdown und HTML. Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie `markdown` die Eigenschaft in einer Nachricht festlegen. Standardmäßig ist `markdown` auf `true` festgelegt. Wenn Sie stattdessen HTML verwenden möchten, legen Sie auf `markdown` . `false`

Wenn Sie die Eigenschaft `themeColor` angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.

Zum Angeben des Renderingstils für `activityImage` können Sie `activityImageType` folgendes festlegen:

| Wert | Beschreibung |
| --- | --- |
| `avatar` | Standard; `activityImage` wird als Kreis zugeschnitten. |
| `article` | `activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei. |

Weitere Informationen zu den Eigenschaften von Connectorkarten finden Sie unter [Referenz zu Nachrichtenkarten mit Aktionen.](/outlook/actionable-messages/card-reference) Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:

* `heroImage`
* `hideOriginalBody`
* `startGroup` immer wie `true` in Teams behandelt
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Beispiel für eine Office 365-Connectorkarte

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

Teams unterstützt die Belegkarte. Es handelt sich um eine Karte, mit der ein Bot dem Benutzer eine Quittung bereitstellen kann. Sie enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.

### <a name="support-for-receipt-cards"></a>Unterstützung für Belegkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Beispiel für eine Belegkarte

![Beispiel für eine Belegkarte](~/assets/images/cards/receipt.png)

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

* [Belegkarten Node.js](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Belegkarte C #](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Signin-Karte

Mit der Anmeldekarte kann ein Bot einen Benutzer zur Anmeldung anfordern. Es wird in Teams in einer etwas anderen Form als im Bot Framework unterstützt. Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` unterstützt: und `openUrl` .

Die Anmeldeaktion kann von jeder beliebigen Karte in Teams verwendet werden, nicht nur von der Anmeldekarte. Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams-Authentifizierungsfluss für Bots](~/bots/how-to/authentication/auth-flow-bot.md).

### <a name="support-for-signin-cards"></a>Unterstützung für Anmeldekarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Zusätzliche Informationen zu Anmeldekarten

Bot Framework-Referenz:

* [Signin card Node.js](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Signin-Karte C #](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Miniaturansichtskarte

Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-thumbnail-cards"></a>Unterstützung für Miniaturansichtskarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Eigenschaften einer Miniaturansichtskarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| subtitle | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| Bilder | Array von Bildern | Bild, das oben auf der Karte angezeigt wird. Seitenverhältnis 1:1 quadratisch. |
| Schaltflächen | Array von Aktionsobjekten | Aktionssatz, der auf die aktuelle Karte anwendbar ist. Maximal 6. |
| tippen | Action-Objekt | Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

### <a name="example-of-a-thumbnail-card"></a>Beispiel für eine Miniaturansichtskarte

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

* [Miniaturansichtskarten Node.js](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Miniaturansichtskarte C #](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Kartensammlungen

Teams unterstützt Kartensammlungen.

Kartensammlungen umfassen `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` . Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.

## <a name="carousel-collection"></a>Karussellsammlung

Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugeordneten Aktionsschaltflächen.

### <a name="support-for-carousel-collections"></a>Unterstützung für Karussellsammlungen

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.

### <a name="properties-of-a-carousel-card"></a>Eigenschaften einer Karussellkarte

Die Eigenschaften einer Karussellkarte sind mit denen der Hero- und Miniaturansichtskarten identisch.

### <a name="example-of-a-carousel-collection"></a>Beispiel für eine Karussellsammlung

![Beispiel für ein Karussell von Karten](~/assets/images/cards/carousel.png)

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

### <a name="syntax-for-carousel-collections"></a>Syntax für Karussellsammlungen

`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.

## <a name="list-collection"></a>Listensammlung

### <a name="support-for-list-collections"></a>Unterstützung für Listensammlungen

Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugeordneten Aktionsschaltflächen.

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-list-collection"></a>Beispiel für eine Listensammlung

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

Die Eigenschaften sind identisch mit der Hero- oder Miniaturansichtskarte.

Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.

> [!NOTE]
> Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.

### <a name="syntax-for-list-collections"></a>Syntax für Listensammlungen

`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.

## <a name="cards-not-supported-in-teams"></a>In Teams nicht unterstützte Karten

Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch nicht von Teams unterstützt:

* Animationskarten
* Audiokarten
* Grafikkarten
