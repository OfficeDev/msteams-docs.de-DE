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
# <a name="add-a-bot-menu-in-microsoft-teams"></a><span data-ttu-id="5adbc-104">Hinzufügen eines bot-Menüs in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5adbc-104">Add a bot menu in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="5adbc-105">Um die Suche zu unterstützen und die Benutzer über die Funktionalität Ihres bot zu informieren, können Sie jetzt Menüs hinzufügen, die immer dann angezeigt werden, wenn der Benutzer mit Ihrem bot interagiert.</span><span class="sxs-lookup"><span data-stu-id="5adbc-105">To aid discovery and to help educate users about your bot’s functionality, you can now add menus that surface whenever the user interacts with your bot.</span></span> <span data-ttu-id="5adbc-106">Im Menü wird der Befehlstext angezeigt und auch Hilfetext bereitgestellt, beispielsweise ein Verwendungsbeispiel oder eine Beschreibung des Befehls zwecks.</span><span class="sxs-lookup"><span data-stu-id="5adbc-106">The menu will show the command text and also provide help text, such as a usage example or description of the command’s purpose.</span></span>

![Screenshot des bot-Menüs](~/assets/images/bots/bot-menus-bot-menu-sample.png)

<span data-ttu-id="5adbc-108">Wenn ein Benutzer ein Menüelement auswählt, wird die Befehlszeichenfolge in das Textfeld eingefügt, um den Benutzer beim Abschluss der bot-Nachricht zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5adbc-108">When a user selects a menu item, the command string is inserted into the text box to aid in user completion of the bot message.</span></span>

## <a name="bot-menu-support-on-teams-mobile-app"></a><span data-ttu-id="5adbc-109">Unterstützung von bot-Menüs in Microsoft Teams Mobile App</span><span class="sxs-lookup"><span data-stu-id="5adbc-109">Bot menu support on Teams mobile app</span></span>
> [!NOTE] 
> <span data-ttu-id="5adbc-110">Bot-Menüs werden auf mobilen Geräten nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="5adbc-110">Bot menus are not displayed on mobile devices</span></span>

## <a name="app-manifest"></a><span data-ttu-id="5adbc-111">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="5adbc-111">App manifest</span></span>

<span data-ttu-id="5adbc-112">Um ein bot-Menü zu erstellen, fügen [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) Sie dem App-Manifest im Abschnitt bot ein neues Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="5adbc-112">To create a bot menu, add a new [`commandLists`](~/resources/schema/manifest-schema.md#botscommandlists) object to your app manifest under the bot section.</span></span> <span data-ttu-id="5adbc-113">Sie können einzelne Menüs mit separaten Befehlen für jeden Bereich deklarieren, den Ihr bot`personal`unter `groupChat` stützt `team`(, oder) unterstützt jedes Menü bis zu 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="5adbc-113">You can declare individual menus with separate commands for each scope your bot supports (`personal`, `groupChat` or `team`) Each menu supports up to 10 commands.</span></span>

### <a name="manifest-excerpt---single-menu-for-both-scopes"></a><span data-ttu-id="5adbc-114">Manifest-Ausschnitt – einzelnes Menü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="5adbc-114">Manifest excerpt - single menu for both scopes</span></span>

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

### <a name="manifest-excerpt---separate-menu-per-scope"></a><span data-ttu-id="5adbc-115">Manifest-Auszug – separates Menü pro Bereich</span><span class="sxs-lookup"><span data-stu-id="5adbc-115">Manifest excerpt - separate menu per scope</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="5adbc-116">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="5adbc-116">Best practices</span></span>

* <span data-ttu-id="5adbc-117">Halten Sie es einfach: das bot-Menü soll die Hauptfunktionen Ihres bot präsentieren.</span><span class="sxs-lookup"><span data-stu-id="5adbc-117">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="5adbc-118">Halten Sie es kurz: Menü Optionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen-Sie sollten einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="5adbc-118">Keep it short: Menu options shouldn’t be extremely long and complex natural language statements - they should be simple commands.</span></span>
* <span data-ttu-id="5adbc-119">Immer verfügbar: Aktionen/Befehle im bot-Menü sollten immer aufrufbaren sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der bot befindet.</span><span class="sxs-lookup"><span data-stu-id="5adbc-119">Always available: Bot menu actions/commands should be always invokable, regardless of the state of the conversation or the dialog the bot is in.</span></span>
