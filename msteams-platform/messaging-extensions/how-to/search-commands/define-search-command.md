---
title: Definieren von Suchbefehlen für die Messaging Erweiterung
author: clearab
description: Definieren von Suchbefehlen für die Messaging Erweiterung für Microsoft Teams-apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: b6837fb8a131d8ce3e2bbd0c51c2861dbffda2bc
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674391"
---
# <a name="define-messaging-extension-search-commands"></a>Definieren von Suchbefehlen für die Messaging Erweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mit den Suchbefehlen für die Nachrichten Erweiterung können Benutzer externe Systeme durchsuchen und die Ergebnisse der Suche in eine Nachricht in Form einer Karte einfügen.

## <a name="choose-messaging-extension-invoke-locations"></a>Auswählen von Speicherorten für Messaging Erweiterungs Aufrufe

Das erste, was Sie entscheiden müssen, ist, wo Ihr Suchbefehl (oder genauer gesagt, *aufgerufen*) aus ausgelöst werden kann. Ihr Suchbefehl kann über einen oder beide der folgenden Speicherorte aufgerufen werden:

* Die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten
* Durch @mentioning im Befehlsfeld

Wenn der Benutzer im Bereich zum Verfassen von Nachrichten aufgerufen wird, hat er die Möglichkeit, die Ergebnisse an die Unterhaltung zu senden. Wenn der Benutzer über das Befehlsfeld aufgerufen wird, kann er mit der resultierenden Karte interagieren oder ihn zur Verwendung an einer anderen Stelle kopieren.

## <a name="add-the-command-to-your-app-manifest"></a>Hinzufügen des Befehls zum App-Manifest

Nachdem Sie sich entschieden haben, wie Benutzer mit Ihrem Suchbefehl interagieren sollen, ist es an der Zeit, Sie dem App-Manifest hinzuzufügen. Zu diesem Zweck fügen Sie ein neues `composeExtension` Objekt zur obersten Ebene des JSON-App-Manifests hinzu. Sie können dies entweder mit Hilfe von App Studio oder manuell tun.

### <a name="create-a-command-using-app-studio"></a>Erstellen eines Befehls mit App Studio

In den folgenden Schritten wird davon ausgegangen, dass Sie bereits [eine Messaging Erweiterung erstellt](~/messaging-extensions/how-to/create-messaging-extension.md)haben.

1. Öffnen Sie auf dem Microsoft Teams-Client **App Studio** , und wählen Sie die Registerkarte **Manifest-Editor** aus.
2. Wenn Sie Ihr App-Paket bereits in App Studio erstellt haben, wählen Sie es aus der Liste aus. Wenn dies nicht der Fall ist, können Sie ein vorhandenes App-Paket importieren.
3. Klicken Sie im Abschnitt Command auf die Schaltfläche **Hinzufügen** .
4. Wählen Sie **zulassen, dass Benutzer ihren Dienst nach Informationen Abfragen und diesen in eine Nachricht einfügen**.
5. Fügen Sie eine **Befehls-ID** und einen **Titel**hinzu.
6. Wählen Sie aus, wo der Suchbefehl ausgelöst werden soll. Das Auswählen von **Nachricht** ändert derzeit nicht das Verhalten des Suchbefehls.
7. Fügen Sie den Suchparameter hinzu.
8. Klicken Sie auf Speichern.

### <a name="manually-create-a-command"></a>Manuelles Erstellen eines Befehls

Um den Suchbefehl für die Messaging-Erweiterung manuell Ihrem App-Manifest hinzuzufügen, müssen Sie dem `composeExtension.commands` Array von Objekten die Parameter "folgt" hinzufügen.

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Diese ID wird von der Benutzeranforderung eingeschlossen. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl ausführt. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Muss `query` sein. | Nein | 1.4 |
|`initialRun` | Bei Festlegung auf " **true**" gibt an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Mögliche Werte sind `message`, `compose`oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Außerdem müssen Sie die Details des Such Parameters hinzufügen, mit dem der Text, der für den Benutzer sichtbar ist, im Microsoft Teams-Client definiert wird.

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Statische Liste von Parametern für den Befehl. | Nein | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt den Zweck oder das Beispiel dieses Parameters des Werts, der angegeben werden sollte. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurzer benutzerfreundlicher Parameter Titel oder Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Legt den Typ der erforderlichen Eingabe fest. Mögliche Werte sind `text`: `textarea`, `number`, `date`, `time`, `toggle`,. Default ist auf festgelegt`text` | Nein | 1.4 |

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Im folgenden sehen Sie ein Beispiel für `composeExtensions` ein Objekt, das einen Suchbefehl definiert. Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifest-Schema Siehe: [App-Manifest-Schema](~/resources/schema/manifest-schema.md).

```json
{
...
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [{
          "id": "searchCmd",
          "description": "Search Bing for information on the web",
          "title": "Search",
          "initialRun": true,
          "parameters": [{
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }]
        }
      ]
    }
  ],
...
}
```

## <a name="next-steps"></a>Weitere Schritte

Nachdem Sie den Suchbefehl hinzugefügt haben, müssen Sie [die Suchanforderung verarbeiten](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]