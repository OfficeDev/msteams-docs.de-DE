---
title: Einführung in Karten
description: Beschreibt Karten und deren Verwendung in Bots, Connectors und Messagingerweiterungen
localization_priority: Normal
ms.topic: conceptual
keywords: Connectors bots karten messaging
ms.openlocfilehash: 77dcbb7d0472b584623e878df956a6165296f4cf
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088752"
---
# <a name="cards"></a>Karten

Eine *Karte* ist ein Benutzeroberflächencontainer für kurze oder verwandte Informationen. Karten können mehrere Eigenschaften und Anlagen aufweisen. Karten können Schaltflächen enthalten, die [Kartenaktionen auslösen können.](~/task-modules-and-cards/cards/cards-actions.md)

## <a name="adaptive-cards"></a>Adaptive Karten

[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows. Sie sind der empfohlene Kartentyp für die Teams Entwicklung. Allgemeine Informationen vom Team für adaptive Karten finden Sie unter [Adaptive Cards Overview](/adaptive-cards). Sie können adaptive Karten überall verwenden, an der Sie vorhandene Hero-Karten, Office365-Karten und Miniaturansichtskarten verwenden können.

Neben adaptiven Karten unterstützt Teams zwei weitere Kartentypen:

* Connectorkarten, die als Teil von Office 365 werden.
* Einfache Karten aus dem Botframework, z. B. Miniaturansichten und Heldenkarten.

Diese Kartentypen werden in der folgenden Teams [beschrieben.](~/task-modules-and-cards/cards/cards-reference.md)

Teams verwendet Karten an drei verschiedenen Stellen:

* Connectors
* Bots
* Messaging-Erweiterungen

## <a name="adaptive-cards-and-incoming-webhooks"></a>Adaptive Karten und eingehende Webhooks

> [!NOTE]
>
> ✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.
>
> ✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html) [**undAction.Execute**](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

## <a name="cards-in-connectors"></a>Karten in Connectors

Karten wurden zuerst als Teil von Outlook und Office 365 definiert und als Teil von Connectors Office 365 verwendet. Wie viele Office 365 unterstützt Teams Connectors. Weitere Informationen zu Connectors finden Sie in [Office 365 Connectors for Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md), und die Spezifikation für Karten in Connectors finden Sie unter [Actionable message card reference](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Karten in Bots

Der Microsoft Bot Framework die Kartenspezifikation durch Hinzufügen einer Reihe vordefinierter Karten erweitert, die Bots als Teil von Botnachrichten verwenden können. Teams unterstützt Bots mithilfe des Bot Frameworks, unterstützt jedoch einen etwas anderen Satz dieser Karten. Allgemeine Informationen zu Karten in Bot Framework finden Sie unter Hinzufügen von [Rich-Card-Anlagen zu Nachrichten.](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards) Diese Karten werden als einfache Karten in *Teams.*

Bots in Teams können jede Art von Karte verwenden: einfach, connector oder adaptive. Karten, die von Bots in Teams unterstützt werden, finden Sie unter [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md).  

## <a name="cards-in-messaging-extensions"></a>Karten in Messagingerweiterungen

[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können auch eine Karte zurückgeben. Messagingerweiterungen können jede Art von Karte verwenden: einfach, connector oder adaptive. Diese Karten finden Sie im Teams [Card Reference](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="card-reference"></a>Kartenreferenz

Alle karten, die von Teams verwendet werden, sind im Teams [Kartenreferenz aufgeführt.](~/task-modules-and-cards/cards/cards-reference.md) Diese Referenz beschreibt auch die Unterschiede zwischen Bot Framework-Karten und Karten in Teams.
