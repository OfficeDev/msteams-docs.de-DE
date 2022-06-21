---
title: Unterstützte Textformatierung in Unterhaltungen
description: In diesem Modul erfahren Sie mehr über die Unterstützung der Textformatierung in Bot-Unterhaltungen und das Formatieren von Textinhalten in Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/29/2018
ms.openlocfilehash: 0aea1472a323c0161567c4661c02956568cb2187
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189733"
---
# <a name="formatting-bot-messages"></a>Formatierung von Bot-Mitteilungen

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

Informationen zum Formatieren in Karten finden Sie [unter Teams Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Plattformübergreifender Support

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Karten (nur XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| Kopfzeile (Ebenen 1&ndash;3) | ✖                  | ✔                |
| Durchgestrichen             | ✖                  | ✔                |
| Horizontale Regel           | ✖                  | ✖                |
| ungeordnete Liste            | ✖                  | ✔                |
| Sortierte Liste              | ✖                  | ✔                |
| vorformatierter Text         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| Link                 | ✔                  | ✔                |
| Bildverknüpfung                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung der Textformatierung variiert je nach Nachrichtentyp und Plattform.

#### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| Kopfzeile (Ebenen 1&ndash;3) | ✖       | ✖   | ✖       |
| Durchgestrichen             | ✔       | ✔   | ✖       |
| Horizontale Regel           | ✖       | ✖   | ✖       |
| ungeordnete Liste            | ✔       | ✖   | ✖       |
| Sortierte Liste              | ✔       | ✖   | ✖       |
| vorformatierter Text         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| Link                 | ✔       | ✔   | ✔       |
| Bildverknüpfung                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Beispiele für Textformatierung

| Format | Beispiel | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| Kopfzeile (Ebenen 1&ndash;3) | **Text** | `### Text` | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| Bildverknüpfung | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
