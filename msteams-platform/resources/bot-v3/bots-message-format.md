---
title: Bot-Nachrichtenformat
description: In diesem Modul erfahren Sie mehr über die Formatierung von Bot-Nachrichten
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 9e331a17940ee482a0c2adcb81b57a17823ab668
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190167"
---
# <a name="message-formatting-for-bots"></a>Nachrichtenformatierung für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message)Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| PLAIN | Der Text sollte als Unformatierung ohne Formatierung behandelt werden. |
| MARKDOWN | Der Text sollte als Markdown-Formatierung behandelt und entsprechend im Kanal gerendert werden. siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |
| XML | Der Text ist einfaches XML-Markup. siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Teams unterstützt eine Teilmenge von Markdown- und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung.
* Funktionsreiche Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Rich-Karten unterstützen keine Markdown- oder Tabellenformatierung.

## <a name="cross-platform-support"></a>Plattformübergreifender Support

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Rich-Karten (nur XML) |
| ---                       | :---: | :---: |
| bold                      | ✔️️ | ❌ |
| italic                    | ✔️ | ✔️ |
| Kopfzeile (Ebenen 1&ndash;3) | ❌ | ✔️ |
| Durchgestrichen             | ❌ | ✔️ |
| Horizontale Regel           | ❌ | ❌ |
| ungeordnete Liste            | ❌ | ✔️ |
| Sortierte Liste              | ❌ | ✔️ |
| vorformatierter Text         | ✔️ | ✔️ |
| blockquote                | ✔️ | ✔️ |
| Link                 | ✔️ | ✔️ |
| Bildverknüpfung                | ✔️ | ❌ |

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung der Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔️ | ✔️ | ✔️ |
| italic                    | ✔️ | ✔️ | ✔️ |
| Kopfzeile (Ebenen 1&ndash;3) | ❌ | ❌ | ❌ |
| Durchgestrichen             | ✔️ | ✔️ | ❌ |
| Horizontale Regel           | ❌ | ❌ | ❌ |
| ungeordnete Liste            | ✔️ | ❌ | ❌ |
| Sortierte Liste              | ✔️ | ❌ | ❌ |
| vorformatierter Text         | ✔️ | ✔️ | ✔️ |
| blockquote                | ✔️ | ✔️ | ✔️ |
| Link                 | ✔️ | ✔️ | ✔️ |
| Bildverknüpfung                | ✔️ | ✔️ | ✔️ |

### <a name="cards"></a>Karten

Weitere Informationen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) zur Unterstützung von Karten.
