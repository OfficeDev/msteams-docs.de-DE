---
title: Einführung in Karten
description: Beschreibt Karten und deren Verwendung in Bots, Connectors und Messagingerweiterungen
keywords: Connectors Bots Karten Messaging
ms.openlocfilehash: 00c649a1339f05b782e03a2c0db5cba2445f66bc
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777924"
---
# <a name="cards"></a>Karten

Eine *Karte* ist ein Benutzeroberflächencontainer für kurze oder verwandte Informationen. Karten können mehrere Eigenschaften und Anlagen aufweisen. Karten können Schaltflächen enthalten, die [Kartenaktionen auslösen können.](~/task-modules-and-cards/cards/cards-actions.md)

## <a name="adaptive-cards"></a>Adaptive Karten

[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows. Sie sind der empfohlene Kartentyp für die Entwicklung neuer Teams. Allgemeine Informationen vom Team für adaptive Karten finden Sie in der [Übersicht über adaptive Karten.](/adaptive-cards) Sie können adaptive Karten überall dort verwenden, wo Sie vorhandene Herokarten, Office365-Karten und Miniaturansichtskarten verwenden können.

Neben adaptiven Karten unterstützt Teams zwei weitere Arten von Karten:

* Connectorkarten, die als Teil von Office 365-Connectors verwendet werden.
* Einfache Karten aus dem Bot-Framework, z. B. Miniaturansichten und Herokarten.

Diese Kartentypen werden in der Kartenreferenz zu [Teams genauer beschrieben.](~/task-modules-and-cards/cards/cards-reference.md)

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

Karten wurden zuerst als Teil von Outlook und Office 365 definiert und werden als Teil von Office 365-Connectors verwendet. Wie viele Office 365-Anwendungen unterstützt Teams Connectors. Weitere Informationen zu Connectors in [Office 365-Connectors für Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)und die Spezifikation für Karten in Connectors finden Sie in referenzierbaren Nachrichtenkarten für [Aktionen.](/outlook/actionable-messages/card-reference)

## <a name="cards-in-bots"></a>Karten in Bots

Das Microsoft Bot Framework erweiterte die Kartenspezifikation durch Hinzufügen einer Reihe vordefinierter Karten, die Bots als Teil von Botnachrichten verwenden können. Teams unterstützt Bots, die das Bot Framework verwenden, unterstützt jedoch einen etwas anderen Satz dieser Karten. Allgemeine Informationen zu Karten in Bot Framework finden Sie unter "Hinzufügen von [Rich-Card-Anlagen zu Nachrichten".](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards) Diese Karten werden in Teams *als einfache* Karten bezeichnet.

Bots in Teams können jede Art von Karte verwenden: einfach, connector oder adaptive. Karten, die von Bots in Teams unterstützt werden, sind in der Kartenreferenz zu [Teams detailliert.](~/task-modules-and-cards/cards/cards-reference.md)  

## <a name="cards-in-messaging-extensions"></a>Karten in Messagingerweiterungen

[Messagingerweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können auch eine Karte zurückgeben. Messagingerweiterungen können jede Art von Karte verwenden: einfach, Connector oder adaptive Karte. Diese Karten finden Sie in der [Teams-Kartenreferenz.](~/task-modules-and-cards/cards/cards-reference.md)

## <a name="card-reference"></a>Kartenreferenz

Alle von Teams verwendeten Karten sind in der Kartenreferenz für [Teams aufgeführt.](~/task-modules-and-cards/cards/cards-reference.md) In dieser Referenz werden auch die Unterschiede zwischen Bot -Framework-Karten und -Karten in Teams beschrieben.
