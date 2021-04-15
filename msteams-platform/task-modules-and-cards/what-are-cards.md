---
title: Einführung in Karten
description: Beschreibt Karten und deren Verwendung in Bots, Connectors und Messagingerweiterungen
ms.topic: conceptual
keywords: Connectors bots karten messaging
ms.openlocfilehash: c2fe0aea142a96643e33e16acc08bcfd8c33e92e
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696458"
---
# <a name="cards"></a>Karten

Eine *Karte* ist ein Benutzeroberflächencontainer für kurze oder verwandte Informationen. Karten können mehrere Eigenschaften und Anlagen aufweisen. Karten können Schaltflächen enthalten, die [Kartenaktionen auslösen können.](~/task-modules-and-cards/cards/cards-actions.md)

## <a name="adaptive-cards"></a>Adaptive Karten

[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows. Sie sind der empfohlene Kartentyp für die neue Teams-Entwicklung. Allgemeine Informationen vom Team für adaptive Karten finden Sie unter [Adaptive Cards Overview](/adaptive-cards). Sie können adaptive Karten überall verwenden, an der Sie vorhandene Hero-Karten, Office365-Karten und Miniaturansichtskarten verwenden können.

Zusätzlich zu adaptiven Karten unterstützt Teams zwei weitere Kartentypen:

* Connectorkarten, die als Teil von Office 365-Connectors verwendet werden.
* Einfache Karten aus dem Botframework, z. B. Miniaturansichten und Heldenkarten.

Diese Kartentypen werden in der Teams-Kartenreferenz [genauer beschrieben.](~/task-modules-and-cards/cards/cards-reference.md)

Teams verwendet Karten an drei verschiedenen Orten:

* Connectors
* Bots
* Messaging-Erweiterungen

## <a name="adaptive-cards-and-incoming-webhooks"></a>Adaptive Karten und eingehende Webhooks

> [!NOTE]
>
> ✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.
>
> ✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

## <a name="cards-in-connectors"></a>Karten in Connectors

Karten wurden zunächst als Teil von Outlook und Office 365 definiert und als Teil von Office 365 Connectors verwendet. Wie viele office 365-Anwendungen unterstützt Teams Connectors. Weitere Informationen zu Connectors in [Office 365 Connectors für Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)und die Spezifikation für Karten in Connectors finden Sie unter [Actionable message card reference](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Karten in Bots

Das Microsoft Bot Framework hat die Kartenspezifikation erweitert, indem eine Reihe vordefinierter Karten hinzugefügt wurde, die Bots als Teil von Botnachrichten verwenden können. Teams unterstützt Bots, die das Bot Framework verwenden, unterstützt jedoch einen etwas anderen Satz dieser Karten. Allgemeine Informationen zu Karten in Bot Framework finden Sie unter Hinzufügen von [Rich-Card-Anlagen zu Nachrichten.](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards) Diese Karten werden in *Teams als einfache Karten* bezeichnet.

Bots in Teams können jede Art von Karte verwenden: einfach, connector oder adaptive. Karten, die von Bots in Teams unterstützt werden, finden Sie unter [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).  

## <a name="cards-in-messaging-extensions"></a>Karten in Messagingerweiterungen

[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können auch eine Karte zurückgeben. Messagingerweiterungen können jede Art von Karte verwenden: einfach, connector oder adaptive. Diese Karten finden Sie in der [Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="card-reference"></a>Kartenreferenz

Alle von Teams verwendeten Karten sind in der [Teams-Kartenreferenz aufgeführt.](~/task-modules-and-cards/cards/cards-reference.md) In diesem Verweis werden auch die Unterschiede zwischen Bot Framework-Karten und -Karten in Teams beschrieben.
