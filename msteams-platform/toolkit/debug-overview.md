---
title: Debuggen Sie Ihre Teams-App
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Ihre Teams-App im Teams-Toolkit debuggen und wichtige Features des Teams-Toolkits.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 111f45a8ed0b5246a75d1a1adbda9b124c1e9578
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833149"
---
# <a name="debug-your-teams-app"></a>Debuggen Sie Ihre Teams-App

Das Teams-Toolkit unterstützt Sie beim Debuggen und Anzeigen einer Vorschau Ihrer Microsoft Teams-App. Debuggen ist der Prozess der Überprüfung, Erkennung und Behebung von Problemen oder Fehlern, um sicherzustellen, dass das Programm in Teams erfolgreich ausgeführt wird.

::: zone pivot="visual-studio-code"

## <a name="debug-your-teams-app-for-visual-studio-code"></a>Debuggen Ihrer Teams-App für Visual Studio Code

Teams Toolkit in Microsoft Visual Studio Code automatisiert den Debugprozess. Sie können Fehler erkennen und beheben sowie eine Vorschau der Teams-App anzeigen. Sie können auch Debugeinstellungen anpassen, um Ihre Registerkarte oder Ihren Bot zu erstellen.

## <a name="debug-your-microsoft-teams-app-for-visual-studio-code"></a>Debuggen Ihrer Microsoft Teams-App für Visual Studio Code

Das Teams-Toolkit in Visual Studio Code automatisiert den Debugprozess. Sie können Fehler erkennen und beheben sowie eine Vorschau der Teams-App anzeigen. Sie können auch Debugeinstellungen anpassen, um Ihre Registerkarte oder Ihren Bot zu erstellen.

Während des Debugvorgangs:

* Teams Toolkit startet automatisch App-Dienste, startet Debugger und lädt die Teams-App quer.
* Das Teams-Toolkit überprüft die Voraussetzungen während des Debughintergrundprozesses.
* Ihre Teams-App steht nach dem Debuggen lokal im Teams-Webclient als Vorschau zur Verfügung.
* Sie können ebenfalls Debugeinstellungen anpassen, um Ihre Botendpunkte, Ihr Entwicklungszertifikat, oder Ihre Teilkomponente zum Laden Ihrer konfigurierten App zu verwenden.
* Microsoft Visual Studio Code ermöglicht Ihnen das Debuggen von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions.

## <a name="key-debug-features-of-teams-toolkit"></a>Wichtige Debugfeatures des Teams-Toolkits

Das Teams-Toolkit unterstützt die folgenden Debugfeatures:

* [Debugging starten](#start-debugging)
* [Debuggen mit mehreren Zielen](#multi-target-debugging)
* [Umschalthaltepunkte](#toggle-breakpoints)
* [Hot Reload](#hot-reload)
* [Debuggen beenden](#stop-debugging)

Das Teams-Toolkit führt während des Debugprozesses Hintergrundfunktionen aus, einschließlich der Überprüfung der für das Debuggen erforderlichen Voraussetzungen. Sie können den Fortschritt des Überprüfungsprozesses im Ausgabekanal von Teams Toolkit anzeigen. Im Setupprozess können Sie Ihre Teams-App registrieren und konfigurieren.

### <a name="start-debugging"></a>Debugging starten

Sie können **F5** als einzelnen Vorgang drücken, um das Debuggen zu starten. Das Teams-Toolkit beginnt mit der Überprüfung der Voraussetzungen, registriert die Azure AD-App, die Teams-App und den Bot und startet Dienste und den Browser.

### <a name="multi-target-debugging"></a>Debuggen mit mehreren Zielen

Teams Toolkit nutzt die Multi-Target-Debugging-Funktion zum gleichzeitigen Debuggen von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions.

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Sie können Haltepunkte in den Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions umschalten. Die Haltepunkte werden ausgeführt, wenn Sie in einem Webbrowser mit der Teams-App interagieren. Die folgende Abbildung zeigt den Haltepunkt umschalten:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="Umschalthaltepunkte" lightbox="../assets/images/teams-toolkit-v2/debug/toggle-points.png":::

### <a name="hot-reload"></a>Hot Reload

Sie können die Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions gleichzeitig beim Debuggen der Teams-App aktualisieren und speichern. Die App wird neu geladen, und der Debugger wird erneut an die Programmiersprachen angehängt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="hot-reload für Quellcodes" lightbox="../assets/images/teams-toolkit-v2/debug/hot-reload.png":::

### <a name="stop-debugging"></a>Debuggen beenden

Wenn Sie das lokale Debuggen abgeschlossen haben, können Sie **beenden (UMSCHALT+F5)** oder **[Alt] Trennen (UMSCHALT+F5)** auf der symbolleiste des unverankerten Debuggens auswählen, um alle Debugsitzungen zu beenden und Aufgaben zu beenden. Die folgende Abbildung zeigt die Aktion „Debuggen beenden“:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="Debuggen beenden":::

## <a name="prepare-for-debug"></a>Vorbereiten des Debugvorgangs

Die folgenden Schritte helfen Ihnen bei der Vorbereitung auf das Debuggen:

### <a name="sign-in-to-microsoft-365"></a>Bei Microsoft 365 anmelden

Wenn Sie sich bereits für Microsoft 365 registriert haben, melden Sie sich bei Microsoft 365 an. Weitere Informationen finden Sie unter [Microsoft 365-Entwicklerprogramm](tools-prerequisites.md#microsoft-365-developer-program).

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Stellen Sie sicher, dass Sie Haltepunkte für die Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions umschalten können. Weitere Informationen finden Sie unter [Umschalten von Haltepunkten](#toggle-breakpoints).

## <a name="customize-debug-settings"></a>Anpassen von Debugeinstellungen

Mit dem Teams-Toolkit können Sie die Debugeinstellungen anpassen, um Ihre Registerkarte oder Ihren Bot zu erstellen. Weitere Informationen zur vollständigen Liste der anpassbaren Optionen finden Sie in der [Dokumentation zu Debugeinstellungen](https://aka.ms/teamsfx-debug-tasks).

### <a name="customize-scenarios"></a>Anpassen von Szenarien

<br>

<details>

<summary><b>Überspringen von Voraussetzungsprüfungen</b></summary>

Aktualisieren `.fx/configs/tasks.json` Sie in unter`"prerequisites"``"Validate & install prerequisites"` > `"args"` >  die Voraussetzungsprüfungen, die Sie überspringen möchten.

  :::image type="content" source="../assets/images/teams-toolkit-v2/debug/skip-prerequisite-checks.png" alt-text="Überspringen der Voraussetzungsprüfungen":::

</details>

<details>
<summary><b>Verwenden des Entwicklungszertifikats</b></summary>

1. Deaktivieren `.fx/configs/tasks.json`Sie `"devCert"` in unter `"Validate & install prerequisites"``"prerequisites"` > `"args"` > .
1. Legen Sie "SSL_CRT_FILE" und "SSL_KEY_FILE" in `.env.teamsfx.local` auf Ihren Zertifikatdateipfad und Schlüsseldateipfad fest.

</details>

<details>
<summary><b>Anpassen von NPM-Installationsargumenten</b></summary>

Legen `.fx/configs/tasks.json`Sie in npmInstallArgs unter `"Install npm packages"`fest.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/customize-npm-install.png" alt-text="Installieren des npm-Pakets":::

</details>

<details>
<summary><b>Ändern von Ports</b></summary>

* Bot
  1. `"3978"` Suchen Sie im gesamten Projekt nach , und suchen Sie nach Darstellungen in `tasks.json`, `ngrok.yml` und `index.js`.
  1. Ersetzen Sie es durch Ihren Port.
     :::image type="content" source="../assets/images/teams-toolkit-v2/debug/modify-ports-bot.png" alt-text="Ersetzen Ihres Ports für bot":::
* Tab
  1. Suchen Sie in `.fx/configs/tasks.json`nach `"53000"`.
  1. Ersetzen Sie es durch Ihren Port.
     :::image type="content" source="../assets/images/teams-toolkit-v2/debug/modify-ports-tab.png" alt-text="Ersetzen Des Ports für Registerkarte":::

</details>

<details>
<summary><b>Verwenden Ihres eigenen App-Pakets</b></summary>

Legen `.fx/configs/tasks.json`Sie in unter `"Build & upload Teams manifest"` auf den Pfad Ihres App-Pakets fest`"appPackagePath"`.

  :::image type="content" source="../assets/images/teams-toolkit-v2/debug/app-package-path.png" alt-text="Verwenden Ihres eigenen App-Paketpfads":::

</details>

<details>
<summary><b>Verwenden Eines eigenen Tunnels</b></summary>

1. In `.fx/configs/tasks.json` können Sie unter `"Start Teams App Locally"`aktualisieren `"Start Local tunnel"`.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-local-tunnel.png" alt-text="Verwenden Eines eigenen Tunnels":::
1. Starten Sie Ihren eigenen Tunneldienst, und aktualisieren `"botMessagingEndpoint"` Sie dann unter auf `"Set up bot"`Ihren eigenen Nachrichtenendpunkt in `.fx/configs/tasks.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/set-up-bot.png" alt-text="Messagingendpunkt aktualisieren":::

</details>

<details>

<summary><b>Umgebungsvariablen hinzufügen</b></summary>

Sie können der `.env.teamsfx.local`Datei Umgebungsvariablen für Registerkarte, Bot, Nachrichtenerweiterung und Azure Functions hinzufügen. Das Teams-Toolkit lädt die Umgebungsvariablen, die Sie hinzugefügt haben, um Dienste während des lokalen Debuggens zu starten.

 > [!NOTE]
 > Stellen Sie sicher, dass Sie einen neuen lokalen Debugvorgang starten, nachdem Sie neue Umgebungsvariablen hinzugefügt haben, da die Umgebungsvariablen hot reload nicht unterstützen.

</details>

<details>
<summary><b>Teilkomponente debuggen</b></summary>

Teams Toolkit nutzt Visual Studio Code Multi-Target-Debugging zum gleichzeitigen Debuggen von Registerkarten, Bots, Nachrichtenerweiterungen und Azure-Funktionen. Sie können `.vscode/launch.json` und `.vscode/tasks.json` aktualisieren, um Teilkomponenten zu debuggen. Wenn Sie die Registerkarte nur in einer Registerkarte plus Bot mit Azure Functions Projekt debuggen möchten, führen Sie die folgenden Schritte aus:

1. Aktualisieren Sie `"Attach to Bot"` und `"Attach to Backend"` aus der Debugverbindung in `.vscode/launch.json`.

   ```json
   {
       "name": "Debug (Edge)",
        "configurations": [
           "Attach to Frontend (Edge)",
           // "Attach to Bot",
           // "Attach to Backend""
           ],
           "preLaunchTask": "Pre Debug Check & Start All",
           "presentation": {
               "group": "all",
               "order": 1
           },
           "stopAll": true

   }
   ```

2. Aktualisieren Sie `"Start Backend"` und `"Start Bot"` aus der Aufgabe Alle starten in .vscode/tasks.json.

   ```json
   {
                                           
       "label": "Start All",
       "dependsOn": [
           "Start Frontend",
             // "Start Backend",
             // "Start Bot"

         ]
              
   }
   ```

</details>

## <a name="next"></a>Weiter

> [!div class="nextstepaction"]
> [Lokales Debuggen Ihrer App](debug-local.md)

::: zone-end

::: zone pivot="visual-studio"

## <a name="debug-your-teams-app-using-visual-studio"></a>Debuggen Ihrer Teams-App mit Visual Studio

Teams Toolkit automatisiert App-Startdienste, initiiert das Debuggen und lädt die Teams-App quer. Nach dem Debuggen können Sie eine Vorschau der Teams-App im Teams-Webclient anzeigen. Sie können auch Debugeinstellungen anpassen, um Ihre Botendpunkte oder Umgebungsvariablen zum Laden Ihrer konfigurierten App zu verwenden. Visual Studio ermöglicht ihnen das Debuggen von Registerkarten, Bots und Nachrichtenerweiterungen. Während des Debugprozesses unterstützt das Teams-Toolkit die folgenden Debugfeatures:

* Vorbereiten von Teams-App-Abhängigkeiten
* Debugging starten
* Umschalthaltepunkte
* Hot Reload
* Debuggen beenden

## <a name="prerequisites"></a>Voraussetzungen

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022, Version 17.3 | Sie können die Enterprise Edition von Visual Studio und die Workload "ASP.NET" und Microsoft Teams-Entwicklungstools installieren. |
| &nbsp; | Teams Toolkit | Eine Visual Studio-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
| &nbsp; | [Vorbereiten Ihres Microsoft 365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |
| &nbsp; | [Microsoft 365-Entwicklerkonto](../concepts/build-and-test/prepare-your-o365-tenant.md) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |
| &nbsp; | Azure-Tools und [Microsoft Azure CLI](/cli/azure/install-azure-cli) | Azure-Tools für den Zugriff auf gespeicherte Daten oder die Bereitstellung eines cloudbasierten Back-Ends für Ihre Teams-App in Azure. |
|&nbsp;  | **Optional** | &nbsp; |
|&nbsp; |[Ngrok](https://ngrok.com/) | Ngrok wird verwendet, um externe Nachrichten von Azure Bot Framework an Ihren lokalen Computer weiterzuleiten.|

## <a name="key-features-of-teams-toolkit"></a>Wichtige Features des Teams-Toolkits

Sie können die folgenden wichtigsten Features des Teams-Toolkits sehen, die den lokalen Debugprozess Ihrer Teams-App automatisieren:

### <a name="prepare-teams-app-dependencies"></a>Vorbereiten von Teams-App-Abhängigkeiten

Teams Toolkit bereitet lokale Debugabhängigkeiten vor und registriert Ihre Teams-App im Mandanten in Ihrem Konto. Für Bot- und Nachrichtenerweiterungs-Apps registriert und konfiguriert das Teams Toolkit den Bot.

### <a name="start-debugging"></a>Debugging starten

Sie können das Debuggen mit einem einzelnen Vorgang ausführen, drücken Sie **F5** , um das Debuggen zu starten. Teams Toolkit erstellt Code, startet Dienste und startet die App in Ihrem Browser.

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Sie können Haltepunkte in den Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure-Funktionen umschalten. Die Haltepunkte werden ausgeführt, wenn Sie mit der Teams-App in Ihrem Webbrowser interagieren.
Die folgende Abbildung zeigt die Umschalthaltepunkte:

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png" alt-text="Breakpoints für lokales Debuggen" lightbox="../assets/images/debug-teams-app/vs-localdebug-toggle-breakpoint.png":::

### <a name="hot-reload"></a>Hot Reload

Wählen Sie **Hot Reload** aus, um Ihre Änderungen in Ihrer Teams-App anzuwenden, wenn Sie die Quellcodes während des Debuggens gleichzeitig aktualisieren und speichern möchten.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload.png" alt-text="Symbol &quot;Hot Reload&quot; auswählen":::

Wählen Sie in der Dropdownliste die Option **Hot Reload dateispeichern** aus, um automatisches Hot Reload zu aktivieren.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-hot-reload-filesave.png" alt-text="Auswählen von Hot Reload beim Speichern der Datei":::
  
   > [!Tip]
   > Weitere Informationen zu Hot Reload Funktion von Visual Studio während des Debuggens finden Sie unter <https://aka.ms/teamsfx-vs-hotreload>.

### <a name="stop-debugging"></a>Debuggen beenden

Wählen Sie **Debuggen beenden** aus, wenn das lokale Debuggen abgeschlossen ist.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Stopdebug.png" alt-text="Symbol &quot;Debug beenden&quot; auswählen":::

## <a name="customize-debug-settings"></a>Anpassen von Debugeinstellungen

Sie können die Debugeinstellung für Ihre Teams-App anpassen, um Ihre Botendpunkte zu verwenden und Umgebungsvariablen hinzuzufügen:

### <a name="use-your-bot-endpoint"></a>Verwenden Ihres Bot-Endpunkts

Sie können die siteEndpoint-Konfiguration in **.fx/configs/config.local.json** auf Ihren Endpunkt festlegen.

```
"bot": {
    "siteEndpoint": "https://baidu.com"
}
```

### <a name="add-environment-variables"></a>Umgebungsvariablen hinzufügen

Sie können **environmentVariables** zur Datei **launchSettings.json** hinzufügen.

:::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-environment-variables.png" alt-text="Hinzufügen benutzerdefinierter Umgebungsvariablen":::

### <a name="launch-teams-app-as-a-web-app"></a>Starten der Teams-App als Web-App

Sie können die Teams-App als Web-App starten, anstatt im Teams-Client auszuführen.

1. Wählen Sie **eigenschaften** > **launchSettings.json** in Projektmappen-Explorer Bereich unter Ihrem Projekt aus.
1. Entfernen Sie **"launchUrl"** aus der Datei.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png" alt-text="Starten von Teams als Web-App durch Entfernen von launchurl" lightbox="../assets/images/debug-teams-app/vs-localdebug-launch-teamsapp-webapp.png":::

1. Klicken Sie mit der rechten Maustaste auf **Projektmappe** , und wählen Sie **Eigenschaften** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png" alt-text="Klicken Sie mit der rechten Maustaste auf die Lösung, und wählen Sie Eigenschaften aus." lightbox="../assets/images/debug-teams-app/vs-localdebug-solution-properties.png":::

1. Wählen Sie im Dialogfeld **Konfigurationseigenschaften** > **Konfiguration** aus.
1. Deaktivieren Sie das Kontrollkästchen **Bereitstellen** .
1. Wählen Sie **OK** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png" alt-text="Deaktivieren der Bereitstellung in Konfigurationseigenschaften" lightbox="../assets/images/debug-teams-app/vs-localdebug-disable-deploy.png":::

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Debuggen von Hintergrundprozessen](debug-background-process.md)
* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Vorschau und Anpassen des Teams-App-Manifests](TeamsFx-preview-and-customize-app-manifest.md)
