---
title: Hinzufügen von Funktionen zu Ihren Teams-Apps
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Funktionen des Teams-Toolkits hinzufügen.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 5f0aa26276c2db7651fac473049cac0aa75f14dd
ms.sourcegitcommit: dccb48902e08484692ab927415bcd3d61dc50db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2022
ms.locfileid: "67806857"
---
# <a name="add-capabilities-to-teams-apps"></a>Hinzufügen von Funktionen zu Teams-Apps

Durch das Hinzufügen von Funktionen mit dem Teams-Toolkit können Sie zusätzliche Features zu Ihrer vorhandenen Microsoft Teams-App hinzufügen. Der Vorteil des Hinzufügens weiterer Funktionen besteht darin, dass Sie Ihrer App weitere Funktionen hinzufügen können, indem Sie quellcodes automatisch mithilfe des Teams-Toolkits hinzufügen. Sie können auch verschiedene Funktionen basierend auf dem Projekt auswählen, das Sie in Ihrer Teams-App erstellt haben. In der folgenden Tabelle sind die Funktionen der Teams-App aufgeführt:

|Funktion|Beschreibung|Weitere unterstützte Funktionen|
|--------|-------------|-----------------|
|**Einfache Teams-App**|              |
| Tab |  Registerkarten sind einfache HTML-Tags, die sich auf im App-Manifest deklarierte Domänen beziehen. Sie können Registerkarten als Teil des Kanals innerhalb eines Teams, eines Gruppenchats oder einer persönlichen App für einen einzelnen Benutzer hinzufügen.|Registerkarte, Benachrichtigungs-Bot, Befehls-Bot, Bot, Nachrichtenerweiterung|
|Registerkarte "SPFx"| SPFx-Registerkarten-Apps werden in Microsoft 365 gehostet und unterstützen das Entwickeln und Hosten Ihrer clientseitigen SPFx-Lösung|Keine|
|SSO-aktivierte Registerkarte|Sie können eine SSO-aktivierte Registerkarten-App erstellen, die es dem Benutzer mit dem Feature für einmaliges Anmelden ermöglicht|SSO-aktivierte Registerkarte, Benachrichtigungs-Bot, Befehls-Bot, Bot, Nachrichtenerweiterung|
| Bot |  Bots helfen bei der Interaktion mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule.|Nachrichtenerweiterung, SSO-aktivierte Registerkarte, Registerkarte|
| Nachrichtenerweiterung | Nachrichtenerweiterungen helfen bei der Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client.|Bot, SSO-aktivierte Registerkarte, Registerkarte|
|**Szenariobasierte Teams-App**|             |
| Benachrichtigungs-Bot | Der Benachrichtigungs-Bot sendet proaktiv Nachrichten im Teams-Kanal oder Gruppenchat oder persönlichen Chat. Sie können den Benachrichtigungs-Bot mit einer HTTP-Anforderung auslösen, z. B. Karten oder Texte. |SSO-aktivierte Registerkarte, Registerkarte|
| Befehlsbot | Mit dem Befehls-Bot können Sie sich wiederholende Aufgaben mithilfe eines Befehls-Bots automatisieren. Es reagiert auf einfache Befehle, die in Chats mit adaptiven Karten gesendet werden. |SSO-aktivierte Registerkarte, Registerkarte|

> [!NOTE]
> Sie können Registerkarten bis zu 16 Instanzen hinzufügen. Was Ihre Bot- und Nachrichtenerweiterung betrifft, können Sie jeweils eine für jede Instanz hinzufügen.

## <a name="add-capabilities"></a>Fähigkeiten hinzufügen

Sie können Funktionen mit den folgenden Methoden hinzufügen:

* [Verwenden des Teams-Toolkits in Microsoft Visual Studio Code](#using-teams-toolkit-in-microsoft-visual-studio-code)
* [Verwenden der Befehlspalette](#using-the-command-palette)
* [Verwenden von TeamsFx CLI](#using-teamsfx-cli)

### <a name="using-teams-toolkit-in-microsoft-visual-studio-code"></a>Verwenden des Teams-Toolkits in Microsoft Visual Studio Code

   1. Öffnen Sie **Visual Studio Code**.
   1. Wählen Sie in der Aktivitätsleiste das **Teams-Toolkit** aus.
   1. Wählen Sie unter **"ENTWICKLUNG****" die Option "Features hinzufügen"** aus.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/select-feature123.png" alt-text="Hinzufügen von Funktionen aus dem Teams-Toolkit":::

      > [!NOTE]
      > Nachdem Sie die Funktionen in Ihrer Teams-App erfolgreich hinzugefügt haben, müssen Sie diese für jede Umgebung bereitstellen.

### <a name="using-the-command-palette"></a>Verwenden der Befehlspalette

   1. Wählen Sie **"****Ansichtsbefehlspalette** > ... oder **STRG+UMSCHALT+P**" aus.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add-capabilities-command-palette.png" alt-text="Hinzufügen von Funktionen aus Befehlspapatte":::

   1. Geben Sie **Teams ein: Fügen Sie Features hinzu**.
   1. Drücken Sie die EINGABETASTE.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/teams-add-features.png" alt-text="So fügen Sie Funktionen mithilfe der Befehlspalette hinzu.":::

   1. Wählen Sie im Popup die Funktion aus, die Sie in Ihrem Projekt hinzufügen müssen.

       :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/notification-add-capabilities.png" alt-text="Benachrichtigung":::

### <a name="using-teamsfx-cli"></a>Verwenden von TeamsFx CLI

* Wechseln Sie in das Verzeichnis für **Ihr Projekt**.
* In der folgenden Tabelle sind die Funktionen und erforderlichen Befehle aufgeführt:

  |Funktion und Szenario| Befehl|
  |-----------------------|----------|
  |So fügen Sie einen Benachrichtigungs-Bot hinzu |`teamsfx add notification`|
  |So fügen Sie den Befehlsbot hinzu |`teamsfx add command-and-response`|
  |So fügen Sie eine sso-aktivierte Registerkarte hinzu |`teamsfx add sso-tab`|
  |So fügen Sie eine Registerkarte hinzu |`teamsfx add tab`|
  |So fügen Sie einen Bot hinzu |`teamsfx add bot`|
  |So fügen Sie eine Nachrichtenerweiterung hinzu |`teamsfx add message extension`|

## <a name="changes-after-adding-capabilities"></a>Änderungen nach dem Hinzufügen von Funktionen

In der folgenden Tabelle sind die Änderungen aufgeführt, die in den Dateien Ihrer App beim Hinzufügen der Funktionen zu sehen sind:

|Funktion hinzufügen|Beschreibung| Änderungen|
|------------|------------------------|---------|
|Bot, Nachrichtenerweiterung und Registerkarte|Enthält eine **Hello World-Bot**&nbsp;- oder Registerkartenanwendungsvorlage in Ihr Projekt.|Ein Front-End-Bot- oder Registerkartenvorlagencode wird einem Unterordner mit Pfad `yourProjectFolder/bot` bzw `yourProjectFolder/tab` . Pfad hinzugefügt.|
| Bot, Nachrichtenerweiterung und Registerkarte |Enthält die erforderlichen Skripts für Visual Studio Code und wird ausgeführt, wenn Sie Ihre Anwendung lokal debuggen möchten. |Dateien `launch.json` und `task.json` ordnerunter `.vscode` werden aktualisiert.|
| Bot- und Nachrichtenerweiterung|Enthält Bot- oder Registerkarteninformationen in der Manifestdatei, die Ihre Anwendung in der Teams-Plattform darstellt.|Die Datei`manifest.template.json` unter `templates/appPackage` dem Ordner wird aktualisiert, die registerkartenbezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung auf der Teams-Plattform darstellt. Die Änderungen sind in der ID Ihres Bots, den Bereichen Ihres Bots und den Befehlen sichtbar, auf die der Hello World-Bot oder die Registerkartenanwendung reagieren kann.|
|Tab|Enthält Bot- oder Registerkarteninformationen in der Manifestdatei, die Ihre Anwendung in der Teams-Plattform darstellt.|Die Datei`manifest.template.json` unter `templates/appPackage` dem Ordner wird aktualisiert, die registerkartenbezogene Informationen in der Manifestdatei enthält, die Ihre Anwendung auf der Teams-Plattform darstellt. Die Änderungen sind auf konfigurierbaren und statischen Registerkarten und bereichen der Registerkarten sichtbar.|
|Bot, Nachrichtenerweiterung und Registerkarte|Enthält Bot-&nbsp;oder Registerkarteninformationen in teamsfx- und Bereitstellungsdateien, die für die Integration von Azure-Funktionen vorgesehen sind.|Dateien unter `templates/azure/teamsfx` werden aktualisiert, und `templates/azure/provision/xxx`Bicep-Dateien werden neu generiert.|
|Bot, Nachrichtenerweiterung und Registerkarte|Stellt sicher, dass Ihr Projekt mit den richtigen Konfigurationen für neu hinzugefügte Funktionen festgelegt ist.|Dateien unter `.fx/config` werden neu generiert|

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

* Befolgen Sie die schrittweise Anleitung zum Erstellen [eines Befehlsbots](../sbs-gs-commandbot.yml) in Microsoft Teams.

* Befolgen Sie die schrittweise Anleitung zum Erstellen [eines Benachrichtigungs-Bots](../sbs-gs-notificationbot.yml) in Microsoft Teams.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen eines neuen Teams-Projekts](create-new-project.md)
