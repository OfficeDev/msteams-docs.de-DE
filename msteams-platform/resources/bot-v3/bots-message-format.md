---
title: Bot-Nachrichtenformat
description: Beschreibt die Details der Formatierung für Botnachrichten
keywords: teams scenarios channels conversation bot message
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

* Nur Textnachrichten unterstützen keine Tabellenformatierung.
* Rich Cards unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Eigenschaften titeln oder untertiteln.
* Rich Cards unterstützen keine Markdown- oder Tabellenformatierung.

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden, um sicherzustellen, dass Ihre Formatierung auf allen plattformen funktioniert, die von Microsoft Teams unterstützt werden.

| Format                     | Nur-Text-Nachrichten | Rich Cards (nur XML) |
| ---                       | :---: | :---: |
| bold                      | ✔ | ✖ |
| italic                    | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✔ |
| strikethrough             | ✖ | ✔ |
| horizontale Regel           | ✖ | ✖ |
| Ungeordnete Liste            | ✖ | ✔ |
| geordnete Liste              | ✖ | ✔ |
| vorformatierter Text         | ✔ | ✔ |
| blockquote                | ✔ | ✔ |
| Link                 | ✔ | ✔ |
| Bildlink                | ✔ | ✖ |

## <a name="support-by-individual-platform"></a>Unterstützung durch einzelne Plattform

Die Unterstützung für die Textformatierung variiert je nach Nachrichtentyp und Plattform.

### <a name="text-only-messages"></a>Nur-Text-Nachrichten

| Format                     | Desktop | iOS | Android |
| ---                       | :---: | :---: | :---: |
| bold                      | ✔ | ✔ | ✔ |
| italic                    | ✔ | ✔ | ✔ |
| Kopfzeile (Ebenen 1 &ndash; 3) | ✖ | ✖ | ✖ |
| strikethrough             | ✔ | ✔ | ✖ |
| horizontale Regel           | ✖ | ✖ | ✖ |
| Ungeordnete Liste            | ✔ | ✖ | ✖ |
| geordnete Liste              | ✔ | ✖ | ✖ |
| vorformatierter Text         | ✔ | ✔ | ✔ |
| blockquote                | ✔ | ✔ | ✔ |
| Link                 | ✔ | ✔ | ✔ |
| Bildlink                | ✔ | ✔ | ✔ |

### <a name="cards"></a>Karten

Weitere Informationen finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) zur Unterstützung in Karten.
