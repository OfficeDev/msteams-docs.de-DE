---
title: Universelle Aktionen für suchbasierte Nachrichtenerweiterungen
author: v-ypalikila
description: In diesem Artikel erfahren Sie mehr über universelle Aktionen und die automatische Aktualisierung für adaptive Karten in suchbasierten Nachrichtenerweiterungen.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
ms.openlocfilehash: 78b8c525b51603245fc379a826fa0cc11cbc5fd8
ms.sourcegitcommit: 176bbca74ba46b7ac298899d19a2d75087fb37c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2022
ms.locfileid: "68376592"
---
# <a name="universal-actions-for-search-based-message-extensions"></a>Universelle Aktionen für suchbasierte Nachrichtenerweiterungen

Adaptive Karten in suchbasierten Nachrichtenerweiterungen unterstützen jetzt universelle Aktionen. Um universelle Aktionen für suchbasierte Nachrichtenerweiterungen zu aktivieren, muss die App dem [Schema für universelle Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#schema-for-universal-actions-for-adaptive-cards) sowie den folgenden Anforderungen entsprechen:

1. Für die App muss ein Unterhaltungs-Bot im App-Manifest definiert sein.
1. Wenn Sie bereits über einen Unterhaltungs-Bot verfügen, müssen Sie denselben Bot verwenden, der in Ihrer Nachrichtenerweiterung verwendet wird.
1. Wenn die Karte in einer Gruppe gesendet wird, muss die App den Bot im Manifest angeben `team` oder `groupchat` den Bereich festlegen.

Beispiel für ein JSON-Schema mit `team` und `groupchat` Werten:

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

Aktivieren Sie die automatische Aktualisierung für adaptive Karten in suchbasierten Nachrichtenerweiterungen, um sicherzustellen, dass Benutzern immer die neuesten Informationen angezeigt werden. Definieren Sie `userIds` zum Aktivieren das Array entweder in  `29:<ID>` der Eigenschaft oder `8:orgid:<AAD ID>` das Format in der `refresh` Eigenschaft. Weitere Informationen finden Sie [unter Arbeiten mit universellen Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#user-ids-in-refresh).

Beispiel für `userIds` ein Array in der `refresh` Eigenschaft:

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
> Die automatische Aktualisierung ist für alle Benutzer im Gruppenchat oder -kanal mit *mindestens* 60 Benutzern aktiviert. Für Unterhaltungen (Gruppenchat oder Kanal) mit mehr als 60 Benutzern können Benutzer die Schaltfläche "Aktualisieren" im Menü "Nachrichtenoptionen" verwenden, um das neueste Ergebnis zu erhalten.

`Action.Execute` Beispiel für die `refresh` Eigenschaft:

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

## <a name="just-in-time-install"></a>Just-in-Time-Installation

Mit Just-in-Time (JIT) können Sie eine Karte oder Nachrichtenerweiterung für mehrere Benutzer in einem Gruppenchat oder Kanal installieren. Um universelle Aktionen in suchbasierten Nachrichtenerweiterungen zu unterstützen, wird Ihr Bot der Unterhaltung hinzugefügt, in der die Karte (mit `Action.Execute`) vom Benutzer gesendet wird.

Wenn ein Benutzer eine Karte auswählt und sie in einem Gruppenchat oder Kanal sendet,  wird eine JIT-Installationsaufforderung angezeigt. Nachdem der Benutzer die **Sendeoption** ausgewählt hat, wird die App für alle Benutzer im Chat oder Kanal im Hintergrund hinzugefügt.

> [!NOTE]
> Für Apps, die nicht definiert sind `Action.Execute` und `refresh` für die kein Schema definiert ist, wird die Installationsaufforderung den Benutzern nicht angezeigt.

Beispiel für einen dynamischen ME- und JIT-Installationsbenutzerablauf:

  :::image type="content" source="../../../assets/videos/dynamic-me-jit-flow.gif" alt-text="GIF zeigt den Benutzerablauf für eine dynamische Nachrichtenerweiterung und JIT-Installation an.":::

## <a name="see-also"></a>Siehe auch

* [Nachrichtenerweiterungen](../../what-are-messaging-extensions.md)
* [Universal-Aktionen für adaptive Karten](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Overview.md)
