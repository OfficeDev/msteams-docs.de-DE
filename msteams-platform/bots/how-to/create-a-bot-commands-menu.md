---
title: Erstellen eines Befehlsmenüs für Ihren Bot
author: surbhigupta
description: So erstellen Sie ein Befehlsmenü für Ihren Microsoft Teams-Bot
ms.topic: how-to
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: f29261a1d22f7629ffe17b444b42af6f5df1e792
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156450"
---
# <a name="bot-command-menus"></a>Bot-Befehlsmenüs

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste von Befehlen für Ihren Bot hinzufügen. Die Liste der Befehle wird den Benutzern im Bereich zum Verfassen von Nachrichten angezeigt, wenn sie sich in Einer Unterhaltung mit Ihrem Bot befinden. Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Feld zum Verfassen von Nachrichten einzufügen, und wählen Sie **"Senden"** aus.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Bot-Befehlsmenü](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

![Befehlsmenü für mobile Bots](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Erstellen eines Befehlsmenüs für Ihren Bot

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können sie entweder mit **App Studio** erstellen oder manuell im App-Manifest hinzufügen.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Erstellen eines Befehlsmenüs für Ihren Bot mit App Studio

Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot ist, dass Sie ein vorhandenes App-Manifest bearbeiten müssen. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes Manifest bearbeiten.

**So erstellen Sie ein Befehlsmenü für Ihren Bot mit App Studio**

1. Öffnen Sie Teams, und wählen Sie im linken Bereich **Apps** aus. Suchen Sie auf der Seite **"Apps"** nach **App Studio,** und wählen Sie **"Öffnen"** aus. 
   > [!NOTE]
   > Wenn Sie nicht über **App Studio** verfügen, können Sie es herunterladen. Weitere Informationen finden Sie unter [Installieren von App Studio.](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio)

    ![App-Studio](./conversations/media/AppStudio.png)

2. Wählen Sie in **App Studio** die Registerkarte **"Manifest-Editor"** aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren. Weitere Informationen finden Sie unter [Aktualisieren eines App-Pakets.](~/get-started/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package)

3. Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **"Funktionen"** die Option **"Bots" aus.**

4. Wählen Sie im rechten Bereich des **Manifest-Editors** und im Abschnitt **"Befehle"** die Option **"Hinzufügen"** aus. Der Bildschirm **"Neuer Befehl"** wird angezeigt.

    ![App Studio-Befehlsmenü Schaltfläche "Hinzufügen"](./conversations/media/AppStudio-CommandMenu-Add.png)

5. Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.

6. Geben Sie den **Hilfetext** ein, der unter dem Befehlstext im Menü angezeigt werden muss. **Hilfetext** muss eine kurze Erläuterung des Befehlszwecks sein.

7. Aktivieren Sie die **Kontrollkästchen "Bereich",** um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **"Speichern"** aus.

    ![Menüschaltfläche für neue Befehle in App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen sie ein Befehlsmenü für Ihren Bot, indem Sie Manifest.jsaktivieren

Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht darin, es direkt in der Manifestdatei zu erstellen, während Sie Ihren Bot-Quellcode entwickeln. Gehen Sie folgendermaßen vor, um diese Methode zu verwenden:

* Jedes Menü unterstützt bis zu zehn Befehle.
* Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereichen funktioniert.
* Erstellen Sie für jeden Bereich ein anderes Befehlsmenü.

#### <a name="manifest-example-for-single-menu-for-both-scopes"></a>Manifestbeispiel für ein einzelnes Menü für beide Bereiche

Der Manifest-Beispielcode für ein einzelnes Menü für beide Bereiche lautet wie folgt:

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

Der Manifest-Beispielcode für das Menü für jeden Bereich lautet wie folgt:

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

Sie müssen Menübefehle in Ihrem Bot-Code behandeln, während Sie Nachrichten von Benutzern behandeln. Sie können Menübefehle in Ihrem Bot-Code behandeln, indem Sie den **\@ Erwähnungsteil** des Nachrichtentexts analysieren.

## <a name="handle-menu-commands-in-your-bot-code"></a>Behandeln von Menübefehlen in Ihrem Bot-Code

Bots in einer Gruppe oder einem Kanal reagieren nur, wenn sie in einer Nachricht erwähnt `@botname` werden. Jede Nachricht, die von einem Bot empfangen wird, wenn sie sich in einem Gruppen- oder Kanalbereich befindet, enthält ihren Namen im zurückgegebenen Nachrichtentext. Vor der Verarbeitung des zurückgegebenen Befehls muss ihre Nachrichtenparsing die Nachricht verarbeiten, die von einem Bot mit seinem Namen empfangen wurde.

> [!NOTE]
> Um die Befehle im Code zu verarbeiten, werden sie als reguläre Nachricht an Ihren Bot gesendet. Sie müssen sie so behandeln, wie Sie andere Nachrichten von Ihren Benutzern behandeln würden. Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein. Der Benutzer muss dann diesen Text wie bei jeder anderen Nachricht senden.

# <a name="c"></a>[C#](#tab/dotnet)

Sie können den **\@ Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die mit dem Microsoft Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der `Activity` Klasse mit dem Namen `RemoveRecipientMention` .

Der C#-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Sie können den **\@ Erwähnungsteil** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der `TurnContext` Klasse mit dem Namen `removeMentionText` .

Der JavaScript-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

Sie können den **@Mention** Teil des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der `TurnContext` Klasse mit dem Namen `remove_recipient_mention` .

Der Python-Code zum Analysieren des **\@ Erwähnungsteils** des Nachrichtentexts lautet wie folgt:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Um ein reibungsloses Funktionieren ihres Botcodes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.

## <a name="command-menu-best-practices"></a>Bewährte Methoden für Befehlsmenüs

Es folgen die bewährten Methoden für das Befehlsmenü:

* Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots darstellen.
* Kurz halten: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen natürlichen Sprachanweisungen sein. Sie müssen einfache Befehle sein.
* Lassen Sie es aufrufbar: Bot-Menüaktionen oder -Befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder dem Dialogfeld, in dem sich der Bot befindet.

> [!NOTE]
> Wenn Sie Befehle aus dem Manifest entfernen, müssen Sie die App erneut bereitstellen, um die Änderungen zu implementieren. Im Allgemeinen erfordern alle Änderungen am Manifest, dass Sie Ihre App erneut bereitstellen müssen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kanal- und Gruppenunterhaltungen](~/bots/how-to/conversations/channel-and-group-conversations.md)
