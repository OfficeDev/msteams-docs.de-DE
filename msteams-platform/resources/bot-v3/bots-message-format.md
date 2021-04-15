---
title: Bot-Nachrichtenformat
description: Beschreibt die Details der Formatierung für Botnachrichten
keywords: teams scenarios channels conversation bot message
ms.topic: reference
ms.date: 05/20/2019
ms.openlocfilehash: 4eccc8af8f2cdad153998a13502df2a1baf9ceec
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696619"
---
# <a name="message-formatting-for-bots"></a>Nachrichtenformatierung für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht [`TextFormat`](/bot-framework/dotnet/bot-builder-dotnet-create-messages#customizing-a-message) gerendert wird.

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
* Rich Cards unterstützen nur die Formatierung in der Texteigenschaft, nicht in den Titel- oder Untertiteleigenschaften
* Rich Cards unterstützen keine Markdown- oder Tabellenformatierung

## <a name="cross-platform-support"></a>Plattformübergreifende Unterstützung

Um sicherzustellen, dass Ihre Formatierung auf allen von Microsoft Teams unterstützten Plattformen funktioniert, beachten Sie, dass einige Formatvorlagen derzeit nicht auf allen Plattformen unterstützt werden.

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

Unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md) finden Sie Unterstützung in Karten.
