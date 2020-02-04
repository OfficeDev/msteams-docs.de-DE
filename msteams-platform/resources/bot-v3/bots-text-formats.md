---
title: Unterstützte Textformatierung in Unterhaltungen
description: Beschreibt Unterstützung für Textformatierung in bot-Unterhaltungen
keywords: Bots Conversations Messaging
ms.date: 03/29/2018
ms.openlocfilehash: cc6cba697a1f6907bfb13b94740e7bf9e92596da
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674112"
---
# <a name="formatting-bot-messages"></a>Formatieren von bot-Nachrichten

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale [`TextFormat`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

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

Informationen zur Formatierung in Karten finden Sie in der Referenz zu den [Teams-Karten](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, sollten Sie beachten, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Cards (nur XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| Kopfzeile (Ebenen 1&ndash;3) | ✖                  | ✔                |
| durchgestrichen             | ✖                  | ✔                |
| Horizontale Regel           | ✖                  | ✖                |
| Unsortierte Liste            | ✖                  | ✔                |
| sortierte Liste              | ✖                  | ✔                |
| Vorformatierter Text         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| Link                 | ✔                  | ✔                |
| Bild Link                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

#### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| Kopfzeile (Ebenen 1&ndash;3) | ✖       | ✖   | ✖       |
| durchgestrichen             | ✔       | ✔   | ✖       |
| Horizontale Regel           | ✖       | ✖   | ✖       |
| Unsortierte Liste            | ✔       | ✖   | ✖       |
| sortierte Liste              | ✔       | ✖   | ✖       |
| Vorformatierter Text         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| Link                 | ✔       | ✔   | ✔       |
| Bild Link                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Beispiele für Textformatierungen

| Format | Beispiel | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| Kopfzeile (Ebenen 1&ndash;3) | **Text** | `### Text` | `<h3>Text</h3>` |
| durchgestrichen | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| Unsortierte Liste | <ul><li>text</li><li>text</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| sortierte Liste | <ol><li>text</li><li>text</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| Bild Link | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
