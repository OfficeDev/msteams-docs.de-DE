---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt das Hinzufügen von Funktionen des Teams Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: a0ebea1fb05e3583c90c41596da98a25d89f9b4c
ms.sourcegitcommit: 74623035d7c18194e339f566c820e0653bc3d8b6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65656761"
---
# <a name="add-capabilities-to-teams-apps"></a>Hinzufügen von Funktionen zu Teams-Apps

Das Hinzufügen von Funktionen in Teams Toolkit hilft Ihnen, Ihrer vorhandenen Teams-App zusätzliche Funktionen hinzuzufügen. In der folgenden Tabelle sind die Teams App-Funktionen aufgeführt:

|**Funktion**|**Beschreibung**|
|--------|-------------|
| Registerkarten |  Registerkarten sind einfache HTML-Tags, die sich auf im App-Manifest deklarierte Domänen beziehen. Sie können Registerkarten als Teil des Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|
| Bots |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule.|
| Nachrichtenerweiterungen | Nachrichtenerweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.|

## <a name="advantages"></a>Vorteile

Die folgende Liste bietet Vorteile zum Hinzufügen weiterer Funktionen in TeamsFx:

* Bietet Komfort
* Fügt Ihrer App weitere Funktionen hinzu, indem Quellcodes automatisch mit Teams Toolkit hinzugefügt werden.

## <a name="limitations"></a>Einschränkungen

Die folgende Liste enthält Einschränkungen zum Hinzufügen weiterer Funktionen in TeamsFx:

* Sie können Registerkarten bis zu 16 Instanzen hinzufügen.
* Sie können einen Bot und eine Nachrichtenerweiterung für jede Instanz hinzufügen.

## <a name="add-capabilities"></a>Fähigkeiten hinzufügen

**Sie können Funktionen mit den folgenden Methoden hinzufügen:**

* So fügen Sie Funktionen mithilfe des Teams Toolkits in Visual Studio Code hinzu
* So fügen Sie Funktionen mithilfe der Befehlspalette hinzu

  > [!Note]
  > Sie müssen für jede Umgebung bereitstellen, nachdem Sie die Funktionen in Ihrer Teams App erfolgreich hinzugefügt haben.

* **So fügen Sie Funktionen mithilfe des Teams Toolkits in Visual Studio Code hinzu:**

   1. Öffnen Sie **Visual Studio Code**.
   1. Wählen Sie im linken Bereich **Teams Toolkit** aus.
   1. Wählen Sie unter **"ENTWICKLUNG****" die Option "Features hinzufügen"** aus.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="Eine aktualisierte" border="true":::

* **So fügen Sie Funktionen mithilfe der Befehlspalette hinzu:**

   1. Öffnen Sie **die Befehlspalette**.
   1. Geben Sie **Teams:Features hinzufügen ein**.
   1. Drücken Sie **EINGABE**.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/Teams-add-features.png" alt-text="Teamfeature" border="true":::

   1. Wählen Sie im Popup die Funktion aus, die Sie in Ihrem Projekt hinzufügen möchten.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Benachrichtigung" border="true":::

## <a name="add-capabilities-using-teamsfx-cli"></a>Hinzufügen von Funktionen mithilfe von TeamsFx CLI

* Ändern des Verzeichnisses in Ihr **Projektverzeichnis**
* In der folgenden Tabelle sind die Funktionen und erforderlichen Befehle aufgeführt:

  |Funktion und Szenario| Befehl|
  |-----------------------|----------|
  |So fügen Sie einen Benachrichtigungs-Bot hinzu |`teamsfx add notification `|
  |So fügen Sie den Befehlsbot hinzu |`teamsfx add command-and-response `|
  |So fügen Sie eine sso-aktivierte Registerkarte hinzu |`teamsfx add sso-tab`|
  |So fügen Sie eine Registerkarte hinzu |`teamsfx add tab`|
  |So fügen Sie einen Bot hinzu |`teamsfx add bot`|
  |So fügen Sie eine Nachrichtenerweiterung hinzu |`teamsfx add message extension`|

## <a name="available-capabilities-to-add-for-different-teams-project"></a>Verfügbare Funktionen zum Hinzufügen für verschiedene Teams Projekts

Sie können verschiedene Funktionen basierend auf dem Projekt hinzufügen, das Sie in Teams App erstellt haben.
In der folgenden Tabelle sind die verfügbaren Funktionen aufgeführt, die Sie in Ihrem Projekt hinzufügen können:

|Vorhandene Funktionen|Weitere unterstützte Funktionen|
|--------------------|--------------------|
|registerkarte SPFx |None|
|SSO-aktivierte Registerkarte |SSO-aktivierte Registerkarte, Benachrichtigungs-Bot, Befehls-Bot, Bot, Nachrichtenerweiterung|
|Benachrichtigungs-Bot |SSO-aktivierte Registerkarte, Registerkarte|
|Befehlsbot |SSO-aktivierte Registerkarte, Registerkarte|
|Tab |Registerkarte, Benachrichtigungs-Bot, Befehls-Bot, Bot, Nachrichtenerweiterung|
|Bot |Nachrichtenerweiterung, SSO-aktivierte Registerkarte, Registerkarte|
|Nachrichtenerweiterung |Bot, SSO-aktivierte Registerkarte, Registerkarte |

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

* Befolgen Sie die schrittweise Anleitung zum Erstellen [eines Benachrichtigungs-Bots](../sbs-gs-notificationbot.yml) in Microsoft Teams.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen eines neuen Teams Projekts](create-new-project.md)
