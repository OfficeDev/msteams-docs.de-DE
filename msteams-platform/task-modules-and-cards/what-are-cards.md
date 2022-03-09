---
title: Karten
description: Beschreibung von Karten und deren Verwendung in Bots, Connectors und Messaging-Erweiterungen
ms.localizationpriority: high
keywords: Connectors Bots Karten Messaging
ms.topic: overview
ms.openlocfilehash: 249a83c8a41ddfa3a7409ce897238389114db165
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2022
ms.locfileid: "63398652"
---
# <a name="cards"></a>Karten

Bei einer Karte handelt es sich um einen Benutzeroberflächencontainer für kurze oder verknüpfte Informationen. Karten können mehrere Eigenschaften und Anhänge aufweisen sowie Schaltflächen enthalten, über die [Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md) ausgelöst werden können. Mithilfe von Karten können Sie Informationen in Gruppen organisieren und Benutzern die Möglichkeit geben, mit bestimmten Teilen der Informationen zu interagieren.

Die Bots für Microsoft Teams unterstützen die folgenden Arten von Karten:

* Adaptive Karte
* Hero-Karte
* Listenkarte
* Office 365-Connectorkarte
* Belegkarte
* Anmeldekarte
* Miniaturbildkarte
* Kartensammlungen

Je nach Kartentyp können Sie Ihren Karten Rich-Text-Formatierung mittels Markdown oder HTML hinzufügen. Karten, die von Bots und Messaging-Erweiterungen in Microsoft Teams verwendet werden, fügen die folgenden Kartenaktionen hinzu bzw. reagieren darauf: `openUrl`, `messageBack`, `imBack`, `invoke` und `signin`.

In Microsoft Teams werden Karten an drei verschiedenen Orten verwendet:

* Connectors
* Bots
* Messaging-Erweiterungen

## <a name="cards-in-connectors"></a>Karten in Connectors

Karten wurden zuerst als Bestandteil von Outlook und Office 365 definiert und werden jetzt als Bestandteil von Office 365-Connectors verwendet. Wie viele Office 365-Anwendungen, unterstützt auch Microsoft Teams Connectors. Weitere Informationen finden Sie unter [Office 365-Connectors für Microsoft Teams](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md). Sie finden die Spezifikation für Karten in Connectors unter [Referenz zu Aktion erfordernde Nachrichtenkarten](/outlook/actionable-messages/card-reference).

## <a name="cards-in-bots"></a>Karten in Bots

Das Microsoft Bot Framework erweitert die Kartenspezifikation durch das Hinzufügen einer Reihe vordefinierter Karten, die Bots als Teil von Botnachrichten verwenden können. Microsoft Teams unterstützt Bots, die das Bot-Framework nutzen, unterstützt jedoch einen anderen Satz dieser Karten. Allgemeine Informationen zu Karten im Bot Framework finden Sie unter [Hinzufügen umfangreicher Kartenanlagen zu Nachrichten](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards). Diese Karten werden in Microsoft Teams als einfache Karten bezeichnet.

Bots in Microsoft Teams können einfache Karten, Connectorkarten oder adaptive Karten verwenden. [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md) enthält Informationen zu Karten, die von Bots in Microsoft Teams unterstützt werden.

## <a name="cards-in-messaging-extensions"></a>Karten in Messaging-Erweiterungen

[Messaging-Erweiterungen](~/messaging-extensions/what-are-messaging-extensions.md) können ebenfalls eine Karte zurückgeben. Messaging-Erweiterungen können einfache Karten, Connectorkarten oder adaptive Karten verwenden. Diese Karten befinden sich unter [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md).

## <a name="types-of-cards"></a>Kartentypen

Alle von Microsoft Teams verwendeten Karten sind unter [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md) aufgeführt. In dieser Referenz werden auch die Unterschiede zwischen Bot Framework-Karten und Karten in Microsoft Teams beschrieben.

## <a name="adaptive-cards"></a>Adaptive Karten

[Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card) sind eine neue produktübergreifende Spezifikation für Karten in Microsoft-Produkten, einschließlich Bots, Cortana, Outlook und Windows. Sie werden als Kartentyp für die Entwicklung neuer Microsoft Teams-Lösungen empfohlen. Allgemeine Informationen vom für adaptive Karten zuständigen Team finden Sie unter [Übersicht über adaptive Karten](/adaptive-cards). Sie können adaptive Karten überall dort verwenden, wo Sie vorhandene Hero-Karten, Office 365-Karten und Miniaturbildkarten verwenden.

Neben adaptiven Karten unterstützt Microsoft Teams noch zwei andere Arten von Karten:

* Connectorkarten: Diese werden als Bestandteil von Office 365-Connectors verwendet.
* Einfache Karten: Werden vom Bot-Framework verwendet, z. B. Miniaturbild- und Hero-Karten.

### <a name="people-picker-in-adaptive-cards"></a>Personenauswahl in adaptiven Karten

Die [Personenauswahl](cards/people-picker.md#people-picker-in-adaptive-cards), die als Eingabesteuerelement adaptiven Karten hinzugefügt wurde, ermöglicht die Suche und Auswahl von Personen. Sie können sie in Chats, Kanälen, Aufgabenmodulen und Registerkarten verwenden. Mobilgeräte- und Desktopclients unterstützen die Personenauswahl, die eine Inlineeingabe ermöglicht.

### <a name="type-ahead-search-in-adaptive-cards"></a>Vorschlagssuche in adaptiven Karten  

Die Vorschlagssuche, die als Eingabesteuerelement adaptiven Karten hinzugefügt wurde, liefert eine [dynamische Suchfunktion](~/task-modules-and-cards/cards/dynamic-search.md) über ein dynamisch geladenes Dataset. Darüber hinaus können Benutzer innerhalb einer Liste mit einer begrenzten Anzahl von Auswahlmöglichkeiten eine statische Vorschlagssuche durchführen. Mobilgeräte- und Desktopclients unterstützen die dynamische Vorschlagssuche.

### <a name="adaptive-cards-and-incoming-webhooks"></a>Adaptive Karten und eingehende Webhooks

> [!NOTE]
>
> * Alle systemeigenen Schemaelemente adaptiver Karten, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.
> * Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)und [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

Mit adaptiven Karten mit eingehenden Webhooks können Sie die umfangreichen und flexiblen Funktionen adaptiver Karten nutzen. Dabei werden Daten mithilfe eingehender Webhooks in Microsoft Teams über ihren Webdienst gesendet.

## <a name="support-for-azure-ad-object-id-and-upn-in-user-mention"></a>Unterstützung für Azure AD Objekt-ID und UPN in Benutzererwähnung

Bots mit adaptiven Karten unterstützen Benutzererwähnungs-IDs, z. B. Microsoft Azure Active Directory (Azure AD)-Objekt-IDs und den Benutzerprinzipalnamen (User Principle Name, UPN) zusätzlich zu den bestehenden IDs. Eingehende Webhooks beginnen mit der Unterstützung der Benutzererwähnung in der adaptiven Karte mit der Azure AD-Objekt-ID und dem UPN.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kartentypen](~/task-modules-and-cards/cards/cards-reference.md)

## <a name="see-also"></a>Siehe auch

* [Formatieren von Karten in Microsoft Teams](~/task-modules-and-cards/cards/cards-format.md)
* [Entwerfen adaptiver Karten](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Adaptive Karten in Bots](../bots/how-to/conversations/conversation-messages.md#adaptive-cards)
