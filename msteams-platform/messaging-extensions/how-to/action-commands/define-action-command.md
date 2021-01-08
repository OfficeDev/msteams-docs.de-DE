---
title: Definieren von Aktionsbefehlen für Messagingerweiterungen
author: clearab
description: Übersicht über Aktionsbefehle für Messagingerweiterungen
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: be2135477c4234187f374aef215f90e8329fb74e
ms.sourcegitcommit: 5739245903278d521ec920427248b6b48676e637
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "49778401"
---
# <a name="define-messaging-extension-action-commands"></a>Definieren von Aktionsbefehlen für Messagingerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Aktionsbefehle ermöglichen es Ihnen, Ihren Benutzern ein modales Popup (in Teams als Aufgabenmodul bezeichnet) zu präsentieren, um Informationen zu sammeln oder anzuzeigen, dann ihre Interaktion zu verarbeiten und Informationen in Teams zurückzuschicken. Vor dem Erstellen des Befehls müssen Sie sich entscheiden:

1. Wo kann der Aktionsbefehl ausgelöst werden?
1. Wie wird das Aufgabenmodul erstellt?
1. Wird die endgültige Nachricht oder Karte von einem Bot an den Kanal gesendet, oder wird die Nachricht oder Karte in den Bereich zum Verfassen von Nachrichten eingefügt, damit der Benutzer sie übermitteln kann?

## <a name="choose-action-command-invoke-locations"></a>Auswählen von Aktionsbefehlsaufrufen

Als Erstes müssen Sie entscheiden, von wo ihr Aktionsbefehl ausgelöst (oder genauer *gesagt)* werden kann. Durch Angeben des Befehls in Ihrem App-Manifest kann der Befehl von einem oder mehreren der `context` folgenden Speicherorte aufgerufen werden:

* Die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten.
* Durch @mentioning Ihrer App im Befehlsfeld. Hinweis: Sie können nicht mit einer Botnachricht antworten, die direkt in die Unterhaltung eingefügt wird, wenn Ihre Messagingerweiterung über das Befehlsfeld aufgerufen wird.
* Direkt aus einer vorhandenen Nachricht über die ... Überlaufmenü einer Nachricht. Hinweis: Der erste Aufruf an Ihren Bot enthält ein JSON-Objekt, das die Nachricht enthält, aus der er aufgerufen wurde, die Sie verarbeiten können, bevor Sie sie mit einem Aufgabenmodul präsentieren.

## <a name="choose-how-to-build-your-task-module"></a>Auswählen, wie Sie Das Aufgabenmodul erstellen

Sie müssen nicht nur auswählen, von wo aus der Befehl aufgerufen werden kann, sondern auch auswählen, wie das Formular im Aufgabenmodul für Ihre Benutzer auffüllt. Sie haben drei Optionen zum Erstellen des Formulars, das innerhalb des Aufgabenmoduls gerendert wird:

* **Statische Parameterliste –** Dies ist die einfachste Option. Sie können eine Liste von Parametern (Eingabefelder) in Ihrem App-Manifest definieren, das vom Teams-Client gerendert wird. Mit dieser Option können Sie die Formatierung nicht steuern.
* **Adaptive Karte** – Sie können eine adaptive Karte verwenden, die eine bessere Kontrolle über die Benutzeroberfläche bietet, Sie jedoch weiterhin auf die verfügbaren Steuerelemente und Formatierungsoptionen einschränkt.
* **Eingebettete Webansicht** : Wenn Sie vollständige Kontrolle über die Benutzeroberfläche und die Steuerelemente benötigen, können Sie eine benutzerdefinierte Webansicht in das Aufgabenmodul einbetten.

Wenn Sie ihr Aufgabenmodul mit einer statischen Liste von Parametern erstellen, wird die Messagingerweiterung zum ersten Mal von einem Benutzer übermittelt. Wenn Sie eine eingebettete Webansicht oder eine adaptive Karte verwenden, muss Ihre Messagingerweiterung ein erstes Aufrufereignis vom Benutzer behandeln, das Aufgabenmodul erstellen und an den Client zurückgeben.

## <a name="choose-how-the-final-message-will-be-sent"></a>Auswählen, wie die endgültige Nachricht gesendet wird

In den meisten Fällen führt der Aktionsbefehl dazu, dass eine Karte in das Feld zum Verfassen von Nachrichten eingefügt wird. Der Benutzer kann dann entscheiden, ob er es in den Kanal oder Chat senden soll. Die Nachricht stammt in diesem Fall vom Benutzer, und Ihr Bot kann die Karte nicht weiter bearbeiten oder aktualisieren.

Wenn Ihre Messagingerweiterung aus dem Feld zum Verfassen oder direkt aus einer Nachricht ausgelöst wird, kann Ihr Webdienst die endgültige Antwort direkt in den Kanal oder Chat einfügen. In diesem Fall stammt die adaptive Karte vom Bot, der Bot kann sie aktualisieren, und der Bot kann bei Bedarf auch auf den Unterhaltungsthread antworten. Sie müssen das Objekt ihrem App-Manifest hinzufügen, indem Sie dieselbe ID verwenden `bot` und die entsprechenden Bereiche definieren.

## <a name="add-the-command-to-your-app-manifest"></a>Hinzufügen des Befehls zum App-Manifest

Nachdem Sie nun entschieden haben, wie Benutzer mit Ihrem Aktionsbefehl interagieren sollen, ist es an der Zeit, ihn ihrem App-Manifest hinzuzufügen. Dazu fügen Sie der obersten Ebene ihres App-Manifest-JSON ein `composeExtension` neues Objekt hinzu. Sie können dies entweder mithilfe von App Studio oder manuell tun.

### <a name="create-a-command-using-app-studio"></a>Erstellen eines Befehls mit App Studio

Bei den folgenden Schritten wird davon ausgegangen, dass Sie [bereits eine Messagingerweiterung erstellt haben.](~/messaging-extensions/how-to/create-messaging-extension.md)

1. Öffnen Sie im Microsoft Teams-Client **App Studio,** und wählen Sie die Registerkarte **"Manifest-Editor"** aus.
2. Wenn Sie Ihr App-Paket bereits in App Studio erstellt haben, wählen Sie es aus der Liste aus. Wenn nicht, können Sie ein vorhandenes App-Paket importieren.
3. Klicken **Sie** im Befehlsabschnitt auf die Schaltfläche "Hinzufügen".
4. Choose **Allow users to trigger actions in external services while inside of Teams**.
5. Wenn Sie einen statischen Satz von Parametern zum Erstellen des Aufgabenmoduls verwenden möchten, wählen Sie diese Option aus. Andernfalls können Sie **einen dynamischen Satz von Parametern von Ihrem Bot abrufen.**
6. Fügen Sie eine **Befehls-ID und** einen **Titel hinzu.**
7. Wählen Sie aus, von wo ihr Aktionsbefehl ausgelöst werden soll.
8. Wenn Sie Parameter für Ihr Aufgabenmodul verwenden, fügen Sie den ersten hinzu.
9. Click Save
10. Wenn Sie weitere Parameter hinzufügen  müssen, klicken Sie im Abschnitt **"Parameter"** auf die Schaltfläche "Hinzufügen", um sie hinzuzufügen.

### <a name="manually-create-a-command"></a>Manuelles Erstellen eines Befehls

Zum manuellen Hinzufügen des Befehls für die aktionsbasierte Messagingerweiterung zu Ihrem App-Manifest müssen Sie dem Objektarray die folgenden `composeExtension.commands` Parameter hinzufügen.

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Muss `action` sein. | Nein | 1.4 |
| `fetchTask` | `true` für eine adaptive Karte oder eingebettete Webansicht für Ihr Aufgabenmodul, für eine statische Liste von Parametern oder beim Laden der `false` Webansicht durch eine `taskInfo` | Nein | 1.4 |
| `context` | Optionales Wertearray, das definiert, von wo aus die Messagingerweiterung aufgerufen werden kann. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Wenn Sie eine statische Liste von Parametern verwenden, fügen Sie diese ebenfalls hinzu.

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
| `parameters` | Statische Liste der Parameter für den Befehl. Nur verwenden, wenn `fetchTask` dies der `false` | Nein | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke dieses Parameters oder ein Beispiel für den Wert, der angegeben werden sollte. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parametertitel oder eine Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Auf den typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` | Nein | 1.4 |

Wenn Sie eine eingebettete Webansicht verwenden, können Sie optional das Objekt hinzufügen, um Ihre Webansicht zu erhalten, ohne `taskInfo` den Bot direkt auf den Bot zu rufen. Wenn Sie diese Option verwenden, ähnelt das Verhalten der Verwendung einer statischen Liste von Parametern, da die erste Interaktion mit Ihrem Bot auf die Absendenaktion des [Aufgabenmoduls reagiert.](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md) Wenn Sie ein Objekt verwenden, stellen Sie `taskInfo` sicher, dass Sie auch den `fetchTask` Parameter auf `false` festlegen.

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
|`taskInfo`|Angeben des Aufgabenmoduls, das beim Verwenden eines Befehls für eine Messagingerweiterung vorab entladen werden soll| Nein | 1.4 |
|`taskInfo.title`|Titel des anfänglichen Aufgabenmoduls|Nein | 1.4 |
|`taskInfo.width`|Breite des Aufgabenmoduls – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"|Nein | 1.4 |
|`taskInfo.height`|Höhe des Aufgabenmoduls – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"|Nein | 1.4 |
|`taskInfo.url`|Url der anfänglichen Webansicht|Nein | 1.4 |

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Nachfolgend sehen Sie ein Beispiel für ein `composeExtensions` Objekt, das zwei Aktionsbefehle definiert. Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifestschema siehe: [App-Manifestschema.](~/resources/schema/manifest-schema.md)

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

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie entweder eine adaptive Karte oder eine eingebettete Webansicht ohne Objekt verwenden, sollten `taskInfo` Sie:

* [Erstellen und Antworten mit einem Aufgabenmodul](~/messaging-extensions/how-to/action-commands/create-task-module.md)

Wenn Sie Parameter oder eine eingebettete Webansicht mit einem Objekt verwenden, besteht der `taskInfo` nächste Schritt für Sie darin:

* [Reagieren auf Absenden des Aufgabenmoduls](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
