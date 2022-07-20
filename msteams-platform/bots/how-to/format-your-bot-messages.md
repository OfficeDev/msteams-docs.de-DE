---
title: Formatieren von Bot-Nachrichten
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Ihren Bot-Nachrichten umfangreiche Formatierungen und Formatvorlagen hinzufügen, z. B. durchgestrichene, sortierte und ungeordnete Liste, Link, Bildlink und mehr.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 43a64a5ab7d44058831b643f2516839c248e9af1
ms.sourcegitcommit: 904cca011c3f27d1d90ddd80c3d0300a8918e412
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2022
ms.locfileid: "66895482"
---
# <a name="format-your-bot-messages"></a>Formatieren von Bot-Nachrichten

Mithilfe der Nachrichtenformatierung können Sie das Beste der Bot-Nachrichten hervorheben. Sie können Ihre Bot-Nachrichten so formatieren, dass sie Rich-Karten als Anlagen enthalten, die interaktive Elemente wie Schaltflächen, Text, Bilder, Audio, Video usw. enthalten.

> [!NOTE]
> Der Grenzwert für die Größe von Botnachrichten beträgt 40 KB. Wenn der Grenzwert für die Größe der Bot-Nachricht 40 KB überschreitet, erhält der Bot einen `413` Statuscode (RequestEntityTooLarge), der den Fehlercode `MessageSizeTooBig`enthält. Der Grenzwert für die Bot-Nachrichtengröße umfasst die gesamte Nachrichtennutzlast, die als UTF-16 codiert ist, und enthält keine Base64-codierten Bilder.

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
* Rich-Karten unterstützen keine Markdown- oder Tabellenformatierung.

Nachdem Sie Textinhalte formatiert haben, stellen Sie sicher, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Teams unterstützt werden.

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
