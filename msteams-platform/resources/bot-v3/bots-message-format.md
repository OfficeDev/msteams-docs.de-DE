---
title: Bot-Nachrichtenformat
description: Beschreibt die Details der Formatierung von Bot-Nachrichten
keywords: Teams-Szenarien Kanäle Konversation Bot Nachricht
ms.topic: reference
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: a9566331b259ba77f6770ff6394e8a788769af5d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566474"
---
# <a name="message-formatting-for-bots"></a>Nachrichtenformatierung für Bots

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

* Nur Textnachrichten unterstützen keine Tabellenformatierung.
* Rich Cards unterstützen die Formatierung nur in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften.
* Rich Cards unterstützen keine Markdown- oder Tabellenformatierung.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen Plattformen funktioniert, die von Microsoft Teams unterstützt werden, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

| Format                     | Nur Textnachrichten | Rich Cards (nur XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| Header (Ebenen 1 &ndash; 3) | ✖ | ✔ |
| Durchgestrichen             | ✖ | ✔ |
| Horizontale Regel           | ✖ | ✖ |
| ungeordnete Liste            | ✖ | ✔ |
| geordnete Liste              | ✖ | ✔ |
| vorformatierter Text         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| Link                 | ✔ | ✔ |
| Bildlink                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Unterstützung durch individuelle Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur Textnachrichten

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| Header (Ebenen 1 &ndash; 3) | ✖ | ✖ | ✖ |
| Durchgestrichen             | ✔ | ✔ | ✖ |
| Horizontale Regel           | ✖ | ✖ | ✖ |
| ungeordnete Liste            | ✔ | ✖ | ✖ |
| geordnete Liste              | ✔ | ✖ | ✖ |
| vorformatierter Text         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| Link                 | ✔ | ✔ | ✔ |
| Bildlink                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Weitere Informationen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) für Unterstützung in Karten.
