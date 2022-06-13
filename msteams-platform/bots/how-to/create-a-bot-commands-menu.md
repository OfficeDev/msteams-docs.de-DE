---
title: Ein Befehlsmenü für Ihren Bot erstellen
author: surbhigupta
description: Erfahren Sie, wie Sie ein Befehlsmenü für Ihren Microsoft Teams-Bot mit Codebeispielen erstellen.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
keywords: Befehlsmenü verfassen Nachricht Unterhaltung @erwähnen
ms.openlocfilehash: 5b96a9b995806678596cc8cedd45f4bb6e80827c
ms.sourcegitcommit: 6f1bd36b1071e256bdc14e6ccb31dfdda9ca6d6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2022
ms.locfileid: "66048990"
---
# <a name="bot-command-menus"></a>Bot-Befehlsmenüs

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen. Die Liste der Befehle wird den Benutzern im Nachrichtenbereich zum Verfassen angezeigt, wenn sie mit Ihrem Bot in Verbindung stehen. Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Feld zum Verfassen von Nachrichten einzufügen, und wählen Sie **Senden** aus.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="conversations/Media/bot-menu-sample.png" alt-text="Bot-Befehlsmenü":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="conversations/Media/mobile-bot-menu-sample.png" alt-text="Mobile-bot-command-menu":::

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Ein Befehlsmenü für Ihren Bot erstellen

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können sie entweder mit **App Studio** erstellen oder manuell im App-Manifest hinzufügen.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Erstellen eines Befehlsmenüs mit App Studio für Ihren Bot

Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot besteht darin, dass Sie ein vorhandenes App-Manifest bearbeiten müssen. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.

**So erstellen Sie mit App Studio ein Befehlsmenü für Ihren Bot**

1. Öffnen Sie Teams, und wählen Sie im linken Bereich **Apps** aus. Suchen Sie auf der Seite **Apps** nach **App Studio**, und wählen Sie **Öffnen** aus.

   > [!WARNING]
   > Wenn Sie App Studio verwendet haben, empfehlen wir, das Entwicklerportal zum Konfigurieren, Verteilen und Verwalten Ihrer Teams-Apps zu testen. App Studio wird bis zum 30. Juni 2022 eingestellt.

   :::image type="content" source="conversations/Media/AppStudio.png" alt-text="appstudio-media":::

2. Wählen Sie in **App Studio** die Registerkarte **Manifest-Editor** aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren. Weitere Informationen finden Sie [unter Update C#-App-Paket in App Studio](../../get-started/deploy-csharp-app-studio.md)

3. Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **Funktionen** die Option **Bots aus**.

4. Wählen Sie im rechten Bereich des **Manifesteditors** und im Abschnitt **Befehle** die Option **Hinzufügen** aus. Der Bildschirm **Neuer Befehl** wird angezeigt.

   :::image type="content" source="media/AppStudio-CommandMenu-Add.png" alt-text="App-Paketdatei auswählen" lightbox="media/AppStudio-CommandMenu-Add.png "border="true":::

5. Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.

6. Geben Sie den **Hilfetext** ein, der unter dem Befehlstext im Menü angezeigt werden muss. Der **Hilfetext** muss eine kurze Erläuterung des Zwecks des Befehls sein.

7. Aktivieren Sie die Kontrollkästchen **Bereich**, um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **Speichern** aus.

   :::image type="content" source="media/AppStudio-NewCommandMenu.png" alt-text="App Studio-Menüschaltfläche &quot;Neue Befehle&quot; "lightbox="media/AppStudio-NewCommandMenu.png "border="true":::


### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen eines Befehlsmenüs für Ihren Bot durch Bearbeiten von Manifest.json

Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht darin, es direkt in der Manifestdatei zu erstellen, während Sie den Bot-Quellcode entwickeln. Um diese Methode anzuwenden, sollten Sie die folgenden Punkte beachten:

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

Sie können den Nachrichtentextteil **@Erwähnung** mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Dies ist eine Methode der `TurnContext`-Klasse mit Namen `remove_recipient_mention`.

Der Python-Code zum Analysieren des Nachrichtentextteils **\@Erwähnung** lautet wie folgt:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Um eine reibungslose Funktionsweise Ihres Bot-Codes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.

## <a name="command-menu-best-practices"></a>Bewährte Methoden für das Befehlsmenü

Im Folgenden werden die bewährten Methoden für das Befehlsmenü aufgeführt:

* Halten Sie es einfach: Das Bot-Menü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Halten Sie es kurz: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen Anweisungen in natürlicher Sprache sein. Sie müssen einfache Befehle sein.
* Lassen Sie es aufrufbar: Bot-Menüaktionen oder -Befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der Bot befindet.

> [!NOTE]
> Wenn Sie Befehle aus Ihrem Manifest entfernen, müssen Sie Ihre App erneut bereitstellen, um die Änderungen zu implementieren. Generell gilt, dass Sie bei Änderungen am Manifest Ihre Anwendung neu bereitstellen müssen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kanal- und Gruppenunterhaltungen](~/bots/how-to/conversations/channel-and-group-conversations.md)
