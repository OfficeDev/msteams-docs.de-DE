---
title: Erstellen eines Befehlsmenüs für Ihren Bot
author: surbhigupta
description: Erfahren Sie, wie Sie ein Befehlsmenü für Ihren Microsoft Teams Bot mit Codebeispielen erstellen.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
keywords: Befehlsmenü nachrichtenunterhaltung verfassen @mention
ms.openlocfilehash: 6f4b9cdac76fc9beb42a39dde3b320036ea580b5
ms.sourcegitcommit: e40383d9081bf117030f7e6270140e6b94214e8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65102554"
---
# <a name="bot-command-menus"></a>Bot-Befehlsmenüs

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen. Die Liste der Befehle wird den Benutzern im Nachrichtenbereich zum Verfassen angezeigt, wenn sie mit Ihrem Bot in Verbindung stehen. Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Feld zum Verfassen von Nachrichten einzufügen, und wählen Sie **"Senden**" aus.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Bot-Befehlsmenü](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

![Befehlsmenü "Mobiler Bot"](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Erstellen eines Befehlsmenüs für Ihren Bot

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können sie entweder mit **App Studio** erstellen oder manuell im App-Manifest hinzufügen.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Erstellen eines Befehlsmenüs für Ihren Bot mit App Studio

Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot besteht darin, dass Sie ein vorhandenes App-Manifest bearbeiten müssen. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.

**So erstellen Sie ein Befehlsmenü für Ihren Bot mit App Studio**

1. Öffnen Sie Teams, und wählen Sie im linken Bereich **"Apps**" aus. Suchen Sie auf der Seite **"Apps** " nach **App Studio**, und wählen Sie **"Öffnen**" aus.
   > [!NOTE]
   > Wenn Sie nicht über **App Studio** verfügen, können Sie es herunterladen. Weitere Informationen finden Sie [unter Installieren von App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).

    :::image type="content" source="/media/AppStudio.png" alt-text="Installieren von App Studio"lightbox="media/AppStudio.png"border="true":::

2. Wählen Sie in **App Studio** die Registerkarte " **Manifest-Editor** " aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren. Weitere Informationen finden Sie unter [Aktualisieren eines App-Pakets](~/get-started/deploy-csharp-app-studio.md).

3. Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **"Funktionen"** die Option **"Bots" aus**.

4. Wählen Sie im rechten Bereich des **Manifest-Editors** und im Abschnitt **"Befehle"** die Option **"Hinzufügen"** aus. Der Bildschirm " **Neuer Befehl** " wird angezeigt.

    :::image type="content" source="/media/AppStudio-CommandMenu-Add.png" alt-text="Auswählen des App-Pakets"lightbox="/media/AppStudio-CommandMenu-Add.png"border="true":::

5. Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.

6. Geben Sie den **Hilfetext** ein, der unter dem Befehlstext im Menü angezeigt werden muss. **Hilfetext** muss eine kurze Erläuterung des Zwecks des Befehls sein.

7. Aktivieren Sie die Kontrollkästchen **"Bereich"** , um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **"Speichern"** aus.

:::image type="content" source="/media/AppStudio-NewCommandMenu.png" alt-text="App Studio-Menüschaltfläche &quot;Neue Befehle&quot;"lightbox="/media/AppStudio-NewCommandMenu.png"border="true":::

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen eines Befehlsmenüs für Ihren Bot durch Bearbeiten von Manifest.json

Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht darin, es direkt in der Manifestdatei zu erstellen, während Sie Den Bot-Quellcode entwickeln. Gehen Sie folgendermaßen vor, um diese Methode zu verwenden:

* Jedes Menü unterstützt bis zu zehn Befehle.
* Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereichen funktioniert.
* Erstellen Sie für jeden Bereich ein anderes Befehlsmenü.

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a>Manifestbeispiel für ein einzelnes Menü für beide Bereiche

Der Manifestbeispielcode für ein einzelnes Menü für beide Bereiche lautet wie folgt:

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

#### <a name="manifest-example-for-the-menu-for-each-scope"></a>Manifestbeispiel für das Menü für jeden Bereich

Der Manifestbeispielcode für das Menü für jeden Bereich lautet wie folgt:

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

Sie müssen Menübefehle in Ihrem Bot-Code behandeln, während Sie nachrichten von Benutzern behandeln. Sie können Menübefehle in Ihrem Bot-Code verarbeiten, indem Sie den **\@Erwähnungsteil** des Nachrichtentexts analysieren.

## <a name="handle-menu-commands-in-your-bot-code"></a>Behandeln von Menübefehlen in Ihrem Bot-Code

Bots in einer Gruppe oder einem Kanal antworten nur, wenn sie in einer Nachricht erwähnt `@botname` werden. Jede Nachricht, die von einem Bot empfangen wird, wenn sie sich in einer Gruppe oder einem Kanalbereich befindet, enthält ihren Namen im Nachrichtentext. Bevor der zurückgegebene Befehl behandelt wird, muss die Nachrichten analysiert werden, die von einem Bot mit seinem Namen empfangen wurde.

> [!NOTE]
> Um die Befehle im Code zu verarbeiten, werden sie als normale Nachricht an Ihren Bot gesendet. Sie müssen sie so behandeln, wie Sie jede andere Nachricht von Ihren Benutzern behandeln würden. Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein. Der Benutzer muss diesen Text dann wie für jede andere Nachricht senden.

# <a name="c"></a>[C#](#tab/dotnet)

Sie können den **\@Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die mit dem Microsoft Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der Klasse mit dem `Activity` Namen `RemoveRecipientMention`.

Der C#-Code zum Analysieren des **\@Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Sie können den **\@Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der Klasse mit dem `TurnContext` Namen `removeMentionText`.

Der JavaScript-Code zum Analysieren des **\@Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

Sie können den **@Mention** Teil des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der Klasse mit dem `TurnContext` Namen `remove_recipient_mention`.

Der Python-Code zum Analysieren des **\@Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Um eine reibungslose Funktionsweise Ihres Bot-Codes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.

## <a name="command-menu-best-practices"></a>Bewährte Methoden im Befehlsmenü

Im Folgenden werden die bewährten Methoden für das Befehlsmenü aufgeführt:

* Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Kurz halten: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen Anweisungen in natürlicher Sprache sein. Es müssen einfache Befehle sein.
* Lassen Sie es aufrufbar: Bot-Menüaktionen oder -Befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet.

> [!NOTE]
> Wenn Sie Befehle aus Ihrem Manifest entfernen, müssen Sie Ihre App erneut bereitstellen, um die Änderungen zu implementieren. Im Allgemeinen müssen Sie bei Änderungen am Manifest Ihre App erneut bereitstellen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kanal- und Gruppenunterhaltungen](~/bots/how-to/conversations/channel-and-group-conversations.md)
