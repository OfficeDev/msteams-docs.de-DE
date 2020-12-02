---
title: Erstellen eines Befehlsmenüs für Ihren bot
author: clearab
description: Vorgehensweise Erstellen eines Befehlsmenüs für Ihren Microsoft Teams-bot
ms.topic: overview, command menu
ms.author: anclear
ms.openlocfilehash: ccbacc6ec6f18a38512d81dc898d0b14357d6ef7
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552486"
---
# <a name="bot-command-menus"></a>Bot-Befehlsmenüs

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

> [!Note]
> Bot-Menüs werden nicht auf mobilen Clients angezeigt.

Mit dem Befehl Menü hinzufügen für Ihren bot können Sie eine Reihe von Kern Befehlen definieren, auf die ihr bot immer Antworten kann. Die Liste der Befehle wird dem Benutzer über dem Bereich zum Verfassen von Nachrichten angezeigt, wenn Sie mit Ihrem bot in Kontakt kommen. Wenn Sie einen Befehl aus der Liste auswählen, wird die Befehlszeichenfolge in das Meldungsfeld verfassen eingefügt, dann müssen alle Benutzer die Option **senden** auswählen.

![Bot-Befehlsmenü](./conversations/media/bot-menu-sample.png)

## <a name="create-a-command-menu-for-your-bot"></a>Erstellen eines Befehlsmenüs für Ihren bot

Befehlsmenüs werden in Ihrem App-Manifest definiert. Sie können entweder App Studio verwenden, um Sie bei der Erstellung zu unterstützen, oder diese manuell hinzufügen.

### <a name="creating-a-command-menu-for-your-bot-using-app-studio"></a>Erstellen eines Befehlsmenüs für Ihren bot mithilfe von App Studio

In den hier beschriebenen Anweisungen wird davon ausgegangen, dass Sie ein vorhandenes App-Manifest bearbeiten. Die Schritte zum Hinzufügen eines Befehlsmenüs sind identisch, unabhängig davon, ob Sie ein neues Manifest erstellen oder ein vorhandenes bearbeiten.

1. Öffnen Sie App Studio aus dem... Überlaufmenü auf der linken Navigations Schiene. Wenn Sie kein App-Studio zur Verfügung haben, können Sie es herunterladen. Weitere Informationen zur Verwendung von App Studio finden Sie unter [Installing App Studio](https://aka.ms/teams-app-studio#installing-app-studio) .

    ![App Studio](./conversations/media/AppStudio.png)

2. Klicken Sie in App Studio auf die Registerkarte **Manifest-Editor** .

3. Wählen Sie in der linken Spalte der Manifest-Editor-Ansicht im Abschnitt " **Funktionen** " die Option " **Bots**" aus.

4. Klicken Sie in der rechten Spalte der Manifest-Editor-Ansicht im Abschnitt **Befehle** auf die Schaltfläche **Hinzufügen** .

    ![Schaltfläche "App Studio-Befehlsmenü hinzufügen"](./conversations/media/AppStudio-CommandMenu-Add.png)

5. Der Bildschirm **neuer Befehl** wird angezeigt. Geben Sie den **Befehlstext** ein, der als Menübefehl angezeigt werden soll, und der **Hilfetext** , den Sie direkt unter dem Befehlstext im Menü anzeigen möchten. Dies sollte eine kurze Erläuterung des Zwecks des Befehls sein.

6. Wählen Sie als nächstes die Bereiche aus, in denen dieses Befehlsmenü angezeigt werden soll, und wählen Sie dann die Schaltfläche **Speichern** aus.

    ![Schaltfläche "App Studio-Befehlsmenü hinzufügen"](./conversations/media/AppStudio-NewCommandMenu.png)

### <a name="creating-a-command-menu-for-your-bot-by-editing-manifestjson"></a>Erstellen eines Befehlsmenüs für Ihren bot durch Bearbeiten von **Manifest.jsauf**

Ein weiterer gültiger Ansatz zum Erstellen eines Befehlsmenüs besteht darin, es beim Entwickeln Ihres bot-Quellcodes direkt in der Manifestdatei zu erstellen. Hier sind einige Punkte, die Sie bei der Verwendung dieses Ansatzes beachten sollten:

1. Jedes Menü unterstützt bis zu 10 Befehle.

2. Sie können ein einzelnes Befehlsmenü erstellen, das in allen Bereichen verwendet werden kann.

3. Sie können für jeden Bereich ein anderes Befehlsmenü erstellen.

#### <a name="manifest-example---single-menu-for-both-scopes"></a>Manifest-Beispiel – einzelnes Menü für beide Bereiche

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

#### <a name="manifest-example---menu-for-each-scope"></a>Manifest-Beispielmenü für jeden Bereich

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

## <a name="handling-menu-commands-in-your-bot-code"></a>Behandeln von Menübefehlen in Ihrem bot-Code

Bots in einer Gruppe oder einem Kanal reagieren nur, wenn Sie in einer Nachricht erwähnt werden ("@botname"). Daher werden alle Nachrichten, die von einem bot empfangen werden, wenn Sie sich in einer Gruppe oder einem Kanalbereich befinden, im zurückgegebenen Nachrichtentext einen eigenen Namen enthalten. Sie müssen sicherstellen, dass Ihre Nachrichten Analyse diese behandelt, bevor der zurückgegebene Befehl verarbeitet wird.

> **Hinweis:** Um die Befehle im Code zu behandeln, werden Sie als reguläre Nachricht an Ihren bot gesendet. Sie müssen diese wie für jede andere Nachricht von Ihren Benutzern behandeln. Es handelt sich lediglich um eine Benutzeroberflächen Behandlung, die vorkonfigurierten Text in das Textfeld einfügt. Der Benutzer muss diesen Text dann wie für jede andere Nachricht senden.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Sie können den **\@ mention** -Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode der `Activity` benannten Klasse `RemoveRecipientMention` .

```csharp
var modifiedText = turnContext.Activity.RemoveRecipientMention();
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

Sie können den **\@ mention** -Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode der `TurnContext` benannten Klasse `removeMentionText` .

```javascript
const modifiedText = TurnContext.removeMentionText(turnContext.activity, turnContext.activity.recipient.id);
```

# <a name="python"></a>[Python](#tab/python)


Sie können den **@mention** Teil des Nachrichtentexts mithilfe einer statischen mit dem Microsoft bot Framework bereitgestellten Methode analysieren – eine Methode der `TurnContext` benannten Klasse `remove_recipient_mention` .

```python
modified_text = TurnContext.remove_recipient_mention(turn_context.activity)
```

* * *

## <a name="command-menu-best-practices"></a>Bewährte Methoden im Befehlsmenü

* **Halten Sie es einfach**: das bot-Menü soll die Hauptfunktionen Ihres bot präsentieren.
* **Halten Sie es kurz**: Menü Optionen sollten nicht extrem lang und komplexe natürliche Sprachanweisungen sein – Sie sollten einfache Befehle sein.
* **Keep it aufrufbaren**: bot-Menü Aktionen/-Befehle sollten immer verfügbar sein, unabhängig vom Status der Unterhaltung oder des Dialogs, in dem sich der bot befindet.

> **Hinweis:** Wenn Sie Befehle aus ihrem Manifest entfernen, müssen Sie Ihre APP erneut bereitstellen, damit die Änderungen wirksam werden. Im Allgemeinen ist dies für alle Änderungen am Manifest erforderlich.
