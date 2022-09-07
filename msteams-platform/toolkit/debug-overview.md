---
title: Debuggen Sie Ihre Teams-App
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Ihre Teams-App im Teams-Toolkit und die wichtigsten Features des Teams-Toolkits debuggen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
ms.openlocfilehash: 8545d4bbd97a6a4c5065c279368505f18dd5a14a
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617141"
---
# <a name="debug-your-microsoft-teams-app"></a>Debuggen Ihrer Microsoft Teams-App

Mit dem Microsoft Teams-Toolkit können Sie Ihre Teams-App debuggen und eine Vorschau anzeigen. Debuggen ist der Prozess des Überprüfens, Erkennens und Behebens von Problemen oder Fehlern, um sicherzustellen, dass das Programm in Teams erfolgreich ausgeführt wird.

Während des Debugprozesses:

* Das Teams-Toolkit startet automatisch App-Dienste, startet Debugger und lädt die Teams-App quer.
* Das Teams-Toolkit überprüft die Voraussetzungen während des Debug-Hintergrundprozesses.
* Ihre Teams-App steht nach dem Debuggen lokal im Teams-Webclient zur Vorschau zur Verfügung.
* Sie können ebenfalls Debugeinstellungen anpassen, um Ihre Botendpunkte, Ihr Entwicklungszertifikat, oder Ihre Teilkomponente zum Laden Ihrer konfigurierten App zu verwenden.
* Mit Microsoft Visual Studio Code können Sie Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions debuggen.

## <a name="key-debug-features-of-teams-toolkit"></a>Wichtige Debugfeatures des Teams-Toolkits

Das Teams-Toolkit unterstützt die folgenden Debugfeatures:

* [Debugging starten](#start-debugging)
* [Debuggen mit mehreren Zielen](#multi-target-debugging)
* [Umschalthaltepunkte](#toggle-breakpoints)
* [Hot Reload](#hot-reload)
* [Debuggen beenden](#stop-debugging)

Das Teams-Toolkit führt während des Debugprozesses Hintergrundfunktionen aus, einschließlich der Überprüfung der für das Debuggen erforderlichen Voraussetzungen. Sie können den Fortschritt des Überprüfungsprozesses im Ausgabekanal des Teams-Toolkits sehen. Im Setupprozess können Sie Ihre Teams-App registrieren und konfigurieren.

### <a name="start-debugging"></a>Debugging starten

Sie können **F5** als einzelnen Vorgang drücken, um das Debuggen zu starten. Das Teams-Toolkit beginnt mit der Überprüfung der Voraussetzungen, registriert die Azure AD-App, die Teams-App und den Bot und startet Dienste und den Browser.

### <a name="multi-target-debugging"></a>Debuggen mit mehreren Zielen

Teams Toolkit nutzt die Multi-Target-Debugging-Funktion zum gleichzeitigen Debuggen von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions.

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Sie können Haltepunkte in den Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions umschalten. Die Haltepunkte werden ausgeführt, wenn Sie in einem Webbrowser mit der Teams-App interagieren. Die folgende Abbildung zeigt den Umschalter:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/toggle-points.png" alt-text="Umschalthaltepunkte" lightbox="../assets/images/teams-toolkit-v2/debug/toggle-points.png":::

### <a name="hot-reload"></a>Hot Reload

Sie können die Quellcodes von Registerkarte, Bot, Nachrichtenerweiterung und Azure Functions gleichzeitig aktualisieren und speichern, wenn Sie die Teams-App debuggen. Die App wird neu geladen, und der Debugger wird erneut an die Programmiersprachen angehängt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hot-reload.png" alt-text="hot-reload für Quellcodes" lightbox="../assets/images/teams-toolkit-v2/debug/hot-reload.png":::

### <a name="stop-debugging"></a>Debuggen beenden

Wenn Sie das lokale Debuggen abgeschlossen haben, können Sie in der unverankerten Debugsymbolleiste **"Beenden" (UMSCHALT+F5)** oder **"[ALT] Trennen" (UMSCHALT+F5)** auswählen, um alle Debugsitzungen zu beenden und Aufgaben zu beenden. Die folgende Abbildung zeigt die Aktion „Debuggen beenden“:

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/stop-debug.png" alt-text="Debuggen beenden":::

## <a name="prepare-for-debug"></a>Vorbereiten des Debuggens

Die folgenden Schritte helfen Ihnen bei der Vorbereitung auf das Debuggen:

### <a name="sign-in-to-microsoft-365"></a>Bei Microsoft 365 anmelden

Wenn Sie sich bereits für Microsoft 365 registriert haben, melden Sie sich bei Microsoft 365 an. Weitere Informationen finden Sie unter [Microsoft 365-Entwicklerprogramm](tools-prerequisites.md#microsoft-365-developer-program)

### <a name="toggle-breakpoints"></a>Umschalthaltepunkte

Stellen Sie sicher, dass Sie Haltepunkte in den Quellcodes von Registerkarten, Bots, Nachrichtenerweiterungen und Azure Functions umschalten können. Weitere Informationen finden Sie unter [Umschalten von Haltepunkten](#toggle-breakpoints)

## <a name="customize-debug-settings"></a>Anpassen von Debugeinstellungen

Das Teams-Toolkit deaktiviert einige Voraussetzungen und ermöglicht es Ihnen, die Debugeinstellungen anzupassen, um Ihre Registerkarte oder Ihren Bot zu erstellen:

<br>

<details>
<summary><b>Verwenden Ihres Bot-Endpunkts</b></summary>

1. In den Visual Studio Code-Einstellungen müssen Sie sicherstellen, **dass Ngrok installiert und gestartet ist (ngrok)**.

1. Sie können die Konfiguration auf `.fx/configs/config.local.json` Ihren Endpunkt festlegen`siteEndpoint`.

```json
{
    "bot": {
        "siteEndpoint": "https://your-bot-tunneling-url"
    }
}

```

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/bot-endpoint.png" alt-text="Anpassen des Bot-Endpunkts":::

</details>

<details>
<summary><b>Verwenden des Entwicklungszertifikats</b></summary>

1. In den Visual Studio Code-Einstellungen müssen Sie das Kontrollkästchen **Sicherstellen, dass das Entwicklungszertifikat vertrauenswürdig ist (devCert)** deaktivieren.

1. Sie können ihren Zertifikatdateipfad und den Schlüsseldateipfad festlegen `sslCertFile` und `sslKeyFile` konfigurieren `.fx/configs/config.local.json` .

```json
{
    "frontend": {
        "sslCertFile": "",
        "sslKeyFile": ""
    }
}
```

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate-customize.png" alt-text="Anpassen des Zertifikats":::

</details>

<details>
<summary><b>Verwenden Sie Ihre Startskripts, um App Services zu starten</b></summary>

1. Für die Registerkarte müssen Sie das Skript in `tabs/package.json`aktualisieren`dev:teamsfx`.

1. Für Bot- oder Nachrichtenerweiterungen müssen Sie das Skript in `bot/package.json`aktualisieren`dev:teamsfx`.

1. Für Azure Functions müssen Sie das Skript in `api/package.json` und für das TypeScript-Updateskript `watch:teamsfx` aktualisieren`dev:teamsfx`.

   > [!NOTE]
   > Derzeit unterstützen die Tab-, Bot- und Nachrichtenerweiterungs-Apps sowie die Azure Functions-Ports keine Anpassungen.

</details>

<details>
<summary><b>Umgebungsvariablen hinzufügen</b></summary>

Sie können der `.env.teamsfx.local`Datei Umgebungsvariablen für Registerkarte, Bot, Nachrichtenerweiterung und Azure Functions hinzufügen. Das Teams-Toolkit lädt die Umgebungsvariablen, die Sie hinzugefügt haben, um Dienste während des lokalen Debuggens zu starten.

 > [!NOTE]
 > Starten Sie nach dem Hinzufügen neuer Umgebungsvariablen ein neues lokales Debuggen, da Hot Reload von den Umgebungsvariablen nicht unterstützt wird.

</details>

<details>
<summary><b>Teilkomponente debuggen</b></summary>

Teams Toolkit nutzt Visual Studio Code Multi-Target-Debugging zum gleichzeitigen Debuggen von Registerkarten, Bots, Nachrichtenerweiterungen und Azure-Funktionen. Sie können `.vscode/launch.json` und `.vscode/tasks.json` aktualisieren, um Teilkomponenten zu debuggen. Wenn Sie die Registerkarte nur in einer Registerkarte plus Bot mit Azure Functions Projekt debuggen möchten, führen Sie die folgenden Schritte aus:

1. Kommentar **`Attach to Bot`** und **`Attach to Backend`** aus Debugverbindung in `.vscode/launch.json`.

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

2. Kommentieren **`Start Backend`** Sie den Bot aus der Aufgabe "Alle starten" in ".vscode/tasks.json".

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

## <a name="see-also"></a>Siehe auch

* [Debuggen von Hintergrundprozessen](debug-background-process.md)
* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Vorschau und Anpassen des Teams-App-Manifests](TeamsFx-preview-and-customize-app-manifest.md)
