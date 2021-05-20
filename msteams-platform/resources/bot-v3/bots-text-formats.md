---
title: Unterstützte Textformatierung in Unterhaltungen
description: Beschreibt die Unterstützung der Textformatierung in Bot-Unterhaltungen
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

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| einfach | Der Text sollte als Rohtext behandelt werden, ohne dass eine Formatierung angewendet wird. |
| MARKDOWN | Der Text sollte als Markdown-Formatierung behandelt und entsprechend auf dem Kanal gerendert werden. Siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |
| Xml | Der Text ist ein einfaches XML-Markup; Siehe [Formatieren von Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge von Markdown- und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur Textnachrichten unterstützen keine Tabellenformatierung

Informationen zum Formatieren in Karten finden Sie [unter Teams Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md).

### <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur Textnachrichten | Karten (nur XML) |
|---------------------------|--------------------|------------------|
| bold                      | ✔                  | ✖                |
| italic                    | ✔                  | ✔                |
| Header (Ebenen 1 &ndash; 3) | ✖                  | ✔                |
| Durchgestrichen             | ✖                  | ✔                |
| Horizontale Regel           | ✖                  | ✖                |
| ungeordnete Liste            | ✖                  | ✔                |
| geordnete Liste              | ✖                  | ✔                |
| vorformatierter Text         | ✔                  | ✔                |
| blockquote                | ✔                  | ✔                |
| Link                 | ✔                  | ✔                |
| Bildlink                | ✔                  | ✖                |

### <a name="support-by-individual-platform"></a>Unterstützung durch individuelle Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

#### <a name="text-only-messages"></a>Nur Textnachrichten

| Format                     | Desktop | iOS | Android |
|---------------------------|---------|-----|---------|
| bold                      | ✔       | ✔   | ✔       |
| italic                    | ✔       | ✔   | ✔       |
| Header (Ebenen 1 &ndash; 3) | ✖       | ✖   | ✖       |
| Durchgestrichen             | ✔       | ✔   | ✖       |
| Horizontale Regel           | ✖       | ✖   | ✖       |
| ungeordnete Liste            | ✔       | ✖   | ✖       |
| geordnete Liste              | ✔       | ✖   | ✖       |
| vorformatierter Text         | ✔       | ✔   | ✔       |
| blockquote                | ✔       | ✔   | ✔       |
| Link                 | ✔       | ✔   | ✔       |
| Bildlink                | ✔       | ✔   | ✔       |

### <a name="examples-of-text-formatting"></a>Beispiele für Textformatierung

| Format | Beispiel | Markdown | XML (HTML) |
| --- | --- | --- | --- |
| bold | **text** | `**text**` | `<strong>text</strong>` |
| italic | *text* | `*text*` | `<em>text</em>` |
| Header (Ebenen 1 &ndash; 3) | **Text** | `### Text` | `<h3>Text</h3>` |
| Durchgestrichen | ~~text~~ | `~~text~~` | `<strike>text</strike>` |
| ungeordnete Liste | <ul><li>text</li><li>text</li></ul> | `* text`<br>`* text` | `<ul><li>text</li><li>text</li></ul>` |
| geordnete Liste | <ol><li>text</li><li>text</li></ol> | `1. text`<br>`2. text` | `<ol><li>text</li><li>text</li></ol>` |
| vorformatierter Text | `text` | `` `text` `` | `<pre>text</pre>` |
| blockquote | <blockquote>text</blockquote> | `>text` | `<blockquote>text</blockquote>` |
| Link | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` | `<a href="https://www.bing.com/">Bing</a>` |
| Bildlink | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `![Duck on a rock](http://aka.ms/Fo983c)` | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |
