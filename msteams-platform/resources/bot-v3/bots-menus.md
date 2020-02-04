---
title: Hinzufügen eines bot-Menüs
description: Beschreibt das Erstellen von Menüs für Bots in Microsoft Teams
keywords: Erstellen von Teams-Bots-Menüs
ms.date: 05/20/2019
ms.openlocfilehash: 36a224dc21cccc5fcd1047e45e3d749e7ca19ea7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674119"
---
# <a name="add-a-bot-menu-in-microsoft-teams"></a>Hinzufügen eines bot-Menüs in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Um die Suche zu unterstützen und die Benutzer über die Funktionalität Ihres bot zu informieren, können Sie jetzt Menüs hinzufügen, die immer dann angezeigt werden, wenn der Benutzer mit Ihrem bot interagiert. Im Menü wird der Befehlstext angezeigt und auch Hilfetext bereitgestellt, beispielsweise ein Verwendungsbeispiel oder eine Beschreibung des Befehls zwecks.

![Screenshot des bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um den Benutzer beim Abschluss der bot-Nachricht zu unterstützen.

## <a name="bot-menu-support-on-teams-mobile-app"></a>Unterstützung von bot-Menüs in Microsoft Teams Mobile App
> [!NOTE] 
> Bot-Menüs werden auf mobilen Geräten nicht angezeigt

## <a name="app-manifest"></a>App-Manifest

Um ein bot-Menü zu erstellen, fügen [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Sie dem App-Manifest im Abschnitt bot ein neues Objekt hinzu. Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr bot`personal`unter `groupChat` stützt `team`(, oder) unterstützt jedes Menü bis zu 10 Befehle.

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a>Manifest-Ausschnitt – einzelnes Menü für beide Bereiche

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a>Manifest-Auszug – separates Menü pro Bereich

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

* Halten Sie es einfach: das bot-Menü soll die Hauptfunktionen Ihres bot präsentieren.
* Halten Sie es kurz: Menü Optionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen-Sie sollten einfache Befehle sein.
* Immer verfügbar: Aktionen/Befehle im bot-Menü sollten immer aufrufbaren sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der bot befindet.
