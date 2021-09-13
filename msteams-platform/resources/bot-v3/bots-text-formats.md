---
title: Unterstützte Textformatierung in Unterhaltungen
description: Beschreibt die Unterstützung von Textformatierungen in Bot-Unterhaltungen
keywords: Bots Unterhaltungen Messaging
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 03/29/2018
ms.openlocfilehash: 466b2383230ce0cf8086ba4a3dd45a5488ed24b2
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156106"
---
# <a name="formatting-bot-messages"></a>Formatierung von Bot-Mitteilungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| einfach | Der Text sollte als Rohtext ohne Formatierung behandelt werden. |
| MARKDOWN | Der Text sollte als Markdown-Formatierung behandelt und entsprechend im Kanal gerendert werden. weitere Informationen finden Sie unter Formatieren von [Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |
| Xml | Der Text ist einfaches XML-Markup. weitere Informationen finden Sie unter Formatieren von [Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge von Markdown- und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung

Informationen zum Formatieren von Karten finden Sie unter [Teams Kartenreferenz.](~/task-modules-and-cards/cards/cards-reference.md)

### <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Karten (nur XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖                  | ✔                |
| Durchgestrichen             | ✖                  | ✔                |
| Horizontale Regel           | ✖                  | ✖                |
| Ungeordnete Liste            | ✖                  | ✔                |
| Sortierte Liste              | ✖                  | ✔                |
| Vorformatierter Text         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| Link                 | ✔                  | ✔                |
| Bildlink                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Support nach einzelner Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

#### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖       | ✖   | ✖       |
| Durchgestrichen             | ✔       | ✔   | ✖       |
| Horizontale Regel           | ✖       | ✖   | ✖       |
| Ungeordnete Liste            | ✔       | ✖   | ✖       |
| Sortierte Liste              | ✔       | ✖   | ✖       |
| Vorformatierter Text         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| Link                 | ✔       | ✔   | ✔       |
| Bildlink                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Beispiele für Textformatierungen

| Format | Beispiel | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text` | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| Sortierte Liste | <ol><li>text</li><li>text</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| Vorformatierter Text | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
