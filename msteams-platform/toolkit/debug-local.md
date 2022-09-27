---
title: Lokales Debuggen Ihrer Teams-App
author: surbhigupta
description: In diesem Modul lernen Sie, wie Sie Ihre Teams-App lokal im Teams-Toolkit und wichtige Features des Teams-Toolkits debuggen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 24d231ef7a76ede1d45176d5869caa9a76a791be
ms.sourcegitcommit: c1032ea4f48c4bbf5446798ff7d46d7e6e9f55d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68026962"
---
# <a name="debug-your-teams-app-locally"></a>Lokales Debuggen Ihrer Teams-App

Mit dem Teams-Toolkit können Sie Ihre Microsoft Teams-App lokal debuggen und eine Vorschau anzeigen. Während des Debugprozesses startet das Teams-Toolkit automatisch App-Dienste, startet Debugger und lädt die Teams-App quer. Sie können eine Vorschau Ihrer Teams-App im Teams-Webclient lokal nach dem Debuggen anzeigen.

::: zone pivot="visual-studio-code"

## <a name="debug-your-microsoft-teams-app-locally-for-visual-studio-code"></a>Lokales Debuggen Ihrer Microsoft Teams-App für Visual Studio Code

Das Teams-Toolkit in Visual Studio Code bietet Ihnen die Funktionen, um das Debuggen Ihrer Teams-App lokal zu automatisieren. Mit Visual Studio können Sie Registerkarten-, Bot- und Nachrichtenerweiterungen debuggen. Sie müssen das Teams-Toolkit einrichten, bevor Sie Ihre App debuggen.

## <a name="set-up-your-teams-toolkit-for-debugging"></a>Einrichten Ihres Teams-Toolkits für das Debuggen

Die folgenden Schritte helfen Ihnen beim Einrichten Ihres Teams-Toolkits, bevor Sie den Debugprozess initiieren:

# <a name="windows"></a>[Windows](#tab/Windows)

1. Wählen Sie **debuggen (Edge)** oder **Debuggen (Chrome)** in der Aktivitätsleiste aus der Dropdownliste **AUSFÜHREN UND DEBUGgen aus** .

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Browseroption":::

1. Wählen Sie **"Startdebugging ausführen** > " (F5) aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Debugging starten":::

3. Wählen Sie **Anmelden** bei Ihrem Microsoft 365-Konto aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Anmelden":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Microsoft 365-Entwicklerprogramm zu erfahren. Ihr Standardwebbrowser wird geöffnet, damit Sie sich mit Ihren Anmeldeinformationen bei Ihrem Microsoft 365-Konto anmelden können.

4. Wählen Sie **Installieren** aus, um das Entwicklungszertifikat für localhost zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Zertifikat":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Entwicklungszertifikat zu erfahren.

5. Wählen Sie im Angezeigten Dialogfeld **"Sicherheitswarnung**" die Option **"Ja**" aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="Zertifizierungsstelle":::

Das Toolkit startet entsprechend Ihrer Auswahl eine neue Edge- oder Chrome-Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.  

# <a name="macos"></a>[macOS](#tab/macOS)

1. Wählen Sie **Debug Edge** oder **Debug Chrome** aus der Dropdownliste **AUSFÜHREN UND DEBUGgen aus** .

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Browserlisten":::

1. Wählen Sie **Debuggen starten (F5)** oder  **Ausführen** aus, um Ihre Teams-App im Debugmodus auszuführen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Debuggen Ihrer App":::

3. Wählen Sie **Anmelden** bei Ihrem Microsoft 365-Konto aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Anmelden beim M365-Konto":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Microsoft 365-Entwicklerprogramm zu erfahren. Ihr Standardwebbrowser wird geöffnet, damit Sie sich mit Ihren Anmeldeinformationen bei Ihrem Microsoft 365-Konto anmelden können.

4. Wählen Sie **Installieren** aus, um das Entwicklungszertifikat für localhost zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Zertifikat":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Entwicklungszertifikat zu erfahren.

5. Geben Sie Ihren **Benutzernamen** und **Ihr Kennwort** ein, und wählen Sie " **Einstellungen aktualisieren"** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="Mac-Anmeldung":::

Das Teams-Toolkit startet Ihre Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.

---

## <a name="debug-your-app"></a>Debuggen Ihrer App

Nach dem anfänglichen Einrichtungsprozess startet das Teams-Toolkit die folgenden Prozesse:

* [Startet App-Dienste](#starts-app-services)
* [Startet Debugkonfigurationen](#launches-debug-configurations)
* [Lädt die Teams-App quer](#sideloads-the-teams-app)

### <a name="starts-app-services"></a>Startet App-Dienste

Führt Aufgaben wie in definiert aus `.vscode/tasks.json`.

|  Komponente |  Aufgabenname  | Ordner |
| --- | --- | --- |
|  Tab |  **Front-End starten** |  Registerkarten |
|  Bot- oder Nachrichtenerweiterungen |  **Bot starten** |  Bot |
|  Azure Functions |  **Back-End starten** |  API |

In der folgenden Abbildung werden aufgabennamen auf den Registerkarten **OUTPUT** und **TERMINAL** des Visual Studio Code angezeigt, während registerkarte, Bot oder Nachrichtenerweiterung ausgeführt wird, und Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal.png" alt-text="Startet App-Dienste":::

### <a name="launches-debug-configurations"></a>Startet Debugkonfigurationen

Startet die Debugkonfigurationen gemäß definition in `.vscode/launch.json`.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Debugger starten":::

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für Das Projekt mit Registerkarten-, Bot- oder Nachrichtenerweiterungs-App sowie Azure Functions aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp |
| --- | --- | --- |
|  Tab |  **An Front-End (Edge) anfügen** oder  **An Front-End (Chrome) anfügen**  |  pwa-msedge oder pwa-chrome  |
|  Bot- oder Nachrichtenerweiterungen |   **An Bot anfügen** |  pwa-node |
| Azure Functions |   **An Back-End anfügen** |  pwa-node |

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für Das Projekt mit Bot-App, Azure Functions und ohne Registerkarten-App aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp  |
| --- | --- | --- |
|  Bot- oder Nachrichtenerweiterung  | **Bot starten (Edge)** oder  **Bot starten (Chrome)**  |   pwa-msedge oder pwa-chrome  |
|  Bot- oder Nachrichtenerweiterung  |   **An Bot anfügen** |  pwa-node  |
|  Azure Functions |  **An Back-End anfügen** |  pwa-node |

### <a name="sideloads-the-teams-app"></a>Lädt die Teams-App quer

Die Konfiguration **"An Frontend anfügen** " oder **"Bot starten** " startet eine Edge- oder Chrome-Browserinstanz, um den Teams-Client auf der Webseite zu laden. Nachdem der Teams-Client geladen wurde, lädt Teams die Teams-App quer, die durch die in den Startkonfigurationen von [Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}) definierte Querladen-URL gesteuert wird. Wenn der Teams-Client im Webbrowser geladen wird, wählen Sie gemäß Ihrer Anforderung **"Hinzufügen"** aus, oder wählen Sie eine Option aus der Dropdownliste aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="Hinzufügen des lokalen Debuggens" lightbox="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png":::

   Ihre App wird Teams hinzugefügt!

## <a name="next"></a>Weiter

> [!div class="nextstepaction"]
> [Debuggen von Hintergrundprozessen](debug-background-process.md)

::: zone-end

::: zone pivot="visual-studio"

## <a name="debug-your-teams-app-locally-using-visual-studio"></a>Lokales Debuggen Ihrer Teams-App mit Visual Studio

Mit dem Teams-Toolkit können Sie Ihre Microsoft Teams-App lokal debuggen und eine Vorschau anzeigen. Mit Visual Studio können Sie Registerkarten-, Bot- und Nachrichtenerweiterungen debuggen. Sie können Ihre App lokal in Visual Studio mithilfe des Teams-Toolkits debuggen, indem Sie Folgendes ausführen:

### <a name="set-up-ngrok-only-for-bot-and-message-extension-app"></a>Einrichten von ngrok (nur für Bot- und Nachrichtenerweiterungs-App)

Verwenden Sie eine Eingabeaufforderung, um diesen Befehl auszuführen:

```
ngrok http 5130
```

### <a name="set-up-your-teams-toolkit"></a>Einrichten des Teams-Toolkits

Führen Sie die folgenden Schritte mithilfe des Teams-Toolkits aus, um Ihre App nach dem Erstellen eines Projekts zu debuggen:

1. Klicken Sie mit der rechten Maustaste auf Ihr **Projekt**.
1. Wählen Sie **"Teams-Toolkit** > **vorbereiten Teams-App-Abhängigkeiten" aus**.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png" alt-text="Abhängigkeiten von Teams-Apps für das lokale Debuggen" lightbox="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname "MyTeamsApp1"

   Ihr Microsoft 365-Konto muss über die Berechtigung zum Querladen verfügen, bevor Sie sich anmelden.  Stellen Sie sicher, dass Ihre Teams-App in den Mandanten hochgeladen werden kann, andernfalls kann Ihre Teams-App im Teams-Client nicht ausgeführt werden.

1. Melden Sie sich bei Ihrem **Microsoft 365-Konto** an, und wählen Sie dann **"Weiter"** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-signin-m365.png" alt-text="Anmelden beim Microsoft 365-Konto":::

   > [!Note]
   > Weitere Informationen zum Querladen von Berechtigungen finden Sie unter <https://aka.ms/teamsfx-sideloading-option>.

1. Wählen Sie **"Debuggen** > **starten"** oder direkt **F5** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Startdebug.png" alt-text="Debuggen starten":::

   Visual Studio startet die Teams-App innerhalb des Microsoft Teams-Clients in Ihrem Browser.

   > [!Note]
   > Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-debug>.

1. Nachdem Microsoft Teams geladen wurde, wählen Sie **"Hinzufügen"** aus, um Ihre App in Teams zu installieren.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-add-loadapp.png" alt-text="Wählen Sie &quot;App hinzufügen&quot; aus, um die App zu laden.":::

   > [!TIP]
   > Sie können die Hot Reload-Funktion von Visual Studio auch während des Debuggens verwenden. Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-hotreload>.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie beim Debuggen der Benachrichtigungs-Bot-App eine HTTP-Anforderung an "<http://localhost:5130/api/notification>" posten, um eine Benachrichtigung auszulösen. Wenn Sie beim Erstellen des Projekts den HTTP-Trigger ausgewählt haben, können Sie alle API-Tools wie curl (Windows-Eingabeaufforderung), Postman usw. verwenden.

   > [!TIP]
   > Wenn Sie Änderungen an der Teams-App-Manifestdatei (/templates/appPackage/manifest.template.json) vornehmen, stellen Sie sicher, dass Sie den Befehl "Teams-App-Abhängigkeiten vorbereiten" ausführen. Bevor Sie versuchen, die Teams-App erneut lokal auszuführen.

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen von Funktionen zu ihrer Teams-App](add-capability.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen im Teams-Toolkit](TeamsFx-multi-env.md)
