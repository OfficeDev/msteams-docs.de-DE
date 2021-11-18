---
title: Typaheadsuche in adaptiven Karten
author: Rajeshwari-v
description: Beschreibt die Typaheadsuche mit dem Input.ChoiceSet-Steuerelement in adaptiven Karten
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 95041b1a24ac083329a809b8a5989d77e2430e26
ms.sourcegitcommit: e45742fd2aa2ff5e5c15e8f7c20cc14fbef6d441
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2021
ms.locfileid: "61075583"
---
# <a name="typeahead-search-in-adaptive-cards"></a>Typaheadsuche in adaptiven Karten

Die Suchfunktion "Typeahead" in adaptiven Karten bietet eine erweiterte Suchumgebung für `input.choiceset` Komponenten. Es enthält eine Liste der Auswahlmöglichkeiten zum Eingeben von Text in das Suchfeld. Sie können die Typaheadsuche mit adaptiven Karten integrieren, um Daten zu suchen und auszuwählen.

Sie können die Typaheadsuche für die folgenden Suchvorgänge verwenden:

* [Statische Suche](#static-typeahead-search)
* [Dynamische Suche](#dynamic-typeahead-search)

## <a name="static-typeahead-search"></a>Statische Typaheadsuche

Mit der statischen Typaheadsuche können Benutzer anhand von Werten suchen, die in der Nutzlast der adaptiven Karte angegeben `input.choiceset` sind. Die statische Typaheadsuche kann verwendet werden, um dem Benutzer mehrere Auswahlmöglichkeiten anzuzeigen. Die Nutzlastgröße in der statischen Suche nimmt mit der Anzahl der in der Nutzlast angegebenen Auswahlmöglichkeiten zu.
Wenn der Benutzer mit der Eingabe der Texte beginnt, werden die Auswahlmöglichkeiten gefiltert, die teilweise mit der Eingabe übereinstimmen. In der Dropdownliste werden die Eingabezeichen hervorgehoben, die der Suche entsprechen.

Die folgende Abbildung zeigt die statische Typaheadsuche:

![Statische Typaheadsuche](~/assets/images/Cards/static-typeahead-search.gif)

## <a name="dynamic-typeahead-search"></a>Dynamische Typaheadsuche

Die dynamische Typaheadsuche ist nützlich, um Daten aus großen Datasets zu suchen und auszuwählen. Die Datensätze werden dynamisch aus dem in der Kartennutzlast angegebenen Dataset geladen. Die Funktionalität "Typ voraus" hilft beim Herausfiltern der Vom Benutzer eingegebenen Auswahlmöglichkeiten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Dynamische Typaheadsuche](~/assets/images/Cards/dynamic-typeahead-search-desktop.png)

![Dynamische Typahead-Suchbild 2](~/assets/images/Cards/dynamic-typeahead-search-desktop-2.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

Mobile Android- und iOS-Clients unterstützen die Typaheadsuche in adaptiven Karten.

**Szenario**

John ist ein Store-Mitarbeiter, der in einem Xbox-Einzelhandelsgeschäft arbeitet. Der Store verwendet einen Bot, um neue Kaufanforderungen von Kunden zu übernehmen. Ein Kunde kann aus den Tausenden von verfügbaren Spielen suchen. Die Typaheadsuche in adaptiven Karten wird verwendet, um die Auswahlmöglichkeiten von Kunden zu suchen und auszuwählen.

**So verwenden Sie die Typaheadsuche in adaptiven Karten**

1. Benutzer A öffnet den Store-Bot.
1. Benutzer A sendet einen Befehl an den Bot für eine **Neue Kundenanfrage.** Der Bot antwortet mit der adaptiven Karte, die `Input.ChoiceSet` über eine Komponente verfügt.
1. Benutzer A verwendet die Typaheadsuche, um die Informationen basierend auf der Wahl des Kunden zu suchen und auszuwählen.

Die folgende Abbildung veranschaulicht die mobile Erfahrung der Typaheadsuche:

![Statische Typaheadsuche](~/assets/images/Cards/static-typeahead-search.gif)

---

> [!NOTE]
> Mit der dynamischen Suche, z. B. abfragebasierten Messaging-Erweiterungen, können Sie keine umfangreichen Kartenfunktionen abrufen.

## <a name="implement-typeahead-search"></a>Implementieren der Typaheadsuche

`Input.ChoiceSet` ist eine der wichtigen Eingabekomponenten in adaptiven Karten. Sie können ein Typeahead-Suchsteuerelement zur `Input.ChoiceSet` Komponente hinzufügen, um die Typaheadsuche zu implementieren. Sie können die erforderlichen Informationen mit der folgenden Auswahl durchsuchen und auswählen:

* Dropdown, z. B. erweiterte Auswahl.
* Optionsfeld, z. B. einzelne Auswahl.
* Kontrollkästchen, z. B. Mehrfachauswahl.

> [!NOTE]
> Das `Input.ChoiceSet` Steuerelement basiert auf der Formatvorlage und den `isMultiSelect` Eigenschaften.

### <a name="schema-properties"></a>Schemaeigenschaften

Die folgenden Eigenschaften sind die neuen Ergänzungen des [`Input.ChoiceSet`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Schemas, um die Typaheadsuche zu aktivieren:

| Eigenschaft| Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| style | Compact <br/> Erweitert <br/> Filtered | Nein | Fügt der Liste der unterstützten Überprüfungen für statische Typen eine gefilterte Formatvorlage hinzu.|
| choices.data | Data.Query | Nein | Ermöglicht dynamisches Vorausgehen beim Eingeben von Benutzern, indem eine Remoteauswahl aus einem Back-End abgerufen wird. |

### <a name="dataquery-definition"></a>Data.Query-Definition

| Eigenschaft| Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| Typ | Data.Query | Ja | Gibt an, dass es sich um ein Data.Query-Objekt handelt.|
| Dataset | Zeichenfolge | Ja | Gibt den Datentyp an, der dynamisch abgerufen wird. |
| value | Zeichenfolge | Nein | Füllt die Aufrufanforderung an den Bot mit der Eingabe auf, die der Benutzer für die `ChoiceSet` bereitgestellt hat. |
| count | Zahl | Nein | Füllt die Aufrufanforderung an den Bot auf, um die Anzahl der Elemente anzugeben, die zurückgegeben werden müssen. Der Bot ignoriert ihn, wenn die Benutzer einen anderen Betrag senden möchten. | 
| skip | Zahl | Nein | Füllt die Aufrufanforderung an den Bot auf, um anzugeben, dass Benutzer in der Liste paginieren und fortfahren möchten. |

### <a name="example"></a>Beispiel

Die Beispielnutzlast, die die statische und dynamische Typaheadsuche mit einzelnen & Multiauswahloptionen wie folgt enthält:

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "columns": [
        {
          "width": "1",
          "items": [
            {
              "size": null,
              "url": "https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fi.imgur.com%2fhdOYxT8.png",
              "height": "auto",
              "type": "Image"
            }
          ],
          "type": "Column"
        },
        {
          "width": "2",
          "items": [
            {
              "size": "extraLarge",
              "text": "Game Purchase",
              "weight": "bolder",
              "wrap": true,
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "text": "Please fill out the below form to send a game purchase request.",
      "wrap": true,
      "type": "TextBlock"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Game: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "stretch",
          "items": [
            {
              "choices": [
                {
                  "title": "Call of Duty",
                  "value": "call_of_duty"
                },
                {
                  "title": "Death's Door",
                  "value": "deaths_door"
                },
                {
                  "title": "Grand Theft Auto V",
                  "value": "grand_theft"
                },
                {
                  "title": "Minecraft",
                  "value": "minecraft"
                }
              ],
              "style": "filtered",
              "placeholder": "Search for a game",
              "id": "choiceGameSingle",
              "type": "Input.ChoiceSet"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Multi-Game: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "stretch",
          "items": [
            {
              "choices": [
                {
                  "title": "Static Option 1",
                  "value": "static_option_1"
                },
                {
                  "title": "Static Option 2",
                  "value": "static_option_2"
                },
                {
                  "title": "Static Option 3",
                  "value": "static_option_3"
                }
              ],
              "isMultiSelect": true,
              "style": "filtered",
              "choices.data": {
                "type": "Data.Query",
                "dataset": "xbox"
              },
              "id": "choiceGameMulti",
              "type": "Input.ChoiceSet"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "columns": [
        {
          "width": "auto",
          "items": [
            {
              "text": "Needed by: ",
              "wrap": true,
              "height": "stretch",
              "type": "TextBlock"
            }
          ],
          "type": "Column"
        },
        {
          "width": "stretch",
          "items": [
            {
              "id": "choiceDate",
              "type": "Input.Date"
            }
          ],
          "type": "Column"
        }
      ],
      "type": "ColumnSet"
    },
    {
      "text": "Buy and download digital games and content directly from your Xbox console, Windows 10 PC, or at Xbox.com.",
      "wrap": true,
      "type": "TextBlock"
    },
    {
      "text": "Earn points for what you already do on Xbox, then redeem your points on real rewards. Play more, get rewarded. Start earning today.",
      "wrap": true,
      "type": "TextBlock"
    }
  ],
  "actions": [
    {
      "data": {
        "msteams": {
          "type": "invoke",
          "value": {
            "type": "task/submit"
          }
        }
      },
      "title": "Request Purchase",
      "type": "Action.Submit"
    }
  ],
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "version": "1.2"
}
```

## <a name="see-also"></a>Weitere Informationen

* [Universal-Aktionen für adaptive Karten](Universal-actions-for-adaptive-cards/Overview.md)
* [Aufgabenmodule](../what-are-task-modules.md)