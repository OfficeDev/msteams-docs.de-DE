---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt die Add-Funktionen von Teams Toolkit
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: f5563b16646b66795b9451eebc865879294dfd98
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61228007"
---
# <a name="add-capabilities-to-your-teams-apps"></a>Hinzufügen von Funktionen zu Ihren Teams-Apps

Sie können beginnen, eine Teams-App mit einer der Teams App-Funktionen zu erstellen. Während der App-Entwicklung können Sie Teams Toolkit verwenden, um Ihrer Teams App flexibel weitere Funktionen hinzuzufügen. In der folgenden Tabelle werden die Teams App-Funktionen beschrieben:

|**Funktion**|**Beschreibung**|
|--------|-------------|
| Registerkarten |  Registerkarten sind einfache HTML-Tags, die auf Domänen verweisen, die im App-Manifest deklariert sind. Sie können Registerkarten als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|
| Bots |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule.|
| Messaging-Erweiterungen | Messaging-Erweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.|

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Sie sollten bereits ein Teams App-Projekt in VS-Code geöffnet haben.

## <a name="add-capabilities-using-teams-toolkit"></a>Hinzufügen von Funktionen mit Teams Toolkit

> [!IMPORTANT]
> Sie müssen die Bereitstellung für jede Umgebung durchführen, nachdem Sie Ihrer Teams App erfolgreich Funktionen hinzugefügt haben.

1. Wählen Sie im linken Bereich **Teams Toolkit** aus:

    ![Aktivieren des Teams Toolkits](./images/activate-teams-toolkit.png)
  
1. Wählen Sie **"Funktionen hinzufügen" aus:**

    ![Hinzufügen von Funktionen](./images/add-capabilities.png)

      Sie können auch die Befehlspalette öffnen und **Teams: Hinzufügen von Funktionen** eingeben: 
      
      > [!NOTE]
      > Dies entspricht dem Auslösen aus der Strukturansicht.

    ![Alternative Funktionen zum Hinzufügen](./images/alternate-capabilities.png)

1. Wählen Sie im Popup die Funktionen aus, die in Ihr Projekt eingeschlossen werden sollen:

    ![Auswählen von Funktionen](./images/select-capabilities.png)

1. Wählen Sie **OK** aus.

Die ausgewählten Funktionen werden ihrem Projekt erfolgreich hinzugefügt. Das Teams Toolkit generiert Quellcode für neu hinzugefügte Funktionen.

## <a name="add-capabilities-using-teamsfx-cli-in-command-window"></a>Hinzufügen von Funktionen mithilfe von TeamsFx CLI im Befehlsfenster

1. Ändern Sie das Verzeichnis in Das **Projektverzeichnis.**
1. Führen Sie den folgenden Befehl aus, um Ihrem Projekt unterschiedliche Funktionen hinzuzufügen:

   |Funktion und Szenario| Befehl|
   |-----------------------|----------|
   |So fügen Sie eine Registerkarte hinzu|`teamsfx capability add tab`|
   |So fügen Sie einen Bot hinzu|`teamsfx capability add bot`|
   |So fügen Sie eine Messaging-Erweiterung hinzu|`teamsfx capability add messaging-extension`|

## <a name="supported-capabilities-matrix"></a>Matrix der unterstützten Funktionen

Abgesehen von den Funktionen, die Ihre Teams-App bereits bietet, können Sie Ihrer Teams App verschiedene Funktionen hinzufügen. Die folgende Tabelle enthält verschiedene unterstützte Teams App-Funktionen: 

|Vorhandene Funktionen|Weitere Funktionen können hinzugefügt werden|
|--------------------|--------------------|
|Registerkarten mit SPFx|Keine|
|Registerkarten mit Azure|Bots und Messaging-Erweiterungen|
|Bots|Registerkarten|
|Messaging-Erweiterungen|Registerkarten|
|Registerkarten und Bots|Keine|
|Registerkarten und Messaging-Erweiterungen|Keine|
|Registerkarten, Bots und Messaging-Erweiterungen|Keine|

## <a name="what-happens-when-you-add-capabilities"></a>Was geschieht, wenn Sie Funktionen hinzufügen

Nach dem Hinzufügen von Bot- und Messaging-Erweiterungen sind die folgenden Änderungen in Ihrem Projekt:

- Ein Botvorlagencode wird einem Unterordner mit Pfad `yourProjectFolder/bot` hinzugefügt. Dies umfasst eine "Hello World"-Botanwendungsvorlage in Ihr Projekt.
- `launch.json` und `task.json` unter Ordner werden `.vscode` aktualisiert. Dies umfasst die erforderlichen Skripts für Visual Studio Code ausgeführt wird, wenn Sie Ihre Anwendung lokal debuggen möchten. 
- `manifest.remote.template.json` und `manifest.local.template.json` die Datei unter `templates/appPackage` "Ordner" wird aktualisiert. Dazu gehören botbezogene Informationen in der Manifestdatei, die Ihre Anwendung in der Teams-Plattform darstellt. Die Änderung umfasst:
  - Die ID Ihres Bots.
  - Die Bereiche Ihres Bots.
  - Die Befehle, auf die die Hello World-Bot-Anwendung reagieren kann.
- Dateien unter `templates/azure/teamsfx` werden aktualisiert, und vorlagen/azure/provision/xxx.bicep-Datei werden neu generiert.
- Die Datei unter `.fx/config` wird neu generiert. Dadurch wird sichergestellt, dass Ihr Projekt mit den richtigen Konfigurationen für die neu hinzugefügte Funktion festgelegt wird.

Nach dem Hinzufügen der Registerkarte sind die folgenden Änderungen in Ihrem Projekt:

- Ein Vorlagencode für die Front-End-Registerkarte wird einem Unterordner mit Pfad `yourProjectFolder/tab` hinzugefügt. Dies schließt eine Registerkartenanwendungsvorlage "Hello World" in Ihr Projekt ein.
- `launch.json` und `task.json` unter Ordner werden `.vscode` aktualisiert. Dies umfasst die erforderlichen Skripts für Visual Studio Code ausgeführt wird, wenn Sie Ihre Anwendung lokal debuggen möchten. 
- `manifest.remote.template.json` und `manifest.local.template.json` die Datei unter `templates/appPackage` "Ordner" wird aktualisiert. Dazu gehören registerkartenbezogene Informationen in der Manifestdatei, die Ihre Anwendung in der Teams Plattform darstellt. Zu den Änderungen gehören:
  - Die konfigurierbaren und statischen Registerkarten.
  - Die Bereiche der Registerkarten.
- Dateien unter `templates/azure/teamsfx` werden aktualisiert, und vorlagen/azure/provision/xxx.bicep-Datei werden neu generiert.
- Die Datei unter `.fx/config` wird neu generiert. Dadurch wird sichergestellt, dass Ihr Projekt mit den richtigen Konfigurationen für die neu hinzugefügte Funktion festgelegt wird.

## <a name="limitations"></a>Einschränkungen

Derzeit gibt es Einschränkungen bei TeamsFx beim Hinzufügen weiterer Funktionen. Die Einschränkungen sind wie folgt:

- Jede Projektfunktion mehrmals
- Jede Funktion, wenn Sie mit einer Registerkartenanwendung mit SPFx
- Weitere Bot-Funktionen, wenn Ihr Projekt Messaging-Erweiterung enthält
- Weitere Messaging-Erweiterungen, wenn Ihr Projekt einen Bot enthält.

> [!NOTE]
> Wenn Sie sowohl Bot- als auch Messaging-Erweiterungsfunktionen einschließen möchten, wählen Sie diese gleichzeitig aus. Sie können sie entweder hinzufügen, wenn Sie ein neues Projekt oder eine Registerkartenanwendung erstellen.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Bereitstellen von Cloudressourcen](provision.md)

> [!div class="nextstepaction"]
> [Erstellen eines neuen Teams Projekts](create-new-project.md)
