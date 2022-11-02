---
title: Universelle Aktionen für suchbasierte Nachrichtenerweiterungen
author: v-ypalikila
description: In diesem Artikel erfahren Sie mehr über universelle Aktionen und die automatische Aktualisierung für adaptive Karten in suchbasierten Nachrichtenerweiterungen.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
ms.openlocfilehash: 18f5b783797d69144aac82e5ebd95fc30dad57a2
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819968"
---
# <a name="universal-actions-for-search-based-message-extensions"></a>Universelle Aktionen für suchbasierte Nachrichtenerweiterungen

Adaptive Karten in suchbasierten Nachrichtenerweiterungen unterstützen jetzt Universelle Aktionen. Um Universelle Aktionen für suchbasierte Nachrichtenerweiterungen zu aktivieren, muss die App dem [Schema für Universelle Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#schema-for-universal-actions-for-adaptive-cards) sowie den folgenden Anforderungen entsprechen:

1. Für die App muss ein Konversationsbot im App-Manifest definiert sein.
1. Wenn Sie bereits über einen Konversationsbot verfügen, müssen Sie denselben Bot verwenden, der in Ihrer Nachrichtenerweiterung verwendet wird.
1. Wenn die Karte in einer Gruppe gesendet wird, muss die App für ihren Bot im Manifest angeben oder `groupchat` den Bereich angeben`team`.

Beispiel für ein JSON-Schema mit `team` den Werten und `groupchat` :

```json
{
    "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    "id": "%MICROSOFT-APP-ID%",
    "bots": [
        {
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
            "scopes": [
                    "team",
                    "personal",
                    "groupchat"
                ]
        }
    ],
    "composeExtensions": [
        {
            "canUpdateConfiguration": true,
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%", // Use the same bot as what is specified in the bots section above
        }
    ]
}
```

## <a name="automatic-refresh-for-adaptive-cards-in-search-based-message-extensions"></a>Automatische Aktualisierung für adaptive Karten in suchbasierten Nachrichtenerweiterungen

Aktivieren Sie die automatische Aktualisierung für adaptive Karten in suchbasierten Nachrichtenerweiterungen, um sicherzustellen, dass Benutzer immer die neuesten Informationen sehen. Um dies zu aktivieren, definieren Sie `userIds` das Array entweder im  `29:<ID>` -Format oder `8:orgid:<AAD ID>` in der `refresh` -Eigenschaft. Weitere Informationen finden Sie unter [Arbeiten mit universellen Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#user-ids-in-refresh).

Beispiel für ein `userIds` Array in der `refresh` -Eigenschaft:

```json
    {
        "type": "AdaptiveCard",
        "refresh": {
            "userIds": [
                "8:orgid:<AADID>",
                "29:<id>"
            ],
            "action": {
                "type": "Action.Execute",
                "data": {}
            }
        },
        "body": [
            {
                "type": "TextBlock",
                "text": "Hello World!",
                "wrap": true
            }
        ],
        "actions": [
            {
                "type": "Action.Execute",
                "data": {},
                "title": "Hello"
            }
        ]
    }
```

> [!NOTE]
> Die automatische Aktualisierung ist für alle Benutzer im Gruppenchat oder Kanal mit *weniger als oder gleich* 60 Benutzern aktiviert. Für Unterhaltungen (Gruppenchat oder Kanal) mit mehr als 60 Benutzern können Benutzer die Schaltfläche Aktualisieren im Menü mit den Nachrichtenoptionen verwenden, um das neueste Ergebnis zu erhalten.

Beispiel für `Action.Execute` in der `refresh` -Eigenschaft:

```json
    {
        "type": "AdaptiveCard",
        "refresh": {
            "action": {
                "type": "Action.Execute",
                "data": {}
            }
        },
        "body": [
            {
                "type": "TextBlock",
                "text": "Hello World!",
                "wrap": true
            }
        ],
        "actions": [
            {
                "type": "Action.Execute",
                "data": {},
                "title": "Hello"
            }
        ]
    }
```

## <a name="just-in-time-install"></a>Just-In-Time-Installation

Just-in-Time (JIT) ermöglicht es Ihnen, eine Karte oder Nachrichtenerweiterung für mehrere Benutzer in einem Gruppenchat oder Kanal zu installieren. Um universelle Aktionen in suchbasierten Nachrichtenerweiterungen zu unterstützen, wird Ihr Bot der Konversation hinzugefügt, an die die Karte (mit `Action.Execute`) vom Benutzer gesendet wird.

Wenn ein Benutzer eine Karte auswählt und sie in einem Gruppenchat oder Kanal sendet, wird eine **JIT-Installationsaufforderung** angezeigt. Nachdem der Benutzer die **Option "Senden"** ausgewählt hat, wird die App für alle Benutzer im Chat oder Kanal im Hintergrund hinzugefügt.

> [!NOTE]
> Für Apps, für die und `refresh` das Schema nicht `Action.Execute` definiert sind, wird den Benutzern die Installationsaufforderung nicht angezeigt.

Beispiel für einen dynamischen ME- und JIT-Installationsbenutzerflow:

  :::image type="content" source="../../../assets/videos/dynamic-me-jit-flow.gif" alt-text="GIF zeigt den Benutzerflow für eine dynamische Nachrichtenerweiterung und JIT-Installation an.":::

## <a name="see-also"></a>Siehe auch

* [Nachrichtenerweiterungen](../../what-are-messaging-extensions.md)
* [Adaptive Karten](../../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [Universal-Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Overview.md)
