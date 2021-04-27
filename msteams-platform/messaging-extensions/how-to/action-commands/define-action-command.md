---
title: Definieren von Befehlen für Nachrichtenerweiterungsaktion
author: clearab
description: Übersicht über Messagingerweiterungsaktionsbefehle
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f49e821ecb98659b4cfd68f93b37f1a8f611a9fb
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020716"
---
# <a name="define-messaging-extension-action-commands"></a>Definieren von Befehlen für Nachrichtenerweiterungsaktion

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mit Aktionsbefehlen können Sie Ihren Benutzern ein modales Popup präsentieren, das als Aufgabenmodul in Teams bezeichnet wird. Das Aufgabenmodul sammelt oder zeigt Informationen an, verarbeitet die Interaktion und sendet die Informationen zurück an Teams. In diesem Dokument erfahren Sie, wie Sie Aktionsbefehlsaufrufe auswählen, Ihr Aufgabenmodul erstellen, endgültige Nachrichten oder Karten senden, Aktionsbefehle mithilfe von App Studio erstellen oder manuell erstellen. 

Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:

1. [Wo kann der Aktionsbefehl ausgelöst werden?](#select-action-command-invoke-locations)
1. [Wie wird das Aufgabenmodul erstellt?](#select-how-to-create-your-task-module)
1. [Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, damit der Benutzer die Nachricht übermitteln kann?](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a>Auswählen von Aktionsbefehlsaufrufen

Zuerst müssen Sie den Speicherort festlegen, von dem aus der Aktionsbefehl aufgerufen werden muss. Durch Angeben des In-App-Manifests kann Ihr Befehl an einem oder mehreren der folgenden `context` Speicherorte aufgerufen werden:

* Bereich "Nachricht verfassen": Die Schaltflächen am unteren Rand des Bereichs "Verfassen von Nachrichten".
* Befehlsfeld: Durch @mentioning App im Befehlsfeld. 
   > [!NOTE]
   > Wenn die Messagingerweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.

* Nachricht: Direkt von einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht. 
    > [!NOTE] 
    > Der anfängliche Aufruf ihres Bots enthält ein JSON-Objekt, das die Nachricht enthält, von der sie aufgerufen wurde. Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.

In der folgenden Abbildung werden die Speicherorte angezeigt, an denen der Aktionsbefehl aufgerufen wird:

![Aktionsbefehl ruft Speicherorte auf](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a>Auswählen, wie Sie Ihr Aufgabenmodul erstellen

Sie müssen nicht nur auswählen, von wo aus Der Befehl aufgerufen werden kann, sondern auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer auffüllt werden soll. Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:   

* **Statische Liste der Parameter:** Dies ist die einfachste Methode. Sie können eine Liste der Parameter in Ihrem App-Manifest definieren, das der Teams-Client rendert, die Formatierung in diesem Fall jedoch nicht steuern.
* **Adaptive Karte**: Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch weiterhin die verfügbaren Steuerelemente und Formatierungsoptionen einschränkt.
* **Eingebettete Webansicht:** Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu erhalten. 

Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen möchten und wenn der Benutzer das Aufgabenmodul übermittelt, wird die Messagingerweiterung aufgerufen. Bei Verwendung einer eingebetteten Webansicht oder einer adaptiven Karte muss Ihre Messagingerweiterung ein anfängliches Aufrufereignis vom Benutzer behandeln, das Aufgabenmodul erstellen und an den Client zurückgeben.

## <a name="select-how-the-final-message-is-sent"></a>Auswählen, wie die endgültige Nachricht gesendet wird

In den meisten Fällen führt der Aktionsbefehl zu einer Karte, die in das Meldungsfeld Verfassen eingefügt wird. Der Benutzer kann es an den Kanal oder Chat senden. In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn die Messagingerweiterung aus dem Verfassenfeld oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread. Sie müssen das Objekt dem App-Manifest mit derselben ID hinzufügen `bot` und die entsprechenden Bereiche definieren.

## <a name="add-the-action-command-to-your-app-manifest"></a>Hinzufügen des Aktionsbefehls zum App-Manifest

Zum Hinzufügen des Aktionsbefehls zum App-Manifest müssen Sie der obersten Ebene des App-Manifest-JSON ein neues `composeExtension` Objekt hinzufügen. Dazu können Sie eine der folgenden Möglichkeiten verwenden:

* [Erstellen eines Aktionsbefehls mithilfe von App Studio](#create-an-action-command-using-app-studio)
* [Manuelles Erstellen eines Aktionsbefehls](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a>Erstellen eines Aktionsbefehls mithilfe von App Studio

> [!NOTE]
> Voraussetzung für das Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Messagingerweiterung erstellt haben. Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Aktionsbefehl**

1. Öffnen **Sie App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1. Wenn Sie Ihr App-Paket bereits in **App Studio erstellt haben,** wählen Sie es aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren eines App-Pakets unter Funktionen die Option **Messagingerweiterungen** **aus.** Sie erhalten ein Popupfenster zum Einrichten der Messagingerweiterung.
1. Wählen **Sie Einrichten** im Fenster aus, um die Messagingerweiterung in Ihre App-Umgebung zu verwenden. In der folgenden Abbildung wird das Einrichtungsfenster der Messagingerweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>
    
1. Zum Erstellen einer Messagingerweiterung benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen **Sie Die Option Neuer Bot erstellen** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie Erstellen **aus.** In der folgenden Abbildung wird die Boterstellung für die Messagingerweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Wählen **Sie Im** Abschnitt Befehl **der** Seite Messagingerweiterungen die Option Hinzufügen aus, um die Befehle hinzuzufügen, die das Verhalten der Messagingerweiterung bestimmen.   
In der folgenden Abbildung wird die Befehlserweiterung für die Messagingerweiterung angezeigt:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. Wählen **Sie Benutzer zulassen aus, um Aktionen in externen Diensten innerhalb von Teams auszulösen.** In der folgenden Abbildung wird die Aktionsbefehlsauswahl angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>
    
1. Um einen statischen Parametersatz zum Erstellen des Aufgabenmoduls zu verwenden, wählen Sie Definieren einer Reihe statischer Parameter **für den Befehl aus.** 

    In der folgenden Abbildung wird die Auswahl statischer Parameter des Aktionsbefehls angezeigt:

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/> 
   
    Die folgende Abbildung zeigt ein Beispiel für die Einrichtung statischer Parameter: 

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    Die folgende Abbildung zeigt ein Beispiel für statische Parametertests:

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. Um dynamische Parameter zu verwenden, wählen Sie aus, um einen dynamischen Satz **von Parametern aus Ihrem Bot zu holen.** In der folgenden Abbildung wird die Auswahl des Aktionsbefehls angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>
    
1. Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**
1. Wählen Sie den Speicherort aus, an dem Sie den Aktionsbefehl aufrufen möchten. In der folgenden Abbildung wird der Speicherort des Aktionsbefehls angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. Wählen Sie **Speichern** aus.
1. Um weitere Parameter hinzuzufügen, wählen Sie **im** Abschnitt Parameter **die** Schaltfläche Hinzufügen aus.

### <a name="create-an-action-command-manually"></a>Manuelles Erstellen eines Aktionsbefehls

Zum manuellen Hinzufügen des aktionsbasierten Messagingerweiterungsbefehls zum App-Manifest müssen Sie dem Objektarray die folgenden `composeExtension.commands` Parameter hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss eine `action` sein. | Nein | 1.4 |
| `fetchTask` | Diese Eigenschaft ist für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul und für eine statische Liste von Parametern oder beim Laden der Webansicht durch `true` `false` eine `taskInfo` festgelegt. | Nein | 1.4 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Messagingerweiterung aufgerufen wird. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Ist erforderlich? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft beschreibt die statische Liste der Parameter für den Befehl. Verwenden Sie nur, `fetchTask` wenn `false` . | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Parameters, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft ist auf den typ der erforderlichen Eingabe festgelegt. Die möglichen Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` festgelegt. | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, um Ihre Webansicht ohne `taskInfo` direkten Aufruf des Bots zu abrufen. Wenn Sie diese Option auswählen, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern. In that the first interaction with your bot is [responding to the task module submit action](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Wenn Sie ein Objekt `taskInfo` verwenden, müssen Sie den `fetchTask` Parameter auf `false` festlegen.

| Eigenschaftenname | Zweck | Ist erforderlich? | Minimale Manifestversion |
|---|---|---|---|
|`taskInfo`|Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vorab geladen werden soll. | Nein | 1.4 |
|`taskInfo.title`|Titel des anfänglichen Aufgabenmoduls. |Nein | 1.4 |
|`taskInfo.width`|Breite des Aufgabenmoduls, entweder eine Zahl in Pixel oder ein Standardlayout wie `large` , `medium` oder `small` . |Nein | 1.4 |
|`taskInfo.height`|Höhe des Aufgabenmoduls, entweder eine Zahl in Pixel oder ein Standardlayout wie `large` , `medium` oder `small` .|Nein | 1.4 |
|`taskInfo.url`|Anfängliche Webansichts-URL.|Nein | 1.4 | 

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Der folgende Abschnitt ist ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert. Es ist kein Beispiel für das vollständige Manifest. Das vollständige App-Manifestschema finden Sie unter [App-Manifestschema](~/resources/schema/manifest-schema.md):

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
|Messagingerweiterungsaktion für Teams| Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Suche nach Messagingerweiterungen in Teams   |  Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

Wenn Sie entweder eine adaptive Karte oder eine eingebettete Webansicht ohne Objekt verwenden, ist `taskInfo` der nächste Schritt:

> [!div class="nextstepaction"]
> [Erstellen und Reagieren mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem Objekt `taskInfo` verwenden, ist der nächste Schritt:

> [!div class="nextstepaction"]
> [Reagieren auf Absenden des Aufgabenmoduls](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

