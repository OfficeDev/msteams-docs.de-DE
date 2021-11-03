---
title: Definieren von Aktionsbefehlen für Messaging-Erweiterungen
author: surbhigupta
description: Eine Übersicht über Aktionsbefehle für Messaging-Erweiterungen
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: d3876d0fc5d58b54ececaabb9e88da0a6e355b47
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720141"
---
# <a name="define-messaging-extension-action-commands"></a>Definieren von Aktionsbefehlen für Messaging-Erweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mit Aktionsbefehlen können Sie Ihren Benutzern ein modales Popup anzeigen, das als Aufgabenmodul in Teams bezeichnet wird. Das Aufgabenmodul sammelt oder zeigt Informationen an, verarbeitet die Interaktion und sendet die Informationen zurück an Teams. Dieses Dokument führt Sie durch die Auswahl von Aktionsbefehlsaufforderungsspeicherorten, das Erstellen Ihres Aufgabenmoduls, das Senden einer endgültigen Nachricht oder Karte, das Erstellen eines Aktionsbefehls mit App Studio oder das manuelle Erstellen. 

Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:

1. [Wo kann der Aktionsbefehl ausgelöst werden?](#select-action-command-invoke-locations)
1. [Wie wird das Aufgabenmodul erstellt?](#select-how-to-create-your-task-module)
1. [Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, die der Benutzer übermitteln kann?](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a>Auswählen von Aktionsbefehlsaufforderungsspeicherorten

Zunächst müssen Sie den Speicherort festlegen, an dem der Aktionsbefehl aufgerufen werden muss. Durch Angeben des `context` Befehls im App-Manifest kann der Befehl von einem oder mehreren der folgenden Speicherorte aufgerufen werden:

* Bereich zum Verfassen von Nachrichten: Die Schaltflächen unten im Bereich zum Verfassen von Nachrichten.
* Befehlsfeld: Durch @mentioning Ihre App im Befehlsfeld. 
   > [!NOTE]
   > Wenn die Messaging-Erweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.

* Nachricht: Direkt aus einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht. 
    > [!NOTE] 
    > Der anfängliche Aufruf für Ihren Bot enthält ein JSON-Objekt, das die Nachricht enthält, aus der er aufgerufen wurde. Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.

In der folgenden Abbildung werden die Speicherorte angezeigt, an denen der Aktionsbefehl aufgerufen wird:

![Aufrufen von Speicherorten des Aktionsbefehls](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a>Auswählen, wie Das Aufgabenmodul erstellt werden soll

Sie müssen nicht nur auswählen, von wo aus Der Befehl aufgerufen werden kann, sie müssen auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer aufgefüllt werden soll. Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:   

* **Statische Liste von Parametern:** Dies ist die einfachste Methode. Sie können eine Liste von Parametern in Ihrem App-Manifest definieren, die vom Teams Client gerendert wird, die Formatierung kann in diesem Fall jedoch nicht gesteuert werden.
* **Adaptive Karte:** Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch weiterhin auf die verfügbaren Steuerelemente und Formatierungsoptionen beschränkt.
* **Eingebettete Webansicht:** Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu haben. 

Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen und wenn der Benutzer das Aufgabenmodul sendet, wird die Messaging-Erweiterung aufgerufen. Bei Verwendung einer eingebetteten Webansicht oder einer adaptiven Karte muss Ihre Messaging-Erweiterung ein anfängliches Aufrufereignis des Benutzers verarbeiten, das Aufgabenmodul erstellen und an den Client zurückgeben.

## <a name="select-how-the-final-message-is-sent"></a>Auswählen, wie die endgültige Nachricht gesendet wird

In den meisten Fällen führt der Aktionsbefehl zu einer Karte, die in das Feld zum Verfassen von Nachrichten eingefügt wird. Der Benutzer kann es in den Kanal oder Chat senden. In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn die Messaging-Erweiterung aus dem Feld zum Verfassen oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread. Sie müssen das `bot` Objekt dem App-Manifest mit derselben ID hinzufügen und die entsprechenden Bereiche definieren.

## <a name="add-the-action-command-to-your-app-manifest"></a>Hinzufügen des Aktionsbefehls zum App-Manifest

Um den Aktionsbefehl zum App-Manifest hinzuzufügen, müssen Sie der `composeExtension` obersten Ebene des APP-Manifest-JSON ein neues Objekt hinzufügen. Dazu können Sie eine der folgenden Methoden verwenden:

* [Erstellen eines Aktionsbefehls mit App Studio](#create-an-action-command-using-app-studio)
* [Manuelles Erstellen eines Aktionsbefehls](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a>Erstellen eines Aktionsbefehls mit App Studio

Sie können einen Aktionsbefehl mit **App Studio** oder **dem Entwicklerportal** erstellen.

> [!NOTE]
> App Studio wird in Kürze eingestellt. Konfigurieren, verteilen und verwalten Sie Ihre Teams-Apps mit dem neuen [Entwicklerportal.](https://dev.teams.microsoft.com/)

# <a name="app-studio"></a>[App-Studio](#tab/AS)

> [!NOTE]
> Voraussetzung zum Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Messaging-Erweiterung erstellt haben. Informationen zum Erstellen einer Messaging-Erweiterung finden Sie unter [Erstellen einer Messaging-Erweiterung.](~/messaging-extensions/how-to/create-messaging-extension.md)

**So erstellen Sie einen Aktionsbefehl**

1. Öffnen Sie **App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Manifest-Editor"** aus.
1. Wenn Sie Ihr App-Paket bereits in **App Studio** erstellt haben, wählen Sie es aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes Paket.
1. Wählen Sie nach dem Importieren eines **App-Pakets Messaging-Erweiterungen** unter **"Funktionen"** aus. Sie erhalten ein Popupfenster zum Einrichten der Messaging-Erweiterung.
1. Wählen Sie im Fenster **"Einrichten"** aus, um die Messaging-Erweiterung in Ihre App-Oberfläche einzuschließen. In der folgenden Abbildung wird das Einrichtungsfenster der Messaging-Erweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. Um eine Messaging-Erweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie die Option **"Neuen Bot erstellen"** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie **"Erstellen"** aus. Die folgende Abbildung zeigt die Bot-Erstellung für die Messaging-Erweiterung:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Wählen Sie im **Abschnitt "Befehl"** der Seite "Messaging-Erweiterungen" die Option **"Hinzufügen"** aus, um die Befehle einzuschließen, die das Verhalten der Messaging-Erweiterung bestimmen.   
In der folgenden Abbildung wird die Befehlserweiterung für die Messaging-Erweiterung angezeigt:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. Wählen Sie **"Benutzern das Auslösen von Aktionen in externen Diensten innerhalb von Teams erlauben"** aus. In der folgenden Abbildung wird die Aktionsbefehlsauswahl angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. Um einen statischen Parametersatz zum Erstellen des Aufgabenmoduls zu verwenden, wählen Sie **einen Satz statischer Parameter für den Befehl** definieren aus. 

    In der folgenden Abbildung wird die Auswahl der statischen Parameter des Aktionsbefehls angezeigt:

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    Die folgende Abbildung zeigt ein Beispiel für die Einrichtung statischer Parameter: 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    Die folgende Abbildung zeigt ein Beispiel für statische Parametertests:

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. Um dynamische Parameter zu verwenden, wählen Sie aus, um **einen dynamischen Satz von Parametern von Ihrem Bot abzurufen.** In der folgenden Abbildung wird die Auswahl des Aktionsbefehlsparameters angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. Fügen Sie eine **Befehls-ID** und einen **Titel** hinzu.
1. Wählen Sie den Speicherort aus, an dem Sie den Aktionsbefehl aufrufen möchten. In der folgenden Abbildung wird der Aufrufspeicherort des Aktionsbefehls angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. Wählen Sie **Speichern** aus.
1. Um weitere Parameter hinzuzufügen, wählen Sie die Schaltfläche **"Hinzufügen"** im Abschnitt **"Parameter"** aus.

### <a name="create-an-action-command-manually"></a>Manuelles Erstellen eines Aktionsbefehls

Zum manuellen Hinzufügen des aktionsbasierten Messaging-Erweiterungsbefehls zum App-Manifest müssen Sie dem Array von Objekten die folgenden Parameter `composeExtension.commands` hinzufügen:

| Eigenschaftsname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss eine `action` . | Nein | 1.4 |
| `fetchTask` | Diese Eigenschaft wird `true` für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul sowie für eine statische Liste von `false` Parametern oder beim Laden der Webansicht durch eine `taskInfo` festgelegt. | Nein | 1.4 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Messaging-Erweiterung aufgerufen wird. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:

| Eigenschaftsname | Zweck | Ist erforderlich? | Mindestversion des Manifests |
|---|---|---|---|
| `parameters` | Diese Eigenschaft beschreibt die statische Liste der Parameter für den Befehl. Wird nur verwendet, wenn `fetchTask` `false` . | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke des Parameters oder ein Beispiel für den Wert, der angegeben werden soll. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine kurze Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Zu den möglichen Werten gehören `text` , , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist `text` auf . | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, `taskInfo` um Ihre Webansicht abzurufen, ohne Ihren Bot direkt aufzurufen. Wenn Sie diese Option auswählen, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern. In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Wenn Sie ein `taskInfo` Objekt verwenden, müssen Sie den `fetchTask` Parameter auf `false` .

| Eigenschaftsname | Zweck | Ist erforderlich? | Mindestversion des Manifests |
|---|---|---|---|
|`taskInfo`|Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden. | Nein | 1.4 |
|`taskInfo.title`|Titel des anfänglichen Aufgabenmoduls. |Nein | 1.4 |
|`taskInfo.width`|Die Breite des Aufgabenmoduls, entweder eine Zahl in Pixeln oder ein Standardlayout wie `large` , `medium` oder `small` . |Nein | 1.4 |
|`taskInfo.height`|Die Höhe des Aufgabenmoduls, entweder eine Zahl in Pixel oder ein Standardlayout wie `large` , `medium` oder `small` .|Nein | 1.4 |
|`taskInfo.url`|Ursprüngliche Webansichts-URL.|Nein | 1.4 | 

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Der folgende Abschnitt ist ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert. Es ist kein Beispiel für das vollständige Manifest. Das vollständige App-Manifestschema finden Sie unter [App-Manifestschema:](~/resources/schema/manifest-schema.md)

```json
...
"composeExtensions": [
  {
    "botId": "12a3c29f-1fc5-4d97-a142-12bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "addTodo",
        "description": "Create a To Do item",
        "title": "Create To Do",
        "type": "action",
        "context": ["commandBox", "message", "compose"],
        "fetchTask": true,
        "parameters": [
          {
            "name": "Name",
            "description": "To Do Title",
            "title": "Title",
            "inputType": "text"
          },
          {
            "name": "Description",
            "description": "Description of the task",
            "title": "Description",
            "inputType": "textarea"
          },
          {
            "name": "Date",
            "description": "Due date for the task",
            "title": "Date",
            "inputType": "date"
          }
        ]
      },
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Reassign a todo item",
        "type": "action",
        "fetchTask": true,
      }
    ]
  }
]
...
```

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams Messaging-Erweiterungsaktion| Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams Messaging-Erweiterungssuche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

Wenn Sie eine adaptive Karte oder eine eingebettete Webansicht ohne `taskInfo` Objekt verwenden, besteht der nächste Schritt in folgenden Schritten:

> [!div class="nextstepaction"]
> [Erstellen und Antworten mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem `taskInfo` Objekt verwenden, besteht der nächste Schritt darin:

> [!div class="nextstepaction"]
> [Antworten auf das Senden des Aufgabenmoduls](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

