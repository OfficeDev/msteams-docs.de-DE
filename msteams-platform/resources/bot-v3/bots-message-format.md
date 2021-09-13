---
title: Bot-Nachrichtenformat
description: Beschreibt die Details der Formatierung für Botnachrichten.
keywords: Teams-Szenarien Kanäle Unterhaltung Bot-Nachricht
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: e737cd42d2aa00e3e4f302b4917fef67adaa5645
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156606"
---
# <a name="message-formatting-for-bots"></a>Nachrichtenformatierung für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Microsoft Teams unterstützt die folgenden Formatierungsoptionen:

| TextFormat-Wert | Beschreibung |
| --- | --- |
| einfach | Der Text sollte als Rohtext ohne Formatierung behandelt werden. |
| MARKDOWN | Der Text sollte als Markdown-Formatierung behandelt und entsprechend im Kanal gerendert werden. weitere Informationen finden Sie unter Formatieren von [Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |
| Xml | Der Text ist einfaches XML-Markup; weitere Informationen finden Sie unter Formatieren von [Textinhalten](#formatting-text-content) für unterstützte Formatvorlagen. |

## <a name="formatting-text-content"></a>Formatieren von Textinhalten

Microsoft Teams unterstützt eine Teilmenge von Markdown- und XML-Formatierungstags (HTML).

Derzeit gelten die folgenden Einschränkungen:

* Nur-Text-Nachrichten unterstützen keine Tabellenformatierung.
* Rich-Karten unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Rich-Karten unterstützen keine Markdown- oder Tabellenformatierung.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Rich-Karten (nur XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✔ |
| Durchgestrichen             | ✖ | ✔ |
| Horizontale Regel           | ✖ | ✖ |
| Ungeordnete Liste            | ✖ | ✔ |
| Sortierte Liste              | ✖ | ✔ |
| Vorformatierter Text         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| Link                 | ✔ | ✔ |
| Bildlink                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Support nach einzelner Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✖ | ✖ |
| Durchgestrichen             | ✔ | ✔ | ✖ |
| Horizontale Regel           | ✖ | ✖ | ✖ |
| Ungeordnete Liste            | ✔ | ✖ | ✖ |
| Sortierte Liste              | ✔ | ✖ | ✖ |
| Vorformatierter Text         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| Link                 | ✔ | ✔ | ✔ |
| Bildlink                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Weitere Informationen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) für die Unterstützung in Karten.
