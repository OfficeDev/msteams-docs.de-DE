---
title: Definieren von Suchbefehlen für Nachrichtenerweiterungen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Suchbefehle für Nachrichtenerweiterungen für Teams-Apps, um einen Suchbefehl über das App-Manifest und manuell zu erstellen.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: cdc3bd5de10fb85970c74065f12164dc36d81fe3
ms.sourcegitcommit: 69a45722c5c09477bbff3ba1520e6c81d2d2d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2022
ms.locfileid: "67312268"
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

Um den Suchbefehl zu Ihrem App-Manifest hinzuzufügen, müssen Sie ein neues `composeExtension` Objekt auf der obersten Ebene Des App-Manifest-JSON hinzufügen. Sie können den Suchbefehl entweder mithilfe des Entwicklerportals oder manuell hinzufügen.

### <a name="create-a-search-command-using-developer-portal"></a>Erstellen eines Suchbefehls mithilfe des Entwicklerportals

Die Voraussetzung zum Erstellen eines Suchbefehls ist, dass Sie bereits eine Nachrichtenerweiterung erstellt haben müssen. Informationen zum Erstellen einer Nachrichtenerweiterung finden Sie unter [Erstellen einer Nachrichtenerweiterung](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Aktionsbefehl:**

1. Öffnen Sie **das Entwicklerportal** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Apps** " aus. Wenn Sie Ihr App-Paket bereits im **Entwicklerportal** erstellt haben, wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.
1. Wählen Sie nach dem Importieren eines App-Pakets **nachrichtenerweiterungen** unter **"App-Features"** aus.
1. Um eine Nachrichtenerweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie " **Neuen Bot erstellen** " aus, geben Sie dem neuen Bot einen Namen, und wählen Sie dann " **Erstellen"** aus.

   :::image type="content" source="../../../assets/images/tdp/bot-page.png" alt-text="Der Screenshot zeigt, wie Sie einen Bot im Entwicklerportal erstellen.":::

1. Um einen vorhandenen Bot zu verwenden, wählen **Sie einen vorhandenen Bot und** dann die vorhandenen Bots aus der Dropdownliste aus, oder geben **Sie eine Bot-ID ein** , wenn Sie bereits eine Bot-ID erstellt haben.

1. Wählen Sie den Bereich der Messaging-Erweiterung und dann **"Speichern"** aus.

1. Wählen Sie " **Befehl hinzufügen"** im Abschnitt **"Befehl** " aus, um die Befehle einzuschließen, die das Verhalten der Nachrichtenerweiterung bestimmen.
In der folgenden Abbildung wird das Hinzufügen des Befehls für die Nachrichtenerweiterung angezeigt:

   :::image type="content" source="../../../assets/images/tdp/add-a-command.PNG" alt-text="Der Screenshot zeigt, wie Sie einen Befehl hinzufügen, um das Verhalten der Nachrichtenerweiterung zu definieren.":::

1. Wählen Sie **"Suchen** " aus, und geben Sie **Befehls-ID**, **Befehlstitel** und **Befehlsbeschreibung** ein.

1. Geben Sie alle Parameter ein, und wählen Sie den Typ der Eingabe aus der Dropdownliste aus.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-parameter.PNG" alt-text="Der Screenshot zeigt, wie Sie einen Parameter hinzufügen, um den Befehl für die Nachrichtenerweiterung zu definieren.":::

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
