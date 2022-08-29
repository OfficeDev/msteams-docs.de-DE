---
title: Definieren von Aktionsbefehlen für Nachrichtenerweiterungen
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Aktionsbefehle für Messaging-Erweiterungen mit dem App-Manifestbeispiel in Microsoft Teams definieren.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0b51d34aaacfe38c077b03b5df8bb6a9227c5b61
ms.sourcegitcommit: 217025a61ed9c3b76b507fe95563142abc6d0318
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2022
ms.locfileid: "67363459"
---
# <a name="define-message-extension-action-commands"></a>Definieren von Aktionsbefehlen für Nachrichtenerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> Wenn eine Nachrichtenaktion initiiert wird, werden Anlagendetails nicht als Teil der `turncontext` Aufrufaktivität gesendet.

Aktionsbefehle ermöglichen es Ihnen, Ihren Benutzern ein modales Popup zu präsentieren, das als Aufgabenmodul in Teams bezeichnet wird. Das Aufgabenmodul sammelt Informationen oder zeigt diese an, verarbeitet die Interaktion und sendet die Informationen an Teams zurück. In diesem Dokument erfahren Sie, wie Sie Speicherorte zum Aufrufen des Aktionsbefehls auswählen, ein Aufgabenmodul erstellen, die endgültige Nachricht oder Karte senden sowie einen Aktionsbefehl mit App Studio oder manuell erstellen.

Bevor Sie den Aktionsbefehl erstellen, müssen Sie die folgenden Faktoren festlegen:

1. [Von wo kann der Aktionsbefehl ausgelöst werden?](#select-action-command-invoke-locations)
1. [Wie wird das Aufgabenmodul erstellt?](#select-how-to-create-your-task-module)
1. [Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, damit der Benutzer die Nachricht bzw. Karte übermitteln kann?](#select-how-the-final-message-is-sent)

Im folgenden Video erfahren Sie, wie Sie Aktionsbefehle für Nachrichtenerweiterungen definieren:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OANG]
<br>

## <a name="select-action-command-invoke-locations"></a>Auswählen von Speicherorten zum Aufrufen von Aktionsbefehlen

Zuerst müssen Sie den Speicherort festlegen, von dem aus der Aktionsbefehl aufgerufen werden muss. Durch Angabe des `context` im App-Manifests kann der Befehl von einem oder mehreren der folgenden Speicherorte aufgerufen werden:

* Bereich zum Verfassen von Nachrichten: die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten.

    Befehlskontext = compose

* Befehlsfeld: durch @Erwähnen der App im Befehlsfeld.

    Befehlskontext = commandBox

   > [!NOTE]
   > Wenn die Nachrichtenerweiterung über das Befehlsfeld aufgerufen wird, können Sie nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wurde.

* Nachricht: direkt aus einer vorhandenen Nachricht über das `...` Überlaufmenü einer Nachricht.

    Befehlskontext = message

    > [!NOTE]
    > Der anfängliche Aufruf des Bots enthält ein JSON-Objekt, das die Nachricht enthält, aus der er aufgerufen wurde. Sie können die Nachricht verarbeiten, bevor Sie sie mit einem Aufgabenmodul präsentieren.

In der folgenden Abbildung werden die Speicherorte angezeigt, von denen der Aktionsbefehl aufgerufen wird:

:::image type="content" source="~/assets/images/messaging-extension-invoke-locations.png" alt-text="Speicherorte zum Aufrufen von Aktionsbefehlen":::

## <a name="select-how-to-create-your-task-module"></a>Auswählen, wie Sie Ihr Aufgabenmodul erstellen möchten

Sie müssen nicht nur auswählen, von wo aus der Befehl aufgerufen werden kann, sondern auch, wie das Formular im Aufgabenmodul für Ihre Benutzer aufgefüllt werden soll. Sie haben die folgenden drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:

* **Statische Parameterliste**: Dies ist die einfachste Methode. Sie können eine Liste von Parametern in Ihrem App-Manifest definieren, die der Teams-Client rendert, die Formatierung in diesem Fall jedoch nicht steuern.
* **Adaptive Karte**: Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, die Ihnen zur Verfügung stehenden Steuerelemente und Formatierungsoptionen aber dennoch beschränkt.
* **Eingebettete Webansicht**: Sie können eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten, um eine vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente zu haben.

Wenn Sie das Aufgabenmodul mit einer statischen Liste von Parametern erstellen möchten und der Benutzer das Aufgabenmodul übermittelt, wird die Nachrichtenerweiterung aufgerufen. Wenn Sie eine eingebettete Webansicht oder eine adaptive Karte verwenden, muss Ihre Nachrichtenerweiterung ein anfängliches Aufrufereignis vom Benutzer behandeln, das Aufgabenmodul erstellen und an den Client zurücksenden.

## <a name="select-how-the-final-message-is-sent"></a>Auswählen, wie die endgültige Nachricht gesendet wird

In den meisten Fällen führt der Aktionsbefehl dazu, dass eine Karte in das Feld zum Verfassen von Nachrichten eingefügt wird. Der Benutzer kann sie in den Kanal oder Chat senden. In diesem Fall stammt die Nachricht vom Benutzer, und der Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn die Nachrichtenerweiterung über das Feld zum Verfassen oder direkt aus einer Nachricht aufgerufen wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall stammt die adaptive Karte vom Bot, der Bot aktualisiert sie und antwortet bei Bedarf auf den Unterhaltungsthread. Sie müssen das Objekt `bot` dem App-Manifest mit derselben ID hinzufügen und die entsprechenden Bereiche definieren.

## <a name="add-the-action-command-to-your-app-manifest"></a>Hinzufügen des Aktionsbefehls zum App-Manifest

Um den Aktionsbefehl zum App-Manifest hinzuzufügen, müssen Sie der obersten Ebene des App-Manifest-JSON ein neues Objekt `composeExtension` hinzufügen. Dazu können Sie eine der folgenden Methoden verwenden:

* [Erstellen eines Aktionsbefehls mithilfe des Entwicklerportals](#create-an-action-command-using-developer-portal)
* [Manuelles Erstellen eines Aktionsbefehls](#create-an-action-command-manually)

### <a name="create-an-action-command-using-developer-portal"></a>Erstellen eines Aktionsbefehls mithilfe des Entwicklerportals

Sie können einen Aktionsbefehl über das **Entwicklerportal** erstellen.

# <a name="app-studio"></a>[App-Studio](#tab/AS)

> [!NOTE]
> Die Voraussetzung zum Erstellen eines Aktionsbefehls ist, dass Sie bereits eine Nachrichtenerweiterung erstellt haben. Informationen zum Erstellen einer Nachrichtenerweiterung finden Sie unter [Erstellen einer Nachrichtenerweiterung](~/messaging-extensions/how-to/create-messaging-extension.md).

So erstellen Sie einen Aktionsbefehl:

1. Öffnen Sie **das Entwicklerportal** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Apps** " aus. Wenn Sie Ihr App-Paket bereits im **Entwicklerportal** erstellt haben, wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren eines App-Pakets **nachrichtenerweiterungen** unter **"App-Features"** aus.
1. Um eine Nachrichtenerweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie " **Neuen Bot erstellen** " aus, geben Sie dem neuen Bot einen Namen, und wählen Sie dann " **Erstellen"** aus.

   :::image type="content" source="../../../assets/images/tdp/bot-page.png" alt-text="Der Screenshot zeigt, wie Sie einen Bot im Entwicklerportal erstellen.":::

1. Um einen vorhandenen Bot zu verwenden, wählen **Sie einen vorhandenen Bot** und dann die vorhandenen Bots aus der Dropdownliste aus, oder geben **Sie eine Bot-ID ein** , wenn Sie bereits eine Bot-ID erstellt haben.

1. Wählen Sie den Bereich der Messaging-Erweiterung und dann **"Speichern"** aus.

1. Wählen Sie " **Befehl hinzufügen"** im Abschnitt **"Befehl** " aus, um die Befehle einzuschließen, die das Verhalten der Nachrichtenerweiterung bestimmen.

   :::image type="content" source="../../../assets/images/tdp/add-a-command.PNG" alt-text="Screenshot zeigt, wie Sie einen Befehl hinzufügen, um das Verhalten der Nachrichtenerweiterung zu definieren.":::

1. Wählen Sie **"Aktion"** und dann "Parametertyp" aus.

1. Geben Sie **Befehls-ID**, **Befehlstitel** und **Befehlsbeschreibung** ein.

1. Geben Sie alle Parameter ein, und wählen Sie den Typ der Eingabe aus der Dropdownliste aus.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-parameter.PNG" alt-text="Der Screenshot zeigt, wie Sie einen Parameter hinzufügen, um Den Befehl für die Nachrichtenerweiterung zu definieren.":::

1. Wählen Sie unter "**Vorschaulinks****" die Option "Domäne hinzufügen"** aus.

1. Geben Sie eine gültige Domäne ein, und wählen Sie dann **"Hinzufügen"** aus.

   :::image type="content" source="../../../assets/images/tdp/add-domain.PNG" alt-text="Screenshot zeigt, wie Sie Ihrer Messaging-Erweiterung eine gültige Domäne für die Verbreitung von Links hinzufügen.":::

1. Wählen Sie **Speichern**.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-save.PNG" alt-text="Der Screenshot zeigt, wie Sie alle Einstellungen und Parameter für Ihre Nachrichtenerweiterung speichern.":::

**So fügen Sie zusätzliche Parameter hinzu**

1. Wählen Sie im Befehlsbereich die Ellipse und dann den **Parameter "Bearbeiten"** aus.

   :::image type="content" source="../../../assets/images/tdp/edit-parameters.PNG" alt-text="Screenshots zeigen, wie Sie zusätzliche Parameter für Ihre Nachrichtenerweiterung hinzufügen.":::

1. Wählen Sie **"Parameter hinzufügen"** aus, und geben Sie alle Parameter ein.

   :::image type="content" source="../../../assets/images/tdp/add-parameter.PNG" alt-text="Der Screenshot zeigt, wie Sie zusätzliche Parameter für Ihre Nachrichtenerweiterung hinzufügen."lightbox="../../../assets/images/tdp/add-a-parameters.PNG":::

### <a name="create-an-action-command-manually"></a>Manuelles Erstellen eines Aktionsbefehls

Zum manuellen Hinzufügen des Befehls für die aktionsbasierte Nachrichtenerweiterung zum App-Manifest müssen Sie dem Array von Objekten `composeExtension.commands` die folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss eine `action` sein. | Nein | 1.4 |
| `fetchTask` | Diese Eigenschaft ist für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul auf `false` und für eine statische Liste von Parametern oder beim Laden der Webansicht durch eine `taskInfo` auf `true` festgelegt. | Nein | 1.4 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das definiert, von wo aus die Nachrichtenerweiterung aufgerufen wird. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, müssen Sie auch die folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Erforderlich? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft beschreibt die statische Liste von Parametern für den Befehl. Nur verwenden, wenn `fetchTask` gleich `false` ist. | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt den Zweck des Parameters oder ein Beispiel für den Wert, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft ist auf den Typ der erforderlichen Eingabe festgelegt. Folgende Werte stehen zur Verfügung: `text`, `textarea`, `number`, `date`, `time`, `toggle`. Der Standardwert ist `text`. | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie das `taskInfo` Objekt optional hinzufügen, um Ihre Webansicht abzurufen, ohne den Bot direkt aufzurufen. Wenn Sie diese Option auswählen, ist das Verhalten ähnlich wie bei der Verwendung einer statischen Liste von Parametern. Die erste Interaktion mit Ihrem Bot besteht darin, [auf die Aufgabenmodul-Sendeaktion zu reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Wenn Sie ein `taskInfo` Objekt verwenden, müssen Sie den `fetchTask` Parameter auf `false`festlegen.

| Eigenschaftenname | Zweck | Erforderlich? | Minimale Manifestversion |
|---|---|---|---|
|`taskInfo`|Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Nachrichtenerweiterungsbefehl verwenden. | Nein | 1.4 |
|`taskInfo.title`|Titel des anfänglichen Aufgabenmoduls. |Nein | 1.4 |
|`taskInfo.width`|Aufgabenmodulbreite: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. `large`, `medium` oder `small`. |Nein | 1.4 |
|`taskInfo.height`|Aufgabenmodulhöhe: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. `large`, `medium` oder `small`.|Nein | 1.4 |
|`taskInfo.url`|Anfängliche Webansichts-URL.|Nein | 1.4 |

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Der folgende Abschnitt ist ein Beispiel für ein Objekt `composeExtensions`, das zwei Aktionsbefehle definiert. Es ist kein Beispiel für das vollständige Manifest. Das vollständige App-Manifestschema finden Sie unter [App-Manifestschema](~/resources/schema/manifest-schema.md):

```json
...
"composeExtensions": [
  {
    "botId": "c8fa3cf6-b1f0-4ba8-a5bf-a241bc29adf3",
    "scopes": [
      "personal",
      "groupchat"
    ],
    "commands": [
      {
        "id": "To do",
        "type": "action",
        "title": "Create To do",
        "description": "Create a To do",
        "initialRun": true,
        "fetchTask": false,
        "context": [
          "commandBox",
          "compose"
        ],
        "parameters": [
          {
            "name": "Name",
            "title": "Title",
            "description": "To do Title",
            "inputType": "text"
          },
          {
            "name": "Description",
            "title": "Description",
            "description": "Description of the task",
            "inputType": "textarea"
          },
          {
            "name": "Date",
            "title": "Date",
            "description": "Due date for the task",
            "inputType": "date"
          }
        ]
      }
    ],
    "canUpdateConfiguration": true,
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "yourapp.onmicrosoft.com"
          ]
        }
      }
    ]
  }
]
...
```

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams-Nachrichtenerweiterungen – Aktion| Beschreibt, wie Aktionsbefehle definiert werden, ein Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktionen reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-meetingextension-action.yml) zum Erstellen einer aktionsbasierten Teams-Nachrichtenerweiterung.

## <a name="next-step"></a>Nächster Schritt

Wenn Sie entweder eine adaptive Karte oder eine eingebettete Webansicht ohne Objekt `taskInfo` verwenden, gehen Sie im nächsten Schritt wie folgt vor:

> [!div class="nextstepaction"]
> [Aufgabenmodul erstellen und damit reagieren](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie die Parameter oder eine eingebettete Webansicht mit einem `taskInfo` Objekt verwenden, gehen Sie im nächsten Schritt wie folgt vor:

> [!div class="nextstepaction"]
> [Auf das Senden des Aufgabenmoduls reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
