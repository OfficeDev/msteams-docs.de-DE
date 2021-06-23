---
title: Erstellen eines Befehlsmenüs für Ihren Bot
author: surbhigupta
description: So erstellen Sie ein Befehlsmenü für Ihren Microsoft Teams-Bot
ms.topic: how-to
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 0b8793666e6478e69698c355fb9209d2ca5f5d1e
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068998"
---
# <a name="bot-command-menus"></a><span data-ttu-id="46abf-103">Bot-Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="46abf-103">Bot command menus</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="46abf-104">Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste von Befehlen für Ihren Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="46abf-104">To define a set of core commands that your bot can respond to, you can add a command menu with a drop-down list of commands for your bot.</span></span> <span data-ttu-id="46abf-105">Die Liste der Befehle wird den Benutzern im Bereich zum Verfassen von Nachrichten angezeigt, wenn sie sich in Einer Unterhaltung mit Ihrem Bot befinden.</span><span class="sxs-lookup"><span data-stu-id="46abf-105">The list of commands is presented to the users in the compose message area when they are in conversation with your bot.</span></span> <span data-ttu-id="46abf-106">Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Feld zum Verfassen von Nachrichten einzufügen, und wählen Sie **"Senden"** aus.</span><span class="sxs-lookup"><span data-stu-id="46abf-106">Select a command from the list to insert the command string into the compose message box and select **Send**.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="46abf-107">Desktop</span><span class="sxs-lookup"><span data-stu-id="46abf-107">Desktop</span></span>](#tab/desktop)

![Bot-Befehlsmenü](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[<span data-ttu-id="46abf-109">Mobilgerät</span><span class="sxs-lookup"><span data-stu-id="46abf-109">Mobile</span></span>](#tab/mobile)

![Befehlsmenü für mobile Bots](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a><span data-ttu-id="46abf-111">Erstellen eines Befehlsmenüs für Ihren Bot</span><span class="sxs-lookup"><span data-stu-id="46abf-111">Create a command menu for your bot</span></span>

<span data-ttu-id="46abf-112">Befehlsmenüs werden in Ihrem App-Manifest definiert.</span><span class="sxs-lookup"><span data-stu-id="46abf-112">Command menus are defined in your app manifest.</span></span> <span data-ttu-id="46abf-113">Sie können sie entweder mit **App Studio** erstellen oder manuell im App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="46abf-113">You can either use **App Studio** to create them or add them manually in the app manifest.</span></span>

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a><span data-ttu-id="46abf-114">Erstellen eines Befehlsmenüs für Ihren Bot mit App Studio</span><span class="sxs-lookup"><span data-stu-id="46abf-114">Create a command menu for your bot using App Studio</span></span>

<span data-ttu-id="46abf-115">Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot ist, dass Sie ein vorhandenes App-Manifest bearbeiten müssen.</span><span class="sxs-lookup"><span data-stu-id="46abf-115">A prerequisite to create a command menu for your bot is that you must edit an existing app manifest.</span></span> <span data-ttu-id="46abf-116">Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes Manifest bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="46abf-116">The steps to add a command menu are the same, whether you create a new manifest or edit an existing one.</span></span>

<span data-ttu-id="46abf-117">**So erstellen Sie ein Befehlsmenü für Ihren Bot mit App Studio**</span><span class="sxs-lookup"><span data-stu-id="46abf-117">**To create a command menu for your bot using App Studio**</span></span>

1. <span data-ttu-id="46abf-118">Öffnen Sie Teams, und wählen Sie im linken Bereich **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="46abf-118">Open Teams and select **Apps** from the left pane.</span></span> <span data-ttu-id="46abf-119">Suchen Sie auf der Seite **"Apps"** nach **App Studio,** und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="46abf-119">In the **Apps** page, search for **App Studio**, and select **Open**.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="46abf-120">Wenn Sie nicht über **App Studio** verfügen, können Sie es herunterladen.</span><span class="sxs-lookup"><span data-stu-id="46abf-120">If you do not have **App Studio**, you can download it.</span></span> <span data-ttu-id="46abf-121">Weitere Informationen finden Sie unter [Installieren von App Studio.](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio)</span><span class="sxs-lookup"><span data-stu-id="46abf-121">For more information, see [installing App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).</span></span>

    ![App-Studio](./conversations/media/AppStudio.png)

2. <span data-ttu-id="46abf-123">Wählen Sie in **App Studio** die Registerkarte **"Manifest-Editor"** aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren.</span><span class="sxs-lookup"><span data-stu-id="46abf-123">In **App Studio**, select the **Manifest editor** tab. If you do not have an existing app package, you can create or import an existing app.</span></span> <span data-ttu-id="46abf-124">Weitere Informationen finden Sie unter [Aktualisieren eines App-Pakets.](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package)</span><span class="sxs-lookup"><span data-stu-id="46abf-124">For more information, see [update an app package](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).</span></span>

3. <span data-ttu-id="46abf-125">Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **"Funktionen"** die Option **"Bots" aus.**</span><span class="sxs-lookup"><span data-stu-id="46abf-125">In the left pane of the **Manifest editor** and in the **Capabilities** section, select **Bots**.</span></span>

4. <span data-ttu-id="46abf-126">Wählen Sie im rechten Bereich des **Manifest-Editors** und im Abschnitt **"Befehle"** die Option **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="46abf-126">In the right pane of the **Manifest editor** and in the **Commands** section, select **Add**.</span></span> <span data-ttu-id="46abf-127">Der Bildschirm **"Neuer Befehl"** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="46abf-127">The **New Command** screen appears.</span></span>

    ![App Studio-Befehlsmenü Schaltfläche "Hinzufügen"](./conversations/media/AppStudio-CommandMenu-Add.png)

5. <span data-ttu-id="46abf-129">Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="46abf-129">Enter the **Command text** that must appear as the command menu for your bot.</span></span>

6. <span data-ttu-id="46abf-130">Geben Sie den **Hilfetext** ein, der unter dem Befehlstext im Menü angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="46abf-130">Enter the **Help text** that must appear under the command text in the menu.</span></span> <span data-ttu-id="46abf-131">**Hilfetext** muss eine kurze Erläuterung des Befehlszwecks sein.</span><span class="sxs-lookup"><span data-stu-id="46abf-131">**Help text** must be a brief explanation of the purpose of the command.</span></span>

7. <span data-ttu-id="46abf-132">Aktivieren Sie die **Kontrollkästchen "Bereich",** um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **"Speichern"** aus.</span><span class="sxs-lookup"><span data-stu-id="46abf-132">Select the **Scope** check boxes to select where this command menu must appear, and select **Save**.</span></span>

    ![Menüschaltfläche für neue Befehle in App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a><span data-ttu-id="46abf-134">Erstellen sie ein Befehlsmenü für Ihren Bot, indem Sie Manifest.jsaktivieren</span><span class="sxs-lookup"><span data-stu-id="46abf-134">Create a command menu for your bot by editing Manifest.json</span></span>

<span data-ttu-id="46abf-135">Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht darin, es direkt in der Manifestdatei zu erstellen, während Sie Ihren Bot-Quellcode entwickeln.</span><span class="sxs-lookup"><span data-stu-id="46abf-135">Another way to create a command menu is to create it directly in the manifest file while developing your bot source code.</span></span> <span data-ttu-id="46abf-136">Gehen Sie folgendermaßen vor, um diese Methode zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="46abf-136">To use this method, follow these points:</span></span>

* <span data-ttu-id="46abf-137">Jedes Menü unterstützt bis zu zehn Befehle.</span><span class="sxs-lookup"><span data-stu-id="46abf-137">Each menu supports up to ten commands.</span></span>
* <span data-ttu-id="46abf-138">Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereichen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="46abf-138">Create a single command menu that works in all scopes.</span></span>
* <span data-ttu-id="46abf-139">Erstellen Sie für jeden Bereich ein anderes Befehlsmenü.</span><span class="sxs-lookup"><span data-stu-id="46abf-139">Create a different command menu for each scope.</span></span>

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a><span data-ttu-id="46abf-140">Manifestbeispiel für ein einzelnes Menü für beide Bereiche</span><span class="sxs-lookup"><span data-stu-id="46abf-140">Manifest example for single menu for both scopes</span></span>

<span data-ttu-id="46abf-141">Der Manifest-Beispielcode für ein einzelnes Menü für beide Bereiche lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="46abf-141">The manifest example code for single menu for both scopes is as follows:</span></span>

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

#### <a name="manifest-example-for-the-menu-for-each-scope"></a><span data-ttu-id="46abf-142">Manifestbeispiel für das Menü für jeden Bereich</span><span class="sxs-lookup"><span data-stu-id="46abf-142">Manifest example for the menu for each scope</span></span>

<span data-ttu-id="46abf-143">Der Manifest-Beispielcode für das Menü für jeden Bereich lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="46abf-143">The manifest example code for the menu for each scope is as follows:</span></span>

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

<span data-ttu-id="46abf-144">Sie müssen Menübefehle in Ihrem Bot-Code behandeln, während Sie Nachrichten von Benutzern behandeln.</span><span class="sxs-lookup"><span data-stu-id="46abf-144">You must handle menu commands in your bot code as you handle any message from users.</span></span> <span data-ttu-id="46abf-145">Sie können Menübefehle in Ihrem Bot-Code behandeln, indem Sie den **\@ Erwähnungsteil** des Nachrichtentexts analysieren.</span><span class="sxs-lookup"><span data-stu-id="46abf-145">You can handle menu commands in your bot code by parsing out the **\@Mention** portion of the message text.</span></span>

## <a name="handle-menu-commands-in-your-bot-code"></a><span data-ttu-id="46abf-146">Behandeln von Menübefehlen in Ihrem Bot-Code</span><span class="sxs-lookup"><span data-stu-id="46abf-146">Handle menu commands in your bot code</span></span>

<span data-ttu-id="46abf-147">Bots in einer Gruppe oder einem Kanal reagieren nur, wenn sie in einer Nachricht erwähnt `@botname` werden.</span><span class="sxs-lookup"><span data-stu-id="46abf-147">Bots in a group or channel respond only when they are mentioned `@botname` in a message.</span></span> <span data-ttu-id="46abf-148">Jede Nachricht, die von einem Bot empfangen wird, wenn sie sich in einem Gruppen- oder Kanalbereich befindet, enthält ihren Namen im zurückgegebenen Nachrichtentext.</span><span class="sxs-lookup"><span data-stu-id="46abf-148">Every message received by a bot when in a group or channel scope contains its name in the message text returned.</span></span> <span data-ttu-id="46abf-149">Vor der Verarbeitung des zurückgegebenen Befehls muss ihre Nachrichtenparsing die Nachricht verarbeiten, die von einem Bot mit seinem Namen empfangen wurde.</span><span class="sxs-lookup"><span data-stu-id="46abf-149">Before handling the command being returned, your message parsing must handle the message received by a bot with its name.</span></span>

> [!NOTE]
> <span data-ttu-id="46abf-150">Um die Befehle im Code zu verarbeiten, werden sie als reguläre Nachricht an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="46abf-150">To handle the commands in code, they are sent to your bot as a regular message.</span></span> <span data-ttu-id="46abf-151">Sie müssen sie so behandeln, wie Sie andere Nachrichten von Ihren Benutzern behandeln würden.</span><span class="sxs-lookup"><span data-stu-id="46abf-151">You must handle them as you would handle any other message from your users.</span></span> <span data-ttu-id="46abf-152">Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein.</span><span class="sxs-lookup"><span data-stu-id="46abf-152">The commands in code insert pre-configured text into the text box.</span></span> <span data-ttu-id="46abf-153">Der Benutzer muss dann diesen Text wie bei jeder anderen Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="46abf-153">The user must then send that text as they do for any other message.</span></span>

# <a name="c"></a>[<span data-ttu-id="46abf-154">C#</span><span class="sxs-lookup"><span data-stu-id="46abf-154">C#</span></span>](#tab/dotnet)

<span data-ttu-id="46abf-155">Sie können den **\@ Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die mit dem Microsoft Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="46abf-155">You can parse out the **\@Mention** portion of the message text using a static method provided with the Microsoft Bot Framework.</span></span> <span data-ttu-id="46abf-156">Es handelt sich um eine Methode der `Activity` Klasse mit dem Namen `RemoveRecipientMention` .</span><span class="sxs-lookup"><span data-stu-id="46abf-156">It is a method of the `Activity` class named `RemoveRecipientMention`.</span></span>

<span data-ttu-id="46abf-157">Der C#-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="46abf-157">The C# code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[<span data-ttu-id="46abf-158">JavaScript</span><span class="sxs-lookup"><span data-stu-id="46abf-158">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="46abf-159">Sie können den **\@ Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="46abf-159">You can parse out the **\@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="46abf-160">Es handelt sich um eine Methode der `TurnContext` Klasse mit dem Namen `removeMentionText` .</span><span class="sxs-lookup"><span data-stu-id="46abf-160">It is a method of the `TurnContext` class named `removeMentionText`.</span></span>

<span data-ttu-id="46abf-161">Der JavaScript-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="46abf-161">The JavaScript code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[<span data-ttu-id="46abf-162">Python</span><span class="sxs-lookup"><span data-stu-id="46abf-162">Python</span></span>](#tab/python)

<span data-ttu-id="46abf-163">Sie können den **@Mention** Teil des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="46abf-163">You can parse out the **@Mention** portion of the message text using a static method provided with the Bot Framework.</span></span> <span data-ttu-id="46abf-164">Es handelt sich um eine Methode der `TurnContext` Klasse mit dem Namen `remove_recipient_mention` .</span><span class="sxs-lookup"><span data-stu-id="46abf-164">It is a method of the `TurnContext` class named `remove_recipient_mention`.</span></span>

<span data-ttu-id="46abf-165">Der Python-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="46abf-165">The Python code to parse out the **\@Mention** portion of the message text is as follows:</span></span>

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

<span data-ttu-id="46abf-166">Um ein reibungsloses Funktionieren ihres Botcodes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.</span><span class="sxs-lookup"><span data-stu-id="46abf-166">To enable smooth functioning of your bot code, there are few best practices that you must follow.</span></span>

## <a name="command-menu-best-practices"></a><span data-ttu-id="46abf-167">Bewährte Methoden für Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="46abf-167">Command menu best practices</span></span>

<span data-ttu-id="46abf-168">Es folgen die bewährten Methoden für das Befehlsmenü:</span><span class="sxs-lookup"><span data-stu-id="46abf-168">Following are the command menu best practices:</span></span>

* <span data-ttu-id="46abf-169">Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots darstellen.</span><span class="sxs-lookup"><span data-stu-id="46abf-169">Keep it simple: The bot menu is meant to present the key capabilities of your bot.</span></span>
* <span data-ttu-id="46abf-170">Kurz halten: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen natürlichen Sprachanweisungen sein.</span><span class="sxs-lookup"><span data-stu-id="46abf-170">Keep it short: Menu options must not be long and must not be complex natural language statements.</span></span> <span data-ttu-id="46abf-171">Sie müssen einfache Befehle sein.</span><span class="sxs-lookup"><span data-stu-id="46abf-171">They must be simple commands.</span></span>
* <span data-ttu-id="46abf-172">Lassen Sie es aufrufbar: Bot-Menüaktionen oder -Befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder dem Dialogfeld, in dem sich der Bot befindet.</span><span class="sxs-lookup"><span data-stu-id="46abf-172">Keep it invokable: Bot menu actions or commands must always be available, regardless of the state of the conversation or the dialog the bot is in.</span></span>

> [!NOTE]
> <span data-ttu-id="46abf-173">Wenn Sie Befehle aus dem Manifest entfernen, müssen Sie die App erneut bereitstellen, um die Änderungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="46abf-173">If you remove any commands from your manifest, you must redeploy your app to implement the changes.</span></span> <span data-ttu-id="46abf-174">Im Allgemeinen erfordern alle Änderungen am Manifest, dass Sie Ihre App erneut bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="46abf-174">In general, any changes to the manifest require you to redeploy your app.</span></span>

## <a name="next-step"></a><span data-ttu-id="46abf-175">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="46abf-175">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46abf-176">Kanal- und Gruppenunterhaltungen</span><span class="sxs-lookup"><span data-stu-id="46abf-176">Channel and group conversations</span></span>](~/bots/how-to/conversations/channel-and-group-conversations.md)
