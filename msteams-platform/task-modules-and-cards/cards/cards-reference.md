---
title: Karten-Referenz
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
localization_priority: Normal
keywords: Bots-Karten-Referenz
ms.topic: reference
ms.openlocfilehash: cab7f1659759f40beb1aba59531ee6c1a84662c1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566859"
---
# <a name="cards-reference"></a>Karten-Referenz

Die in diesem Dokument aufgeführten Karten werden in Bots für Microsoft Teams unterstützt. Sie basieren auf Karten, die vom Bot Framework definiert sind, aber Teams nicht alle Bot Framework-Karten unterstützt und stattdessen einige Teams Karten hinzugefügt wurden. Unterschiede werden in den Verweisen in diesem Dokument herausgestellt.

## <a name="card-examples"></a>Kartenbeispiele

Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3. Codebeispiele sind auch im Microsoft/BotBuilder-Samples-Repository auf GitHub verfügbar.

* .NET
  * [Fügen Sie Karten als Anlagen zu Nachrichten hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)
  * [Karten Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).

* Node.js
  * [Fügen Sie Karten als Anlagen zu Nachrichten hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
  * [Karten Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).

## <a name="types-of-cards"></a>Kartentypen

Diese Tabelle zeigt die Kartentypen, die Ihnen zur Verfügung stehen:

| Kartentyp | Beschreibung |
| --- | --- |
| [Adaptive Karte](#adaptive-card) | Diese Karte ist eine hochgradig anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. |
| [Heldenkarte](#hero-card) | Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Menge Text. |
| [Listenkarte](#list-card) | Diese Karte ist eine Bildlaufliste von Elementen. |
| [Office 365-Anschlusskarte](#office-365-connector-card) | Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. |
| [Empfangskarte](#receipt-card) | Diese Karte stellt dem Benutzer eine Quittung zur Verfügung. |
| [Signin-Karte](#signin-card) | Diese Karte ermöglicht es einem Bot, anzufordern, dass sich ein Benutzer anmeldet. |
| [Thumbnail-Karte](#thumbnail-card) | Diese Karte enthält in der Regel ein einzelnes Miniaturbild, einen kurzen Text und eine oder mehrere Schaltflächen. |
| [Kartensammlungen](#card-collections) | Diese Karten werden verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben. |

## <a name="common-properties-for-all-cards"></a>Gemeinsame Eigenschaften für alle Karten

### <a name="inline-card-images"></a>Inline-Kartenbilder

Die Karte kann ein Inlinebild enthalten, indem sie einen Link zum öffentlich zugänglichen Bild enthält. Aus Leistungsgründen wird dringend empfohlen, das Image in einem öffentlichen Content-Delivery-Netzwerk (CDN) zu hosten.

Bilder werden nach oben oder unten skaliert, während das Seitenverhältnis beibehalten wird, um den Bildbereich abzudecken. Bilder werden dann von der Mitte abgeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erreichen.

Bilder müssen höchstens 1024×1024 im PNG-, JPEG- oder GIF-Format vorliegen und animiertes GIF nicht unterstützen.

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| url | URL | HTTPS-URL zum Bild. |
| alt | Zeichenfolge | Zugängliche Beschreibung des Bildes. |

> [!NOTE]
> Wenn eine Karte eine Bild-URL enthält, die eine Umleitung vor dem endgültigen Bild durchläuft, wird die Umleitung in der Bild-URL nicht unterstützt. Dies tritt bei Bildern auf, die in der öffentlichen Cloud freigegeben wurden.

### <a name="buttons"></a>Schaltflächen

An der Unterseite der Karte werden Schaltflächen gestapelt angezeigt. Schaltflächentext befindet sich immer in einer einzelnen Zeile und wird abgeschnitten, wenn der Text die Schaltflächenbreite überschreitet. Zusätzliche Schaltflächen, die über die von der Karte unterstützte maximale Anzahl hinausgehen, werden nicht angezeigt.

Weitere Informationen finden Sie unter [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

### <a name="card-formatting"></a>Kartenformatierung

Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="adaptive-card"></a>Adaptive Karte

Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann. Weitere Informationen finden Sie unter [Adaptive Karten v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).

### <a name="support-for-adaptive-cards"></a>Unterstützung für adaptive Karten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * Teams Plattform unterstützt v1.2 oder früher adaptive Kartenfunktionen.
> * Medienelemente werden derzeit in adaptivecard v1.2 auf der Teams Plattform nicht unterstützt.

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

Referenz für Bot Framework:

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
| Untertitel | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| Bilder | Array von Bildern | Bild oben auf der Karte angezeigt. Seitenverhältnis 16:9. |
| Schaltflächen | Array von Aktionsobjekten | Satz von Aktionen, die für die aktuelle Karte gelten. Maximal 6. |
| Tippen | Action-Objekt | Aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

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

Referenz für Bot Framework:

* [Heldenkarte Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [Heldenkarte C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Listenkarte

Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgehen, was die Listensammlung bereitstellen kann. Die Listenkarte enthält eine Bildlaufliste der Elemente.

### <a name="support-for-list-cards"></a>Unterstützung für Listenkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Eigenschaften einer Listenkarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| Elemente | Array von Listenelementen ||
| Schaltflächen | Array von Aktionsobjekten | Satz von Aktionen, die für die aktuelle Karte gelten. Maximal 6. |

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

## <a name="office-365-connector-card"></a>Office 365-Anschlusskarte

Die Office 365-Connectorkarte wird in Teams und nicht in Bot Framework unterstützt. Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen. Diese Karte kapselt eine Connector-Karte, so dass sie von Bots verwendet werden kann. Unterschiede zwischen Anschlusskarten und O365-Karte finden Sie [unter Hinweise auf der Office 365-Anschlusskarte](#notes-on-the-office-365-connector-card).

### <a name="support-for-office-365-connector-cards"></a>Unterstützung für Office 365-Anschlusskarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Eigenschaften der Office 365-Anschlusskarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen. |
| Zusammenfassung | Rich-Text  | Zusammenfassung der Karte. Maximal 2 Zeilen. |
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| themeColor | HEX-String | Farbe, die die aus dem Anwendungsmanifest bereitgestellte accentColor überschreibt. |

### <a name="notes-on-the-office-365-connector-card"></a>Hinweise auf der Office 365-Anschlusskarte

Office 365-Anschlusskarten funktionieren in Microsoft Teams ordnungsgemäß, einschließlich [ActionCard-Aktionen](/outlook/actionable-messages/card-reference#actioncard-action).

Ein wichtiger Unterschied zwischen der Verwendung von Anschlusskarten von einem Stecker und der Verwendung von Anschlusskarten in Ihrem Bot ist die Handhabung von Kartenaktionen.

* Bei einem Connector empfängt der Endpunkt die Kartennutzlast über HTTP POST.
* Bei einem Bot löst die `HttpPOST` Aktion eine Aktivität aus, die nur die `invoke` Aktions-ID und den Körper an den Bot sendet.

Jede Anschlusskarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.

> [!NOTE]
> Zusätzliche Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.

Alle Textfelder unterstützen Markdown und HTML. Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen. Standardmäßig `markdown` ist auf `true` festgelegt. Wenn Sie stattdessen HTML verwenden möchten, setzen Sie `markdown` auf `false` .

Wenn Sie die `themeColor` Eigenschaft angeben, wird die `accentColor` Eigenschaft im App-Manifest überschrieben.

Um den Renderstil für `activityImage` anzugeben, können Sie `activityImageType` wie folgt festlegen:

| Wert | Beschreibung |
| --- | --- |
| `avatar` | Standard; `activityImage` wird als Kreis beschnitten. |
| `article` | `activityImage` wird als Rechteck angezeigt und behält sein Seitenverhältnis bei. |

Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Verwertbare Meldungskartenreferenz](/outlook/actionable-messages/card-reference). Die einzigen Connectorkarteneigenschaften, die Microsoft Teams derzeit nicht unterstützt, sind:

* `heroImage`
* `hideOriginalBody`
* `startGroup`immer wie in Teams behandelt `true`
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Beispiel für eine Office 365-Anschlusskarte

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

## <a name="receipt-card"></a>Empfangskarte

Teams unterstützt die Empfangskarte. Es ist eine Karte, die es einem Bot ermöglicht, dem Benutzer eine Quittung zu geben. Sie enthält in der Regel die Liste der Artikel, die in den Wareneingang aufgenommen werden sollen, z. B. Steuern und Gesamtinformationen.

### <a name="support-for-receipt-cards"></a>Unterstützung für Empfangskarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Beispiel für eine Empfangskarte

![Beispiel für eine Empfangskarte](~/assets/images/cards/receipt.png)

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

### <a name="additional-information-on-receipt-cards"></a>Zusätzliche Informationen zu Denobkarten

Referenz für Bot Framework:

* [Empfangskarte Node.js](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Empfangskarte C #](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Signin-Karte

Mit der Anmeldekarte kann ein Bot einen Benutzer auffordern, sich anzumelden. Es wird in Teams in einer etwas anderen Form unterstützt, als es im Bot Framework zu finden ist. Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen unterstützt: `signin` und `openUrl` .

Die Signin-Aktion kann von jeder Karte in Teams verwendet werden, nicht nur von der Anmeldekarte. Weitere Informationen zur Authentifizierung finden Sie unter [Microsoft Teams Authentifizierungsablauf für Bots](~/bots/how-to/authentication/auth-flow-bot.md).

### <a name="support-for-signin-cards"></a>Unterstützung für Signin-Karten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Zusätzliche Informationen zu Anmeldekarten

Referenz für Bot Framework:

* [Anmeldekarte Node.js](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Anmeldekarte C #](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Thumbnail-Karte

Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.

### <a name="support-for-thumbnail-cards"></a>Unterstützung für Miniaturkarten

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Eigenschaften einer Miniaturansichtskarte

| Eigenschaft | Typ  | Beschreibung |
| --- | --- | --- |
| title | Rich-Text  | Titel der Karte. Maximal 2 Zeilen.|
| Untertitel | Rich-Text  | Untertitel der Karte. Maximal 2 Zeilen.|
| text | Rich-Text  | Text wird unter dem Untertitel angezeigt. Formatierungsoptionen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md). |
| Bilder | Array von Bildern | Bild oben auf der Karte angezeigt. Seitenverhältnis 1:1 Quadrat. |
| Schaltflächen | Array von Aktionsobjekten | Satz von Aktionen, die für die aktuelle Karte gelten. Maximal 6. |
| Tippen | Action-Objekt | Aktiviert, wenn der Benutzer auf die Karte selbst tippt. |

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

Referenz für Bot Framework:

* [Thumbnail-Karte Node.js](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Thumbnail-Karte C #](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Kartensammlungen

Teams unterstützt Kartensammlungen.

Kartensammlungen umfassen `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` . Diese Sammlungen enthalten adaptive, Helden- oder Miniaturkarten.

## <a name="carousel-collection"></a>Karussell-Kollektion

Das [Karussell-Layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell von Karten, optional mit zugehörigen Aktionstasten.

### <a name="support-for-carousel-collections"></a>Unterstützung für Karussell-Sammlungen

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.

### <a name="properties-of-a-carousel-card"></a>Eigenschaften einer Karussellkarte

Die Eigenschaften einer Karussellkarte sind mit denen der Helden- und Miniaturkarten identisch.

### <a name="example-of-a-carousel-collection"></a>Beispiel einer Karussellsammlung

![Beispiel für ein Kartenkarussell](~/assets/images/cards/carousel.png)

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

Das Listenlayout zeigt eine vertikal gestapelte Kartenliste, optional mit zugehörigen Aktionsschaltflächen.

| Bots in Teams | Messaging-Erweiterungen  | Connectors | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-list-collection"></a>Beispiel für eine Listenauflistung

![Beispiel für eine Kartenliste](~/assets/images/cards/list.png)

Die Eigenschaften sind die gleichen wie für die Helden- oder Miniaturansichtskarte.

Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.

> [!NOTE]
> Einige Kombinationen von Listenkarten werden auf iOS und Android noch nicht unterstützt.

### <a name="syntax-for-list-collections"></a>Syntax für Listensammlungen

`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.

## <a name="cards-not-supported-in-teams"></a>Karten, die in Teams nicht unterstützt werden

Die folgenden Karten werden vom Bot Framework implementiert, werden jedoch nicht von Teams unterstützt:

* Animationskarten
* Audiokarten
* Grafikkarten
