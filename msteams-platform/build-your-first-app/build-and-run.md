---
title: Erste Schritte – erstellen und Ausführen ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-APP, die ein "Hello, World!" anzeigt. Nachricht mit dem Microsoft Teams-Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 62c4bd950183ceb64fb30b528661cf84e9210d89
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931777"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Erstellen und Ausführen ihrer ersten Microsoft Teams-App

Sie können direkt in die Microsoft Teams-Entwicklung wechseln, indem Sie eine persönliche RegisterkarteErstellen, die "Hello, World!" anzeigt.

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Verwenden Sie das Microsoft Teams-Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einzurichten.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter** aus.
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, in dem gezeigt wird, wie Ihr App-Projekt mit dem Visual Studio Code Teams-Toolkit konfiguriert wird.":::
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Aktivieren Sie nur die Option **persönliche Registerkarte** , und klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.

## <a name="2-understand-important-app-project-components"></a>2. Grundlegendes zu wichtigen App-Projektkomponenten

Nachdem das Toolkit Ihr Projekt konfiguriert hat, müssen Sie die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams. Die Projektverzeichnisse und-Dateien werden im Bereich "Explorer" von Visual Studio Code angezeigt.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot, in dem App-Projektdateien für eine persönliche Registerkarte in Visual Studio Code angezeigt werden.":::

### <a name="app-scaffolding"></a>App-Gerüste

Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.

Wenn Sie beispielsweise während des Setups eine RegisterkarteErstellen, `App.js` ist die Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt. Das [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) wird aufgerufen, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.

### <a name="app-id"></a>App-ID

Ihre Teams-APP-ID wird benötigt, um Ihre APP mit App Studio zu konfigurieren. Sie finden die ID im `teamsAppId` Objekt, das sich in der Datei des Projekts befindet `package.json` .

## <a name="3-build-and-run-your-app"></a>3. erstellen und Ausführen der APP

Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.

(Diese Informationen sind auch im Toolkit verfügbar `README` .)

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` .

Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!** Nachricht im Terminal. Ihre APP wird gestartet `https://localhost:3000` .

## <a name="4-sideload-your-app-in-teams"></a>4. querladen ihrer app in Microsoft Teams

Ihre APP ist zum Testen in Microsoft Teams verfügbar. Hierzu benötigen Sie ein Konto, das App-Sideloading zulässt. (Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)

> [!TIP]
> Überprüfen Sie vor dem Sideloading Ihrer APP auf Probleme mit der [Überprüfungsfunktion in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), die im Toolkit enthalten ist. Fehler müssen behoben sein, damit die APP erfolgreich querladen.

1. Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.
1. Um Ihre APP-Inhalte in Microsoft Teams anzuzeigen, geben Sie an, wo Ihre APP aktiv ist ( `localhost` ) vertrauenswürdig ist:
   1. Öffnen Sie eine neue Registerkarte in demselben Browserfenster (standardmäßig Google Chrome), die nach Drücken von **F5** geöffnet wurde.
   1. Wechseln Sie zu `https://localhost:3000/tab` der Seite, und fahren Sie fort.
1. Wechseln Sie zurück zu Microsoft Teams. Wählen Sie im Dialogfeld **hinzufügen aus** , um Ihre APP zu installieren.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot mit einem Beispiel für die persönliche Tab-app &quot;Hello, World!&quot;, die in Microsoft Teams läuft.":::

🎉 Herzlichen Glückwunsch! Ihre APP wird in Microsoft Teams gestartet.

## <a name="next-step"></a>Nächster Schritt

Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-app.

> [!div class="nextstepaction"]
> [Zu Ihrer persönlichen Registerkarte hinzufügen](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
