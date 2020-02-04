---
title: Erstellen eines Befehlsmenüs für Ihren bot
author: clearab
description: Vorgehensweise Erstellen eines Befehlsmenüs für Ihren Microsoft Teams-bot
ms.topic: overview, command menu
ms.author: anclear
ms.openlocfilehash: 81efb94fc882aa4653ab162863d5d973aeae87b9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674221"
---
# <a name="bot-command-menus"></a><span data-ttu-id="a2f17-103">Bot-Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="a2f17-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> <span data-ttu-id="a2f17-104">Bot-Menüs werden nicht auf mobilen Clients angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a2f17-104">Bot menus won't appear on mobile clients.</span></span>

<span data-ttu-id="a2f17-105">Mit dem Befehl Menü hinzufügen für Ihren bot können Sie eine Reihe von Kern Befehlen definieren, auf die ihr bot immer Antworten kann.</span><span class="sxs-lookup"><span data-stu-id="a2f17-105">Add command menu for your bot allows you to define a set of core commands your bot can always respond to.</span></span> <span data-ttu-id="a2f17-106">Die Liste der Befehle wird dem Benutzer über dem Bereich zum Verfassen von Nachrichten angezeigt, wenn Sie mit Ihrem bot in Kontakt kommen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-106">The list of commands is presented to the user above the compose message area when they are conversing with your bot.</span></span> <span data-ttu-id="a2f17-107">Wenn Sie einen Befehl aus der Liste auswählen, wird die Befehlszeichenfolge in das Meldungsfeld verfassen eingefügt, dann müssen alle Benutzer die Option **senden**auswählen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-107">Selecting a command from the list will insert the command string into the compose message box, then all users need to do is select **Send**.</span></span>

![Bot-Befehlsmenü](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="a2f17-109">Erstellen eines Befehlsmenüs für Ihren bot</span><span class="sxs-lookup"><span data-stu-id="a2f17-109">Create a command menu for your bot</span></span>

<span data-ttu-id="a2f17-110">Befehlsmenüs werden in Ihrem App-Manifest definiert.</span><span class="sxs-lookup"><span data-stu-id="a2f17-110">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="a2f17-111">Sie können entweder App Studio verwenden, um Sie bei der Erstellung zu unterstützen, oder diese manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-111">You can either use App Studio to help you create them, or add them manually.</span></span>

### <a name="creating-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="a2f17-112">Erstellen eines Befehlsmenüs für Ihren bot mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="a2f17-112">Creating a command menu for your bot using App Studio</span></span>

<span data-ttu-id="a2f17-113">In den hier beschriebenen Anweisungen wird davon ausgegangen, dass Sie ein vorhandenes App-Manifest bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="a2f17-113">The instructions here assume that you'll be editing an existing app manifest.</span></span> <span data-ttu-id="a2f17-114">Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="a2f17-114">The steps for adding a command menu are the same, whether you're creating a new manifest or editing an existing one.</span></span>

1. <span data-ttu-id="a2f17-115">Öffnen Sie App Studio aus dem... Überlaufmenü auf der linken Navigations Schiene.</span><span class="sxs-lookup"><span data-stu-id="a2f17-115">Open App Studio from the ... overflow menu on the left navigation rail.</span></span> <span data-ttu-id="a2f17-116">Wenn Sie kein App-Studio zur Verfügung haben, können Sie es herunterladen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-116">If you don't have App Studio available you can download it.</span></span> <span data-ttu-id="a2f17-117">Weitere Informationen zur Verwendung von App Studio finden Sie unter [Installing App Studio](https://aka.ms/teams-app-studio#installing-app-studio) .</span><span class="sxs-lookup"><span data-stu-id="a2f17-117">See [Installing App Studio](https://aka.ms/teams-app-studio#installing-app-studio) for more information on using App Studio.</span></span>

    ![App Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="a2f17-119">Klicken Sie in App Studio auf die Registerkarte **Manifest-Editor** .</span><span class="sxs-lookup"><span data-stu-id="a2f17-119">Once in App Studio, select the **Manifest editor** tab.</span></span>

3. <span data-ttu-id="a2f17-120">Wählen Sie in der linken Spalte der Manifest-Editor-Ansicht im Abschnitt " **Funktionen** " die Option " **Bots**" aus.</span><span class="sxs-lookup"><span data-stu-id="a2f17-120">In the left column of the manifest editor view in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="a2f17-121">Klicken Sie in der rechten Spalte der Manifest-Editor-Ansicht im Abschnitt **Befehle** auf die Schaltfläche **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="a2f17-121">In the right column of the manifest editor view in the **Commands** section, select the **Add** button.</span></span>

    ![Schaltfläche "App Studio-Befehlsmenü hinzufügen"](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="a2f17-123">Der Bildschirm **neuer Befehl** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a2f17-123">The **New Command** screen appears.</span></span> <span data-ttu-id="a2f17-124">Geben Sie den **Befehlstext** ein, der als Menübefehl angezeigt werden soll, und der **Hilfetext** , den Sie direkt unter dem Befehlstext im Menü anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="a2f17-124">Enter the **Command text** that you want to have appear as the menu command, and the **Help text** that you want to have appear directly under the command text in the menu.</span></span> <span data-ttu-id="a2f17-125">Dies sollte eine kurze Erläuterung des Zwecks des Befehls sein.</span><span class="sxs-lookup"><span data-stu-id="a2f17-125">This should be a brief explanation of the purpose of the command.</span></span>

6. <span data-ttu-id="a2f17-126">Wählen Sie als nächstes die Bereiche aus, in denen dieses Befehlsmenü angezeigt werden soll, und wählen Sie dann die Schaltfläche **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="a2f17-126">Next, select the scope(s) where you want this command menu to appear, then select the **Save** button.</span></span>

    ![Schaltfläche "App Studio-Befehlsmenü hinzufügen"](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="creating-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="a2f17-128">Erstellen eines Befehlsmenüs für Ihren bot durch Bearbeiten von **Manifest. JSON**</span><span class="sxs-lookup"><span data-stu-id="a2f17-128">Creating a command menu for your bot by editing **Manifest.json**</span></span>

<span data-ttu-id="a2f17-129">Ein weiterer gültiger Ansatz zum Erstellen eines Befehlsmenüs besteht darin, es beim Entwickeln Ihres bot-Quellcodes direkt in der Manifestdatei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-129">Another valid approach for creating a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="a2f17-130">Hier sind einige Punkte, die Sie bei der Verwendung dieses Ansatzes beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="a2f17-130">Here are a few things to keep in mind when using this approach:</span></span>

1. <span data-ttu-id="a2f17-131">Jedes Menü unterstützt bis zu 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="a2f17-131">Each menu supports up to 10 commands.</span></span>

2. <span data-ttu-id="a2f17-132">Sie können ein einzelnes Befehlsmenü erstellen, das in allen Bereichen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a2f17-132">You can create a single command menu that will work in all scopes.</span></span>

3. <span data-ttu-id="a2f17-133">Sie können für jeden Bereich ein anderes Befehlsmenü erstellen.</span><span class="sxs-lookup"><span data-stu-id="a2f17-133">You can create a different command menu for each scope</span></span>

#### <a name="manifest-example---single-menu-for-both-scopes"></a><span data-ttu-id="a2f17-134">Manifest-Beispiel – einzelnes Menü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="a2f17-134">Manifest example - single menu for both scopes</span></span>

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

#### <a name="manifest-example---menu-for-each-scope"></a><span data-ttu-id="a2f17-135">Manifest-Beispielmenü für jeden Bereich</span><span class="sxs-lookup"><span data-stu-id="a2f17-135">Manifest example - menu for each scope</span></span>

```json
{
  ...
  "bots":[
    {
      "botId":"<Microsoft app ID for your bot>",
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

## <a name="handling-menu-commands-in-your-bot-code"></a><span data-ttu-id="a2f17-136">Behandeln von Menübefehlen in Ihrem bot-Code</span><span class="sxs-lookup"><span data-stu-id="a2f17-136">Handling menu commands in your bot code</span></span>

<span data-ttu-id="a2f17-137">Bots in einer Gruppe oder einem Kanal reagieren nur, wenn Sie in einer Nachricht erwähnt werden ("@botname").</span><span class="sxs-lookup"><span data-stu-id="a2f17-137">Bots in a group or channel respond only when they are mentioned ("@botname") in a message.</span></span> <span data-ttu-id="a2f17-138">Daher werden alle Nachrichten, die von einem bot empfangen werden, wenn Sie sich in einer Gruppe oder einem Kanalbereich befinden, im zurückgegebenen Nachrichtentext einen eigenen Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="a2f17-138">As a result, every message received by a bot when in a group or channel scope will contain its own name in the message text returned.</span></span> <span data-ttu-id="a2f17-139">Sie müssen sicherstellen, dass Ihre Nachrichten Analyse diese behandelt, bevor der zurückgegebene Befehl verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="a2f17-139">You need to ensure your message parsing handles that before handling the command being returned.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="a2f17-140">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="a2f17-140">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="a2f17-141">Sie können den \*\* \@mention\*\* -Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode `Activity` der benannten `RemoveRecipientMention`Klasse.</span><span class="sxs-lookup"><span data-stu-id="a2f17-141">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="a2f17-142">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="a2f17-142">JavaScript/Node.js</span></span>](#tab/javascript)

<span data-ttu-id="a2f17-143">Sie können den \*\* \@mention\*\* -Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode `TurnContext` der benannten `removeMentionText`Klasse.</span><span class="sxs-lookup"><span data-stu-id="a2f17-143">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `removeMentionText`.</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="pythontabpython"></a>[<span data-ttu-id="a2f17-144">Python</span><span class="sxs-lookup"><span data-stu-id="a2f17-144">Python</span></span>](#tab/python)


<span data-ttu-id="a2f17-145">Sie können den **@mention** Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode der `TurnContext` benannten `remove_recipient_mention`Klasse.</span><span class="sxs-lookup"><span data-stu-id="a2f17-145">You can parse out the **@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework — a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

## <a name="command-menu-best-practices"></a><span data-ttu-id="a2f17-146">Bewährte Methoden im Befehlsmenü</span><span class="sxs-lookup"><span data-stu-id="a2f17-146">Command menu best practices</span></span>

* <span data-ttu-id="a2f17-147">**Halten Sie es einfach**: das bot-Menü soll die Hauptfunktionen Ihres bot präsentieren.</span><span class="sxs-lookup"><span data-stu-id="a2f17-147">**Keep it simple**: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="a2f17-148">**Halten Sie es kurz**: Menü Optionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen sein – Sie sollten einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="a2f17-148">**Keep it short**: Menu options shouldn’t be extremely long and complex natural language statements — they should be simple commands.</span></span>
* <span data-ttu-id="a2f17-149">**Keep it aufrufbaren**: bot-Menü Aktionen/-Befehle sollten immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der bot befindet.</span><span class="sxs-lookup"><span data-stu-id="a2f17-149">**Keep it invokable**: Bot menu actions/commands should always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>
