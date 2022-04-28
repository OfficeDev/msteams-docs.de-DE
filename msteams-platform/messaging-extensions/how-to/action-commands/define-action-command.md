---
title: Definieren von Aktionsbefehlen für die Nachrichtenerweiterung
author: surbhigupta
description: Eine Übersicht über Aktionsbefehle für nachrichtenerweiterungen mit App-Manifestbeispiel
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ae0c39136b69b2759908bbbc54d1fff244eae0af
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65103947"
---
# <a name="define-message-extension-action-commands"></a>Definieren von Aktionsbefehlen für die Nachrichtenerweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Aktionsbefehle ermöglichen es Ihnen, Ihren Benutzern ein modales Popup zu präsentieren, das in Teams als Aufgabenmodul bezeichnet wird. Das Aufgabenmodul sammelt oder zeigt Informationen an, verarbeitet die Interaktion und sendet die Informationen an Teams zurück. In diesem Dokument erfahren Sie, wie Sie Speicherorte für Aktionsbefehle auswählen, Ihr Aufgabenmodul erstellen, endgültige Nachricht oder Karte senden, Aktionsbefehle mit app studio erstellen oder manuell erstellen.

Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:

1. [Woher kann der Aktionsbefehl ausgelöst werden?](#select-action-command-invoke-locations)
1. [Wie wird das Aufgabenmodul erstellt?](#select-how-to-create-your-task-module)
1. [Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, damit der Benutzer die Nachricht übermitteln kann?](#select-how-the-final-message-is-sent)

## <a name="select-action-command-invoke-locations"></a>Auswählen von Aktionsbefehlsspeicherorten

Zuerst müssen Sie den Speicherort festlegen, von dem aus Der Aktionsbefehl aufgerufen werden muss. Durch Angabe des `context` In-App-Manifests kann der Befehl von einem oder mehreren der folgenden Speicherorte aufgerufen werden:

* Nachrichtenbereich verfassen: Die Schaltflächen am unteren Rand des Nachrichtenbereichs zum Verfassen.

    Befehlskontext = Verfassen

* Befehlsfeld: Durch @mentioning Ihrer App im Befehlsfeld.

    Befehlskontext = commandBox

   > [!NOTE]
   > Wenn die Nachrichtenerweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.

* Nachricht: Direkt aus einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht.

    Befehlskontext = Nachricht

    > [!NOTE]
    > Der anfängliche Aufruf ihres Bots enthält ein JSON-Objekt, das die Nachricht enthält, aus der er aufgerufen wurde. Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.

In der folgenden Abbildung werden die Speicherorte angezeigt, an denen der Aktionsbefehl aufgerufen wird:

![Aktionsbefehl ruft Speicherorte auf](~/assets/images/messaging-extension-invoke-locations.png)

## <a name="select-how-to-create-your-task-module"></a>Auswählen, wie Das Aufgabenmodul erstellt wird

Sie müssen nicht nur auswählen, von wo aus Der Befehl aufgerufen werden kann, sondern auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer aufgefüllt werden soll. Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:

* **Statische Parameterliste**: Dies ist die einfachste Methode. Sie können eine Liste von Parametern in Ihrem App-Manifest definieren, die vom Teams Client gerendert werden, die Formatierung kann in diesem Fall jedoch nicht gesteuert werden.
* **Adaptive Karte**: Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie aber dennoch auf die verfügbaren Steuerelemente und Formatierungsoptionen beschränkt.
* **Eingebettete Webansicht**: Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu haben.

Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen möchten und wenn der Benutzer das Aufgabenmodul sendet, wird die Nachrichtenerweiterung aufgerufen. Wenn Sie eine eingebettete Webansicht oder eine adaptive Karte verwenden, muss ihre Nachrichtenerweiterung ein anfängliches Aufrufereignis vom Benutzer behandeln, das Aufgabenmodul erstellen und an den Client zurückgeben.

## <a name="select-how-the-final-message-is-sent"></a>Auswählen, wie die endgültige Nachricht gesendet wird

In den meisten Fällen führt der Aktionsbefehl dazu, dass eine Karte in das Feld zum Verfassen von Nachrichten eingefügt wird. Der Benutzer kann es in den Kanal oder Chat senden. In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn die Nachrichtenerweiterung über das Feld zum Verfassen oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread. Sie müssen das `bot` Objekt dem App-Manifest mit derselben ID hinzufügen und die entsprechenden Bereiche definieren.

## <a name="add-the-action-command-to-your-app-manifest"></a>Hinzufügen des Aktionsbefehls zum App-Manifest

Um den Aktionsbefehl zum App-Manifest hinzuzufügen, müssen Sie der obersten Ebene des App-Manifest-JSON ein neues `composeExtension` Objekt hinzufügen. Dazu können Sie eine der folgenden Methoden verwenden:

* [Erstellen eines Aktionsbefehls mit App Studio](#create-an-action-command-using-app-studio)
* [Manuelles Erstellen eines Aktionsbefehls](#create-an-action-command-manually)

### <a name="create-an-action-command-using-app-studio"></a>Erstellen eines Aktionsbefehls mit App Studio

Sie können einen Aktionsbefehl mit **App Studio** oder **Entwicklerportal** erstellen.

> [!NOTE]
> App Studio wird in Kürze eingestellt. Konfigurieren, verteilen und verwalten Sie Ihre Teams-Apps mit dem neuen [Entwicklerportal](https://dev.teams.microsoft.com/).

# <a name="app-studio"></a>[App-Studio](#tab/AS)

> [!NOTE]
> Die Voraussetzung zum Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Nachrichtenerweiterung erstellt haben. Informationen zum Erstellen einer Nachrichtenerweiterung finden [Sie unter Erstellen einer Nachrichtenerweiterung](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Aktionsbefehl**

1. Öffnen Sie **App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte "**Manifest-Editor**" aus.
1. Wenn Sie Ihr App-Paket bereits in **App Studio** erstellt haben, wählen Sie es aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren eines App-Pakets unter **"Funktionen**" **die Option "Nachrichtenerweiterungen**" aus. Sie erhalten ein Popupfenster zum Einrichten der Nachrichtenerweiterung.
1. Wählen Sie im Fenster " **Einrichten** " aus, um die Nachrichtenerweiterung in Ihre App-Umgebung einzuschließen. In der folgenden Abbildung wird das Fenster zum Einrichten der Nachrichtenerweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. Um eine Nachrichtenerweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie " **Neuen Bot erstellen** " aus, geben Sie einen Namen für den neuen Bot, und wählen Sie **"Erstellen"** aus. In der folgenden Abbildung wird die Bot-Erstellung für die Nachrichtenerweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Wählen Sie im **Abschnitt "Befehl"** der Seite "Nachrichtenerweiterungen" die Option "**Hinzufügen**" aus, um die Befehle einzuschließen, die das Verhalten der Nachrichtenerweiterung bestimmen.
In der folgenden Abbildung wird die Befehlserweiterung für die Nachrichtenerweiterung angezeigt:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>

1. Wählen Sie **"Benutzern erlauben" aus, Aktionen in externen Diensten innerhalb von Teams auszulösen**. In der folgenden Abbildung wird die Aktionsbefehlsauswahl angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-selection.png" alt="action command selection" width="500"/>

1. Wenn Sie einen statischen Parametersatz zum Erstellen des Aufgabenmoduls verwenden möchten, wählen Sie einen **Satz statischer Parameter für den Befehl definieren** aus.

    In der folgenden Abbildung wird die Statische Parameterauswahl des Aktionsbefehls angezeigt:

   <img src="~/assets/images/messaging-extension/action-command-static-parameter-selection.png" alt="action command static parameter selection" width="500"/>

    Die folgende Abbildung zeigt ein Beispiel für die Einrichtung statischer Parameter:

   <img src="~/assets/images/messaging-extension/setting-up-of-static-parameter.png" alt="action command static parameter set-up" width="500"/>

    Die folgende Abbildung zeigt ein Beispiel für statische Parametertests:

   <img src="~/assets/images/messaging-extension/static-parameter-testing.png" alt="action command static parameter testing" width="500"/>

1. Um dynamische Parameter zu verwenden, wählen Sie aus, um **einen dynamischen Satz von Parametern von Ihrem Bot abzurufen**. In der folgenden Abbildung wird die Aktionsbefehlsparameterauswahl angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-dynamic-parameter-selection.png" alt="action command dynamic parameter selection" width="500"/>

1. Fügen Sie eine **Befehls-ID** und einen **Titel** hinzu.
1. Wählen Sie den Speicherort aus, an dem Sie den Aktionsbefehl aufrufen möchten. In der folgenden Abbildung wird der Aktionsbefehlsspeicherort angezeigt:

    <img src="~/assets/images/messaging-extension/action-command-invoke-location.png" alt="action command invoke location" width="500"/>

1. Wählen Sie **Speichern**.
1. Um weitere Parameter hinzuzufügen, wählen Sie die Schaltfläche **"Hinzufügen** " im Abschnitt **"Parameter** " aus.

### <a name="create-an-action-command-manually"></a>Manuelles Erstellen eines Aktionsbefehls

Zum manuellen Hinzufügen des Befehls für die aktionsbasierte Nachrichtenerweiterung zum App-Manifest müssen Sie dem Array von Objekten die `composeExtension.commands` folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestmanifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss ein `action`. | Nein | 1.4 |
| `fetchTask` | Diese Eigenschaft ist für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul und`false` für eine statische Liste von Parametern oder beim Laden der Webansicht durch eine `taskInfo`festgelegt`true`. | Nein | 1.4 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Nachrichtenerweiterung aufgerufen wird. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Ist das erforderlich? | Mindestmanifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft beschreibt die statische Liste der Parameter für den Befehl. Nur verwenden, wenn `fetchTask` `false`ist . | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Werts, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Die möglichen Werte sind `text`, `textarea`, `number`, `date`, `time`, `toggle`. Der Standardwert ist auf `text`. | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie das `taskInfo` Objekt optional hinzufügen, um Ihre Webansicht abzurufen, ohne den Bot direkt aufzurufen. Wenn Sie diese Option auswählen, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern. Die erste Interaktion mit Ihrem Bot besteht darin, [auf die Aktion zum Senden des Aufgabenmoduls zu reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Wenn Sie ein `taskInfo` Objekt verwenden, müssen Sie den `fetchTask` Parameter auf `false`festlegen.

| Eigenschaftenname | Zweck | Ist das erforderlich? | Mindestmanifestversion |
|---|---|---|---|
|`taskInfo`|Geben Sie das Aufgabenmodul an, das bei Verwendung eines Befehls für die Nachrichtenerweiterung vorab geladen werden soll. | Nein | 1.4 |
|`taskInfo.title`|Titel des anfänglichen Aufgabenmoduls. |Nein | 1.4 |
|`taskInfo.width`|Breite des Aufgabenmoduls, entweder eine Zahl in Pixeln oder Standardlayout wie `large`, `medium`oder `small`. |Nein | 1.4 |
|`taskInfo.height`|Höhe des Aufgabenmoduls, entweder eine Zahl in Pixel oder Standardlayout wie `large`, `medium`oder `small`.|Nein | 1.4 |
|`taskInfo.url`|Ursprüngliche Webansichts-URL.|Nein | 1.4 |

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
|Teams Nachrichtenerweiterungsaktion| Beschreibt das Definieren von Aktionsbefehlen, das Erstellen eines Aufgabenmoduls und das Reagieren auf Aufgabenmodul-Sendeaktionen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-meetingextension-action.yml) zum Erstellen Teams aktionsbasierten Nachrichtenerweiterung.

## <a name="next-step"></a>Nächster Schritt

Wenn Sie entweder eine adaptive Karte oder eine eingebettete Webansicht ohne Objekt `taskInfo` verwenden, gehen Sie im nächsten Schritt wie folgt vor:

> [!div class="nextstepaction"]
> [Erstellen und Reagieren mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem `taskInfo` Objekt verwenden, gehen Sie im nächsten Schritt wie folgt vor:

> [!div class="nextstepaction"]
> [Reagieren auf das Übermitteln von Aufgabenmodulen](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
