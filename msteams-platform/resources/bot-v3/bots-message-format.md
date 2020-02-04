---
title: Nachrichtenformat "bot"
description: Beschreibt die Formatierungsdetails für bot-Nachrichten.
keywords: Teams Szenarien Kanäle Unterhaltungs bot-Nachricht
ms.date: 05/20/2019
ms.openlocfilehash: eb0d0303d2b414ff84beab73055be5f057fff11c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674563"
---
# <a name="message-formatting-for-bots"></a>Nachrichtenformatierung für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| Textformat-Wert | Beschreibung |
| --- | --- |
| nur | Der Text sollte als unformatierter Text behandelt werden, ohne dass die Formatierung überhaupt angewendet wird. |
| markdown | Der Text sollte als Abschlag Formatierung behandelt und entsprechend dem Kanal gerendert werden; siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen |
| XML | Der Text ist einfaches XML-Markup; siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge von Abschlags-und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung
* Rich Cards unterstützen die Formatierung nur in der Text-Eigenschaft, nicht in den Eigenschaften Title oder subtitle
* Umfangreiche Karten unterstützen keine Abschlag-oder Tabellenformatierung

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
