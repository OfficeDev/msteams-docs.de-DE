---
title: Formatieren von Bot-Nachrichten
author: surbhigupta
description: Erfahren Sie, wie Sie Botnachrichten wie durchgestrichene, sortierte und ungeordnete Listen, Links oder Bildlinks formatieren und formatieren. Grundlegendes zur plattformübergreifenden Unterstützung.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: b0db9f9d9e55dc3f11474dac4b8c6563caf5fd1b
ms.sourcegitcommit: bb15ce26cd65bec90991b703069424ab4b4e1a61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2022
ms.locfileid: "68772300"
---
# <a name="format-your-bot-messages"></a>Formatieren von Bot-Nachrichten

Mithilfe der Nachrichtenformatierung können Sie das Beste der Bot-Nachrichten hervorheben. Sie können Ihre Botnachrichten so formatieren, dass sie Rich Cards als Anlagen enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder usw. enthalten.

> [!NOTE]
> Die Maximale Größe von Botnachrichten beträgt 40 KB. Wenn der Grenzwert für die Botnachrichtengröße 40 KB überschreitet, empfängt der Bot einen `413` Statuscode (`RequestEntityTooLarge`), der den Fehlercode `MessageSizeTooBig`enthält. Die Größenbeschränkung für Botnachrichten umfasst die gesamte Nachrichtennutzlast, die als UTF-16 codiert ist, und umfasst keine Base64-codierten Bilder.

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

* Reine Textnachrichten unterstützen keine Tabellenformatierung.
* Funktionsreiche Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Rich-Karten unterstützen keine Markdown- oder Tabellenformatierung.

Stellen Sie nach dem Formatieren von Textinhalten sicher, dass Ihre Formatierung auf allen plattformen funktioniert, die von Teams unterstützt werden.

## <a name="cross-platform-support"></a>Plattformübergreifender Support

Einige Formatvorlagen werden derzeit nicht auf allen Plattformen unterstützt. Die folgende Tabelle enthält eine Liste der Formatvorlagen, und welche dieser Formatvorlagen in Nur-Text-Nachrichten und funktionsreichen Karten unterstützt werden:

| Format                     | Nur-Text-Nachrichten | Funktionsreiche Karten – nur XML |
| ---                       | :---: | :---: |
| Fett                      | ✔️️ | ❌ |
| Kursiv                    | ✔️ | ✔️ |
| Header (Stufe 1&ndash;3) | ❌ | ✔️ |
| Durchgestrichen             | ❌ | ✔️ |
| Horizontales Lineal           | ❌ | ❌ |
| Unsortierte Liste            | ❌ | ✔️ |
| Sortierte Liste              | ❌ | ✔️ |
| Vorformatierter Text         | ✔️ | ✔️ |
| Blockzitat                | ✔️ | ✔️ |
| Hyperlink                 | ✔️ | ✔️ |
| Bildverknüpfung                | ❌ | ❌ |

Stellen Sie nach Überprüfung des plattformübergreifenden Supports sicher, dass auch die Unterstützung einzelner Plattformen verfügbar ist.

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung der Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

Die folgende Tabelle enthält eine Liste der Formatvorlagen, die unter Desktop, iOS und Android unterstützt werden:

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| Fett                      | ✔️ | ✔️ | ✔️ |
| Kursiv                    | ✔️ | ✔️ | ✔️ |
| Header (Stufe 1&ndash;3) | ❌ | ❌ | ❌ |
| Durchgestrichen             | ✔️ | ✔️ | ❌ |
| Horizontales Lineal           | ❌ | ❌ | ❌ |
| Unsortierte Liste            | ✔️ | ❌ | ❌ |
| Sortierte Liste              | ✔️ | ❌ | ❌ |
| Vorformatierter Text         | ✔️ | ✔️ | ✔️ |
| Blockzitat                | ✔️ | ✔️ | ✔️ |
| Hyperlink                 | ✔️ | ✔️ | ✔️ |
| Bildverknüpfung                | ❌ | ❌ | ❌ |

### <a name="cards"></a>Karten

Informationen zur Kartenunterstützung finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Nachrichten aktualisieren und löschen](~/bots/how-to/update-and-delete-bot-messages.md)
