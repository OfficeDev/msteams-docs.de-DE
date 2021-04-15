---
title: Unterstützte Textformatierung in Unterhaltungen
description: Beschreibt die Unterstützung der Textformatierung in Botunterhaltungen
keywords: Bots Unterhaltungen Messaging
ms.topic: how-to
ms.date: 03/29/2018
ms.openlocfilehash: d8cb4ffd18871737ed4a64443800938f424910c9
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696059"
---
# <a name="formatting-bot-messages"></a>Formatierung von Bot-Mitteilungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht [`TextFormat`](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| plain | Der Text sollte als Unformatierung ohne Formatierung behandelt werden |
| MARKDOWN | Der Text sollte als Markdownformatierung behandelt und entsprechend auf dem Kanal gerendert werden. weitere [Informationen finden Sie unter Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen |
| xml | Der Text ist einfaches XML-Markup. weitere [Informationen finden Sie unter Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge der Formatierungstags Markdown und XML (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung

Informationen zum Formatieren von Karten finden Sie unter [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen von Microsoft Teams unterstützten Plattformen funktioniert, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Karten (nur XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖                  | ✔                |
| strikethrough             | ✖                  | ✔                |
| horizontale Regel           | ✖                  | ✖                |
| Ungeordnete Liste            | ✖                  | ✔                |
| geordnete Liste              | ✖                  | ✔                |
| vorformatierter Text         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| Link                 | ✔                  | ✔                |
| Bildlink                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

#### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖       | ✖   | ✖       |
| strikethrough             | ✔       | ✔   | ✖       |
| horizontale Regel           | ✖       | ✖   | ✖       |
| Ungeordnete Liste            | ✔       | ✖   | ✖       |
| geordnete Liste              | ✔       | ✖   | ✖       |
| vorformatierter Text         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| Link                 | ✔       | ✔   | ✔       |
| Bildlink                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Beispiele für die Textformatierung

| Format | Beispiel | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| Kopfzeile (Ebenen 1 &ndash; 3) | **Text** | `### Text` | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| Ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
