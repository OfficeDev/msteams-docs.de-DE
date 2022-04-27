---
title: Vorausschauende Suche in Adaptiven Karten
author: Rajeshwari-v
description: Beschreibt die Typkopfsuche mit dem Input.ChoiceSet-Steuerelement in adaptiven Karten.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: d33fce44cbf1ff550d9aa21686111746318bb17e
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073795"
---
# <a name="typeahead-search-in-adaptive-cards"></a>Vorausschauende Suche in Adaptiven Karten

Die Typeahead-Suchfunktion in adaptiven Karten bietet eine erweiterte Sucherfahrung für `input.choiceset` die Komponente. Es enthält eine Liste der Auswahlmöglichkeiten zum Eingeben von Text in das Suchfeld. Sie können die Typkopfsuche mit adaptiven Karten integrieren, um Daten zu durchsuchen und auszuwählen.

Sie können die Typeahead-Suche für die folgenden Suchvorgänge verwenden:

* [Statische Suche](#static-typeahead-search)
* [Dynamische Suche](#dynamic-typeahead-search)

## <a name="static-typeahead-search"></a>Statische Typeaheadsuche

Mit der statischen Typeaheadsuche können Benutzer nach Werten suchen, die in `input.choiceset` der Nutzlast der adaptiven Karte angegeben sind. Die statische Typeaheadsuche kann verwendet werden, um dem Benutzer mehrere Auswahlmöglichkeiten anzuzeigen. Die Nutzlastgröße in der statischen Suche nimmt mit der Anzahl der in der Nutzlast angegebenen Auswahlmöglichkeiten zu.
Wenn der Benutzer mit der Eingabe der Texte beginnt, werden die Auswahlmöglichkeiten gefiltert, die teilweise mit der Eingabe übereinstimmen. In der Dropdownliste werden die Eingabezeichen hervorgehoben, die der Suche entsprechen.

Die folgende Abbildung veranschaulicht die statische Typeaheadsuche:

![Statische Typeaheadsuche](~/assets/images/Cards/static-typeahead-search.gif)

## <a name="dynamic-typeahead-search"></a>Dynamische Typeaheadsuche

Die dynamische Typeaheadsuche ist nützlich, um Daten aus großen Datensätzen zu durchsuchen und auszuwählen. Die Datensätze werden dynamisch aus dem in der Kartennutzlast angegebenen Dataset geladen. Die Typ-voraus-Funktionalität hilft, die Auswahlmöglichkeiten beim Eingeben durch den Benutzer herauszufiltern.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/Cards/dynamic-typeahead-search-desktop.png" alt-text="Dynamische Typeaheadsuche":::

:::image type="content" source="../../assets/images/Cards/dynamic-typeahead-search-desktop-2.png" alt-text="Dynamische Typeaheadsuche 2":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Mobile Android- und iOS-Clients unterstützen die Typkopfsuche in adaptiven Karten.

**Szenario**

John ist ein Store-Mitarbeiter, der in einem Xbox-Einzelhandelsgeschäft arbeitet. Der Store verwendet einen Bot, um neue Kaufanfragen von Kunden zu erhalten. Ein Kunde kann aus tausenden verfügbaren Spielen suchen. Die Typkopfsuche in adaptiven Karten wird verwendet, um die Auswahl der Kunden zu suchen und auszuwählen.

**So verwenden Sie die Typkopfsuche in adaptiven Karten**

1. Benutzer A öffnet den Store-Bot.
1. Benutzer A sendet einen Befehl für eine **Neue Kundenanfrage** an den Bot. Der Bot antwortet mit der adaptiven Karte, die über eine Komponente verfügt `Input.ChoiceSet` .
1. Benutzer A verwendet die Typkopfsuche, um die Informationen basierend auf der Auswahl des Kunden zu durchsuchen und auszuwählen.

Die folgende Abbildung veranschaulicht die mobile Erfahrung der Typeahead-Suche:

![Statische Typeaheadsuche](~/assets/images/Cards/static-typeahead-search.gif)

---

> [!NOTE]
> Mit der dynamischen Suche, z. B. abfragebasierten Messaging-Erweiterungen, können Sie keine umfangreichen Kartenfunktionen erhalten.

## <a name="implement-typeahead-search"></a>Implementieren der Typeahead-Suche

`Input.ChoiceSet` ist eine der wichtigen Eingabekomponenten in adaptiven Karten. Sie können der Komponente ein Typeahead-Suchsteuerelement `Input.ChoiceSet` hinzufügen, um die Typeahead-Suche zu implementieren. Sie können die erforderlichen Informationen mit den folgenden Auswahlmöglichkeiten suchen und auswählen:

* Dropdown, z. B. erweiterte Auswahl.
* Optionsfeld, z. B. einzelne Auswahl.
* Kontrollkästchen, z. B. Mehrfachauswahl.

> [!NOTE]
> Das `Input.ChoiceSet` Steuerelement basiert auf der Formatvorlage und `isMultiSelect` den Eigenschaften.

### <a name="schema-properties"></a>Schemaeigenschaften

Die folgenden Eigenschaften sind die neuen Ergänzungen des Schemas, um die [`Input.ChoiceSet`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) Typeahead-Suche zu aktivieren:

| Eigenschaft| Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| style | Compact <br/> Erweitert <br/> Filtered | Nein | Fügt der Liste der unterstützten Überprüfungen für statische Type-Ahead gefilterte Formatvorlagen hinzu.|
| choices.data | Data.Query | Nein | Ermöglicht dynamisches Vorausschreiben während der Benutzereingabe, indem ein Remotesatz von Auswahlmöglichkeiten aus einem Back-End abgerufen wird. |

### <a name="dataquery-definition"></a>Data.Query-Definition

| Eigenschaft| Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| Typ | Data.Query | Ja | Gibt an, dass es sich um ein Data.Query-Objekt handeln soll.|
| Dataset | Zeichenfolge | Ja | Gibt den Datentyp an, der dynamisch abgerufen wird. |
| value | Zeichenfolge | Nein | Füllt für die Aufrufanforderung an den Bot die Eingabe auf, die der Benutzer für die `ChoiceSet`bereitgestellt hat. |
| count | Zahl | Nein | Füllt die Aufrufanforderung an den Bot auf, um die Anzahl der Elemente anzugeben, die zurückgegeben werden müssen. Der Bot ignoriert dies, wenn die Benutzer einen anderen Betrag senden möchten. |
| skip | Zahl | Nein | Füllt die Aufrufanforderung an den Bot auf, um anzugeben, dass Benutzer paginieren und in der Liste vorankommen möchten. |

### <a name="example"></a>Beispiel

Die Beispielnutzlast mit statischer und dynamischer Typeaheadsuche mit einzelnen & Multiauswahloptionen wie folgt:

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

## <a name="code-snippets-for-invoke-request-and-response"></a>Codeausschnitte für Aufrufanforderung und -antwort

### <a name="invoke-request"></a>Aufrufanforderung

```json
{
    "name": "application/search",
    "type": "invoke",
    "value": {
        "queryText": "fluentui",
        "queryOptions": {
            "skip": 0,
            "top": 15
        },
        "dataset": "npm"
    },
    "locale": "en-US",
    "localTimezone": "America/Los_Angeles",
    // …. other fields
}
```

### <a name="response"></a>Antwort

#### <a name="c"></a>[C#](#tab/csharp)

```csharp
protected override async Task<InvokeResponse> OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
{
    if (turnContext.Activity.Name == "application/search")
    {
 var packages = new[] {
   new { title = "A very extensive set of extension methods", value = "FluentAssertions" },
   new { title = "Fluent UI Library", value = "FluentUI" }};

 var searchResponseData = new
 {
     type = "application/vnd.microsoft.search.searchResponse",
     value = new
     {
  results = packages
     }
 };
 var jsonString = JsonConvert.SerializeObject(searchResponseData);
 JObject jsonData = JObject.Parse(jsonString);
 return new InvokeResponse()
 {
     Status = 200,
     Body = jsonData
 };
    }

    return null;
}
```

#### <a name="nodejs"></a>[Node.js](#tab/nodejs)

```nodejs
  async onInvokeActivity(context) {
    if (context._activity.name == 'application/search') {
      // let searchQuery = context._activity.value.queryText;  // This can be used to filter the results
      var successResult = {
        status: 200,
        body: {
          "type": "application/vnd.microsoft.search.searchResponse",
          "value": {
            "results": [
              {
                "value": "FluentAssertions",
                "title": "A very extensive set of extension methods"
              },
              {
                "value": "FluentUI",
                "title": "Fluent UI Library"
              }
            ]
          }
        }
      }

      return successResult;

    }
  }
```

#### <a name="json"></a>[JSON](#tab/json)

```json
{
    "status": 200,
    "body" : {
        "type": "application/vnd.microsoft.search.searchResponse",
        "value": {
           "results": [
                {
                    "value": "FluentAssertions",
                    "title": "A very extensive set of extension methods."
                },
                {
                    "value": "FluentUI",
                    "title": "Fluent UI Library"
                }
            ]
        }
    }
}
```

---

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** | **C#** | **Node.js** |
|----------------|-----------------|--------------|----------------|
| Typeahead-Suchsteuerelement auf adaptiven Karten | Das Beispiel zeigt die Features des statischen und dynamischen Typeahead-Suchsteuerelements in adaptiven Karten. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-type-ahead-search-adaptive-cards/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-type-ahead-search-adaptive-cards/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Universal-Aktionen für adaptive Karten](Universal-actions-for-adaptive-cards/Overview.md)
* [Aufgabenmodule](../what-are-task-modules.md)
