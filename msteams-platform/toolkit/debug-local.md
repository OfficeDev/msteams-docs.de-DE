---
title: Debuggen Sie Ihre Teams-App
description: Debuggen Sie Ihre Teams-App lokal im Teams-Toolkit
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: 25a851f0dcc956139551a46b713dc2e7df3f626d
ms.sourcegitcommit: 5e5d2d3fb621bcbd9d792a5b450f95167ec8548b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2022
ms.locfileid: "63731862"
---
# <a name="debug-your-teams-app-locally"></a>Lokales Debuggen Ihrer Teams-App

Das Teams-Toolkit hilft Ihnen, Ihre Teams-App lokal zu debuggen und eine Vorschau anzuzeigen. Debuggen ist der Prozess der Überprüfung, Erkennung und Behebung von Problemen oder Fehlern, um sicherzustellen, dass das Programm erfolgreich ausgeführt wird. Mit Visual Studio Code können Sie Registerkarten, Bots, Messaging-Erweiterungen und Azure Functions debuggen. Das Teams-Toolkit unterstützt die folgenden Debugfeatures:

* [Debugging starten](#start-debugging)
* [Debuggen mit mehreren Zielen](#multi-target-debugging)
* [Umschalthaltepunkte](#toggle-breakpoints)
* [Hot Reload](#hot-reload)
* [Debuggen beenden](#stop-debugging)  


Während des Debugvorgangs startet das Teams-Toolkit automatisch App-Dienste, startet Debugger und lädt die Teams-App quer. Die Teams-App steht nach dem Debuggen lokal im Teams-Webclient zur Vorschau zur Verfügung. Sie können ebenfalls Debugeinstellungen anpassen, um Ihre Botendpunkte, Ihr Entwicklungszertifikat, oder Ihre Teilkomponente zum Laden Ihrer konfigurierten App zu verwenden.

## <a name="prerequisite"></a>Voraussetzungen

Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="key-features-of-teams-toolkit"></a>Wichtige Features des Teams-Toolkits

#### <a name="start-debugging"></a>Debugging starten

Sie können einen einzelnen Vorgang ausführen, wählen Sie **F5**, um mit dem Debuggen zu beginnen. Das Teams-Toolkit beginnt mit der Überprüfung der Voraussetzungen, der Registrierung der Azure Active Directory App, der Registrierung der Teams-App, dem Registrieren des Bots, dem Starten von Diensten und dem Starten des Browsers.

#### <a name="multi-target-debugging"></a>Debuggen mit mehreren Zielen

Das Teams-Toolkit verwendet das Debugfeature mit mehreren Zielen, um Registerkarten, Bots, Messagingerweiterungen und Azure Functions gleichzeitig zu debuggen.

#### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Sie können Haltepunkte in den Quellcodes von Registerkarten, Bots, Messagingerweiterungen und Azure Functions umschalten. Die Haltepunkte werden ausgeführt, wenn Sie in einem Webbrowser mit der Teams-App interagieren. Die folgende Abbildung zeigt die Umschalthaltepunkte:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="Umschalthaltepunkte":::

#### <a name="hot-reload"></a>Hot Reload

Sie können die Quellcodes der Registerkarte, des Bots, der Messagingerweiterung und von Azure Functions gleichzeitig aktualisieren und speichern, wenn Sie die Teams-App debuggen. Die App wird neu geladen, und der Debugger wird erneut an die Programmiersprachen angehängt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="hot-reload für Quellcodes":::

#### <a name="stop-debugging"></a>Debuggen beenden

Wenn Sie das lokale Debuggen abgeschlossen haben, können Sie auf der unverankerten Debugsymbolleiste **Beenden** oder **Trennen** auswählen, um alle Debugsitzungen zu beenden und Aufgaben zu beenden. Die folgende Abbildung zeigt die Aktion „Debuggen beenden“:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="Debuggen beenden":::

## <a name="debug-your-teams-app-locally"></a>Lokales Debuggen Ihrer Teams-App

#### <a name="1-set-up-your-teams-toolkit"></a>1. Einrichten des Teams-Toolkits

Führen Sie die folgenden Schritte aus, um Ihre App nach dem Erstellen einer neuen App mithilfe des Teams-Toolkits zu debuggen:

<br>

<details>
<summary><b>Windows</b></summary>

1. Wählen Sie **Edge debuggen** oder **Chrome debuggen** aus der **Ausführen und Debuggen** in der Aktivitätsleiste aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Browseroption" border="false":::

1. Wählen Sie **Debuggen starten (F5)** oder  **Ausführen** aus, um Ihre Teams-App im Debugmodus auszuführen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Debugging starten" border="false":::

3. Wählen Sie **Anmelden** bei Ihrem Microsoft 365-Konto aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Anmelden" border="true":::


   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Microsoft 365-Entwicklerprogramm zu erfahren. Ihr Standardwebbrowser wird geöffnet, damit Sie sich mit Ihren Anmeldeinformationen bei Ihrem Microsoft 365-Konto anmelden können.

4. Wählen Sie **Installieren** aus, um das Entwicklungszertifikat für localhost zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Zertifikat" border="true":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Entwicklungszertifikat zu erfahren.

5. Wählen Sie **Ja** aus, wenn das folgende Dialogfenster angezeigt wird:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="Zertifizierungsstelle" border="true":::

Das Toolkit startet je nach Auswahl eine neue Edge- oder Chrome-Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.  

</details>

<details>
<summary><b>macOS</b></summary>

1. Wählen Sie **Edge debuggen** oder **Chrome debuggen** aus der **Ausführen und Debuggen** in der Aktivitätsleiste aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Browserlisten" border="false":::

1. Wählen Sie **Debuggen starten (F5)** oder  **Ausführen** aus, um Ihre Teams-App im Debugmodus auszuführen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Debuggen Ihrer App" border="false":::

3. Wählen Sie **Anmelden** bei Ihrem Microsoft 365-Konto aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Anmelden beim M365-Konto" border="true":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Microsoft 365-Entwicklerprogramm zu erfahren. Ihr Standardwebbrowser wird geöffnet, damit Sie sich mit Ihren Anmeldeinformationen bei Ihrem Microsoft 365-Konto anmelden können.

4. Wählen Sie **Installieren** aus, um das Entwicklungszertifikat für localhost zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Zertifikat" border="true":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Entwicklungszertifikat zu erfahren.

5. Geben Sie Ihren **Benutzernamen** und **Kennwort** ein, und wählen Sie dann im folgenden Dialogfeld **Updateeinstellungen** aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="Mac-Anmeldung" border="true":::

Das Toolkit startet je nach Auswahl eine neue Edge- oder Chrome-Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients. 

</details>


#### <a name="2-debug-your-app"></a>2. Debuggen Ihrer App 

Nach dem anfänglichen Einrichtungsprozess startet das Teams-Toolkit die folgenden Prozesse:

  a. [Startet App-Dienste](#starts-app-services) </br>
  b. [Startet Debugger](#launches-debuggers)   </br>
  c. [Lädt die Teams-App quer](#sideloads-the-teams-app)
        
#### <a name="starts-app-services"></a>Startet App-Dienste

Führt die in `.vscode/tasks.json` definierten Aufgaben wie folgt aus:

|  Komponente |  Aufgabenname  | Ordner |
| --- | --- | --- |
|  Tab |  **Front-End starten** |  Registerkarten |
|  Bot- oder Messagingerweiterungen |  **Bot starten** |  Bot |
|  Azure Functions |  **Back-End starten** |  api |

In der folgenden Abbildung werden die Aufgabennamen auf der Registerkarte **Ausgabe****Terminal** des Visual Studio Code angezeigt, während die Registerkarte, der Bot oder die Messagingerweiterung ausgeführt wird, und Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal.png" alt-text="Startet App-Dienste":::

#### <a name="launches-debuggers"></a>Startet Debugger

Startet die in `.vscode/launch.json` definierten Debugkonfigurationen wie folgt:

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Debugger starten":::

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für das Projekt mit der Registerkarten-App und der Bot-App aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp |
| --- | --- | --- |
|  Tab |  **An Front-End (Edge) anfügen** oder  **An Front-End (Chrome) anfügen**  |  pwa-msedge oder pwa-chrome  |
|  Bot- oder Messagingerweiterungen |   **An Bot anfügen** |  pwa-node |
| Azure Functions |   **An Back-End anfügen** |  pwa-node |

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für das Projekt mit der Bot-App und ohne Registerkarte aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp  |
| --- | --- | --- |
|  Bot- oder Messagingerweiterung  | **Bot starten (Edge)** oder  **Bot starten (Chrome)**  |   pwa-msedge oder pwa-chrome  |
|  Bot- oder Messagingerweiterung  |   **An Bot anfügen** |  pwa-node  |
|  Azure Functions |  **An Back-End anfügen** |  pwa-node |

#### <a name="sideloads-the-teams-app"></a>Lädt die Teams-App quer

Die Konfiguration **Front-End anfügen** oder **Bot starten** startet eine neue Edge- oder Chrome-Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients. Nachdem der Teams-Client geladen wurde, lädt Teams die Teams-App quer, die von der in den Startkonfigurationen [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint})definierte Sideload-URL gesteuert wird.  Wenn der Teams-Client im Webbrowser geladen wird, wählen Sie **Hinzufügen** aus, oder wählen Sie einen aus der Dropdownliste gemäß Ihren Anforderungen aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="Lokales Debuggen" border="true":::

   Ihre App wird Teams hinzugefügt!

## <a name="customize-debug-settings"></a>Anpassen von Debugeinstellungen

Mit dem Teams-Toolkit können Sie die Debugeinstellungen anpassen, um Ihre Registerkarte oder Ihren Bot zu erstellen, indem Sie einige Voraussetzungen deaktivieren:

<br>

<details>
<summary><b>Verwenden Ihres Bot-Endpunkts</b></summary>

1. Deaktivieren Sie in Visual Studio Code Einstellungen **Stellen Sie sicher, dass Ngrok installiert und gestartet (ngrok) ist**.

1. Legen Sie die Konfiguration von „botDomain“ und „botEndpoint“ in `.fx/configs/localSettings.json` für Ihre Domäne und Ihren Endpunkt fest.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/bot-endpoint.png" alt-text="Anpassen des Bot-Endpunkts":::

</details>

<details>
<summary><b>Verwenden des Entwicklungszertifikats</b></summary>

1. Deaktivieren Sie in Visual Studio Code Einstellungen **Stellen Sie sicher, dass das Entwicklungszertifikat vertrauenswürdig ist (devCert)**.

1. Legen Sie die Konfiguration „SslCertFile“ und „sslKeyFile“ in `.fx/configs/localSettings.json` für den Zertifikatdateipfad und den Schlüsseldateipfad fest.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate-customize.png" alt-text="Anpassen des Zertifikats":::

</details>

<details>
<summary><b>Verwenden Sie Ihre Startskripts, um App Services zu starten</b></summary>

1. Aktualisieren Sie für Registerkarten das `dev:teamsfx`-Skript in `tabs/package.json`.

1. Aktualisieren Sie für Bot- oder Messagingerweiterungen das `dev:teamsfx`-Skript in `bot/package.json`.

1. Aktualisieren Sie für Azure Functions das `dev:teamsfx`-Skript in `api/package.json` und für TypeScript das `watch:teamsfx`-Skript.

   > [!NOTE]
   > Derzeit unterstützen die Registerkarte, der Bot, die Messagingerweiterungs-Apps und Azure Functions Ports keine Anpassung.

</details>

<details>
<summary><b>Umgebungsvariablen hinzufügen</b></summary>

Sie können der `.env.teamsfx.local`-Datei Umgebungsvariablen für die Registerkarte, den Bot, die Messagingerweiterung und Azure Functions hinzufügen. Das Teams-Toolkit lädt die Umgebungsvariablen, die Sie hinzugefügt haben, um Dienste während des lokalen Debuggens zu starten.

 > [!NOTE]
 > Starten Sie nach dem Hinzufügen neuer Umgebungsvariablen ein neues lokales Debuggen, da Hot Reload von den Umgebungsvariablen nicht unterstützt wird.

</details>

<details>
<summary><b>Teilkomponente debuggen</b></summary>


Das Teams-Toolkit verwendet das Visual Studio Code-Debuggen mit mehreren Zielen, um Registerkarten, Bots, Messagingerweiterungen und Azure Functions gleichzeitig zu debuggen. Sie können `.vscode/launch.json` und `.vscode/tasks.json` aktualisieren, um Teilkomponenten zu debuggen. Wenn Sie die Registerkarte nur in einer Registerkarte plus Bot mit Azure Functions Projekt debuggen möchten, führen Sie die folgenden Schritte aus:

1. Kommentieren Sie **An Bot anfügen** und **An Back-End anfügen** aus der Debugverbindung in `.vscode/launch.json`

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

2. Kommentieren **Back-End starten** und "Bot starten" aus "Alle Aufgaben starten" in ".vscode/tasks.json".

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


## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Debuggen von Hintergrundprozessen](debug-background-process.md).

## <a name="see-also"></a>Siehe auch

* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen von Funktionen zu ihrer Teams-App](add-capability.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen im Teams-Toolkit](TeamsFx-multi-env.md)
