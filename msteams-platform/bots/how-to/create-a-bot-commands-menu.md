---
title: Erstellen eines Befehlsmenüs für Ihren Bot
author: clearab
description: Erstellen eines Befehlsmenüs für Ihren Microsoft Teams-Bot
ms.topic: how-to
ms.author: anclear
ms.openlocfilehash: a4d53d8287d425120d24f559b8ffffabebdbcfb4
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995897"
---
# <a name="bot-command-menus"></a><span data-ttu-id="8eec6-103">Bot-Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="8eec6-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> <span data-ttu-id="8eec6-104">Botmenüs werden auf mobilen Clients nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8eec6-104">Bot menus do not appear on mobile clients.</span></span>

<span data-ttu-id="8eec6-105">Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-105">To define a set of core commands that your bot can respond to, you can add a command menu with a drop-down list of commands for your bot.</span></span> <span data-ttu-id="8eec6-106">Die Liste der Befehle wird den Benutzern im Bereich Verfassen von Nachrichten angezeigt, wenn sie mit Ihrem Bot in Unterhaltung sind.</span><span class="sxs-lookup"><span data-stu-id="8eec6-106">The list of commands is presented to the users in the compose message area when they are in conversation with your bot.</span></span> <span data-ttu-id="8eec6-107">Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Meldungsfeld verfassen ein, und wählen Sie **Senden aus.**</span><span class="sxs-lookup"><span data-stu-id="8eec6-107">Select a command from the list to insert the command string into the compose message box and select **Send**.</span></span>

![Befehlsmenü "Bot"](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="8eec6-109">Erstellen eines Befehlsmenüs für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="8eec6-109">Create a command menu for your bot</span></span>

<span data-ttu-id="8eec6-110">Befehlsmenüs werden in Ihrem App-Manifest definiert.</span><span class="sxs-lookup"><span data-stu-id="8eec6-110">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="8eec6-111">Sie können app **Studio** verwenden, um sie zu erstellen, oder sie manuell im App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-111">You can either use **App Studio** to create them or add them manually in the app manifest.</span></span>

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="8eec6-112">Erstellen eines Befehlsmenüs für Ihren Bot mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="8eec6-112">Create a command menu for your bot using App Studio</span></span>

<span data-ttu-id="8eec6-113">Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot ist, dass Sie ein vorhandenes App-Manifest bearbeiten müssen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-113">A prerequisite to create a command menu for your bot is that you must edit an existing app manifest.</span></span> <span data-ttu-id="8eec6-114">Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="8eec6-114">The steps to add a command menu are the same, whether you create a new manifest or edit an existing one.</span></span>

<span data-ttu-id="8eec6-115">**So erstellen Sie ein Befehlsmenü für Ihren Bot mithilfe von App Studio**</span><span class="sxs-lookup"><span data-stu-id="8eec6-115">**To create a command menu for your bot using App Studio**</span></span>

1. <span data-ttu-id="8eec6-116">Öffnen Sie Teams, und wählen **Sie apps** im linken Bereich aus.</span><span class="sxs-lookup"><span data-stu-id="8eec6-116">Open Teams and select **Apps** from the left pane.</span></span> <span data-ttu-id="8eec6-117">Suchen Sie **auf** der Seite Apps nach **App Studio,** und wählen Sie **Öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="8eec6-117">In the **Apps** page, search for **App Studio**, and select **Open**.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="8eec6-118">Wenn Sie nicht über **App Studio verfügen,** können Sie es herunterladen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-118">If you do not have **App Studio**, you can download it.</span></span> <span data-ttu-id="8eec6-119">Weitere Informationen finden Sie unter [Installieren von App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).</span><span class="sxs-lookup"><span data-stu-id="8eec6-119">For more information, see [installing App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).</span></span>

    ![App-Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="8eec6-121">Wählen **Sie in App Studio** die Registerkarte **Manifest-Editor** aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren.</span><span class="sxs-lookup"><span data-stu-id="8eec6-121">In **App Studio**, select the **Manifest editor** tab. If you do not have an existing app package, you can create or import an existing app.</span></span> <span data-ttu-id="8eec6-122">Weitere Informationen finden Sie unter [Update an app package](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).</span><span class="sxs-lookup"><span data-stu-id="8eec6-122">For more information, see [update an app package](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).</span></span>

3. <span data-ttu-id="8eec6-123">Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **Funktionen** die Option **Bots aus.**</span><span class="sxs-lookup"><span data-stu-id="8eec6-123">In the left pane of the **Manifest editor** and in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="8eec6-124">Wählen Sie im rechten Bereich des **Manifest-Editors** und im Abschnitt **Befehle** die Option **Hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="8eec6-124">In the right pane of the **Manifest editor** and in the **Commands** section, select **Add**.</span></span> <span data-ttu-id="8eec6-125">Der **Bildschirm Neuer Befehl** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8eec6-125">The **New Command** screen appears.</span></span>

    ![App Studio-Befehlsmenü Schaltfläche hinzufügen](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="8eec6-127">Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="8eec6-127">Enter the **Command text** that must appear as the command menu for your bot.</span></span>

6. <span data-ttu-id="8eec6-128">Geben Sie den **Hilfetext ein,** der im Menü unter dem Befehlstext angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="8eec6-128">Enter the **Help text** that must appear under the command text in the menu.</span></span> <span data-ttu-id="8eec6-129">**Hilfetext** muss eine kurze Erläuterung des Zwecks des Befehls sein.</span><span class="sxs-lookup"><span data-stu-id="8eec6-129">**Help text** must be a brief explanation of the purpose of the command.</span></span>

7. <span data-ttu-id="8eec6-130">Aktivieren Sie **die Kontrollkästchen** Bereich, um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="8eec6-130">Select the **Scope** check boxes to select where this command menu must appear, and select **Save**.</span></span>

    ![Menüschaltfläche für neue Befehle in App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="8eec6-132">Erstellen eines Befehlsmenüs für Ihren Bot durch Bearbeiten Manifest.js</span><span class="sxs-lookup"><span data-stu-id="8eec6-132">Create a command menu for your bot by editing Manifest.json</span></span>

<span data-ttu-id="8eec6-133">Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht in der direkten Erstellung in der Manifestdatei während der Entwicklung des Bot-Quellcodes.</span><span class="sxs-lookup"><span data-stu-id="8eec6-133">Another way to create a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="8eec6-134">Gehen Sie wie folgt vor, um diese Methode zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="8eec6-134">To use this method, follow these points:</span></span>

* <span data-ttu-id="8eec6-135">Jedes Menü unterstützt bis zu zehn Befehle.</span><span class="sxs-lookup"><span data-stu-id="8eec6-135">Each menu supports up to ten commands.</span></span>
* <span data-ttu-id="8eec6-136">Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereich funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8eec6-136">Create a single command menu that works in all scopes.</span></span>
* <span data-ttu-id="8eec6-137">Erstellen Sie für jeden Bereich ein anderes Befehlsmenü.</span><span class="sxs-lookup"><span data-stu-id="8eec6-137">Create a different command menu for each scope.</span></span>

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a><span data-ttu-id="8eec6-138">Manifestbeispiel für ein einzelnes Menü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="8eec6-138">Manifest example for single menu for both scopes</span></span>

<span data-ttu-id="8eec6-139">Der Manifestbeispielcode für ein einzelnes Menü für beide Bereiche lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8eec6-139">The manifest example code for single menu for both scopes is as follows:</span></span>

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

#### <a name="manifest-example-for-the-menu-for-each-scope"></a><span data-ttu-id="8eec6-140">Manifestbeispiel für das Menü für jeden Bereich</span><span class="sxs-lookup"><span data-stu-id="8eec6-140">Manifest example for the menu for each scope</span></span>

<span data-ttu-id="8eec6-141">Der Manifestbeispielcode für das Menü für jeden Bereich lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8eec6-141">The manifest example code for the menu for each scope is as follows:</span></span>

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

<span data-ttu-id="8eec6-142">Sie müssen Menübefehle in Ihrem Botcode behandeln, während Sie alle Nachrichten von Benutzern verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="8eec6-142">You must handle menu commands in your bot code as you handle any message from users.</span></span> <span data-ttu-id="8eec6-143">Sie können Menübefehle in Ihrem Botcode verarbeiten, indem Sie den Abschnitt **\@ Erwähnung** des Nachrichtentexts aussingen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-143">You can handle menu commands in your bot code by parsing out the **\@Mention** portion of the message text.</span></span>

## <a name="handle-menu-commands-in-your-bot-code"></a><span data-ttu-id="8eec6-144">Behandeln von Menübefehlen in Ihrem Botcode</span><span class="sxs-lookup"><span data-stu-id="8eec6-144">Handle menu commands in your bot code</span></span>

<span data-ttu-id="8eec6-145">Bots in einer Gruppe oder einem Kanal reagieren nur, wenn sie in einer `@botname` Nachricht erwähnt werden.</span><span class="sxs-lookup"><span data-stu-id="8eec6-145">Bots in a group or channel respond only when they are mentioned `@botname` in a message.</span></span> <span data-ttu-id="8eec6-146">Jede Nachricht, die von einem Bot empfangen wird, wenn sie sich in einem Gruppen- oder Kanalbereich befindet, enthält ihren Namen im zurückgegebenen Nachrichtentext.</span><span class="sxs-lookup"><span data-stu-id="8eec6-146">Every message received by a bot when in a group or channel scope contains its name in the message text returned.</span></span> <span data-ttu-id="8eec6-147">Vor der Verarbeitung des zurückgegebenen Befehls muss ihre Nachrichten parsing die Nachricht behandeln, die von einem Bot mit seinem Namen empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="8eec6-147">Before handling the command being returned, your message parsing must handle the message received by a bot with its name.</span></span>

> [!NOTE]
> <span data-ttu-id="8eec6-148">Um die Befehle im Code zu verarbeiten, werden sie als reguläre Nachricht an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="8eec6-148">To handle the commands in code, they are sent to your bot as a regular message.</span></span> <span data-ttu-id="8eec6-149">Sie müssen sie wie jede andere Nachricht von Ihren Benutzern behandeln.</span><span class="sxs-lookup"><span data-stu-id="8eec6-149">You must handle them as you would handle any other message from your users.</span></span> <span data-ttu-id="8eec6-150">Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein.</span><span class="sxs-lookup"><span data-stu-id="8eec6-150">The commands in code insert pre-configured text into the text box.</span></span> <span data-ttu-id="8eec6-151">Der Benutzer muss dann den Text wie für jede andere Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="8eec6-151">The user must then send that text as they do for any other message.</span></span>

# <a name="c"></a>[<span data-ttu-id="8eec6-152">C#</span><span class="sxs-lookup"><span data-stu-id="8eec6-152">C#</span></span>](#tab/dotnet)

<span data-ttu-id="8eec6-153">Sie können den Abschnitt **\@ Erwähnung** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Microsoft Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8eec6-153">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework.</span></span> <span data-ttu-id="8eec6-154">Es handelt sich um eine Methode der `Activity` Klasse namens `RemoveRecipientMention` .</span><span class="sxs-lookup"><span data-stu-id="8eec6-154">It is a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

<span data-ttu-id="8eec6-155">Der C# Code zum Analysieren des Abschnitts **\@ Erwähnung** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8eec6-155">The C# code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[<span data-ttu-id="8eec6-156">JavaScript</span><span class="sxs-lookup"><span data-stu-id="8eec6-156">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="8eec6-157">Sie können den Abschnitt **\@ Erwähnung** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8eec6-157">You can parse out the **\@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="8eec6-158">Es handelt sich um eine Methode der `TurnContext` Klasse namens `removeMentionText` .</span><span class="sxs-lookup"><span data-stu-id="8eec6-158">It is a method of the `TurnContext` class named `removeMentionText`.</span></span>

<span data-ttu-id="8eec6-159">Der JavaScript-Code zum Analysieren des **\@ Abschnitts Erwähnung** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8eec6-159">The JavaScript code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[<span data-ttu-id="8eec6-160">Python</span><span class="sxs-lookup"><span data-stu-id="8eec6-160">Python</span></span>](#tab/python)

<span data-ttu-id="8eec6-161">Sie können den **@Mention** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8eec6-161">You can parse out the **@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="8eec6-162">Es handelt sich um eine Methode der `TurnContext` Klasse namens `remove_recipient_mention` .</span><span class="sxs-lookup"><span data-stu-id="8eec6-162">It is a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

<span data-ttu-id="8eec6-163">Der Python-Code zum Analysieren des **\@ Abschnitts Erwähnung** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8eec6-163">The Python code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

<span data-ttu-id="8eec6-164">Um eine reibungslose Funktionsweise Ihres Botcodes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-164">To enable smooth functioning of your bot code, there are few best practices that you must follow.</span></span>

## <a name="command-menu-best-practices"></a><span data-ttu-id="8eec6-165">Bewährte Methoden im Befehlsmenü</span><span class="sxs-lookup"><span data-stu-id="8eec6-165">Command menu best practices</span></span>

<span data-ttu-id="8eec6-166">Im Folgenden finden Sie die bewährten Methoden für das Befehlsmenü:</span><span class="sxs-lookup"><span data-stu-id="8eec6-166">Following are the command menu best practices:</span></span>

* <span data-ttu-id="8eec6-167">Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots präsentieren.</span><span class="sxs-lookup"><span data-stu-id="8eec6-167">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="8eec6-168">Kurz halten: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen Anweisungen für natürliche Sprachen sein.</span><span class="sxs-lookup"><span data-stu-id="8eec6-168">Keep it short: Menu options must not be long and must not be complex natural language statements.</span></span> <span data-ttu-id="8eec6-169">Es müssen einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="8eec6-169">They must be simple commands.</span></span>
* <span data-ttu-id="8eec6-170">Lassen Sie es unanfehlbar: Bot-Menüaktionen oder -befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet.</span><span class="sxs-lookup"><span data-stu-id="8eec6-170">Keep it invokable: Bot menu actions or commands must always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>

> [!NOTE]
> <span data-ttu-id="8eec6-171">Wenn Sie Befehle aus Ihrem Manifest entfernen, müssen Sie Ihre App erneut bereitstellen, um die Änderungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="8eec6-171">If you remove any commands from your manifest, you must redeploy your app to implement the changes.</span></span> <span data-ttu-id="8eec6-172">Im Allgemeinen erfordern Änderungen am Manifest, dass Sie Ihre App erneut bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="8eec6-172">In general, any changes to the manifest require you to redeploy your app.</span></span>

## <a name="next-step"></a><span data-ttu-id="8eec6-173">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8eec6-173">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8eec6-174">Kanal- und Gruppenunterhaltungen</span><span class="sxs-lookup"><span data-stu-id="8eec6-174">Channel and group conversations</span></span>](~/bots/how-to/conversations/channel-and-group-conversations.md)
