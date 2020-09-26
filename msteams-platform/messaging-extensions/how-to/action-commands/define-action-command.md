---
title: Definieren von Aktions Befehlen für die Nachrichten Erweiterung
author: clearab
description: Eine Übersicht über Messaging-Erweiterungen auf der Microsoft Teams-Plattform
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 89cf92260418701ef4809f5a13750b991b9f7acb
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279682"
---
# <a name="define-messaging-extension-action-commands"></a>Definieren von Aktions Befehlen für die Nachrichten Erweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Aktionsbefehle ermöglichen es Ihnen, Ihren Benutzern ein modales Popup (in Teams als Aufgabenmodul bezeichnet) zu präsentieren, um Informationen zu sammeln oder anzuzeigen, dann ihre Interaktion zu verarbeiten und Informationen in Teams zurückzuschicken. Vor dem Erstellen des Befehls müssen Sie Folgendes entscheiden:

1. Woher kann der Befehl Action ausgelöst werden?
1. Wie wird das Aufgabenmodul erstellt?
1. Wird die letzte Nachricht oder Karte von einem bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Verfassen-Nachrichtenbereich eingefügt, damit der Benutzer übermitteln kann?

## <a name="choose-action-command-invoke-locations"></a>Auswählen eines Aktionsbefehls zum Aufrufen von Speicherorten

Das erste, was Sie entscheiden müssen, ist, wo Ihr Aktionsbefehl (oder genauer gesagt, *aufgerufen*) aus ausgelöst werden kann. Durch Angeben des `context` in Ihrem App-Manifest kann der Befehl von einem oder mehreren der folgenden Speicherorte aufgerufen werden:

* Die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten.
* Durch @mentioning Ihrer APP im Befehlsfeld. Hinweis: Sie können nicht mit einer bot-Nachricht antworten, die direkt in die Unterhaltung eingefügt wird, wenn Ihre Messaging-Erweiterung aus dem Befehlsfeld aufgerufen wird.
* Direkt aus einer vorhandenen Nachricht über die... Überlaufmenü in einer Nachricht. Hinweis: die anfängliche Invoke-Funktion für Ihren bot umfasst ein JSON-Objekt, das die Nachricht enthält, aus der es aufgerufen wurde, die Sie verarbeiten können, bevor Sie Sie mit einem Aufgabenmodul präsentieren.

## <a name="choose-how-to-build-your-task-module"></a>Auswählen der Vorgehensweise zum Erstellen des Aufgabenmoduls

Neben der Auswahl, aus der der Befehl aufgerufen werden kann, müssen Sie auch auswählen, wie das Formular im Aufgabenmodul für die Benutzer aufgefüllt werden soll. Sie haben drei Optionen zum Erstellen des Formulars, das im Aufgabenmodul gerendert wird:

* **Statische Liste von Parametern** -Dies ist die einfachste Option. Sie können eine Liste von Parametern (Eingabefelder) in Ihrem App-Manifest definieren, das vom Microsoft Teams-Client gerendert wird. Mit dieser Option können Sie die Formatierung nicht steuern.
* **Adaptive Karte** – Sie können eine Adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch immer noch auf die verfügbaren Steuerelemente und Formatierungsoptionen beschränkt.
* **Eingebettete Webansicht** : Wenn Sie die vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente benötigen, können Sie eine benutzerdefinierte Webansicht im Aufgabenmodul einbetten.

Wenn Sie Ihr Aufgabenmodul mit einer statischen Liste von Parametern erstellen, wird der erste Aufruf Ihrer Messaging Erweiterung angezeigt, wenn ein Benutzer den Aufgabenmodul übermittelt. Bei Verwendung einer eingebetteten Webansicht oder einer adaptiven Karte muss Ihre Messaging Erweiterung ein anfängliches Invoke-Ereignis des Benutzers verarbeiten, den Aufgabenmodul erstellen und zurück an den Client zurückgeben.

## <a name="choose-how-the-final-message-will-be-sent"></a>Auswählen, wie die abschließende Nachricht gesendet wird

In den meisten Fällen führt Ihr Aktionsbefehl dazu, dass eine Karte in das Meldungsfeld verfassen eingefügt wird. Ihr Benutzer kann dann beschließen, ihn in den Kanal oder Chat zu senden. Die Nachricht kommt in diesem Fall vom Benutzer, und Ihr Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn Ihre Messaging Erweiterung aus dem Feld Verfassen oder direkt aus einer Nachricht ausgelöst wird, kann Ihr Webdienst die abschließende Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall kommt die Adaptive Karte aus dem bot, der Bot kann Sie aktualisieren, und der Bot kann bei Bedarf auch auf den Gesprächsfaden Antworten. Sie müssen das `bot` Objekt Ihrem App-Manifest mit derselben ID hinzufügen und die entsprechenden Bereiche definieren.

## <a name="add-the-command-to-your-app-manifest"></a>Hinzufügen des Befehls zum App-Manifest

Nachdem Sie sich entschieden haben, wie Benutzer mit Ihrem Aktionsbefehl interagieren sollen, ist es an der Zeit, diese dem App-Manifest hinzuzufügen. Zu diesem Zweck fügen Sie ein neues `composeExtension` Objekt zur obersten Ebene des JSON-App-Manifests hinzu. Sie können dies entweder mit Hilfe von App Studio oder manuell tun.

### <a name="create-a-command-using-app-studio"></a>Erstellen eines Befehls mit App Studio

In den folgenden Schritten wird davon ausgegangen, dass Sie bereits [eine Messaging Erweiterung erstellt](~/messaging-extensions/how-to/create-messaging-extension.md)haben.

1. Öffnen Sie auf dem Microsoft Teams-Client **App Studio** , und wählen Sie die Registerkarte **Manifest-Editor** aus.
2. Wenn Sie Ihr App-Paket bereits in App Studio erstellt haben, wählen Sie es aus der Liste aus. Wenn dies nicht der Fall ist, können Sie ein vorhandenes App-Paket importieren.
3. Klicken Sie im Abschnitt Command auf die Schaltfläche **Hinzufügen** .
4. Wählen Sie **Benutzer erlauben, Aktionen in externen Diensten während innerhalb von Teams auszulösen**.
5. Wenn Sie zum Erstellen des Aufgabenmoduls eine statische Gruppe von Parametern verwenden möchten, wählen Sie diese Option aus. Andernfalls wählen Sie aus, um **einen dynamischen Parametersatz aus Ihrem bot abzurufen**.
6. Fügen Sie eine **Befehls-ID** und einen **Titel**hinzu.
7. Wählen Sie aus, wo der Aktionsbefehl ausgelöst werden soll.
8. Wenn Sie Parameter für Ihr Aufgabenmodul verwenden, fügen Sie das erste hinzu.
9. Click Save
10. Wenn Sie weitere Parameter hinzufügen möchten, klicken Sie im Abschnitt **Parameters** auf die Schaltfläche **Hinzufügen** , um Sie hinzuzufügen.

### <a name="manually-create-a-command"></a>Manuelles Erstellen eines Befehls

Wenn Sie den Aktions basierten Messaging Erweiterungs Befehl Ihrem App-Manifest manuell hinzufügen möchten, müssen Sie dem Array von Objekten die Parameter "folgt" hinzufügen `composeExtension.commands` .

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Diese ID wird von der Benutzeranforderung eingeschlossen. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Muss `action` sein. | Nein | 1.4 |
| `fetchTask` | `true` für eine Adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul, `false` für eine statische Liste von Parametern oder beim Laden der Webansicht durch einen `taskInfo` | Nein | 1.4 |
| `context` | Optionales Array von Werten, das definiert, woher die Messaging Erweiterung aufgerufen werden kann. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, werden Sie ebenfalls hinzugefügt.

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Statische Liste von Parametern für den Befehl. Nur verwenden, `fetchTask` Wenn `false` | Nein | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt den Zweck oder das Beispiel dieses Parameters des Werts, der angegeben werden sollte. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parameter Titel oder Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Legt den Typ der erforderlichen Eingabe fest. Mögliche Werte sind `text` :,, `textarea` ,, `number` `date` `time` , `toggle` . Default ist auf festgelegt `text` | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, `taskInfo` um Ihre Webansicht abzurufen, ohne den bot direkt aufzurufen. Wenn Sie diese Option verwenden, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern darin, dass die erste Interaktion mit Ihrem bot [auf die Aufgabe-Modul-Aktion "Submit" reagiert](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md). Wenn Sie ein Objekt verwenden `taskInfo` , müssen Sie auch den `fetchTask` Parameter auf festlegen `false` .

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
|`taskInfo`|Angeben des Aufgabenmoduls, das beim Verwenden eines Messaging Erweiterungs Befehls geladen werden soll| Nein | 1.4 |
|`taskInfo.title`|Titel des ersten Aufgabenmoduls|Nein | 1.4 |
|`taskInfo.width`|Größe des Aufgabenmoduls: entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small"|Nein | 1.4 |
|`taskInfo.height`|Größe des Aufgabenmoduls-entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small"|Nein | 1.4 |
|`taskInfo.url`|Anfängliche webansichts-URL|Nein | 1.4 |

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Im folgenden sehen Sie ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert. Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifest-Schema Siehe: [App-Manifest-Schema](~/resources/schema/manifest-schema.md).

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
        "fetchTask": false,
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

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie eine Adaptive Karte oder eine eingebettete Webansicht ohne `taskInfo` Objekt verwenden, sollten Sie Folgendes tun:

* [Erstellen und Antworten mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie Parameter oder eine eingebettete Webansicht mit einem- `taskInfo` Objekt verwenden, ist der nächste Schritt für Sie:

* [Auf Aufgabenmodul übermitteln reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
