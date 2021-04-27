---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-App, die ein "Hello, World!" anzeigt. mit dem Microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 1b34c3f3121e834abc8a8a92a8a0ac9a049c9e07
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020884"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Erstellen und Ausführen Ihrer ersten Microsoft Teams-App

Starten Sie die Microsoft Teams-Entwicklung, indem Sie eine persönliche Registerkarte erstellen, auf der "Hello, World!" angezeigt wird.
Erstellen und ausführen Sie Ihre erste Teams-App mithilfe der folgenden Schritte:

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Verwenden Sie das Microsoft Teams Toolkit in Visual Studio Code, um Ihr erstes App-Projekt zu einrichten. Erstellen Sie Ihr App-Projekt mithilfe der folgenden Schritte:

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.
1. Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Tab** und dann **Weiter aus.**
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams Toolkit konfigurieren.":::
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Aktivieren Sie nur **die Option Persönliche Registerkarte,** und wählen Sie **am** unteren Bildschirmrand Fertig stellen aus, um Ihr Projekt zu konfigurieren.

## <a name="2-understand-important-app-project-components"></a>2. Verstehen wichtiger Komponenten des App-Projekts

Nachdem Das Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer grundlegenden persönlichen Registerkarte für Teams. Die Projektverzeichnissen und -dateien werden im Explorer-Bereich von Visual Studio angezeigt.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot mit App-Projektdateien für eine persönliche Registerkarte in Visual Studio Code.":::

### <a name="app-scaffolding"></a>App-Gerüst

Das Toolkit erstellt automatisch ein Gerüst für Sie im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben.

Wenn Sie beispielsweise während des Setups eine Registerkarte erstellen, ist die Datei im Verzeichnis wichtig, da sie die Initialisierung und das Routing `App.js` `src/components` Ihrer App behandelt. Es ruft das [Microsoft Teams JavaScript-Client-SDK auf,](../tabs/how-to/using-teams-client-sdk.md) um die Kommunikation zwischen Ihrer App und Teams zu erstellen.

### <a name="app-id"></a>App-ID

Konfigurieren Sie Ihre App mit App Studio mithilfe der Teams-App-ID. Suchen Sie die ID im `teamsAppId` Objekt, das sich in der Projektdatei `package.json` befindet.

## <a name="3-build-and-run-your-app"></a>3. Erstellen und Ausführen Ihrer App

Erstellen und ausführen Sie Ihre App lokal, um Zeit zu sparen. Diese Informationen sind auch im Toolkit `README` verfügbar. Erstellen und ausführen Sie Ihre App mithilfe der folgenden Schritte:

1. Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Sobald sie abgeschlossen sind, wird ein **Kompiliert erfolgreich erstellt!** -Nachricht im Terminal. Ihre App wird auf `https://localhost:3000` ausgeführt.

## <a name="4-sideload-your-app-in-teams"></a>4. Querladen Ihrer App in Teams

Ihre App kann in Teams testen. Dazu müssen Sie über ein Microsoft 365-Entwicklungskonto verfügen, das das Querladen von Apps zulässt. Weitere Informationen zum Öffnen von Konten finden Sie unter [Teams-Entwicklungskonto](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account). 

> [!TIP]
> Überprüfen Sie vor dem Querladen Ihrer App mithilfe der [Überprüfungsfunktion in App Studio,](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)die im Toolkit enthalten ist, nach Problemen. Beheben Sie die Fehler, um die App erfolgreich querladen zu können.

Querladen Ihrer App in Teams mithilfe der folgenden Schritte:

> [!NOTE]
> Um das Querladen zu aktivieren, bevor Sie Ihre App in Teams querladen, führen Sie die Schritte unter [Turn on app sideloading aus.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)

1. Wählen Sie **die F5-Taste** aus, um einen Teams-Webclient in Visual Studio starten.
1. Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, wo Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das nach dem Drücken von **F5 geöffnet wurde.**
   1. Wechseln Sie `https://localhost:3000/tab` zu und fahren Sie mit der Seite fort.
1. Wechseln Sie zurück zu Teams. Wählen Sie im Dialogfeld **Hinzufügen aus, um Ihre** App zu installieren.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für die persönliche Tab-App &quot;Hello, World!&quot;, die in Teams ausgeführt wird.":::

🎉 Herzlichen Glückwunsch! Ihre App wird in Teams ausgeführt.

## <a name="next-step"></a>Nächster Schritt

Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-App.

> [!div class="nextstepaction"]
> [Hinzufügen zu Ihrer persönlichen Registerkarte](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
