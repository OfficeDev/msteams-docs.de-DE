---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 86b5bdea89f49f6e98ce84920e3fbe1cdb4f378e
ms.sourcegitcommit: 781f34af2a95952bf437d0b7236ae995f4e14a08
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60948642"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Entwerfen adaptiver Karten für Ihre Microsoft Teams-App

Eine adaptive Karte enthält einen Freihandform-Textkörper mit Kartenelementen und optionalen Aktionen. Adaptive Karten sind Aktionen erfordernde Inhaltsausschnitte, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen ermöglichen diese Karten eine umfassende Kommunikation mit Ihrer Zielgruppe.

Das Framework für adaptive Karten wird in vielen Microsoft-Produkten verwendet, einschließlich Microsoft Teams. Sie können Karten in Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden. Benutzer können auch Aktionen auf Karten durchführen, wenn diese bereitgestellt werden.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel für eine adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für adaptive Karten, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit. Das UI-Kit deckt auch wesentliche Themen wie Designs, Barrierefreiheit und dynamische Größenanpassung ab.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer für adaptive Karten

Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.

> [!div class="nextstepaction"]
> [Designer für adaptive Karten testen](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Typen von adaptiven Karten

### <a name="hero"></a>Hero

Unsere größte Karte. Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte erzählt.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte." border="false":::

### <a name="thumbnail"></a>Miniaturansicht

Wird zum Senden einer einfachen, Aktionen erfordernden Nachricht verwendet.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte." border="false":::

### <a name="list"></a>Liste

Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erklärung benötigen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Beispiel einer adaptiven Listenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel einer adaptiven Listenkarte." border="false":::

### <a name="digest"></a>Digest

Wird für News-Digests und Round-Up-Beiträge verwendet. Hinweis: Wir empfehlen ein einzelnes Update oder Newselement der Miniaturansichtskarte.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Beispiel einer adaptiven Digestkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Beispiel einer adaptiven Digestkarte." border="false":::

### <a name="media"></a>Medien

Wird verwendet, wenn Sie Text und Medien kombinieren möchten, z. B. Audio oder Video.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Beispiel einer adaptiven Medienkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel einer adaptiven Medienkarte." border="false":::

### <a name="people"></a>Personen

Am besten geeignet, wenn Sie effizient vermitteln möchten, wer an einer Aufgabe beteiligt ist.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Beispiel einer adaptiven Personenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel einer adaptiven Personenkarte." border="false":::

### <a name="request-ticket"></a>Anforderungsticket

Wird verwendet, um von einem Benutzer schnelle Eingaben zum automatischen Erstellen einer Aufgabe oder eines Tickets zu erhalten.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte." border="false":::

### <a name="imageset"></a>ImageSet

Wird verwendet, um mehrere Miniaturansichten von Bildern zu senden.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte." border="false":::

### <a name="actionset"></a>ActionSet

Wird verwendet, wenn der Benutzer eine Schaltfläche auswählen soll, und Sie dann zusätzliche Benutzereingaben über dieselbe Karte erfassen möchten.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte." border="false":::

### <a name="choiceset"></a>ChoiceSet

Wird verwendet, um mehrere Eingaben vom Benutzer zu erfassen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte." border="false":::

## <a name="anatomy"></a>Anatomie

Adaptive Karten sind sehr flexibel. Es wird jedoch dringend empfohlen, mindestens die folgenden Komponenten auf jeder Karte zu verwenden.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten auf einem Mobilgerät." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Kopfzeile**: Sorgen Sie dafür, dass Ihre Kopfzeilen klar und präzise sind.|
|B|**Textkörper**: Übermitteln Sie hier Details, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile aufzunehmen.|
|C|**Primäre Aktionen**: Schließen Sie als bewährte Methode 1 bis 3 primäre Aktionen ein. Es können bis zu sechs eingefügt werden.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Kopfzeile**: Sorgen Sie dafür, dass Ihre Kopfzeilen klar und präzise sind.|
|B|**Textkörper**: Übermitteln Sie hier Details, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile aufzunehmen.|
|C|**Primäre Aktionen**: Schließen Sie als bewährte Methode 1 bis 3 primäre Aktionen ein. Es können bis zu sechs eingefügt werden.|

## <a name="best-practices"></a>Bewährte Methoden

Karten, die für eine schmale Bildschirmskalierung auf breiteren Bildschirmen konzipiert sind (das Gegenteil ist nicht der Fall). Sie sollten auch davon ausgehen, dass Benutzer Ihre Karten nicht nur auf dem Desktop anzeigen.

### <a name="column-layouts"></a>Spaltenlayouts

Dient [`ColumnSet`](https://adaptivecards.io/explorer/ColumnSet.html) zum Formatieren des Karteninhalts in eine Tabelle oder ein Raster. Es gibt mehrere Optionen zum Formatieren der Spaltenbreite. Diese Richtlinien helfen Ihnen zu verstehen, wann sie jeweils verwendet werden.

* `"width": "auto"`: Passt die Größe jeder Spalte in der `ColumnSet` Anpassung an den App-Inhalt an, den Sie in diese Spalte einschließen.
   * **Do:** Verwenden Sie dies, wenn Sie Inhalte mit unterschiedlicher Breite haben und eine bestimmte Spalte nicht priorisieren müssen.
   * **Do**: Für jede `TextBlock`, legen Sie `"wrap": true` fest, da Text standardmäßig nicht umbrochen wird.
   * **Don‘t**: Legen Sie `"width": "auto"` für jeden Spaltencontainer fest. Wenn Sie beispielsweise eine Eingabe und eine Schaltfläche nebeneinander haben, wird die Schaltfläche möglicherweise auf einigen Bildschirmen abgeschnitten. Legen Sie stattdessen `auto` für die Spalte mit Schaltflächen und anderen Inhalten fest, die immer vollständig sichtbar sein müssen.
* `"width": "stretch"`: Ändert die Spaltengröße basierend auf der verfügbaren `ColumnSet`-Breite. Wenn mehrere Spalten den `"stretch"`-Wert verwenden, teilen sie sich gleichermaßen die verfügbare Breite.
   * **Do**: Verwenden Sie eine Spalte, wenn alle anderen Spalten eine statische Breite haben. Beispielsweise haben Sie Miniaturbilder in einer Spalte, die alle 50 Pixel breit sind.
* `"width": "<number>"`: Ändert die Größe von Spalten mit einem Anteil der verfügbaren `ColumnSet`-Breite. Wenn Sie beispielsweise drei Spalten mit `"width": "1"`, `"width": "4"` und `"width": "5"`festlegen, nehmen die Spalten 10, 40 und 50 Prozent der verfügbaren Breite in Anspruch.
* `"width": "<number>px"`: Passt die Spaltengröße auf eine bestimmte Pixelbreite an. Dieser Ansatz ist beim Erstellen von Tabellen nützlich.
   * **Do**: Verwenden Sie diese Einstellung, wenn sich die Breite der Anzeige nicht ändern muss (z. B. Zahlen und Prozentsätze).
   * **Don‘t**: Versehentlich die Breite der Anzeige der Karte überschreiten. Beachten Sie, dass die verfügbare Bildschirmbreite vom Gerät abhängt. Teams Mobile unterstützt auch kein horizontales Scrollen wie Teams Desktop.

#### <a name="example-knowing-when-to-stretch-columns"></a>Beispiel: Wissen, wann Spalten gestreckt werden sollen

# <a name="design"></a>[Entwerfen](#tab/design)

**Do**: Auf diesem Bildschirm befinden sich am unteren Rand der Karte zwei Spalten. Die Breite der Eingabekomponente wird auf `stretch` festgelegt, während die die Breite der Schaltfläche **Auswählen** auf `auto` festgelegt ist. Dadurch wird sichergestellt, dass die Schaltfläche vollständig angezeigt wird.

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-do.png" alt-text="Abbildung zeigt, wie die Spaltenbreite in adaptiven Karten festgelegt wird.":::

**Don‘t**: Auf diesem Bildschirm haben beide Spalten `width` auf `auto` festgelegt. Dadurch wird die Schaltfläche **Auswählen** auf der rechten Seite im Vergleich zur Eingabe leicht abgeschnitten.

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-dont.png" alt-text="Abbildung zeigt, wie die Spaltenbreite in adaptiven Karten nicht festgelegt wird.":::

# <a name="code"></a>[Code](#tab/code)

Hier ist der Code für die Implementierung des Entwurfsbeispiels, dem Sie folgen sollten.

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.2",
  "body": [
    {
      "type": "TextBlock",
      "text": "I wasn't able to identify the type of expense. Select from the list:",
      "wrap": true,
      "id": "typePrompt",
      "spacing": "Medium",
      "size": "Medium"
    },
    {
      "type": "ActionSet",
      "actions": [
        {
          "type": "Action.Submit",
          "title": "Phone Bill",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Phone Bill",
              "action": "Phone Bill"
            },
            "action": "Phone Bill"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Taxi and Other Transportation",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Taxi and Other Transportation",
              "action": "Taxi and Other Transportation"
            },
            "action": "Taxi and Other Transportation"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Entertainment_misc",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Entertainment_misc",
              "action": "Entertainment_misc"
            },
            "action": "Entertainment_misc"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Car Rental",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Car Rental",
              "action": "Car Rental"
            },
            "action": "Car Rental"
          }
        },
        {
          "type": "Action.Submit",
          "title": "Airfare",
          "data": {
            "msteams": {
              "type": "messageBack",
              "displayText": "Airfare",
              "action": "Airfare"
            },
            "action": "Airfare"
          }
        }
      ],
      "spacing": "Medium"
    },
    {
      "type": "TextBlock",
      "text": "     ",
      "wrap": true
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "Input.ChoiceSet",
              "choices": [
                {
                  "title": "Meals",
                  "value": "Meals"
                },
                {
                  "title": "Parking/Tolls",
                  "value": "Parking/Tolls"
                },
                {
                  "title": "Accomodation",
                  "value": "Accomodation"
                },
                {
                  "title": "Fuel-Gas/Petrol/Diesel",
                  "value": "Fuel-Gas/Petrol/Diesel"
                },
                {
                  "title": "Hotel",
                  "value": "Hotel"
                },
                {
                  "title": "Meals - Employees Only",
                  "value": "Meals - Employees Only"
                },
                {
                  "title": "Accomodations",
                  "value": "Accomodations"
                },
                {
                  "title": "Misc.Expenses",
                  "value": "Misc.Expenses"
                },
                {
                  "title": "Please Categorize",
                  "value": "Please Categorize"
                }
              ],
              "placeholder": "All",
              "id": "expenseTypes",
              "value": "Meals - Employees Only"
            }
          ]
        },
        {
          "type": "Column",
          "width": "auto",
          "items": [
            {
              "type": "ActionSet",
              "actions": [
                {
                  "type": "Action.Submit",
                  "title": "Select",
                  "data": {
                    "msteams": {
                      "type": "messageBack",
                      "displayText": "Select",
                      "action": "applyType"
                    },
                    "action": "applyType"
                  }
                }
              ]
            }
          ]
        }
      ],
      "spacing": "ExtraLarge"
    }
  ]
}
```

---

#### <a name="example-using-fewer-columns"></a>Beispiel: Verwenden weniger Spalten

**Do**: Layouts werden auf Mobilgeräten mit weniger Spalten in der Regel besser angezeigt.

:::image type="content" source="~/assets/images/adaptive-cards/column-amount-do.png" alt-text="Abbildung zeigt die richtige Spaltenmenge in adaptiven Karten.":::

**Don't**: Die Verwendung zu vieler Spalten kann Ihre Karteninhalte auf Mobilgeräten überladen.

:::image type="content" source="~/assets/images/adaptive-cards/column-amount-dont.png" alt-text="Abbildung zeigt, wie sich zu viele Spalten negativ auf das Layout der adaptiven Karten auswirken können.":::

#### <a name="example-fixed-width-has-its-place"></a>Beispiel: Feste Breite hat ihre Position

# <a name="design"></a>[Entwerfen](#tab/design)

Wenn sich die Größe von etwas, das Sie anzeigen, nicht ändern muss, legen Sie die Spalten auf eine bestimmte Pixelbreite fest. Dieses Beispiel zeigt die linke Spalte mit einer Größe von 50 Pixeln, während die Beschreibungen neben den Miniaturbildern die Länge der Karte strecken

:::image type="content" source="~/assets/images/adaptive-cards/width-auto-do.png" alt-text="Abbildung zeigt, wie die Spaltenbreite in adaptiven Karten festgelegt wird.":::

# <a name="code"></a>[Code](#tab/code)

Hier ist der Code für die Implementierung des Entwurfsbeispiels.

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "text": "Pick up where you left off?",
      "weight": "bolder"
    },
    {
      "type": "ColumnSet",
      "spacing": "medium",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1083",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "TextBlock",
              "text": "Silver Star Mountain Range"
            },
            {
              "type": "TextBlock",
              "text": "Maps",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.msn.com"
      }
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1082",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "style": "emphasis",
          "items": [
            {
              "type": "TextBlock",
              "text": "Kitchen Remodel for Homes"
            },
            {
              "type": "TextBlock",
              "text": "With EMPHASIS",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.AdaptiveCards.io"
      }
    },
    {
      "type": "ColumnSet",
      "columns": [
        {
          "type": "Column",
          "width": "50px",
          "items": [
            {
              "type": "Image",
              "url": "https://unsplash.it/80?image=1080",
              "size": "medium"
            }
          ]
        },
        {
          "type": "Column",
          "width": "stretch",
          "items": [
            {
              "type": "TextBlock",
              "text": "The Witcher: A Series"
            },
            {
              "type": "TextBlock",
              "text": "Netflix",
              "isSubtle": true,
              "spacing": "none"
            }
          ]
        }
      ],
      "selectAction": {
        "type": "Action.OpenUrl",
        "url": "https://www.outlook.com"
      }
    }
  ],
  "actions": [
    {
      "type": "Action.OpenUrl",
      "title": "Resume all",
      "url": "ms-cortana:resume-all"
    },
    {
      "type": "Action.OpenUrl",
      "title": "More activities",
      "url": "ms-cortana:more-activities"
    }
  ]
}
```

---

### <a name="text"></a>Text

Unabhängig davon, ob Sie [`TextBlock`](https://adaptivecards.io/explorer/TextBlock.html), [`ColumnSet`](https://adaptivecards.io/explorer/ColumnSet.html) oder [`Input.ChoiceSet`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) verwenden, legen Sie die `wrap`-Eigenschaft auf `true` fest, damit Ihr Kartentext auf Mobilgeräten nicht abgeschnitten wird.

#### <a name="example-making-sure-text-doesnt-truncate"></a>Beispiel: Sicherstellen, dass Text nicht abgeschnitten wird

# <a name="design"></a>[Entwerfen](#tab/design)

**Do**: Auf diesem Bildschirm ist auf der Karte eine `wrap`-Eigenschaft auf `true` festgelegt. Dadurch kann der Text an eine beliebige Bildschirmgröße angepasst werden.

:::image type="content" source="~/assets/images/adaptive-cards/text-wrap-true.png" alt-text="Abbildung zeigt, wie Text in adaptiven Karten umbrochen wird.":::

**Don‘t**: Auf diesem Bildschirm verwendet die Karte nicht die `wrap`-Eigenschaft, sodass der Text auf dem Bildschirm eines Mobilgeräts abgeschnitten wird.

:::image type="content" source="~/assets/images/adaptive-cards/text-wrap-false.png" alt-text="Abbildung zeigt, was passieren kann, wenn Sie Text nicht in adaptiven Karten umbrechen.":::

# <a name="code"></a>[Code](#tab/code)

Hier ist der Code für die Implementierung des Entwurfsbeispiels, dem Sie folgen sollten.

```json
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "text": "What cuisine do you want?"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "myColor",
      "style": "compact",
      "isMultiSelect": false,
      "value": "1",
      "choices": [
        {
          "title": "Chineese",
          "value": "1"
        },
        {
          "title": "Indian",
          "value": "2"
        },
        {
          "title": "Italian",
          "value": "3"
        }
      ]
    },
    {
      "type": "TextBlock",
      "text": "Select the dishes that you like?"
    },
    {
      "type": "Input.ChoiceSet",
      "id": "myColor2",
      "style": "expanded",
      "wrap" : true,
      "isMultiSelect": false,
      "value": "1",
      "choices": [
        {
          "title": "Cauliflower with potatoes sautéed with garam masala",
          "wrap" : true,
          "value": "1"
        },
        {
          "title": "Patties of potato mixed with some vegetables fried",
          "wrap" : true,
          "value": "2"
        },
        {
          "title": "Green capsicum with potatoes sautéed with cumin seeds",
          "wrap" : true,
          "value": "3"
        }
      ]
    }
  ]
}
```

---

### <a name="containers"></a>Container

Mit einem `Container` können Sie eine Reihe verwandter Elemente gruppieren.

* **Do**: Verwenden Sie die `style`-Eigenschaft, um einen Container hervorzuheben.
* **Do**: Verwenden Sie die `selectAction`-Eigenschaft, um eine Aktion den anderen Elementen im Container zuzuordnen.
* **Do**: Verwenden Sie die `Action.ToggleVisibility`-Eigenschaft, um eine Gruppe von Elementen reduzierbar zu machen.
* **Don‘t**: Verwenden Sie Container aus einem anderen als dem zuvor erwähnten Grund.

### <a name="images"></a>Bilder

Befolgen Sie diese Richtlinien, wenn Sie Bilder in Ihre Karten einschließen.

* **Do**: Entwerfen Sie Bilder für Bildschirme mit hohem DPI-Wert, um Pixel zu vermeiden. Es ist besser, ein Bild mit 100x100 Pixeln bei 50x50 Pixeln anzuzeigen als umgekehrt.
* **Do**: Wenn Sie die genaue Größe Ihrer Bilder steuern müssen, verwenden Sie die Eigenschaften "`width`" und "`height`".
* **Don‘t**: Fügen Sie die Auffüllung in Ihre Bilder ein. Dies führt in der Regel zu unerwünschten Abständen und Layoutproblemen.
* In Bezug auf die Hintergrundfarbe:
   * **Do**: Verwenden Sie transparente Hintergründe, damit sich Ihre Bilder an jedes Teams-Design anpassen. 
   * **Don‘t**: Fügen Sie eine feste Hintergrundfarbe ein, es sei denn, eine bestimmte Farbe muss für Ihre Benutzer sichtbar sein.
   * **Don‘t**: Fügen Sie einer "`TextBlock`" eine Hintergrundfarbe hinzu, die die Lesbarkeit beeinträchtigt. Wenn Ihr Hintergrund z. B. dunkel ist, verwenden Sie eine hellere Textfarbe und umgekehrt.

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode: Eine adaptive Karte sollte nur eine kleine Gruppe von Aktionen enthalten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Was Sie tun sollten: bis zu sechs primäre Aktionen verwenden

Adaptive Karten unterstützen zwar bis zu sechs primäre Aktionen, auf den meisten Karten werden diese jedoch nicht benötigt. Aktionen sollten klar, präzise und unkompliziert sein. Weniger ist mehr.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode: Benutzer sollten nicht mit zu vielen Aktionen auf einer adaptiven Karte überfordert werden." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Was Sie nicht tun sollten: mehr als sechs primäre Aktionen verwenden

Adaptive Karten sollten schnelle, handlungsrelevante Inhalte präsentieren. Zu viele Aktionen können einen Benutzer überfordern.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Häufigkeit

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode bezüglich der Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a>Was Sie tun sollten: Präzise sein

Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten aus der Ansicht scrollen, werden sie weniger nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als „Rauschen“ wahrnehmen.

## <a name="see-also"></a>Siehe auch

* [Karten- und Aufgabenmodule](~/task-modules-and-cards/cards-and-task-modules.md)
* [Im Teams-Bot unterstützte Karten- und Aufgabenmodule](~/task-modules-and-cards/what-are-task-modules.md)
* [Mit Universal-Aktionen für adaptive Karten arbeiten](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/work-with-universal-actions-for-adaptive-cards.md)
* [Auf die Aktion zum Absenden des Aufgabenmoduls reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
* [Benutzerspezifische Ansichten](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/user-specific-views.md)
