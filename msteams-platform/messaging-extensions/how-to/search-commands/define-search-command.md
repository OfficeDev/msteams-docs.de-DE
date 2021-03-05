---
title: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen
author: clearab
description: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen für Microsoft Teams-Apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 18bac3049fec8fead168c12f2832bfbbb72cf609
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449269"
---
# <a name="define-messaging-extension-search-commands"></a>Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mit der Messaging-Erweiterung von Suchbefehlen können Ihre Benutzer externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen.

> [!NOTE]
> Die Größenbeschränkung für die Karte beträgt 28 KB. Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet. 

## <a name="choose-messaging-extension-invoke-locations"></a>Auswählen von Speicherorten für den Aufruf von Messagingerweiterungen

Als Erstes müssen Sie entscheiden, von wo ihr Suchbefehl ausgelöst (oder speziell *aufgerufen)* werden kann. Der Suchbefehl kann von einem oder beiden der folgenden Speicherorte aufgerufen werden:

* Die Schaltflächen am unteren Rand des Nachrichten verfassenbereichs
* By @mentioning in the command box

Wenn sie aus dem Bereich zum Verfassen von Nachrichten aufgerufen werden, hat der Benutzer die Möglichkeit, die Ergebnisse an die Unterhaltung zu senden. Wenn er über das Befehlsfeld aufgerufen wird, kann der Benutzer mit der resultierenden Karte interagieren oder sie zur Verwendung an anderer Stelle kopieren.

## <a name="add-the-command-to-your-app-manifest"></a>Hinzufügen des Befehls zum App-Manifest

Nachdem Sie nun entschieden haben, wie Benutzer mit Ihrem Suchbefehl interagieren, ist es an der Zeit, ihn ihrem App-Manifest hinzuzufügen. Dazu fügen Sie der obersten Ebene Ihres App-Manifest-JSON ein neues `composeExtension` Objekt hinzu. Sie können dies entweder mithilfe von App Studio oder manuell tun.

### <a name="create-a-command-using-app-studio"></a>Erstellen eines Befehls mithilfe von App Studio

Voraussetzung für das Erstellen eines Suchbefehls ist, dass Sie bereits eine Messagingerweiterung erstellen müssen. Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Suchbefehl**

1. Öffnen Sie im Microsoft Teams-Client **App Studio,** und wählen Sie die **Registerkarte Manifest-Editor** aus.
1. Wenn Sie bereits ein App-Paket im App Studio erstellt **haben,** wählen Sie es aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren eines App-Pakets unter Funktionen die Option **Messagingerweiterungen** **aus.**
1. Wählen **Sie im** Abschnitt **Befehl** auf der Seite Messagingerweiterungen hinzufügen aus.
1. Wählen **Sie Benutzer zulassen, um Ihren Dienst nach Informationen zu fragen und diese in eine Nachricht ein.**
1. Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**
1. Wählen Sie den Speicherort aus, an dem der Suchbefehl ausgelöst werden muss. Das **Auswählen der** Nachricht ändert derzeit nicht das Verhalten Ihres Suchbefehls.
1. Fügen Sie ihren Suchparameter hinzu, und wählen Sie **Speichern aus.**
 
### <a name="manually-create-a-command"></a>Manuelles Erstellen eines Befehls

Zum manuellen Hinzufügen des Suchbefehls für die Messagingerweiterung zum App-Manifest müssen Sie dem Array der Objekte die folgenden `composeExtension.commands` Parameter hinzufügen.

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Eindeutige ID, die Sie diesem Befehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Hilfetext, der angibt, was dieser Befehl macht. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Muss `query` sein. | Nein | 1.4 |
|`initialRun` | Wenn dieser Wert **auf true** festgelegt ist, wird angegeben, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche ausgibt. | Nein | 1.0 |
| `context` | Optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Mögliche Werte sind `message` , `compose` oder `commandBox` . Der Standardwert ist `["compose", "commandBox"]`. | Nein | 1,5 |

Sie müssen auch die Details des Suchparameters hinzufügen, der den Text definiert, der für Den Benutzer im Teams-Client sichtbar ist.

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Statische Liste der Parameter für den Befehl. | Nein | 1.0 |
| `parameter.name` | Der Name des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Beschreibt die Zwecke oder das Beispiel dieses Parameters für den wert, der bereitgestellt werden soll. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Kurze benutzerfreundlicher Parametertitel oder -bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Auf den typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` . Standard ist auf festgelegt `text` | Nein | 1.4 |

#### <a name="app-manifest-example"></a>Beispiel für ein App-Manifest

Im Folgenden finden Sie ein Beispiel für ein `composeExtensions` Objekt, das einen Suchbefehl definiert. Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifestschema siehe: [App-Manifestschema](~/resources/schema/manifest-schema.md).

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

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Suchbefehl hinzugefügt haben, müssen Sie die [Suchanforderung behandeln.](~/messaging-extensions/how-to/search-commands/respond-to-search.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
