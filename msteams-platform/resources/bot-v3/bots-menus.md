---
title: Hinzufügen eines Bot-Menüs
description: Beschreibt das Erstellen von Menüs für Bots in Microsoft Teams
keywords: Teams Bots Menüs Erstellung
ms.topic: how-to
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: da6f36e1b7071b92f6411ab7d2afdccb795946b7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566768"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Hinzufügen eines Bot-Menüs in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Um die Ermittlung zu unterstützen und Benutzer über die Funktionalität Ihres Bots aufzuklären, können Sie jetzt Menüs hinzufügen, die immer dann auftauchen, wenn der Benutzer mit Ihrem Bot interagiert. Das Menü zeigt den Befehlstext an und stellt auch Hilfetext bereit, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Befehlszwecks.

![Screenshot des Bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um die Vervollständigung der Bot-Nachricht durch den Benutzer zu unterstützen.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Bot-Menü-Unterstützung auf Teams mobilen App
> [!NOTE] 
> Bot-Menüs werden auf mobilen Geräten nicht angezeigt.

## <a name="app-manifest"></a>App-Manifest

Um ein Bot-Menü zu erstellen, fügen Sie Ihrem App-Manifest unter dem Abschnitt Bot ein neues [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Objekt hinzu. Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr Bot unterstützt ( `personal` , , oder ) Jedes Menü unterstützt bis zu `groupChat` `team` 10 Befehle.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Manifestauszug - Einzelmenü für beide Bereiche

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Manifestauszug - separates Menü pro Bereich

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

* Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots präsentieren.
* Kurz halten: Menüoptionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen sein - sie sollten einfache Befehle sein.
* Immer verfügbar: Bot-Menüaktionen/Befehle sollten immer invokierbar sein, unabhängig vom Zustand der Unterhaltung oder dem Dialog, in dem sich der Bot befindet.
