---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt die Add-Funktionen von Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 8aedcef132eee34a72f0f2f873bdae3a45529c7c
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768515"
---
# <a name="add-capabilities-to-your-teams-apps"></a>Hinzufügen von Funktionen zu Ihren Teams-Apps

Sie können eine neue Teams-App mit einer der Teams App-Funktionen erstellen. Während der App-Entwicklung können Sie Teams Toolkit verwenden, um Ihrer Teams App weitere Funktionen hinzuzufügen. In der folgenden Tabelle sind die Teams App-Funktionen aufgeführt:

|**Funktion**|**Beschreibung**|
|--------|-------------|
| Registerkarten |  Registerkarten sind einfache HTML-Tags, die auf Domänen verweisen, die im App-Manifest deklariert sind. Sie können Registerkarten als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|
| Bots |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule.|
| Messaging-Erweiterungen | Messaging-Erweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.|

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt im VS-Code geöffnet ist.

## <a name="add-capabilities-using-teams-toolkit"></a>Hinzufügen von Funktionen mit Teams Toolkit

> [!IMPORTANT]
> Sie müssen die Bereitstellung für jede Umgebung durchführen, nachdem Sie Ihrer Teams App erfolgreich Funktionen hinzugefügt haben.

1. Öffnen **Sie Visual Studio Code**.
1. Wählen Sie im linken Bereich **Teams Toolkit** aus.
1. Wählen Sie **"Funktionen hinzufügen" aus:**

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add capabilities.png" alt-text="capabilities":::

   Sie können auch die Befehlspalette öffnen und **Teams: Hinzufügen von Funktionen** eingeben: 
      
    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/tree view capabilities.png" alt-text="Alternative Funktionen":::

1. Wählen Sie im Popup die Funktionen aus, die in Ihr Projekt eingeschlossen werden sollen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select capabilities.png" alt-text="select":::

1. Wählen Sie **OK** aus.

Die ausgewählten Funktionen werden ihrem Projekt erfolgreich hinzugefügt. Das Teams Toolkit generiert Quellcode für neu hinzugefügte Funktionen.

## <a name="add-capabilities-using-teamsfx-cli-in-command-window"></a>Hinzufügen von Funktionen mithilfe von TeamsFx CLI im Befehlsfenster

1. Ändern Sie das Verzeichnis in Das **Projektverzeichnis.**
1. Führen Sie den folgenden Befehl aus, um Ihrem Projekt unterschiedliche Funktionen hinzuzufügen:

   |Funktion und Szenario| Get-Help|
   |-----------------------|----------|
   |So fügen Sie die Registerkarte hinzu|`teamsfx capability add tab`|
   |So fügen Sie einen Bot hinzu|`teamsfx capability add bot`|
   |So fügen Sie eine Messaging-Erweiterung hinzu|`teamsfx capability add messaging-extension`|

## <a name="supported-capabilities-matrix"></a>Matrix der unterstützten Funktionen

Abgesehen von den Funktionen, über die Ihre Teams-App bereits verfügt, können Sie Ihrer Teams App verschiedene Funktionen hinzufügen. Die folgende Tabelle enthält die verschiedenen Teams App-Funktionen: 

|Vorhandene Funktionen|Weitere unterstützte Funktionen können hinzugefügt werden|
|--------------------|--------------------|
|Registerkarten mit SPFx|None|
|Registerkarten mit Azure|Bots und Messaging-Erweiterungen|
|Bots|Registerkarten|
|Messaging-Erweiterungen|Registerkarten|
|Registerkarten und Bots|None|
|Registerkarten und Messaging-Erweiterungen|Keine|
|Registerkarten, Bots und Messaging-Erweiterungen|None|

## <a name="add-capabilities"></a>Hinzufügen von Funktionen

Nach dem Hinzufügen von Bot- und Messaging-Erweiterungen sind die Änderungen in Ihrem Projekt wie folgt:

- Ein Botvorlagencode wird einem Unterordner mit Pfad `yourProjectFolder/bot` hinzugefügt. Dies schließt eine Hello World-Bot-Anwendungsvorlage in Ihr Projekt ein. 
- `launch.json`und `task.json` unter Ordner aktualisiert `.vscode` werden, die erforderliche Skripts für Visual Studio Code enthalten und ausgeführt werden, wenn Sie Ihre Anwendung lokal debuggen möchten. 
- `manifest.remote.template.json`und `manifest.local.template.json` datei unter Ordner aktualisiert `templates/appPackage` werden, die Bot-bezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung in der Teams Platform darstellt. Folgende Änderungen stehen zur Verfügung:
  - Die ID Ihres Bots.
  - Die Bereiche Ihres Bots.
  - Die Befehle, auf die die Hello World-Bot-Anwendung reagieren kann.
- Die Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx` die Bicep-Datei wird neu generiert.
- Die dateien unter `.fx/config` werden neu generiert, wodurch sichergestellt wird, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt ist.

Nach dem Hinzufügen der Registerkarte sind die Änderungen in Ihrem Projekt wie folgt:

- In einem Unterordner mit Pfad wird ein Vorlagencode für die Front-End-Registerkarte `yourProjectFolder/tab` hinzugefügt, der eine Anwendungsvorlage für **hello** world-Registerkarten in Ihr Projekt einschließt.
- `launch.json`und `task.json` unter Ordner aktualisiert `.vscode` werden, die erforderliche Skripts für Visual Studio Code enthalten und ausgeführt werden, wenn Sie Ihre Anwendung lokal debuggen möchten. 
- `manifest.remote.template.json`und `manifest.local.template.json` datei unter Ordner aktualisiert `templates/appPackage` werden, die registerkartenbezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung in der Teams Plattform darstellt, die Änderungen sind wie folgt:
  - Die konfigurierbaren und statischen Registerkarten.
  - Die Bereiche der Registerkarten.
- Die Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx` die Bicep-Datei wird neu generiert.
- Die Datei unter `.fx/config` wird neu generiert, wodurch sichergestellt wird, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt ist.

## <a name="limitations"></a>Einschränkungen

Die Einschränkungen bei TeamsFx beim Hinzufügen weiterer Funktionen sind wie folgt:

- Sie können projektfunktion nicht für mehr als eine Instanz hinzufügen.
- Sie können keine Bot-Funktionen hinzufügen, wenn Ihr Projekt messaging-Erweiterung enthält.
- Sie können keine Messaging-Erweiterung hinzufügen, wenn Ihr Projekt einen Bot enthält.

> [!NOTE]
> Wenn Sie sowohl Bot- als auch Messaging-Erweiterungsfunktionen einschließen möchten, wählen Sie diese gleichzeitig aus. Sie können sie nur hinzufügen, wenn Sie ein neues Projekt oder eine Registerkartenanwendung erstellen.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen eines neuen Teams Projekts](create-new-project.md)
