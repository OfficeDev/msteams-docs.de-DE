---
title: Unterstützte Textformatierung in Unterhaltungen
description: Beschreibt die Unterstützung der Textformatierung in Botunterhaltungen
keywords: Bots Unterhaltungen Messaging
ms.topic: how-to
localization_priority: Normal
ms.date: 03/29/2018
ms.openlocfilehash: dfb91e18a2ad895ae5b48c905046a22449304fc6
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566747"
---
# <a name="formatting-bot-messages"></a>Formatierung von Bot-Mitteilungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| plain | Der Text sollte als Unformatierung behandelt werden, ohne dass eine Formatierung angewendet wurde. |
| MARKDOWN | Der Text sollte als Markdownformatierung behandelt und entsprechend auf dem Kanal gerendert werden. Weitere [Informationen finden Sie unter Formatvorlagenformatieren](#formatting-text-content) von Textinhalten. |
| xml | Der Text ist einfaches XML-Markup. Weitere [Informationen finden Sie unter Formatvorlagenformatieren](#formatting-text-content) von Textinhalten. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge der Formatierungstags Markdown und XML (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung

Informationen zum Formatieren von Karten finden Sie [unter Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden, um sicherzustellen, dass Ihre Formatierung auf allen plattformen funktioniert, die von Microsoft Teams unterstützt werden.

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
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
