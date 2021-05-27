---
title: Erstellen eines Befehlsmenüs für Ihren Bot
author: clearab
description: Erstellen eines Befehlsmenüs für ihren Microsoft Teams Bot
ms.topic: how-to
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: f89c564a2843aaee010774e6b262a96ce4d6530f
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668837"
---
# <a name="bot-command-menus"></a>Bot-Befehlsmenüs

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Um eine Reihe von Kernbefehlen zu definieren, auf die Ihr Bot reagieren kann, können Sie ein Befehlsmenü mit einer Dropdownliste mit Befehlen für Ihren Bot hinzufügen. Die Liste der Befehle wird den Benutzern im Bereich Verfassen von Nachrichten angezeigt, wenn sie mit Ihrem Bot in Unterhaltung sind. Wählen Sie einen Befehl aus der Liste aus, um die Befehlszeichenfolge in das Meldungsfeld verfassen ein, und wählen Sie **Senden aus.**

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Befehlsmenü "Bot"](./conversations/media/bot-menu-sample.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

![Befehlsmenü für mobile Bots](./conversations/media/mobile-bot-menu-sample.png)

* * *

## <a name="create-a-command-menu-for-your-bot"></a>Erstellen eines Befehlsmenüs für Ihren Bot

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können app **Studio** verwenden, um sie zu erstellen, oder sie manuell im App-Manifest hinzufügen.

### <a name="create-a-command-menu-for-your-bot-using-app-studio"></a>Erstellen eines Befehlsmenüs für Ihren Bot mithilfe von App Studio

Eine Voraussetzung zum Erstellen eines Befehlsmenüs für Ihren Bot ist, dass Sie ein vorhandenes App-Manifest bearbeiten müssen. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.

**So erstellen Sie ein Befehlsmenü für Ihren Bot mithilfe von App Studio**

1. Öffnen Teams, und wählen **Sie im** linken Bereich Apps aus. Suchen Sie **auf** der Seite Apps nach **App Studio,** und wählen Sie **Öffnen aus.** 
   > [!NOTE]
   > Wenn Sie nicht über **App Studio verfügen,** können Sie es herunterladen. Weitere Informationen finden Sie unter [Installieren von App Studio](~/concepts/build-and-test/app-studio-overview.md#installing-app-studio).

    ![App-Studio](./conversations/media/AppStudio.png)

2. Wählen **Sie in App Studio** die Registerkarte **Manifest-Editor** aus. Wenn Sie nicht über ein vorhandenes App-Paket verfügen, können Sie eine vorhandene App erstellen oder importieren. Weitere Informationen finden Sie unter [Update an app package](~/tutorials/get-started-dotnet-app-studio.md#use-app-studio-to-update-the-app-package).

3. Wählen Sie im linken Bereich des **Manifest-Editors** und im Abschnitt **Funktionen** die Option **Bots aus.**

4. Wählen Sie im rechten Bereich des **Manifest-Editors** und im Abschnitt **Befehle** die Option **Hinzufügen aus.** Der **Bildschirm Neuer Befehl** wird angezeigt.

    ![App Studio-Befehlsmenü Schaltfläche hinzufügen](./conversations/media/AppStudio-CommandMenu-Add.png)

5. Geben Sie den **Befehlstext** ein, der als Befehlsmenü für Ihren Bot angezeigt werden muss.

6. Geben Sie den **Hilfetext ein,** der im Menü unter dem Befehlstext angezeigt werden muss. **Hilfetext** muss eine kurze Erläuterung des Zwecks des Befehls sein.

7. Aktivieren Sie **die Kontrollkästchen** Bereich, um auszuwählen, wo dieses Befehlsmenü angezeigt werden muss, und wählen Sie **Speichern aus.**

    ![Menüschaltfläche für neue Befehle in App Studio](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="create-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen eines Befehlsmenüs für Ihren Bot durch Bearbeiten Manifest.js

Eine weitere Möglichkeit zum Erstellen eines Befehlsmenüs besteht in der direkten Erstellung in der Manifestdatei während der Entwicklung des Bot-Quellcodes. Gehen Sie wie folgt vor, um diese Methode zu verwenden:

* Jedes Menü unterstützt bis zu zehn Befehle.
* Erstellen Sie ein einzelnes Befehlsmenü, das in allen Bereich funktioniert.
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

Sie müssen Menübefehle in Ihrem Botcode behandeln, während Sie alle Nachrichten von Benutzern verarbeiten. Sie können Menübefehle in Ihrem Botcode verarbeiten, indem Sie den Abschnitt **\@ Erwähnung** des Nachrichtentexts aussingen.

## <a name="handle-menu-commands-in-your-bot-code"></a>Behandeln von Menübefehlen in Ihrem Botcode

Bots in einer Gruppe oder einem Kanal reagieren nur, wenn sie in einer `@botname` Nachricht erwähnt werden. Jede Nachricht, die von einem Bot empfangen wird, wenn sie sich in einem Gruppen- oder Kanalbereich befindet, enthält ihren Namen im zurückgegebenen Nachrichtentext. Vor der Verarbeitung des zurückgegebenen Befehls muss ihre Nachrichten parsing die Nachricht behandeln, die von einem Bot mit seinem Namen empfangen wurde.

> [!NOTE]
> Um die Befehle im Code zu verarbeiten, werden sie als reguläre Nachricht an Ihren Bot gesendet. Sie müssen sie wie jede andere Nachricht von Ihren Benutzern behandeln. Die Befehle im Code fügen vorkonfigurierten Text in das Textfeld ein. Der Benutzer muss dann den Text wie für jede andere Nachricht senden.

# <a name="c"></a>[C#](#tab/dotnet)

Sie können den Abschnitt **\@ Erwähnung** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die mit dem Microsoft Bot Framework. Es handelt sich um eine Methode der `Activity` Klasse namens `RemoveRecipientMention` .

Der C# Code zum Analysieren des Abschnitts **\@ Erwähnung** des Nachrichtentexts lautet wie folgt:

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Sie können den Abschnitt **\@ Erwähnung** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der `TurnContext` Klasse namens `removeMentionText` .

Der JavaScript-Code zum Analysieren des **\@ Abschnitts Erwähnung** des Nachrichtentexts lautet wie folgt:

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)

Sie können den **@Mention** des Nachrichtentexts mithilfe einer statischen Methode analysieren, die im Bot Framework bereitgestellt wird. Es handelt sich um eine Methode der `TurnContext` Klasse namens `remove_recipient_mention` .

Der Python-Code zum Analysieren des **\@ Abschnitts Erwähnung** des Nachrichtentexts lautet wie folgt:

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

Um eine reibungslose Funktionsweise Ihres Botcodes zu ermöglichen, müssen Sie einige bewährte Methoden befolgen.

## <a name="command-menu-best-practices"></a>Bewährte Methoden im Befehlsmenü

Im Folgenden finden Sie die bewährten Methoden für das Befehlsmenü:

* Halten Sie es einfach: Das Botmenü soll die wichtigsten Funktionen Ihres Bots präsentieren.
* Kurz halten: Menüoptionen dürfen nicht lang sein und dürfen keine komplexen Anweisungen für natürliche Sprachen sein. Es müssen einfache Befehle sein.
* Lassen Sie es unanfehlbar: Bot-Menüaktionen oder -befehle müssen immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogfelds, in dem sich der Bot befindet.

> [!NOTE]
> Wenn Sie Befehle aus Ihrem Manifest entfernen, müssen Sie Ihre App erneut bereitstellen, um die Änderungen zu implementieren. Im Allgemeinen erfordern Änderungen am Manifest, dass Sie Ihre App erneut bereitstellen müssen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Kanal- und Gruppenunterhaltungen](~/bots/how-to/conversations/channel-and-group-conversations.md)
