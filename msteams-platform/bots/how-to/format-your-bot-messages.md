---
title: Formatieren von Bot-Nachrichten
author: surbhigupta
description: Fügen Sie Ihren Bot-Nachrichten umfangreiche Formatierungen hinzu, z. B. Durchgestrichen, sortierte und ungeordnete Liste, Link, Bildlink und mehr.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: d8697cf25b0cc08f880f8849ea152d1c30d4c146
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111828"
---
# <a name="format-your-bot-messages"></a>Formatieren von Bot-Nachrichten

Mithilfe der Nachrichtenformatierung können Sie das Beste der Bot-Nachrichten hervorheben. Sie können Ihre Bot-Nachrichten so formatieren, dass sie funktionsreiche Karten enthalten, d. h. Anlagen, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten.

## <a name="format-text-content"></a>Formatieren von Textinhalten

Um Ihre Bot-Nachrichten zu formatieren, können Sie die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message)-Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Bot-Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| `TextFormat`-Wert | Beschreibung |
| --- | --- |
| PLAIN | Der Text muss als Rohtext ohne Formatierung behandelt werden.|
| MARKDOWN | Der Text muss als Markdown-formatiert behandelt und entsprechend im Kanal gerendert werden. |
| XML | Der Text ist einfaches XML-Markup. |

Teams unterstützt eine Reihe von Markdown- und XML- oder HTML-Formatierungstags.

Derzeit gelten die folgenden Einschränkungen für die Formatierung:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung.
* Funktionsreiche Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Funktionsreiche Karten unterstützen keine Markdown- oder Tabellenformatierung.

Stellen Sie nach dem Formatieren von Textinhalten sicher, dass die Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden.

## <a name="cross-platform-support"></a>Plattformübergreifender Support

Einige Formatvorlagen werden derzeit nicht auf allen Plattformen unterstützt. Die folgende Tabelle enthält eine Liste der Formatvorlagen, und welche dieser Formatvorlagen in Nur-Text-Nachrichten und funktionsreichen Karten unterstützt werden:

| Format                     | Nur-Text-Nachrichten | Funktionsreiche Karten – nur XML |
| ---                       | :---: | :---: |
| Fett                      | ✔ | ✖ |
| Kursiv                    | ✔ | ✔ |
| Header (Stufe 1&ndash;3) | ✖ | ✔ |
| Durchgestrichen             | ✖ | ✔ |
| Horizontales Lineal           | ✖ | ✖ |
| Unsortierte Liste            | ✖ | ✔ |
| Sortierte Liste              | ✖ | ✔ |
| Vorformatierter Text         | ✔ | ✔ |
| Blockzitat                | ✔ | ✔ |
| Hyperlink                 | ✔ | ✔ |
| Bildverknüpfung                | ✔ | ✖ |

Stellen Sie nach Überprüfung des plattformübergreifenden Supports sicher, dass auch die Unterstützung einzelner Plattformen verfügbar ist.

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung der Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

Die folgende Tabelle enthält eine Liste der Formatvorlagen, die unter Desktop, iOS und Android unterstützt werden:

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| Fett                      | ✔ | ✔ | ✔ |
| Kursiv                    | ✔ | ✔ | ✔ |
| Header (Stufe 1&ndash;3) | ✖ | ✖ | ✖ |
| Durchgestrichen             | ✔ | ✔ | ✖ |
| Horizontales Lineal           | ✖ | ✖ | ✖ |
| Unsortierte Liste            | ✔ | ✖ | ✖ |
| Sortierte Liste              | ✔ | ✖ | ✖ |
| Vorformatierter Text         | ✔ | ✔ | ✔ |
| Blockzitat                | ✔ | ✔ | ✔ |
| Hyperlink                 | ✔ | ✔ | ✔ |
| Bildverknüpfung                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Informationen zur Kartenunterstützung finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Nachrichten aktualisieren und löschen](~/bots/how-to/update-and-delete-bot-messages.md)
