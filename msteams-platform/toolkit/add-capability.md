---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt das Hinzufügen von Funktionen des Teams Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 7778a5747ae6b5118d5ebeac857e2a9944cff62b
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654540"
---
# <a name="add-capabilities-to-your-teams-apps"></a>Hinzufügen von Funktionen zu ihrer Teams-App

Während der App-Entwicklung können Sie eine neue Teams-App mit Teams App-Funktion erstellen. In der folgenden Tabelle sind die Teams App-Funktionen aufgeführt:

|**Funktion**|**Beschreibung**|
|--------|-------------|
| Registerkarten |  Registerkarten sind einfache HTML-Tags, die auf Im App-Manifest deklarierte Domänen verweisen. Sie können Registerkarten als Teil des Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|
| Bots |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule|
| Nachrichtenerweiterungen | Nachrichtenerweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client|

## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Stellen Sie sicher, dass Sie das Teams-App-Projekt in VS-Code geöffnet haben.

## <a name="limitations"></a>Einschränkungen

Die Einschränkungen für TeamsFx beim Hinzufügen weiterer Funktionen lauten wie folgt:

* Sie können Registerkarten bis zu 16 Instanzen hinzufügen.
* Sie können Bot- und Nachrichtenerweiterungen für jeweils eine Instanz hinzufügen.

## <a name="add-capabilities"></a>Fähigkeiten hinzufügen

> [!Note]
> Sie müssen die Bereitstellung für jede Umgebung durchführen, nachdem Sie Ihrer Teams-App erfolgreich Funktionen hinzugefügt haben.
* Sie können funktionen mit Teams Toolkit in Visual Studio Code hinzufügen

    1. **öffnen Microsoft Visual Studio Code**
    1. Auswählen **Teams Toolkits** im linken Bereich
    1. Wählen Sie **"Funktionen hinzufügen" aus.**

        :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add capabilities.png" alt-text="capabilities":::

*   Sie können auch die Befehlspalette öffnen und Teams eingeben: Funktionen hinzufügen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/tree view capabilities.png" alt-text="Alternative Funktionen":::


    1. Wählen Sie im Popup die Funktionen aus, die in Ihr Projekt aufgenommen werden sollen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select capabilities.png" alt-text="select":::

    2. Wählen Sie **"OK**" aus.

Die ausgewählten Funktionen wurden erfolgreich zu Ihrem Projekt hinzugefügt. Das Teams Toolkit generiert Quellcode für neu hinzugefügte Funktionen

## <a name="add-capabilities-using-teamsfx-cli-in-command-window"></a>Hinzufügen von Funktionen mithilfe der TeamsFx CLI im Befehlsfenster

1. Ändern des Verzeichnisses in Ihr **Projektverzeichnis**
1. Führen Sie den folgenden Befehl aus, um Ihrem Projekt unterschiedliche Funktionen hinzuzufügen:

   |Funktion und Szenario| Befehl|
   |-----------------------|----------|
   |So fügen Sie eine Registerkarte hinzu|`teamsfx capability add tab`|
   |So fügen Sie einen Bot hinzu|`teamsfx capability add bot`|
   |So fügen Sie eine Nachrichtenerweiterung hinzu|`teamsfx capability add messaging-extension`|

## <a name="supported-capabilities"></a>Unterstützte Funktionen

Neben den Funktionen, über die Ihre Teams App bereits verfügt, können Sie ihrer Teams App unterschiedliche Funktionen hinzufügen. Die folgende Tabelle enthält die verschiedenen Teams App-Funktionen:

|Vorhandene Funktionen|Weitere unterstützte Funktionen|
|--------------------|--------------------|
|Registerkarten mit SPFx|None|
|Registerkarten mit Azure|Bot- und Nachrichtenerweiterung|
|Bot|Registerkarten|
|Nachrichtenerweiterung|Registerkarten und Bot|
|Registerkarten und Bot|Registerkarten und Nachrichtenerweiterung|
|Registerkarten und Nachrichtenerweiterung|Registerkarten und Bot|
|Registerkarten, Bot und Nachrichtenerweiterung|Registerkarten|
|Registerkarten |Bot- und Nachrichtenerweiterung|

## <a name="add-bot-tab-and-message-extension"></a>Hinzufügen von Bots, Registerkarten und Nachrichtenerweiterungen

Nach dem Hinzufügen eines Bots und einer Nachrichtenerweiterung sind die Änderungen in Ihrem Projekt wie folgt:

* Ein Botvorlagencode wird einem Unterordner mit Pfad `yourProjectFolder/bot`hinzugefügt. Dazu gehört eine **Hello** World-Bot-Anwendungsvorlage in Ihr Projekt.
* `launch.json`und `task.json` unter `.vscode` Ordner aktualisiert werden, die erforderliche Skripts für Visual Studio Code enthält, und wird ausgeführt, wenn Sie Ihre Anwendung lokal debuggen möchten
* `manifest.template.json`datei under `templates/appPackage` folder is updated, which includes the bot related information in the manifest file that represents your application in the Teams Platform. Folgende Änderungen stehen zur Verfügung:
  * Die ID Ihres Bots
  * Die Bereiche Ihres Bots
  * Die Befehle, auf die die Hello World Bot-Anwendung reagieren kann
* Die Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx`Bicep-Dateien werden neu generiert.
* Die Dateien unter `.fx/config` werden neu generiert, wodurch sichergestellt wird, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt wird.

Nach dem Hinzufügen der Registerkarte sind die Änderungen in Ihrem Projekt wie folgt:

* Ein Code für eine Frontend-Registerkartenvorlage wird einem Unterordner mit Pfad `yourProjectFolder/tab`hinzugefügt, der eine Anwendungsvorlage für die Registerkarte " **Hello World** " in Ihr Projekt enthält.
* `launch.json`und `task.json` unter `.vscode` Ordner aktualisiert werden, die erforderliche Skripts für Visual Studio Code enthält, und wird ausgeführt, wenn Sie Ihre Anwendung lokal debuggen möchten
* `manifest.template.json`datei under `templates/appPackage` folder is updated, which includes tab-related information in the manifest file that represents your application in the Teams Platform. Die Änderungen sind:
  * Die konfigurierbaren und statischen Registerkarten
  * Die Bereiche der Registerkarten
* Die Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx`die Bicep-Datei wird neu generiert.
* Die Datei unter `.fx/config` wird neu generiert, wodurch sichergestellt wird, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt wird.

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

* Befolgen Sie die schrittweise Anleitung zum Erstellen [des Befehls-Bots](../sbs-gs-commandbot.yml) in Microsoft Teams

* Befolgen Sie die [schrittweise Anleitung zum Erstellen eines Benachrichtigungs-Bots](../sbs-gs-notificationbot.yml) in Microsoft Teams.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen eines neuen Teams Projekts](create-new-project.md)
