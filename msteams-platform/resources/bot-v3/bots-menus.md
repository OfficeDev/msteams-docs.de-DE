---
title: Hinzufügen eines Botmenüs
description: Beschreibt, wie Menüs für Bots in Microsoft Teams
keywords: Erstellen von Teams-Bots-Menüs
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 6f339f23298c14607eb1d9ca12daa50bcc98775b
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452900"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Hinzufügen eines Botmenüs in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Um die Ermittlung zu unterstützen und Benutzer über die Funktionen Ihres Bots zu informieren, können Sie jetzt Menüs hinzufügen, die angezeigt werden, wenn der Benutzer mit Ihrem Bot interagiert. Im Menü wird der Befehlstext angezeigt und auch Hilfetext bereitgestellt, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Befehlszwecks.

![Screenshot des Bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um den Benutzer beim Abschließen der Bot-Nachricht zu unterstützen.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Bot-Menüunterstützung für Teams mobile App

> [!NOTE]
> Bot-Menüs werden nicht auf mobilen Geräten angezeigt.

## <a name="app-manifest"></a>App-Manifest

Um ein Botmenü zu erstellen, fügen Sie Ihrem App-Manifest unter dem Bot-Abschnitt ein neues [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Objekt hinzu. Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, `groupChat`den Ihr Bot unterstützt (`personal`oder `team`) Jedes Menü unterstützt bis zu 10 Befehle.

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

* Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Halten Sie es kurz: Menüoptionen sollten nicht extrem lange und komplexe natürliche Sprachanweisungen sein – sie sollten einfache Befehle sein.
* Immer verfügbar: Bot-Menüaktionen/-befehle sollten immer aufgerufen werden können, unabhängig vom Status der Unterhaltung oder dem Dialogfeld, in dem sich der Bot befindet.
