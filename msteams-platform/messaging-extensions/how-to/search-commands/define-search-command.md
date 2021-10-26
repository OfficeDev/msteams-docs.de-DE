---
title: Definieren von Suchbefehlen für Messaging-Erweiterungen
author: surbhigupta
description: Definieren sie Suchbefehle für Messaging-Erweiterungen für Microsoft Teams Apps.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: none
ms.openlocfilehash: aaea89aa14e556dfa00e81e8ec72fe5fb4bbe744
ms.sourcegitcommit: 781e7b82240075e9d1f55e97f3f1dcbba82a5e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2021
ms.locfileid: "60566365"
---
# <a name="define-messaging-extension-search-commands"></a>Definieren von Suchbefehlen für Messaging-Erweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Suchbefehle für Messaging-Erweiterungen ermöglichen Benutzern das Durchsuchen externer Systeme und das Einfügen der Ergebnisse dieser Suche in eine Nachricht in Form einer Karte. In diesem Dokument erfahren Sie, wie Sie Suchbefehlsaufforderungsspeicherorte auswählen und den Suchbefehl ihrem App-Manifest hinzufügen.

> [!NOTE]
> Die Maximale Größe der Ergebniskarte beträgt 28 KB. Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.

## <a name="select-search-command-invoke-locations"></a>Auswählen von Suchbefehlsaufforderungsspeicherorten

Der Suchbefehl wird von einem oder beiden der folgenden Speicherorte aufgerufen:

* Bereich zum Verfassen von Nachrichten: Die Schaltflächen unten im Bereich zum Verfassen von Nachrichten.
* Befehlsfeld: Nach @mentioning im Befehlsfeld.

  Wenn der Suchbefehl aus dem Bereich zum Verfassen von Nachrichten aufgerufen wird, sendet der Benutzer die Ergebnisse an die Unterhaltung. Wenn sie über das Befehlsfeld aufgerufen wird, interagiert der Benutzer mit der resultierenden Karte oder kopiert sie zur Verwendung an anderer Stelle.

In der folgenden Abbildung werden die Aufrufpositionen des Suchbefehls angezeigt:

![Suchbefehl ruft Speicherorte auf](~/assets/images/messaging-extension/search-command-invoke-locations.png)

## <a name="add-the-search-command-to-your-app-manifest"></a>Hinzufügen des Suchbefehls zum App-Manifest

Um den Suchbefehl zu Ihrem App-Manifest hinzuzufügen, müssen Sie ein neues `composeExtension` Objekt auf der obersten Ebene Ihres App-Manifest-JSON hinzufügen. Sie können den Suchbefehl entweder mithilfe von App Studio oder manuell hinzufügen.

### <a name="create-a-search-command"></a>Erstellen eines Suchbefehls 

Sie können suchbefehl mit ** App Studio** oder **Entwicklerportal** erstellen.

> [!NOTE]
>  App Studio wird in Kürze entpriesen. Konfigurieren, verteilen und verwalten Sie Ihre Teams-Apps mit dem neuen [Entwicklerportal.](https://dev.teams.microsoft.com/)

# <a name="app-studio"></a>[App-Studio](#tab/AS)

> [!NOTE]
> Voraussetzung für die Erstellung eines Suchbefehls ist, dass Sie bereits eine Messaging-Erweiterung erstellt haben müssen. Informationen zum Erstellen einer Messaging-Erweiterung finden Sie unter [Erstellen einer Messaging-Erweiterung.](~/messaging-extensions/how-to/create-messaging-extension.md)

**So erstellen Sie einen Suchbefehl**

1. Öffnen Sie **App Studio** über den Microsoft Teams-Client, und wählen Sie die Registerkarte **"Manifest-Editor"** aus.
1.  Wenn Sie Ihr App-Paket bereits in **App Studio** erstellt haben, wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes Paket.
1. Wählen Sie nach dem Importieren des **App-Pakets Messaging-Erweiterungen** unter **"Funktionen"** aus. Sie erhalten ein Popupfenster zum Einrichten der Messaging-Erweiterung.
1. Wählen Sie im Fenster **"Einrichten"** aus, um die Messaging-Erweiterung in Ihre App-Oberfläche einzuschließen. In der folgenden Abbildung wird die Einrichtungsseite der Messaging-Erweiterung angezeigt: 

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. Um die Messaging-Erweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie die Option **"Neuen Bot erstellen"** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie **"Erstellen"** aus. Die folgende Abbildung zeigt die Bot-Erstellung für die Messaging-Erweiterung:

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. Wählen Sie im **Abschnitt "Befehl"** der Seite "Messaging-Erweiterungen" die Option **"Hinzufügen"** aus, um die Befehle einzuschließen, die das Verhalten der Messaging-Erweiterung bestimmen.   
In der folgenden Abbildung wird die Befehlserweiterung für die Messaging-Erweiterung angezeigt:

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>
1. Wählen Sie **Zulassen, dass Benutzer Ihren Dienst nach Informationen abfragen und diese in eine Nachricht einfügen.** In der folgenden Abbildung wird die Auswahl des Suchbefehlsparameters angezeigt:

    <img src="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt="search command parameter selection" width="500"/>

1. Fügen Sie eine **Befehls-ID** und einen **Titel** hinzu.
1. Wählen Sie den Speicherort aus, an dem der Suchbefehl aufgerufen werden muss. Das Auswählen der **Nachricht** ändert derzeit nicht das Verhalten des Suchbefehls. In der folgenden Abbildung wird der Aufrufspeicherort des Suchbefehls angezeigt:

    <img src="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt="search command invoke location selection]" width="500"/>

1. Fügen Sie Den Suchparameter hinzu, und wählen Sie **"Speichern"** aus.

# <a name="developer-portal"></a>[Entwicklerportal](#tab/DP)

**So erstellen Sie einen Suchbefehl mithilfe des Entwicklerportals**

1. Wechseln Sie zum **[Entwicklerportal.](https://dev.teams.microsoft.com/)**
    
   <img src="~/assets/images/tdp/tdp_home_1.png" alt="Screenshot of TDP" width="500"/>
    
1. Wechseln Sie zu **"Apps".**
    
    <img width="500px" alt="Screenshot of TDP Open" src="~/assets/images/tdp/screen2.png"/>
    
1. Wenn Sie Ihr App-Paket bereits im **Entwicklerportal** erstellt haben, wählen Sie es aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, wählen Sie **"Vorhandene App importieren"** aus.

    <img width="500px" alt="Screenshot of import app in tdp" src="~/assets/images/tdp/screen3.png"/>

1. Wechseln Sie zu **App-Features.**  

    <img width="500px" alt="TDP messaging extension" src="~/assets/images/tdp/tdp-me.png"/>

1. Wählen Sie **Messaging-Erweiterungen** aus **App-Features** aus. Ein Popupfenster wird angezeigt, um die Messaging-Erweiterung einzurichten.
    
   <img width="500px" alt="TDP messaging extension set up" src="~/assets/images/tdp/tdp-app-me.png"/>

1. Wählen Sie in der Dropdownliste unter **Nachrichtenerweiterungs-ID** **einen Nachrichtenerweiterungs-Bot** aus, und wählen Sie **"Speichern"** aus.

    <img width="500px" alt="TDP messaging extension bot" src="~/assets/images/tdp/tdp-me-bot.png"/>

1. Wählen Sie **"Befehl hinzufügen"** aus. Ein Popupfenster wird angezeigt, um einen Befehl hinzuzufügen.

    <img width="500px" alt="TDP messaging extension command" src="~/assets/images/tdp/tdp-me-add-command.png"/>

1. Wählen Sie **suchbasiert** aus, um den Befehl zu suchen, und geben Sie Befehlsfelder ein.

    <img width="500px" alt="TDP messaging extension search command" src="~/assets/images/tdp/tdp-me-search-command.png"/>

1. Geben Sie Parameterfelder ein, und wählen Sie **"Speichern"** aus.

    <img width="500px" alt="TDP messaging extension search parameter" src="~/assets/images/tdp/tdp-me-search-parameter.png"/>

---


### <a name="create-a-search-command-manually"></a>Manuelles Erstellen eines Suchbefehls 

Zum manuellen Hinzufügen des Suchbefehls für die Messaging-Erweiterung zu Ihrem App-Manifest müssen Sie dem Array von Objekten die folgenden Parameter `composeExtension.commands` hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Mindestversion des Manifests |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie dem Suchbefehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Diese Eigenschaft ist ein Hilfetext, der angibt, was dieser Befehl bewirkt. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss eine `query` . | Nein | 1.4 |
|`initialRun` | Wenn diese Eigenschaft auf **"true"** festgelegt ist, gibt sie an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Sie müssen die Details des Suchparameters hinzufügen, der den Text definiert, der für Den Benutzer im Teams-Client sichtbar ist.

| Eigenschaftenname | Zweck | Ist erforderlich? | Mindestversion des Manifests |
|---|---|---|---|
| `parameters` | Diese Eigenschaft definiert eine statische Liste von Parametern für den Befehl. | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke des Parameters oder das Beispiel des Werts, der angegeben werden muss. Dieser Wert wird in der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine kurze Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text` , , , , , `textarea` `number` `date` `time` `toggle` . Der Standardwert ist auf `text` . | Nein | 1.4 |

#### <a name="example"></a>Beispiel

Der folgende Abschnitt ist ein Beispiel für das einfache App-Manifest des Objekts, das `composeExtensions` einen Suchbefehl definiert: 

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
Das vollständige App-Manifest finden Sie unter [App-Manifestschema.](~/resources/schema/manifest-schema.md)

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams Messaging-Erweiterungsaktion| Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams Messaging-Erweiterungssuche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Antworten Sie auf die Suchbefehle.](~/messaging-extensions/how-to/search-commands/respond-to-search.md)

