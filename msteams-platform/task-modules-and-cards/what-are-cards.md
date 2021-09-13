---
title: Karten
description: Beschreibt Karten und deren Verwendung in Bots, Connectors und Messaging-Erweiterungen
ms.localizationpriority: medium
keywords: Connectors Bots Karten Messaging
ms.topic: overview
ms.openlocfilehash: 345e37a9af00c2f3300cc76f4b44b83cc47d0392
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156878"
---
# <a name="cards"></a>Karten

Eine Karte ist ein Benutzeroberflächencontainer für kurze oder verwandte Informationen. Karten können mehrere Eigenschaften und Anlagen aufweisen und Schaltflächen enthalten, die [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md)auslösen. Mithilfe von Karten können Sie Informationen in Gruppen organisieren und Benutzern die Möglichkeit geben, mit bestimmten Teilen der Informationen zu interagieren.

Die Bots für Teams unterstützen die folgenden Arten von Karten: adaptive Karte, Favoritenkarte, Listenkarte, Office 365 Connectorkarte, Belegkarte, Anmeldekarte, Miniaturansichtskarte und Kartensammlungen. Je nach Kartentyp können Sie Rich-Text-Formatierungen entweder mit Markdown oder HTML zu Ihren Karten hinzufügen. Karten, die von Bots und Messaging-Erweiterungen in Microsoft Teams verwendet werden, fügen diese Kartenaktionen hinzu und reagieren darauf, `openUrl` , `messageBack` , und `imBack` `invoke` `signin` .

Teams verwendet Karten an drei verschiedenen Stellen:

* Connectors
* Bots
* Messaging-Erweiterungen

## <a name="cards-in-connectors"></a>Karten in Connectors

Karten wurden zuerst als Teil von Outlook und Office 365 definiert und werden jetzt als Teil Office 365 Connectors verwendet. Wie viele Office 365 Anwendungen unterstützt Teams Connectors. Weitere Informationen finden Sie unter [Office 365 Connectors für Teams.](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) Sie finden die Spezifikation für Karten in Connectors in Referenz [zu Nachrichtenkarten](/outlook/actionable-messages/card-reference)mit Aktionen.

## <a name="cards-in-bots"></a>Karten in Bots

Die Microsoft Bot Framework erweitert die Kartenspezifikation, indem eine Reihe vordefinierter Karten hinzugefügt wird, die Bots als Teil von Botnachrichten verwenden können. Teams unterstützt Bots mithilfe des Bot-Frameworks, unterstützt jedoch einen anderen Satz dieser Karten. Allgemeine Informationen zu Karten in Bot Framework finden Sie unter [Hinzufügen von Rich-Card-Anlagen zu Nachrichten.](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards) Diese Karten werden in Teams als einfache Karten bezeichnet.

Bots in Teams können einfache Karten, Connectorkarten oder adaptive Karten verwenden. [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md) bieten Informationen zu Karten, die von Bots in Teams unterstützt werden.

## <a name="cards-in-messaging-extensions"></a>Karten in Messaging-Erweiterungen

[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können auch eine Karte zurückgeben. Messaging-Erweiterungen können einfache Karten, Connectorkarten oder adaptive Karten verwenden. Diese Karten befinden sich in [Kartentypen.](~/task-modules-and-cards/cards/cards-reference.md)

## <a name="types-of-cards"></a>Kartentypen

Alle von Teams verwendeten Karten werden in [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md)aufgeführt. In dieser Referenz werden auch die Unterschiede zwischen Bot Framework-Karten und Karten in Teams beschrieben.

## <a name="adaptive-cards"></a>Adaptive Karten

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows. Sie sind der empfohlene Kartentyp für neue Teams Entwicklung. Allgemeine Informationen vom Team für adaptive Karten finden Sie unter ["Übersicht über adaptive Karten".](/adaptive-cards) Sie können adaptive Karten überall verwenden, wo Sie vorhandene Hero-Karten, Office 365-Karten und Miniaturansichtskarten verwenden.

Zusätzlich zu adaptiven Karten unterstützt Teams zwei andere Arten von Karten:

* Verbinderkarten: Werden als Teil von Office 365 Connectors verwendet.
* Einfache Karten: Werden vom Bot-Framework verwendet, z. B. miniaturansichten und Favoritenkarten.

### <a name="adaptive-cards-and-incoming-webhooks"></a>Adaptive Karten und eingehende Webhooks

> [!VIDEO https://www.youtube-nocookie.com/embed/y5pbJI43Zvg]

> [!NOTE]
> * Alle systemeigenen Schemaelemente adaptiver Karten mit Ausnahme `Action.Submit` von , werden vollständig unterstützt.
> * Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)und [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Mit adaptiven Karten mit eingehenden Webhooks können Sie die umfangreichen und flexiblen Funktionen adaptiver Karten nutzen. Es sendet Daten mit eingehenden Webhooks in Teams von ihrem Webdienst.

## <a name="see-also"></a>Siehe auch

* [Formatieren von Karten in Teams](~/task-modules-and-cards/cards/cards-format.md)
* [Entwerfen adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md)