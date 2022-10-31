---
title: Lokales Debuggen Ihrer Teams-App
author: surbhigupta
description: In diesem Modul lernen Sie, wie Sie Ihre Teams-App lokal im Teams-Toolkit und wichtige Features des Teams-Toolkits debuggen.
ms.author: v-amprasad
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/21/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 65eb9599bb60b35448aaf1b6239fc155b7d397d5
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791573"
---
# <a name="debug-your-teams-app-locally"></a>Lokales Debuggen Ihrer Teams-App

Das Teams-Toolkit hilft Ihnen, Ihre Microsoft Teams-App lokal zu debuggen und eine Vorschau anzuzeigen. Während des Debugvorgangs startet Teams Toolkit automatisch App-Dienste, startet Debugger und lädt die Teams-App quer. Sie können Ihre Teams-App nach dem Debuggen lokal im Teams-Webclient anzeigen.

::: zone pivot="visual-studio-code"

## <a name="debug-your-microsoft-teams-app-locally-for-visual-studio-code"></a>Lokales Debuggen Ihrer Microsoft Teams-App für Visual Studio Code

Das Teams-Toolkit in Visual Studio Code bietet Ihnen die Features zum automatisieren des lokalen Debuggens Ihrer Teams-App. Visual Studio ermöglicht ihnen das Debuggen von Registerkarten, Bots und Nachrichtenerweiterungen. Sie müssen das Teams-Toolkit einrichten, bevor Sie Ihre App debuggen.

> [!NOTE]
>
> Sie können Ihr altes Teams Toolkit-Projekt aktualisieren, um neue Aufgaben zu verwenden. Weitere Informationen finden Sie in [der Dokumentation zu Debugeinstellungen](https://aka.ms/teamsfx-debug-upgrade-new-tasks).

## <a name="set-up-your-teams-toolkit-for-debugging"></a>Einrichten Ihres Teams-Toolkits für das Debuggen

Die folgenden Schritte helfen Ihnen beim Einrichten Ihres Teams Toolkits, bevor Sie den Debugprozess initiieren:

# <a name="windows"></a>[Windows](#tab/Windows)

1. Wählen Sie in der Aktivitätsleiste in der Dropdownliste **AUSFÜHREN UND DEBUGGEN die** Option **Debuggen (Edge)** oder **Debuggen (Chrome)** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/debug-run.png" alt-text="Browseroption":::

1. Wählen Sie **Debuggen starten ausführen** > **(F5)** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/start-debugging.png" alt-text="Debugging starten":::

3. Wählen Sie **Anmelden** bei Ihrem Microsoft 365-Konto aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/microsoft365-signin.png" alt-text="Anmelden":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Microsoft 365-Entwicklerprogramm zu erfahren. Ihr Standardwebbrowser wird geöffnet, damit Sie sich mit Ihren Anmeldeinformationen bei Ihrem Microsoft 365-Konto anmelden können.

4. Wählen Sie **Installieren** aus, um das Entwicklungszertifikat für localhost zu installieren.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/install-certificate.png" alt-text="Zertifikat":::

   > [!TIP]
   > Sie können **Weitere Informationen** auswählen, um mehr über das Entwicklungszertifikat zu erfahren.

5. Wählen Sie **Ja** aus, im Dialogfeld **Sicherheitswarnung** wird angezeigt:

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/development-certificate.png" alt-text="Zertifizierungsstelle":::

Das Toolkit startet entsprechend Ihrer Auswahl eine neue Edge- oder Chrome-Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.  

# <a name="macos"></a>[macOS](#tab/macOS)

1. Wählen Sie in der Dropdownliste **AUSFÜHREN UND DEBUGGEN die** Option Debug **Edge** oder **Debug Chrome debuggen** aus.

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

5. Geben Sie Ihren **Benutzernamen** und **Ihr Kennwort** ein, und wählen Sie dann **Einstellungen aktualisieren** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/debug/mac-settings.png" alt-text="Mac-Anmeldung":::

Teams Toolkit startet Ihre Browserinstanz und öffnet eine Webseite zum Laden des Teams-Clients.

---

## <a name="debug-your-app"></a>Debuggen Ihrer App

Nach der ersten Einrichtung startet Teams Toolkit die folgenden Prozesse:

* [Startet App-Dienste](#starts-app-services)
* [Startet Debugkonfigurationen](#launches-debug-configurations)
* [Lädt die Teams-App quer](#sideloads-the-teams-app)

### <a name="starts-app-services"></a>Startet App-Dienste

Führt Tasks wie in definiert aus `.vscode/tasks.json`.

|  Komponente |  Aufgabenname  | Ordner |
| --- | --- | --- |
|  Tab |  **Front-End starten** |  Registerkarten |
|  Bot- oder Nachrichtenerweiterungen |  **Bot starten** |  Bot |
|  Azure Functions |  **Back-End starten** |  API |

Die folgende Abbildung zeigt Aufgabennamen auf den Registerkarten **AUSGABE** und **TERMINAL** von Visual Studio Code während der Ausführung der Registerkarte, der Bot- oder Nachrichtenerweiterung und Azure Functions.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/Terminal1.png" alt-text="Startet App-Dienste" lightbox="../assets/images/teams-toolkit-v2/debug/Terminal1.png":::

### <a name="launches-debug-configurations"></a>Startet Debugkonfigurationen

Startet die Debugkonfigurationen, wie in `.vscode/launch.json`definiert.

:::image type="content" source="../assets/images/teams-toolkit-v2/debug/launch-debuggers.png" alt-text="Debugger starten":::

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für Projekte mit Registerkarte, Bot- oder Nachrichtenerweiterungs-App und Azure Functions aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp |
| --- | --- | --- |
|  Tab |  **An Front-End (Edge) anfügen** oder  **An Front-End (Chrome) anfügen**  |  pwa-msedge oder pwa-chrome  |
|  Bot- oder Nachrichtenerweiterungen |   **An Bot anfügen** |  pwa-node |
| Azure Functions |   **An Back-End anfügen** |  pwa-node |

In der folgenden Tabelle sind die Debugkonfigurationsnamen und -typen für Projekte mit Bot-App, Azure Functions und ohne Registerkarten-App aufgeführt:

|  Komponente |  Debugkonfigurationsname  | Debugkonfigurationstyp  |
| --- | --- | --- |
|  Bot- oder Nachrichtenerweiterung  | **Bot starten (Edge)** oder  **Bot starten (Chrome)**  |   pwa-msedge oder pwa-chrome  |
|  Bot- oder Nachrichtenerweiterung  |   **An Bot anfügen** |  pwa-node  |
|  Azure Functions |  **An Back-End anfügen** |  pwa-node |

### <a name="sideloads-the-teams-app"></a>Lädt die Teams-App quer

Die Konfiguration **An Front-End anfügen** oder **Bot starten** startet eine Edge- oder Chrome-Browserinstanz, um den Teams-Client auf der Webseite zu laden. Nachdem der Teams-Client geladen wurde, lädt Teams die Teams-App quer, die von der url für das Querladen gesteuert wird, die in den Startkonfigurationen [von Microsoft Teams](https://teams.microsoft.com/l/app/>${localTeamsAppId}?installAppPackage=true&webjoin=true&${account-hint}) definiert ist. Wenn der Teams-Client im Webbrowser geladen wird **, wählen Sie** hinzufügen aus, oder wählen Sie eine Option aus der Dropdownliste gemäß Ihren Anforderungen aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png" alt-text="Lokales Debuggen hinzufügen" lightbox="../assets/images/teams-toolkit-v2/debug/hello-local-debug.png":::

   Ihre App wird Teams hinzugefügt!

## <a name="next"></a>Weiter

> [!div class="nextstepaction"]
> [Debuggen von Hintergrundprozessen](debug-background-process.md)

::: zone-end

::: zone pivot="visual-studio"

## <a name="debug-your-teams-app-locally-using-visual-studio"></a>Lokales Debuggen Ihrer Teams-App mithilfe von Visual Studio

Das Teams-Toolkit hilft Ihnen, Ihre Microsoft Teams-App lokal zu debuggen und eine Vorschau anzuzeigen. Visual Studio ermöglicht ihnen das Debuggen von Registerkarten, Bots und Nachrichtenerweiterungen. Sie können Ihre App lokal in Visual Studio mithilfe des Teams-Toolkits debuggen, indem Sie Folgendes ausführen:

### <a name="set-up-ngrok-only-for-bot-and-message-extension-app"></a>Einrichten von ngrok (nur für Bot- und Nachrichtenerweiterungs-App)

Verwenden Sie eine Eingabeaufforderung, um diesen Befehl auszuführen:

```
ngrok http 5130
```

### <a name="set-up-your-teams-toolkit"></a>Einrichten des Teams-Toolkits

Führen Sie die folgenden Schritte mithilfe des Teams-Toolkits aus, um Ihre App zu debuggen, nachdem Sie ein Projekt erstellt haben:

1. Klicken Sie mit der rechten Maustaste auf Ihr **Projekt**.
1. Wählen Sie **Teams Toolkit****Prepare Teams App Dependencies (Teams-Toolkit: Teams-App-Abhängigkeiten vorbereiten) aus**. > 

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png" alt-text="Teams-App-Abhängigkeiten für lokales Debuggen" lightbox="../assets/images/debug-teams-app/vs-localdebug-teamsappdependencies.png":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname MyTeamsApp1.

   Ihr Microsoft 365-Konto muss über die Berechtigung zum Querladen verfügen, bevor Sie sich anmelden.  Stellen Sie sicher, dass Ihre Teams-App in den Mandanten hochgeladen werden kann. Andernfalls kann Ihre Teams-App nicht im Teams-Client ausgeführt werden.

1. Melden Sie sich bei Ihrem **Microsoft 365-Konto** an, und wählen Sie dann **Weiter aus.**

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-signin-m365.png" alt-text="Anmelden beim Microsoft 365-Konto":::

   > [!Note]
   > Weitere Informationen zum Querladen von Berechtigungen finden Sie unter <https://aka.ms/teamsfx-sideloading-option>.

1. Wählen Sie **Debuggen** > **Debuggen debuggen starten** aus, oder wählen Sie direkt **F5** aus.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-Startdebug.png" alt-text="Debuggen starten":::

   Visual Studio startet die Teams-App im Microsoft Teams-Client in Ihrem Browser.

   > [!Note]
   > Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-debug>.

1. Nachdem Microsoft Teams geladen wurde, wählen Sie **Hinzufügen** aus, um Ihre App in Teams zu installieren.

   :::image type="content" source="../assets/images/debug-teams-app/vs-localdebug-add-loadapp.png" alt-text="Auswählen von &quot;Hinzufügen&quot; zum Laden der App":::

   > [!TIP]
   > Sie können auch die Hot Reload-Funktion von Visual Studio während des Debuggens verwenden. Weitere Informationen finden Sie unter <https://aka.ms/teamsfx-vs-hotreload>.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie die HTTP-Anforderung an `http://localhost:5130/api/notification` senden, um eine Benachrichtigung auszulösen, wenn Sie die Benachrichtigungsbot-App debuggen. Wenn Sie beim Erstellen des Projekts HTTP-Trigger ausgewählt haben, können Sie beliebige API-Tools wie curl (Windows-Eingabeaufforderung), Postman usw. verwenden.

   > [!TIP]
   > Wenn Sie Änderungen an der Teams-App-Manifestdatei (/templates/appPackage/manifest.template.json) vornehmen, stellen Sie sicher, dass Sie den Befehl Vorbereiten von Teams-App-Abhängigkeiten ausführen. Bevor Sie versuchen, die Teams-App erneut lokal auszuführen.

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen von Funktionen zu ihrer Teams-App](add-capability.md)
* [Bereitstellen in die Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen im Teams-Toolkit](TeamsFx-multi-env.md)
