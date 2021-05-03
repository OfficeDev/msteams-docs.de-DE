---
title: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen
author: clearab
description: Definieren von Suchbefehlen für Messagingerweiterungen für Microsoft Teams Apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 19f1fdf7bd4efdbb0de11d1abad341ec24bc27bd
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696811"
---
# <a name="define-messaging-extension-search-commands"></a>Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Suchbefehle für Messagingerweiterungen ermöglichen Benutzern das Durchsuchen externer Systeme und das Einfügen der Ergebnisse dieser Suche in eine Nachricht in Form einer Karte. In diesem Dokument erfahren Sie, wie Sie Suchbefehlsaufrufe auswählen und den Suchbefehl ihrem App-Manifest hinzufügen.

> [!NOTE]
> Die Größenbeschränkung für die Karte beträgt 28 KB. Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.

## <a name="select-search-command-invoke-locations"></a>Auswählen von Suchbefehlsaufrufen

Der Suchbefehl wird von einem oder beiden der folgenden Speicherorte aufgerufen:

* Bereich "Nachricht verfassen": Die Schaltflächen am unteren Rand des Bereichs "Verfassen von Nachrichten".
* Befehlsfeld: Durch @mentioning im Befehlsfeld.

Wenn der Suchbefehl aus dem Bereich zum Verfassen von Nachrichten aufgerufen wird, sendet der Benutzer die Ergebnisse an die Unterhaltung. Wenn sie über das Befehlsfeld aufgerufen wird, interagiert der Benutzer mit der resultierenden Karte oder kopiert sie zur Verwendung an anderer Stelle.

In der folgenden Abbildung werden die Aufrufpositionen des Suchbefehls angezeigt:

![Suchbefehl ruft Speicherorte auf](~/assets/images/messaging-extension/search-command-invoke-locations.png)

## <a name="add-the-search-command-to-your-app-manifest"></a>Hinzufügen des Suchbefehls zum App-Manifest

Zum Hinzufügen des Suchbefehls zum App-Manifest müssen Sie der obersten Ebene ihres App-Manifest-JSON ein neues `composeExtension` Objekt hinzufügen. Sie können den Suchbefehl entweder mithilfe von App Studio oder manuell hinzufügen.

### <a name="create-a-search-command-using-app-studio"></a>Erstellen eines Suchbefehls mithilfe von App Studio

Voraussetzung für das Erstellen eines Suchbefehls ist, dass Sie bereits eine Messagingerweiterung erstellt haben müssen. Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Suchbefehl**

1. Öffnen **Sie App Studio** im Microsoft Teams Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1.  Wenn Sie Ihr App-Paket bereits in **App Studio erstellt haben,** wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren des App-Pakets die Option **Messagingerweiterungen** unter **Funktionen aus.** Sie erhalten ein Popupfenster zum Einrichten der Messagingerweiterung.
1. Wählen **Sie Einrichten** im Fenster aus, um die Messagingerweiterung in Ihre App-Umgebung zu verwenden. In der folgenden Abbildung wird die Seite zum Einrichten der Messagingerweiterung angezeigt: 

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. Zum Erstellen der Messagingerweiterung benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen **Sie Die Option Neuer Bot erstellen** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie Erstellen **aus.** In der folgenden Abbildung wird die Boterstellung für die Messagingerweiterung angezeigt:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Wählen **Sie Im** Abschnitt Befehl **der** Seite Messagingerweiterungen die Option Hinzufügen aus, um die Befehle hinzuzufügen, die das Verhalten der Messagingerweiterung bestimmen.   
In der folgenden Abbildung wird die Befehlserweiterung für die Messagingerweiterung angezeigt:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>
1. Wählen **Sie Benutzer zulassen aus, um Ihren Dienst nach Informationen zu fragen, und fügen Sie diese in eine Nachricht ein.** In der folgenden Abbildung wird die Auswahl des Suchbefehlsparameters angezeigt:

    <img src="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt="search command parameter selection" width="500"/>

1. Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**
1. Wählen Sie den Speicherort aus, an dem der Suchbefehl aufgerufen werden muss. Das **Auswählen der** Nachricht ändert derzeit nicht das Verhalten Ihres Suchbefehls. In der folgenden Abbildung wird der Speicherort des Suchbefehls angezeigt:

    <img src="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt="search command invoke location selection]" width="500"/>

1. Fügen Sie ihren Suchparameter hinzu, und wählen Sie **Speichern aus.**

### <a name="create-a-search-command-manually"></a>Manuelles Erstellen eines Suchbefehls 

Zum manuellen Hinzufügen des Suchbefehls für die Messagingerweiterung zu Ihrem App-Manifest müssen Sie dem Objektarray die folgenden `composeExtension.commands` Parameter hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie dem Suchbefehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Diese Eigenschaft ist ein Hilfetext, der angibt, was dieser Befehl macht. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss eine `query` sein. | Nein | 1.4 |
|`initialRun` | Wenn diese Eigenschaft auf **true** festgelegt ist, gibt sie an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Sie müssen die Details des Suchparameters hinzufügen, der den text definiert, der für Den Benutzer im Client Teams wird.

| Eigenschaftenname | Zweck | Ist erforderlich? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft definiert eine statische Liste von Parametern für den Befehl. | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Parameters, der angegeben werden muss. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` festgelegt. | Nein | 1.4 |

#### <a name="example"></a>Beispiel

Der folgende Abschnitt ist ein Beispiel für das einfache App-Manifest des `composeExtensions` Objekts, das einen Suchbefehl definiert: 

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
Das vollständige App-Manifest finden Sie unter [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams Messagingerweiterungsaktion| Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams messaging extension search   |  Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Reagieren Sie auf die Suchbefehle](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

