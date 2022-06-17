---
title: Hinzufügen eines Botmenüs
description: In diesem Modul erfahren Sie, wie Sie ein Bot-Menü in Microsoft Teams hinzufügen und Menüs für Bots in Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: ed65699b930d3e5334dd7fbb03da18a1482d6e5d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143382"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Hinzufügen eines Botmenüs in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Um die Ermittlung zu erleichtern und Benutzer über die Funktionen Ihres Bots zu informieren, können Sie jetzt Menüs hinzufügen, die angezeigt werden, wenn der Benutzer mit Ihrem Bot interagiert. Das Menü zeigt den Befehlstext an und stellt auch Hilfetext bereit, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Befehlszwecks.

![Screenshot des Bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um die Vervollständigung der Bot-Nachricht durch den Benutzer zu unterstützen.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Bot-Menüunterstützung für Teams mobile App

> [!NOTE]
> Bot-Menüs werden auf mobilen Geräten nicht angezeigt.

## <a name="app-manifest"></a>App-Manifest

Um ein Bot-Menü zu erstellen, fügen Sie ihrem App-Manifest im Abschnitt "Bot" ein neues [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Objekt hinzu. Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr Bot unterstützt (`personal`oder `groupChat``team`) Jedes Menü unterstützt bis zu 10 Befehle.

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

* Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Halten Sie es kurz: Menüoptionen sollten nicht sehr lange und komplexe Anweisungen in natürlicher Sprache sein – sie sollten einfache Befehle sein.
* Immer verfügbar: Bot-Menüaktionen/Befehle sollten immer aufgerufen werden können, unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet.
