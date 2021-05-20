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
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="ae09a-104">Hinzufügen eines Bot-Menüs in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ae09a-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="ae09a-105">Um die Ermittlung zu unterstützen und Benutzer über die Funktionalität Ihres Bots aufzuklären, können Sie jetzt Menüs hinzufügen, die immer dann auftauchen, wenn der Benutzer mit Ihrem Bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="ae09a-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="ae09a-106">Das Menü zeigt den Befehlstext an und stellt auch Hilfetext bereit, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Befehlszwecks.</span><span class="sxs-lookup"><span data-stu-id="ae09a-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Screenshot des Bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="ae09a-108">Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um die Vervollständigung der Bot-Nachricht durch den Benutzer zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ae09a-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="ae09a-109">Bot-Menü-Unterstützung auf Teams mobilen App</span><span class="sxs-lookup"><span data-stu-id="ae09a-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="ae09a-110">Bot-Menüs werden auf mobilen Geräten nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ae09a-110">Bot menus are not displayed on mobile devices.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="ae09a-111">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="ae09a-111">App manifest</span></span>

<span data-ttu-id="ae09a-112">Um ein Bot-Menü zu erstellen, fügen Sie Ihrem App-Manifest unter dem Abschnitt Bot ein neues [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae09a-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="ae09a-113">Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr Bot unterstützt ( `personal` , , oder ) Jedes Menü unterstützt bis zu `groupChat` `team` 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="ae09a-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat`, or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="ae09a-114">Manifestauszug - Einzelmenü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="ae09a-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="ae09a-115">Manifestauszug - separates Menü pro Bereich</span><span class="sxs-lookup"><span data-stu-id="ae09a-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="ae09a-116">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="ae09a-116">Best practices</span></span>

* <span data-ttu-id="ae09a-117">Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots präsentieren.</span><span class="sxs-lookup"><span data-stu-id="ae09a-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="ae09a-118">Kurz halten: Menüoptionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen sein - sie sollten einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="ae09a-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="ae09a-119">Immer verfügbar: Bot-Menüaktionen/Befehle sollten immer invokierbar sein, unabhängig vom Zustand der Unterhaltung oder dem Dialog, in dem sich der Bot befindet.</span><span class="sxs-lookup"><span data-stu-id="ae09a-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
