---
title: Hinzufügen eines Botmenüs
description: Beschreibt das Erstellen von Menüs für Bots in Microsoft Teams
keywords: Erstellen von Teams-Bots-Menüs
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: f4190d0b21abbe00994e082000202b7bc65b917c
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019769"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Hinzufügen eines Botmenüs in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Um die Suche zu unterstützen und Benutzer über die Funktionalität Ihres Bots aufzuklären, können Sie jetzt Menüs hinzufügen, die angezeigt werden, wenn der Benutzer mit Ihrem Bot interagiert. Das Menü zeigt den Befehlstext an und enthält auch Hilfetext, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Zwecks des Befehls.

![Screenshot des Botmenüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um den Benutzer beim Ausfüllen der Botnachricht zu helfen.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Bot-Menüunterstützung in mobilen Teams-Apps
> [!NOTE] 
> Botmenüs werden auf mobilen Geräten nicht angezeigt

## <a name="app-manifest"></a>App-Manifest

Um ein Botmenü zu erstellen, fügen Sie ihrem App-Manifest unter dem [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Bot-Abschnitt ein neues Objekt hinzu. Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr Bot unterstützt ( oder ) Jedes Menü unterstützt bis `personal` `groupChat` zu `team` 10 Befehle.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Manifestauszug – einzelnes Menü für beide Bereiche

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "scopes": [
        "personal",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team",
            "personal"
          ],
          "commands":[
            {
              "title":"Help",
              "description":"Displays this help message"
            },
            {
              "title":"Search Flights",
              "description":"Search flights from Seattle to Phoenix May 2-5 departing after 3pm"
            },
            {
              "title":"Search Hotels",
              "description":"Search hotels in Portland tonight"
            },
            {
              "title":"Best Time to Fly",
              "description":"Best time to fly to London for a 5 day trip this summer"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Manifestauszug – separates Menü pro Bereich

```json
{
  ...
  "bots":[
    {
      "botId":"[Microsoft app ID for your bot]",
      "scopes": [
        "groupChat",
        "team"
      ],
      "commandLists":[
        {
          "scopes":[
            "team"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for channels"
            }
          ]
        },
        {
          "scopes":[
            "groupChat"
          ],
          "commands":[
            {
            "title":"help",
            "description":"Displays this help message for group chat"
            }
          ]
        }
      ]
    }
  ],
  ...
}
```

## <a name="best-practices"></a>Bewährte Methoden

* Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots präsentieren.
* Kurz: Menüoptionen sollten keine extrem langen und komplexen Anweisungen für natürliche Sprachen sein , sie sollten einfache Befehle sein.
* Immer verfügbar: Bot-Menüaktionen/-befehle sollten unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet, immer zur Verfügung stehen.
