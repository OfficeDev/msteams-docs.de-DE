---
title: Formatieren von Bot-Nachrichten
author: clearab
description: Hinzufügen von reichhaltigen Formatierungen zu Botnachrichten
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 39b82e78e061653eaa3e3b66c10a611d005924bd
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697004"
---
# <a name="format-your-bot-messages"></a>Formatieren von Bot-Nachrichten

Mit der Nachrichtenformatierung können Sie das Beste in Botnachrichten herausbringen. Sie können Ihre Botnachrichten so formatieren, dass sie umfangreiche Karten enthalten, die Anlagen sind, die interaktive Elemente enthalten, z. B. Schaltflächen, Text, Bilder, Audio, Video und so weiter.

## <a name="format-text-content"></a>Formatieren von Textinhalten

Zum Formatieren Ihrer Botnachrichten können Sie die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Botnachricht [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| `TextFormat` value | Beschreibung |
| --- | --- |
| plain | Der Text muss als Unformatierung ohne Formatierung behandelt werden.|
| MARKDOWN | Der Text muss als Markdownformatierung behandelt und entsprechend auf dem Kanal gerendert werden. |
| xml | Der Text ist einfaches XML-Markup. |

Teams unterstützt eine Teilmenge von Markdown- und XML- oder HTML-Formatierungstags.

Derzeit gelten die folgenden Einschränkungen für die Formatierung:

* Nur Textnachrichten unterstützen keine Tabellenformatierung.
* Rich Cards unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln.
* Rich Cards unterstützen keine Markdown- oder Tabellenformatierung.

Nachdem Sie Textinhalte formatiert haben, stellen Sie sicher, dass Ihre Formatierung auf allen von Microsoft Teams unterstützten Plattformen funktioniert.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Einige Formatvorlagen werden derzeit nicht auf allen Plattformen unterstützt. Die folgende Tabelle enthält eine Liste der Formatvorlagen und welche dieser Formatvorlagen in nur Textnachrichten und Rich Cards unterstützt werden:

| Format                     | Nur-Text-Nachrichten | Rich Cards – nur XML |
| ---                       | :---: | :---: |
| Fett                      | ✔ | ✖ |
| Kursiv                    | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✔ |
| Durchgestrichen             | ✖ | ✔ |
| Horizontales Lineal           | ✖ | ✖ |
| Unsortierte Liste            | ✖ | ✔ |
| Sortierte Liste              | ✖ | ✔ |
| Vorformatierter Text         | ✔ | ✔ |
| Blockquote                | ✔ | ✔ |
| Hyperlink                 | ✔ | ✔ |
| Bildlink                | ✔ | ✖ |

Stellen Sie nach dem Überprüfen der plattformübergreifenden Unterstützung sicher, dass auch die Unterstützung durch einzelne Plattformen verfügbar ist.

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung für die Textformatierung variiert je nach Art der Nachricht und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

Die folgende Tabelle enthält eine Liste der Formatvorlagen und welche dieser Formatvorlagen auf Desktop, iOS und Android unterstützt werden:

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| Fett                      | ✔ | ✔ | ✔ |
| Kursiv                    | ✔ | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✖ | ✖ |
| Durchgestrichen             | ✔ | ✔ | ✖ |
| Horizontales Lineal           | ✖ | ✖ | ✖ |
| Unsortierte Liste            | ✔ | ✖ | ✖ |
| Sortierte Liste              | ✔ | ✖ | ✖ |
| Vorformatierter Text         | ✔ | ✔ | ✔ |
| Blockquote                | ✔ | ✔ | ✔ |
| Hyperlink                 | ✔ | ✔ | ✔ |
| Bildlink                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Kartenunterstützung finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Nachrichten aktualisieren und löschen](~/bots/how-to/update-and-delete-bot-messages.md)
