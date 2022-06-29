---
title: Definieren von Suchbefehlen für Nachrichtenerweiterungen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Suchbefehle für Nachrichtenerweiterungen für Teams-Apps, um einen Suchbefehl über das App-Manifest und manuell zu erstellen.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: c131a511c5c16eac4bf57093bbbeed9bd4172e97
ms.sourcegitcommit: ffc57e128f0ae21ad2144ced93db7c78a5ae25c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66503942"
---
# <a name="define-message-extension-search-commands"></a>Definieren von Suchbefehlen für Nachrichtenerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mithilfe von Suchbefehlen für Nachrichtenerweiterungen können Benutzer externe Systeme durchsuchen und die Ergebnisse dieser Suche in form einer Karte in eine Nachricht einfügen. In diesem Dokument erfahren Sie, wie Sie Speicherorte für Suchbefehle auswählen und dem App-Manifest den Suchbefehl hinzufügen.

> [!NOTE]
> Die Maximale Größe der Ergebniskarte beträgt 28 KB. Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.

Im folgenden Video erfahren Sie, wie Sie Suchbefehle für Nachrichtenerweiterungen definieren:
<br>

> [!VIDEO <https://www.microsoft.com/en-us/videoplayer/embed/RE4OIvK>]
<br>

## <a name="select-search-command-invoke-locations"></a>Auswählen von Suchbefehlsspeicherorten

Der Suchbefehl wird an einem oder an beiden der folgenden Speicherorte aufgerufen:

* Bereich zum Verfassen von Nachrichten: die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten.
* Befehlsfeld: Durch @mentioning im Befehlsfeld.

  Wenn der Suchbefehl aus dem Nachrichtenbereich zum Verfassen aufgerufen wird, sendet der Benutzer die Ergebnisse an die Unterhaltung. Wenn sie über das Befehlsfeld aufgerufen wird, interagiert der Benutzer mit der resultierenden Karte oder kopiert sie zur Verwendung an anderer Stelle.

In der folgenden Abbildung werden die Aufrufspeicherorte des Suchbefehls angezeigt:

:::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-locations.png" alt-text="Suchbefehl ruft Speicherorte auf":::

## <a name="add-the-search-command-to-your-app-manifest"></a>Hinzufügen des Suchbefehls zum App-Manifest

Um den Suchbefehl zu Ihrem App-Manifest hinzuzufügen, müssen Sie ein neues `composeExtension` Objekt auf der obersten Ebene Des App-Manifest-JSON hinzufügen. Sie können den Suchbefehl entweder mithilfe von App Studio oder manuell hinzufügen.

### <a name="create-a-search-command-using-app-studio"></a>Erstellen eines Suchbefehls mit App Studio

Die Voraussetzung zum Erstellen eines Suchbefehls ist, dass Sie bereits eine Nachrichtenerweiterung erstellt haben müssen. Informationen zum Erstellen einer Nachrichtenerweiterung finden Sie unter [Erstellen einer Nachrichtenerweiterung](~/messaging-extensions/how-to/create-messaging-extension.md).

So erstellen Sie einen Suchbefehl:

1. Öffnen Sie **App Studio** über den Microsoft Teams-Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.
1. Wenn Sie Ihr App-Paket bereits in **App Studio** erstellt haben, wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Nach dem Importieren des App-Pakets wählen Sie **"Nachrichtenerweiterungen** " unter **"Funktionen"** aus. Sie erhalten ein Popupfenster zum Einrichten der Nachrichtenerweiterung.
1. Wählen Sie im Fenster **Einrichten** aus, um die Nachrichtenerweiterung in Ihre App-Umgebung einzuschließen. Die folgende Abbildung zeigt die Seite zum Einrichten der Nachrichtenerweiterung:

    :::image type="content" source="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt-text="Einrichten von Messaging-Erweiterungen":::

1. Zum Erstellen der Nachrichtenerweiterung benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie die Option **Neuen Bot erstellen** aus, geben Sie dem neuen Bot einen Namen, und wählen Sie **Erstellen** aus. In der folgenden Abbildung wird die Boterstellung für die Nachrichtenerweiterung angezeigt:

    :::image type="content" source="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt-text="Erstellen eines Bots für die Messaging-Erweiterung":::

1. Um einen vorhandenen Bot zu verwenden, wählen Sie **Vorhandenen Bot verwenden** und dann **Aus einem meiner vorhandenen Bots auswählen** aus, um die vorhandenen Bots aus der Dropdownliste auszuwählen. Geben Sie einen **Botnamen** ein, und wählen Sie **Speichern** aus, oder wählen Sie **Mit einer anderen Bot-ID verbinden** aus, wenn Sie bereits eine Bot-ID erstellt haben. Geben Sie einen **Botnamen** ein, und wählen Sie **Speichern** aus.

    :::image type="content" source="~/assets/images/messaging-extension/use-existing-bot.png" alt-text="Verwenden eines vorhandenen Bots für die Messaging-Erweiterung":::

1. Wählen Sie im **Abschnitt "Befehl**" der Seite "Nachrichtenerweiterungen" die Option "**Hinzufügen**" aus, um die Befehle einzuschließen, die das Verhalten der Nachrichtenerweiterung bestimmen.
In der folgenden Abbildung wird das Hinzufügen des Befehls für die Nachrichtenerweiterung angezeigt:

    :::image type="content" source="~/assets/images/messaging-extension/include-command.png" alt-text="Einschließen des Befehls":::

1. Wählen Sie **"Benutzern erlauben" aus, Ihren Dienst nach Informationen abzufragen und diese in eine Nachricht einzufügen**. Die folgende Abbildung zeigt die Auswahl des Suchbefehlsparameters:

    :::image type="content" source="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt-text="Suchbefehlsparameterauswahl":::

1. Fügen Sie eine **Befehls-ID** und einen **Titel** hinzu.
1. Wählen Sie den Speicherort aus, an dem der Suchbefehl aufgerufen werden muss. In der folgenden Abbildung wird der Speicherort für den Aufruf des Suchbefehls angezeigt:

    :::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt-text="Suchbefehl ruft Standortauswahl auf":::

1. Fügen Sie Ihren Suchparameter hinzu, und wählen Sie **"Speichern" aus**.

### <a name="create-a-search-command-manually"></a>Manuelles Erstellen eines Suchbefehls

Zum manuellen Hinzufügen des Suchbefehls für die Nachrichtenerweiterung zum App-Manifest müssen Sie dem Array von Objekten die folgenden Parameter `composeExtension.commands` hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie dem Suchbefehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `description` | Diese Eigenschaft ist ein Hilfetext, der angibt, was dieser Befehl tut. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss ein `query`. | Nein | 1.4 |
|`initialRun` | Wenn diese Eigenschaft auf **"true**" festgelegt ist, gibt sie an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Sie müssen die Details des Suchparameters hinzufügen, der den Text definiert, der für Ihren Benutzer im Teams-Client sichtbar ist.

| Eigenschaftenname | Zweck | Erforderlich? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft definiert eine statische Liste von Parametern für den Befehl. | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Dies wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Werts, der angegeben werden muss. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text`, `textarea`, `number`, `date`, `time`. `toggle` Der Standardwert ist auf `text`. | Nein | 1.4 |

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

Das vollständige App-Manifest finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams Nachrichtenerweiterungen – Suche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung](../../../sbs-messagingextension-searchcommand.yml) zum Erstellen einer suchbasierten Nachrichtenerweiterung.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Antworten Sie auf die Suchbefehle](~/messaging-extensions/how-to/search-commands/respond-to-search.md).
