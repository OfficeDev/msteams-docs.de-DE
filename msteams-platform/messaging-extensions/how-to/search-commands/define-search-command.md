---
title: Definieren von Suchbefehlen für Nachrichtenerweiterungen
author: surbhigupta
description: Erfahren Sie mehr über Suchbefehle für Nachrichtenerweiterungen für Teams-Apps, um einen Suchbefehl über das App-Manifest und manuell zu erstellen.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 9ec7ea734e331fcfb563702d18284f4831c369f6
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820178"
---
# <a name="define-message-extension-search-commands"></a>Definieren von Suchbefehlen für Nachrichtenerweiterungen

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Mithilfe von Suchbefehlen für Nachrichtenerweiterungen können Benutzer externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen. In diesem Dokument erfahren Sie, wie Sie Speicherorte für den Suchbefehl auswählen und dem App-Manifest den Suchbefehl hinzufügen.

> [!NOTE]
> Die Größenbeschränkung für Ergebniskarten beträgt 28 KB. Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.

Im folgenden Video erfahren Sie, wie Sie Suchbefehle für Nachrichtenerweiterungen definieren:
<br>

> [!VIDEO <https://www.microsoft.com/en-us/videoplayer/embed/RE4OIvK>]
<br>

## <a name="select-search-command-invoke-locations"></a>Auswählen von Suchbefehlsaufrufspeicherorten

Der Suchbefehl wird von einem oder beiden der folgenden Speicherorte aufgerufen:

* Bereich zum Verfassen von Nachrichten: die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten.
* Befehlsfeld: Durch @mentioning im Befehlsfeld.

Wenn ein Suchbefehl aus dem Nachrichtenbereich zum Verfassen aufgerufen wird, sendet der Benutzer die Ergebnisse an die Unterhaltung. Wenn sie über das Befehlsfeld aufgerufen wird, interagiert der Benutzer mit der resultierenden Karte oder kopiert sie zur Verwendung an anderer Stelle.

Die folgende Abbildung zeigt die Aufrufspeicherorte des Suchbefehls:

:::image type="content" source="~/assets/images/messaging-extension/search-command-invoke-locations.png" alt-text="Screenshot: Aufruforte eines Suchbefehls in einem Teams-Kanal":::

## <a name="add-the-search-command-to-your-app-manifest"></a>Hinzufügen des Suchbefehls zu Ihrem App-Manifest

Um den Suchbefehl zu Ihrem App-Manifest hinzuzufügen, müssen Sie der obersten Ebene Des App-Manifest-JSON ein neues `composeExtension` -Objekt hinzufügen. Sie können den Suchbefehl entweder mithilfe des Entwicklerportals oder manuell hinzufügen.

### <a name="create-a-search-command-using-developer-portal"></a>Erstellen eines Suchbefehls mithilfe des Entwicklerportals

Voraussetzung zum Erstellen eines Suchbefehls ist, dass Sie bereits eine Nachrichtenerweiterung erstellt haben. Informationen zum Erstellen einer Nachrichtenerweiterung finden Sie unter [Erstellen einer Nachrichtenerweiterung](~/messaging-extensions/how-to/create-messaging-extension.md).

**So erstellen Sie einen Aktionsbefehl:**

1. Öffnen Sie **das Entwicklerportal** über den Microsoft Teams-Client, und wählen Sie die Registerkarte **Apps** aus. Wenn Sie Ihr App-Paket bereits im **Entwicklerportal** erstellt haben, wählen Sie aus der Liste aus. Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes Paket.
1. Wählen Sie nach dem Importieren eines App-Pakets unter **App-Features** **die Option Nachrichtenerweiterungen** aus.
1. Um eine Nachrichtenerweiterung zu erstellen, benötigen Sie einen von Microsoft registrierten Bot. Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen. Wählen Sie die Option **Neuen Bot erstellen** aus, geben Sie dem neuen Bot einen Namen, und wählen Sie dann **Erstellen** aus.

   :::image type="content" source="../../../assets/images/tdp/bot-page.png" alt-text="Screenshot: Optionen zum Konfigurieren eines Bots für eine App im Teams-Entwicklerportal":::

1. Um einen vorhandenen Bot zu verwenden, wählen **Sie Vorhandenen Bot auswählen** und die vorhandenen Bots aus der Dropdownliste aus, oder wählen **Sie Bot-ID eingeben** aus, wenn Sie bereits eine Bot-ID erstellt haben.

1. Wählen Sie den Bereich der Messagingerweiterung und dann **Speichern** aus.

1. Wählen Sie im Abschnitt **Befehl** die Option **Befehl hinzufügen** aus, um die Befehle einzuschließen, die über das Verhalten der Nachrichtenerweiterung entscheiden.
In der folgenden Abbildung wird das Hinzufügen des Befehls für die Nachrichtenerweiterung angezeigt:

   :::image type="content" source="../../../assets/images/tdp/add-a-command.PNG" alt-text="Screenshot: Hinzufügen eines Befehls im Teams-Entwicklerportal zum Definieren des Verhaltens der Nachrichtenerweiterung":::

1. Wählen Sie **Suchen** aus, und geben Sie **Befehls-ID**, **Befehlstitel** und **Befehlsbeschreibung ein**.

1. Geben Sie alle Parameter ein, und wählen Sie den Typ der Eingabe aus der Dropdownliste aus.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-parameter.PNG" alt-text="Screenshot: Hinzufügen eines Parameters zum Definieren Ihres Befehls im Teams-Entwicklerportal für eine Nachrichtenerweiterung":::

1. Wählen Sie unter **Vorschaulinks** **die Option Domäne hinzufügen** aus.

1. Geben Sie eine gültige Domäne ein, und wählen Sie dann **Hinzufügen** aus.

   :::image type="content" source="../../../assets/images/tdp/add-domain.PNG" alt-text="Screenshot: Hinzufügen einer gültigen Domäne zu Ihrer Messaging-Erweiterung zum Entpacken von Links":::

1. Wählen Sie **Speichern** aus.

   :::image type="content" source="../../../assets/images/tdp/add-a-command-save.PNG" alt-text="Screenshot: Speichern aller Einstellungen und Parameter für die Nachrichtenerweiterung":::

**So fügen Sie zusätzliche Parameter hinzu**

1. Wählen Sie im Befehlsabschnitt die Auslassungspunkte und dann **Parameter bearbeiten** aus.

   :::image type="content" source="../../../assets/images/tdp/edit-parameters.PNG" alt-text="Screenshots zeigen, wie Sie Parameter für Ihre Nachrichtenerweiterung bearbeiten.":::

1. Wählen Sie **Parameter hinzufügen** aus, und geben Sie alle Parameter ein.

   :::image type="content" source="../../../assets/images/tdp/add-parameter.PNG" alt-text="Screenshot: Hinzufügen zusätzlicher Parameter für Ihre Nachrichtenerweiterung"lightbox="../../../assets/images/tdp/add-a-parameters.PNG":::

### <a name="create-a-search-command-manually"></a>Manuelles Erstellen eines Suchbefehls

Um den Befehl für die Nachrichtenerweiterungssuche manuell zu Ihrem App-Manifest hinzuzufügen, müssen Sie ihrem `composeExtension.commands` Array von Objekten die folgenden Parameter hinzufügen:

| Eigenschaftenname | Zweck | Pflichtfeld? | Minimale Manifestversion |
|---|---|---|---|
| `id` | Diese Eigenschaft ist eine eindeutige ID, die Sie dem Suchbefehl zuweisen. Die Benutzeranforderung enthält diese ID. | Ja | 1.0 |
| `title` | Diese Eigenschaft ist ein Befehlsname. Dieser Wert wird auf der Benutzeroberfläche (UI) angezeigt. | Ja | 1.0 |
| `description` | Diese Eigenschaft ist ein Hilfetext, der angibt, was dieser Befehl bewirkt. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `type` | Diese Eigenschaft muss ein `query`sein. | Nein | 1.4 |
|`initialRun` | Wenn diese Eigenschaft auf **true** festgelegt ist, gibt dies an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt. | Nein | 1.0 |
| `context` | Diese Eigenschaft ist ein optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist. Die möglichen Werte sind `message`, `compose` oder `commandBox`. Der Standardwert lautet `["compose", "commandBox"]`. | Nein | 1,5 |

Sie müssen die Details des Suchparameters hinzufügen, der den Für Ihren Benutzer im Teams-Client sichtbaren Text definiert.

| Eigenschaftenname | Zweck | Erforderlich? | Minimale Manifestversion |
|---|---|---|---|
| `parameters` | Diese Eigenschaft definiert eine statische Liste von Parametern für den Befehl. | Nein | 1.0 |
| `parameter.name` | Diese Eigenschaft beschreibt den Namen des Parameters. Der `parameter.name` wird in der Benutzeranforderung an Ihren Dienst gesendet. | Ja | 1.0 |
| `parameter.description` | Diese Eigenschaft beschreibt die Zwecke des Parameters oder ein Beispiel für den Wert, der bereitgestellt werden muss. Dieser Wert wird auf der Benutzeroberfläche angezeigt. | Ja | 1.0 |
| `parameter.title` | Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine Bezeichnung. | Ja | 1.0 |
| `parameter.inputType` | Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt. Mögliche Werte sind `text`, `textarea`, `number`, `date`, `time`, . `toggle` Der Standardwert ist auf `text`festgelegt. | Nein | 1.4 |
| `parameters.value` | Anfangswert für den Parameter. Derzeit wird der Wert nicht unterstützt. | Nein | 1,5 |

#### <a name="example"></a>Beispiel

Der folgende Abschnitt enthält ein Beispiel für das einfache App-Manifest des Objekts, das `composeExtensions` einen Suchbefehl definiert:

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
|Teams Nachrichtenerweiterungen – Suche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../../sbs-messagingextension-searchcommand.yml) , um eine suchbasierte Nachrichtenerweiterung zu erstellen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Reagieren Sie auf die Suchbefehle](~/messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="see-also"></a>Siehe auch

* [Karten](../../../task-modules-and-cards/what-are-cards.md)
* [Aufgabenmodule](../../../task-modules-and-cards/what-are-task-modules.md)
* [App-Manifestschema für Teams](../../../resources/schema/manifest-schema.md)
* [Entwicklerportal für Teams](../../../concepts/build-and-test/teams-developer-portal.md)
* [Nachrichtenerweiterungen](../../what-are-messaging-extensions.md)
