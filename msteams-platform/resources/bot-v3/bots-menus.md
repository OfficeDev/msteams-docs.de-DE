---
title: Hinzufügen eines Botmenüs
description: Beschreibt das Erstellen von Menüs für Bots in Microsoft Teams
keywords: Erstellen von Teams-Bots-Menüs
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
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="5bdd3-104">Hinzufügen eines Botmenüs in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5bdd3-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="5bdd3-105">Um die Suche zu unterstützen und Benutzer über die Funktionalität Ihres Bots aufzuklären, können Sie jetzt Menüs hinzufügen, die angezeigt werden, wenn der Benutzer mit Ihrem Bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="5bdd3-106">Das Menü zeigt den Befehlstext an und enthält auch Hilfetext, z. B. ein Verwendungsbeispiel oder eine Beschreibung des Zwecks des Befehls.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Screenshot des Botmenüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="5bdd3-108">Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um den Benutzer beim Ausfüllen der Botnachricht zu helfen.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="5bdd3-109">Botmenüunterstützung für Teams mobile App</span><span class="sxs-lookup"><span data-stu-id="5bdd3-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="5bdd3-110">Botmenüs werden auf mobilen Geräten nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-110">Bot menus are not displayed on mobile devices.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="5bdd3-111">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="5bdd3-111">App manifest</span></span>

<span data-ttu-id="5bdd3-112">Um ein Botmenü zu erstellen, fügen Sie ihrem App-Manifest unter dem [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Bot-Abschnitt ein neues Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="5bdd3-113">Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr Bot unterstützt ( , oder ) Jedes Menü unterstützt bis `personal` `groupChat` zu `team` 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat`, or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="5bdd3-114">Manifestauszug – einzelnes Menü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="5bdd3-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="5bdd3-115">Manifestauszug – separates Menü pro Bereich</span><span class="sxs-lookup"><span data-stu-id="5bdd3-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="5bdd3-116">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="5bdd3-116">Best practices</span></span>

* <span data-ttu-id="5bdd3-117">Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots präsentieren.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="5bdd3-118">Kurz: Menüoptionen sollten keine extrem langen und komplexen Anweisungen für natürliche Sprachen sein , sie sollten einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="5bdd3-119">Immer verfügbar: Bot-Menüaktionen/-befehle sollten unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet, immer zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
