---
title: Ein Befehlsmenü für Ihren Bot erstellen
author: surbhigupta
description: Erfahren Sie, wie Sie ein Befehlsmenü für Ihren Microsoft Teams-Bot erstellen und behandeln sowie bewährte Methoden. Erfahren Sie, wie Sie Befehle aus Ihrem Manifest entfernen.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 0e0f9ce9ada0cde0aa6f7b6b29c7badb07dd7db9
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100903"
---
# <a name="create-a-commands-menu"></a>Ein Befehlsmenü erstellen

> [!NOTE]
> Es wird empfohlen, einen Befehlsbot zu erstellen, indem Sie die schrittweise Anleitung zum [Erstellen eines Befehlsbots mit JavaScript](../../sbs-gs-commandbot.yml) mithilfe des Entwicklungstools der neuen Generation für Teams befolgen. Weitere Informationen zum Teams-Toolkit finden Sie unter [Teams Toolkit Overview for Visual Studio Code](../../toolkit/teams-toolkit-fundamentals.md) and [Teams Toolkit overview for Visual Studio](../../toolkit/teams-toolkit-overview-visual-studio.md).

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen. Die Liste der Befehle wird den Benutzern im Nachrichtenbereich zum Verfassen angezeigt, wenn sie mit Ihrem Bot in Verbindung stehen. Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Feld zum Verfassen von Nachrichten einzufügen, und wählen Sie **Senden** aus.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="conversations/Media/bot-menu-sample.png" alt-text="Bot-Befehlsmenü":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="conversations/Media/mobile-bot-menu-sample.png" alt-text="Mobile-bot-command-menu":::

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Ein Befehlsmenü für Ihren Bot erstellen

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können sie entweder über das **Entwicklerportal** erstellen oder manuell im App-Manifest hinzufügen.

### <a name="create-a-command-menu-for-your-bot-using-developer-portal"></a>Erstellen eines Befehlsmenüs für Ihren Bot mithilfe des Entwicklerportals

Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot besteht darin, dass Sie ein vorhandenes App-Manifest bearbeiten müssen. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.

So erstellen Sie ein Befehlsmenü für Ihren Bot mithilfe des Entwicklerportals:

1. Öffnen Sie Teams, und wählen Sie im linken Bereich **Apps** aus. Suchen Sie auf der Seite **"Apps** " nach **dem Entwicklerportal**, und wählen Sie dann **"Öffnen**" aus.

   :::image type="content" source="../../assets/images/tdp/add-dev-portal.png" alt-text="Screenshot zeigt, wie Sie das Entwicklerportal im Teams-Client hinzufügen.":::
  
1. Wählen Sie im **Entwicklerportal** die Registerkarte **"Apps** " aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren. Weitere Informationen finden Sie im [Entwicklerportal für Teams](../../concepts/build-and-test/teams-developer-portal.md).

1. Wählen Sie die Registerkarte **"Apps** ", dann im linken Bereich " **App-Features** " und dann " **Bots**" aus.

1. Wählen Sie im Abschnitt **"Befehle****" die Option "Befehl hinzufügen**" aus.

   :::image type="content" source="../../assets/images/tdp/add-a-bot-command.png" alt-text="Der Screenshot zeigt, wie Sie einen Befehl für Ihren Bot im Entwicklerportal hinzufügen.":::

1. Geben Sie den **Befehl** ein, der als Befehlsmenü für Ihren Bot angezeigt wird.

1. Geben Sie die **Beschreibung** ein, die unter dem Befehlstext im Menü angezeigt wird. **Die Beschreibung** muss eine kurze Erläuterung des Zwecks des Befehls sein.

1. Aktivieren Sie das Kontrollkästchen **"Bereich"** , und wählen Sie dann **"Hinzufügen"** aus.
   Dadurch wird definiert, wo das Befehlsmenü angezeigt werden muss.

   :::image type="content" source="../../assets/images/tdp/bot-command.png" alt-text="Screenshot zeigt, wie Sie einen Befehl, eine Beschreibung und Bereiche für Ihren Bot hinzufügen.":::

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen eines Befehlsmenüs für Ihren Bot durch Bearbeiten von Manifest.json

Another way to create a command menu is to create it directly in the manifest file while developing your bot source code. To use this method, follow these points:

* Jedes Menü unterstützt bis zu 10 Befehle.
* Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereichen funktioniert.
* Erstellen Sie für jeden Bereich ein anderes Befehlsmenü.

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a>Beispielmanifest für ein einzelnes Menü für beide Bereiche

Der Beispielmanifestcode für ein einzelnes Menü für beide Bereiche lautet wie folgt:

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

#### <a name="manifest-example-for-the-menu-for-each-scope"></a>Beispielmanifest für das Menü für jeden Bereich

Der Beispielmanifestcode für das Menü für jeden Bereich lautet wie folgt:

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

Sie müssen Menübefehle in Ihrem Bot-Code behandeln, so wie Sie jede Nachricht von Benutzern behandeln. Sie können Menübefehle in Ihrem Bot-Code behandeln, indem Sie den Nachrichtentextteil **\@Erwähnung** analysieren.

## <a name="handle-menu-commands-in-your-bot-code"></a>Behandeln von Menübefehlen in Ihrem Bot-Code

Bots in einer Gruppe oder einem Kanal antworten nur, wenn sie in einer Nachricht mit `@botname` erwähnt werden. Jede Nachricht, die von einem Bot empfangen wird, wenn er sich in einer Gruppe oder einem Kanalbereich befindet, enthält seinen Namen im Nachrichtentext. Bevor die Rückgabe des Befehls behandelt wird, muss die Nachrichten analysiert werden, die von einem Bot mit seinem Namen empfangen wurde.

> [!NOTE]
> Um die Befehle im Code zu behandeln, werden sie als normale Nachricht an Ihren Bot gesendet. Sie müssen sie so behandeln, wie Sie jede andere Nachricht von Ihren Benutzern behandeln würden. Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein. Der Benutzer muss diesen Text dann wie für jede andere Nachricht senden.

# <a name="c"></a>[C#](#tab/dotnet)

Sie können den Nachrichtentextteil **\@Erwähnung** mithilfe einer statischen Methode analysieren, die mit dem Microsoft Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der Klasse `Activity` mit dem Namen `RemoveRecipientMention`.

Der C#-Code zum Analysieren des Nachrichtentextteils **\@Erwähnung** lautet wie folgt:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Sie können den Nachrichtentextteil **\@Erwähnung** mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der Klasse `TurnContext` mit dem Namen `removeMentionText`.

Der JavaScript-Code zum Analysieren des Nachrichtentextteils **\@Erwähnung** lautet wie folgt:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

You can parse out the **@Mention** portion of the message text using a static method provided with the Bot Framework. It is a method of the `TurnContext` class named `remove_recipient_mention`.

Der Python-Code zum Analysieren des Nachrichtentextteils **\@Erwähnung** lautet wie folgt:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Um eine reibungslose Funktionsweise Ihres Bot-Codes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.

## <a name="command-menu-best-practices"></a>Bewährte Methoden für das Befehlsmenü

Im Folgenden werden die bewährten Methoden für das Befehlsmenü aufgeführt:

* Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Keep it short: Menu options must not be long and must not be complex natural language statements. They must be simple commands.
* Lassen Sie es aufrufbar: Bot-Menüaktionen oder -Befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der Bot befindet.

> [!NOTE]
> Wenn Sie Befehle aus Ihrem Manifest entfernen, müssen Sie Ihre App erneut bereitstellen, um die Änderungen zu implementieren. Generell gilt, dass Sie bei Änderungen am Manifest Ihre Anwendung neu bereitstellen müssen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kanal- und Gruppenunterhaltungen](~/bots/how-to/conversations/channel-and-group-conversations.md)
