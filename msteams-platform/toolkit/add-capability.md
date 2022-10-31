---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Funktionen des Teams-Toolkits hinzufügen.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: a0bec3166228b53dd4a6da336b42632ba2475582
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791755"
---
# <a name="add-capabilities-to-teams-apps"></a>Hinzufügen von Funktionen zu Teams-Apps

Durch das Hinzufügen von Funktionen mit dem Teams-Toolkit können Sie zusätzliche Features in Ihre vorhandene Microsoft Teams-App aufnehmen. Der Vorteil des Hinzufügens weiterer Funktionen besteht darin, dass Sie Ihrer App weitere Funktionen hinzufügen können, indem Sie mithilfe des Teams Toolkits automatisch Quellcodes hinzufügen. Sie können auch verschiedene Funktionen basierend auf dem Projekt auswählen, das Sie in Ihrer Teams-App erstellt haben. In der folgenden Tabelle sind die Funktionen der Teams-App aufgeführt:

|Funktion|Beschreibung|Andere unterstützte Funktionen|
|--------|-------------|-----------------|
|**Einfache Teams-App**|              |
| Tab |  Registerkarten sind einfache HTML-Tags, die auf im App-Manifest deklarierte Domänen verweisen. Sie können Registerkarten als Teil des Kanals innerhalb eines Team-, Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|Registerkarte, Benachrichtigungsbot, Befehlsbot, Bot, Nachrichtenerweiterung|
|Registerkarte "SPFx"| SPFx-Registerkarten-Apps werden in Microsoft 365 gehostet und unterstützen das Entwickeln und Hosten Ihrer clientseitigen SPFx-Lösung.|Keine|
|Registerkarte "SSO-enabled" (SSO-fähig)|Sie können eine SSO-fähige Registerkarten-App erstellen, die dem Benutzer das Einmalige Anmelden ermöglicht.|SSO-fähige Registerkarte, Benachrichtigungsbot, Befehlsbot, Bot, Nachrichtenerweiterung|
| Bot |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule.|Nachrichtenerweiterung, Registerkarte "SSO-fähig", Registerkarte|
| Nachrichtenerweiterung | Nachrichtenerweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.|Bot, Registerkarte "SSO-fähig", Registerkarte|
|**Szenariobasierte Teams-App**|             |
| Benachrichtigungsbot | Der Benachrichtigungsbot sendet proaktiv Nachrichten im Teams-Kanal oder Gruppenchat oder persönlichen Chat. Sie können den Benachrichtigungsbot mit einer HTTP-Anforderung auslösen, z. B. Karten oder SMS. |Registerkarte "SSO-fähig", Registerkarte|
| Befehlsbot | Mit dem Befehlsbot können Sie sich wiederholende Aufgaben mithilfe eines Befehlsbots automatisieren. Es reagiert auf einfache Befehle, die in Chats mit adaptiven Karten gesendet werden. |Registerkarte "SSO-fähig", Registerkarte|
| Workflowbot| Der Workflowbot ermöglicht Benutzern die Interaktion mit einer adaptiven Karte, die durch das Feature adaptive Karten-Aktionshandler in der Workflowbot-App aktiviert wird.|Registerkarte "SSO-fähig", Registerkarte|

> [!NOTE]
> Sie können Registerkarten bis zu 16 Instanzen hinzufügen. Was Ihren Bot und Ihre Nachrichtenerweiterung betrifft, können Sie für jede Instanz jeweils eine hinzufügen.

## <a name="add-capabilities"></a>Fähigkeiten hinzufügen

Sie können Funktionen mit den folgenden Methoden hinzufügen:

* [Verwenden des Teams-Toolkits in Microsoft Visual Studio Code](#using-teams-toolkit-in-microsoft-visual-studio-code)
* [Verwenden der Befehlspalette](#using-the-command-palette)
* [Verwenden der TeamsFx CLI](#using-teamsfx-cli)

### <a name="using-teams-toolkit-in-microsoft-visual-studio-code"></a>Verwenden des Teams-Toolkits in Microsoft Visual Studio Code

   1. Öffnen Sie **Visual Studio Code**.
   1. Wählen Sie **teams Toolkit** in der Aktivitätsleiste aus.
   1. Wählen Sie unter **ENTWICKLUNG** **die Option Features hinzufügen** aus.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="Hinzufügen von Funktionen aus dem Teams-Toolkit":::

      > [!NOTE]
      > Nachdem Sie die Funktionen in Ihrer Teams-App erfolgreich hinzugefügt haben, müssen Sie für jede Umgebung bereitstellen.

### <a name="using-the-command-palette"></a>Verwenden der Befehlspalette

   1. Wählen Sie **Befehlspalette anzeigen** > **...** oder **STRG+UMSCHALT+P** aus.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add-capabilities-command-palette.png" alt-text="Hinzufügen von Funktionen aus befehls palatte":::

   1. Geben Sie **Teams: Features hinzufügen** ein.
   1. Drücken Sie die EINGABETASTE.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/teams-add-features.png" alt-text="So fügen Sie Funktionen mithilfe der Befehlspalette hinzu.":::

   1. Wählen Sie im Popupfenster die Funktion aus, die Sie in Ihrem Projekt hinzufügen müssen.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Benachrichtigung":::

### <a name="using-teamsfx-cli"></a>Verwenden der TeamsFx CLI

* Wechseln Sie in das Verzeichnis für **Ihr Projekt**.
* In der folgenden Tabelle sind die Funktionen und erforderlichen Befehle aufgeführt:

  |Funktion und Szenario| Get-Help|
  |-----------------------|----------|
  |So fügen Sie einen Benachrichtigungsbot hinzu |`teamsfx add notification`|
  |So fügen Sie einen Befehlsbot hinzu |`teamsfx add command-and-response`|
  |So fügen Sie die Registerkarte "SSO-fähig" hinzu |`teamsfx add sso-tab`|
  |So fügen Sie die Registerkarte hinzu |`teamsfx add tab`|
  |So fügen Sie einen Bot hinzu |`teamsfx add bot`|
  |So fügen Sie eine Nachrichtenerweiterung hinzu |`teamsfx add message extension`|

## <a name="changes-after-adding-capabilities"></a>Änderungen nach dem Hinzufügen von Funktionen

In der folgenden Tabelle sind die Änderungen aufgeführt, die beim Hinzufügen der Funktionen in den Dateien Ihrer App angezeigt werden:

|Funktion hinzufügen|Beschreibung| Änderungen|
|------------|------------------------|---------|
|Bot, Nachrichtenerweiterung und Registerkarte|Schließt eine **App-Vorlage für einen Hello World-Bot**&nbsp;oder eine Registerkarte in Ihr Projekt ein.|Ein Front-End-Bot- oder Tab-Vorlagencode wird einem Unterordner mit pfad `yourProjectFolder/bot` bzw `yourProjectFolder/tab` . hinzugefügt.|
| Bot, Nachrichtenerweiterung und Registerkarte |Enthält die erforderlichen Skripts für Visual Studio Code und wird ausgeführt, wenn Sie Ihre Anwendung lokal debuggen möchten. |Dateien `launch.json` und `task.json` unter `.vscode` ordner werden aktualisiert.|
| Bot- und Nachrichtenerweiterung|Enthält Bot- oder Tabstoppinformationen in der Manifestdatei, die Ihre Anwendung in der Teams-Plattform darstellt.|Die Datei`manifest.template.json` unter `templates/appPackage` dem Ordner wird aktualisiert, die registerkartenbezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung in der Teams-Plattform darstellt. Die Änderungen sind in der ID Ihres Bots, den Bereichen Ihres Bots und den Befehlen sichtbar, auf die der Hello World-Bot oder die Registerkartenanwendung reagieren kann.|
|Tab|Enthält Bot- oder Tabstoppinformationen in der Manifestdatei, die Ihre Anwendung in der Teams-Plattform darstellt.|Die Datei `manifest.template.json` unter `templates/appPackage` dem Ordner wird aktualisiert, die registerkartenbezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung in der Teams-Plattform darstellt. Die Änderungen sind in konfigurierbaren und statischen Registerkarten sowie in Bereichen der Registerkarten sichtbar.|
|Bot, Nachrichtenerweiterung und Registerkarte|Enthält Bot- oder Tab-bezogene&nbsp;Informationen in teamsfx und Bereitstellungsdateien, die für die Integration von Azure-Funktionen vorgesehen sind.|Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx`Bicep-Dateien werden neu generiert.|
|Bot, Nachrichtenerweiterung und Registerkarte|Stellt sicher, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt ist.|Dateien unter `.fx/config` werden neu generiert.|

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [Schritt-für-Schritt-Anleitung zum Erstellen eines Befehlsbots](../sbs-gs-commandbot.yml) in Microsoft Teams.

* Befolgen Sie die [Schritt-für-Schritt-Anleitung zum Erstellen eines Benachrichtigungsbots](../sbs-gs-notificationbot.yml) in Microsoft Teams.

* Befolgen Sie die [Schritt-für-Schritt-Anleitung zum Erstellen eines Workflowbots](../sbs-gs-workflow-bot.yml) in Microsoft Teams.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen eines neuen Teams-Projekts](create-new-project.md)
