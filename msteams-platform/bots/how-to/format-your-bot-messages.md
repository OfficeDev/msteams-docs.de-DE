---
title: Formatieren von Bot-Nachrichten
author: surbhigupta
description: Hinzufügen umfangreicher Formatierungen zu Ihren Bot-Nachrichten
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 1c5c4fc9190712e042398882ae95d31673fc0f37
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156446"
---
# <a name="format-your-bot-messages"></a>Formatieren von Bot-Nachrichten

Mithilfe der Nachrichtenformatierung können Sie die besten Botnachrichten bereitstellen. Sie können Ihre Bot-Nachrichten so formatieren, dass sie umfangreiche Karten enthalten, die Anlagen sind, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten.

## <a name="format-text-content"></a>Formatieren von Textinhalten

Um Ihre Bot-Nachrichten zu formatieren, können Sie die optionale Eigenschaft festlegen, [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) um zu steuern, wie der Textinhalt Ihrer Bot-Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| `TextFormat` Wert | Beschreibung |
| --- | --- |
| einfach | Der Text muss als Rohtext behandelt werden, ohne dass eine Formatierung angewendet wird.|
| MARKDOWN | Der Text muss als Markdownformatierung behandelt und entsprechend im Kanal gerendert werden. |
| Xml | Der Text ist einfaches XML-Markup. |

Teams unterstützt eine Teilmenge von Markdown- und XML- oder HTML-Formatierungstags.

Derzeit gelten die folgenden Einschränkungen für die Formatierung:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung.
* Rich-Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Rich-Karten unterstützen keine Markdown- oder Tabellenformatierung.

Stellen Sie nach dem Formatieren von Textinhalten sicher, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Einige Stile werden derzeit nicht auf allen Plattformen unterstützt. Die folgende Tabelle enthält eine Liste der Formatvorlagen und welche dieser Formatvorlagen in Nur-Text-Nachrichten und Rich-Karten unterstützt werden:

| Format                     | Nur-Text-Nachrichten | Rich-Karten – nur XML |
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

Stellen Sie nach der Überprüfung der plattformübergreifenden Unterstützung sicher, dass auch die Unterstützung durch einzelne Plattformen verfügbar ist.

## <a name="support-by-individual-platform"></a>Support nach einzelner Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

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

Informationen zur Kartenunterstützung finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Nachrichten aktualisieren und löschen](~/bots/how-to/update-and-delete-bot-messages.md)
