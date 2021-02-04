---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-App, die "Hello, World!" anzeigt. -Nachricht mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 46a92f54cdbf68e28510c0bd4cc0b7018cfaae3c
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093950"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Erstellen und Ausführen Ihrer ersten Microsoft Teams-App

Starten Sie die Microsoft Teams-Entwicklung, indem Sie eine persönliche Registerkarte erstellen, auf der "Hello, World!" angezeigt wird.
Erstellen und führen Sie Ihre erste Teams-App mit den folgenden Schritten aus:

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Verwenden Sie das Microsoft Teams Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einrichten. Erstellen Sie Ihr App-Projekt mithilfe der folgenden Schritte:

1. In Visual Studio Code, select **Microsoft Teams** on the left Activity Bar and choose Create a new Teams :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **app**.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" die Option **"Tab"** und dann **"Weiter" aus.**
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams Toolkit konfigurieren.":::
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.)
1. Aktivieren Sie nur die Registerkarte "Persönlich", und **wählen** Sie "Fertig stellen" am unteren Rand des Bildschirms aus, um Ihr Projekt zu konfigurieren. 

## <a name="2-understand-important-app-project-components"></a>2. Verstehen wichtiger Komponenten des App-Projekts

Nachdem Das Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams. Die Projektverzeichnissen und Dateien werden im Explorerbereich von Visual Studio Code angezeigt.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot showing app project files for a personal tab in Visual Studio Code.":::

### <a name="app-scaffolding"></a>App-Gerüst

Das Toolkit erstellt automatisch ein Gerüst für Sie im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben.

Wenn Sie beispielsweise während des Setups eine Registerkarte erstellen, ist die Datei im Verzeichnis wichtig, da sie die Initialisierung und das Routing `App.js` `src/components` Ihrer App behandelt. Es ruft das [Microsoft Teams JavaScript-Client-SDK auf,](../tabs/how-to/using-teams-client-sdk.md) um die Kommunikation zwischen Ihrer App und Teams zu herstellen.

### <a name="app-id"></a>App-ID

Konfigurieren Sie Ihre App mit App Studio mithilfe der Teams-App-ID. Suchen Sie die ID im `teamsAppId` Objekt, das sich in der Projektdatei `package.json` befindet.

## <a name="3-build-and-run-your-app"></a>3. Erstellen und Ausführen Ihrer App

Erstellen Und führen Sie Ihre App lokal aus, um Zeit zu sparen. Diese Informationen sind auch im Toolkit `README` verfügbar. Erstellen Und führen Sie Ihre App mit den folgenden Schritten aus:

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.
1. Ausführen `npm start` .

Nach Abschluss des Vorgangs wird ein **kompiliertes Programm erfolgreich erstellt.** im Terminal zu senden. Ihre App wird unter `https://localhost:3000` ausgeführt.

## <a name="4-sideload-your-app-in-teams"></a>4. Querladen Ihrer App in Teams

Ihre App kann in Teams testbereit sein. Dazu müssen Sie über ein Microsoft 365-Entwicklungskonto verfügen, das das Querladen von Apps ermöglicht. Weitere Informationen zum Öffnen von Konten finden Sie unter [Teams-Entwicklungskonto.](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account) 

> [!TIP]
> Überprüfen Sie vor dem Querladen Ihrer App auf Probleme, indem Sie das Validierungsfeature [in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)verwenden, das im Toolkit enthalten ist. Beheben Sie die Fehler, um die App erfolgreich quer zu laden.

Querladen Ihrer App in Teams mithilfe der folgenden Schritte:

> [!NOTE]
> Um das Querladen zu aktivieren, bevor Sie Ihre App in Teams querladen, führen Sie die Schritte in [Turn on app sideloading aus.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

1. Wählen Sie **die F5-TASTE** aus, um einen Teams-Webclient in Visual Studio starten.
1. Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, dass der Ort, an dem Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte im selben Browserfenster (standardmäßig Google Chrome), das nach drücken von **F5 geöffnet wurde.**
   1. Wechseln Sie `https://localhost:3000/tab` zu der Seite, und fahren Sie mit der Seite fort.
1. Wechseln Sie zurück zu Teams. Wählen Sie im Dialogfeld **"Hinzufügen" aus, um** Ihre App zu installieren.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für eine persönliche Registerkarten-App &quot;Hello, World!&quot;, die in Teams ausgeführt wird.":::

🎉 Herzlichen Glückwunsch! Ihre App wird in Teams ausgeführt.

## <a name="next-step"></a>Nächster Schritt

Erweitern Sie die persönliche Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie einen anderen Typ von Teams-App.

> [!div class="nextstepaction"]
> [Zu Ihrer persönlichen Registerkarte hinzufügen](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
