---
title: Formatieren von bot-Nachrichten
author: clearab
description: Hinzufügen von Rich-Formatierung zu ihren bot-Nachrichten
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a11d01233481371c66562e0fa27ab805b06e9391
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674226"
---
# <a name="format-your-bot-messages"></a>Formatieren von bot-Nachrichten

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| Textformat-Wert | Beschreibung |
| --- | --- |
| nur | Der Text sollte als unformatierter Text ohne angewendete Formatierung behandelt werden.|
| markdown | Der Text sollte als Abschlag Formatierung behandelt und entsprechend auf dem Kanal gerendert werden. *Siehe* [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |
| XML | Der Text ist einfaches XML-Markup. *Siehe* [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge von Abschlags-und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung.
* Rich Cards unterstützen nur die Formatierung in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle.
* Umfangreiche Karten unterstützen keine Abschlag-oder Tabellenformatierung.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, sollten Sie beachten, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Rich Cards (nur XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| Kopfzeile (Ebenen 1&ndash;3) | ✖ | ✔ |
| durchgestrichen             | ✖ | ✔ |
| Horizontale Regel           | ✖ | ✖ |
| Unsortierte Liste            | ✖ | ✔ |
| sortierte Liste              | ✖ | ✔ |
| Vorformatierter Text         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| Link                 | ✔ | ✔ |
| Bild Link                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| Kopfzeile (Ebenen 1&ndash;3) | ✖ | ✖ | ✖ |
| durchgestrichen             | ✔ | ✔ | ✖ |
| Horizontale Regel           | ✖ | ✖ | ✖ |
| Unsortierte Liste            | ✔ | ✖ | ✖ |
| sortierte Liste              | ✔ | ✖ | ✖ |
| Vorformatierter Text         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| Link                 | ✔ | ✔ | ✔ |
| Bild Link                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Siehe Karten [Formatierung](~/task-modules-and-cards/cards/cards-format.md) für die Unterstützung von Karten.
