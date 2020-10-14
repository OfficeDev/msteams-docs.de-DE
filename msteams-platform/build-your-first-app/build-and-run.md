---
title: Erste Schritte – erstellen und Ausführen ihrer ersten App
author: heath-hamilton
description: Erstellen Sie schnell eine Microsoft Teams-APP, die ein "Hello, World!" anzeigt. Nachricht mit dem Microsoft Teams-Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: quickstart
ms.openlocfilehash: 20c9eee14649cda23e1d682940f489e78cba24b9
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452645"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Erstellen und Ausführen ihrer ersten Microsoft Teams-App

Sie können direkt in die Microsoft Teams-Entwicklung wechseln, indem Sie eine persönliche RegisterkarteErstellen, die "Hello, World!" anzeigt.

## <a name="1-create-your-app-project"></a>1. Erstellen des App-Projekts

Verwenden Sie das Microsoft Teams-Toolkit in Visual Studio Code, um Ihr erstes App-Projekt einzurichten.

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
:::image type="content" source="../assets/images/build-your-first-app/create-teams-app.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::
1. Geben Sie einen Namen für Ihre Teams-App ein. (Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter**aus.
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::
1. Aktivieren Sie die Option **persönliche Registerkarte** , und klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.

## <a name="2-understand-important-app-project-components"></a>2. Grundlegendes zu wichtigen App-Projektkomponenten

Nachdem das Toolkit Ihr Projekt konfiguriert hat, müssen Sie die Komponenten zum Erstellen einer einfachen persönlichen Registerkarte für Teams. Die Projektverzeichnisse und-Dateien werden im Bereich "Explorer" von Visual Studio Code angezeigt.

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::

Lassen Sie uns einen Moment Zeit nehmen, um einige der wichtigsten Dateien zu verstehen, mit denen Microsoft Teams-App-Entwickler arbeiten.

### <a name="app-manifest-manifestjson"></a>App-Manifest ( `manifest.json` )

Im Verzeichnis befindet `.publish` sich das App-Manifest als Ausgangspunkt für ein beliebiges App-Projekt. Das Manifest definiert die grundlegenden Attribute Ihrer APP und verweist auf erforderliche Ressourcen. Wenn Sie eine App installieren, analysiert Microsoft Teams das Manifest, um zu verstehen, wie Ihre APP auf dem Client gerendert wird.

### <a name="app-scaffolding"></a>App-Gerüste

Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.

Wenn Sie beispielsweise während des Setups eine RegisterkarteErstellen, `App.js` ist die Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt. Das [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) wird aufgerufen, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.

### <a name="app-package-developmentzip"></a>App-Paket ( `Development.zip` )

Im Verzeichnis befindet `.publish` , benötigen Sie das App-Paket, um [Ihre APP](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Microsoft Teams querladen. Das Paket wird auch verwendet, wenn im [App-Katalog oder AppSource Ihrer Organisation veröffentlicht](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) wird. [AppSource](../concepts/deploy-and-publish/appsource/publish.md)

Hier finden Sie einige Details zu den App-Paketdateien:

|Name|Typ|Größe|Speicherort des Manifests|Toolkit-Dateiname|
|---|---|:---:|:---:|-----|
|**App-Manifest**|`.json`| — | — |`.publish/manifest.json`|
|**Farb Logo**|`.png`|192 &times; 192 Pixel|`icon.color`|`.publish/color.png`|
|**Gliederungs Logo**|`.png`|32 &times; 32 Pixel|`icon.outline`|`.publish/outline.png`|

## <a name="3-run-your-app"></a>3. führen Sie Ihre APP aus.

Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.

(Diese Informationen sind auch im Toolkit verfügbar `README` .)

1. Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .
1. Ausführen `npm start` . Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!** Nachricht im Terminal.
1. Öffnen Sie einen Browser, und wechseln Sie zu `https://localhost:3000` , um eine leere Webseite mit dem Namen **Microsoft Teams-Registerkarte**anzuzeigen. (Keine Sorge, dass auf der Seite kein Inhalt angezeigt wird.)<br/>
   :::image type="content" source="../assets/images/build-your-first-app/local-host-tab.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a>4. Einrichten eines sicheren Tunnels für Ihre APP

Ihre APP ist auf Ihrem lokalen Webserver aktiv. Wenn Sie Ihre APP in Microsoft Teams ausführen möchten, müssen Sie den `localhost` Zugriff über HTTPS vornehmen.

Installieren Sie [ngrok](https://ngrok.com/download) , falls noch nicht geschehen. Wenn Sie dieses Tool ausführen, erstellen Sie zwei global verfügbare URLs, die auf Ihren lokalen Webserver ( `http://localhost:3000` ) deuten. Sie benötigen die Weiterleitungs-URL, die mit beginnt `HTTPS` .

1. Öffnen Sie ein neues Terminal, und führen Sie es aus `ngrok http 3000` .
1. Kopieren Sie die von Ihnen angegebene HTTPS-URL (siehe das folgende Beispiel).
:::image type="content" source="../assets/images/build-your-first-app/ngrok-running.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::
1. Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .
1. Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL. (Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ba5.ngrok.io` .)

Das App-Manifest zeigt jetzt auf die Stelle, an der Sie die APP hosten.

## <a name="5-sideload-your-app-in-teams"></a>5. querladen ihrer app in Microsoft Teams

Wenn Ihre APP über HTTPS läuft und darauf zugegriffen werden kann, sind Sie bereit, Sie in Microsoft Teams hochzuladen.

> [!TIP]
> Überprüfen Sie vor dem Sideloading Ihrer APP auf Probleme, die die [Validierungsfunktion des Toolkits](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool)verwenden. Fehler müssen behoben sein, damit die APP erfolgreich querladen.

1. Melden Sie sich mit Ihrem Konto beim Microsoft Teams-Client an, das App-Sideloading zulässt. (Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)
1. Wählen Sie **apps**aus, und wählen Sie dann **benutzerdefinierte App hochladen**aus.
1. Wechseln Sie zu Ihrem APP `.publish` -Projektordner, und wählen Sie aus `Development.zip` . Eine modale Installation wird angezeigt.
:::image type="content" source="../assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::
1. Wählen Sie **Hinzufügen** aus, um Ihre APP zu installieren.
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot, der zeigt, wie Sie eine neue APP mit dem Visual Studio Code Teams-Toolkit erstellen.":::

🎉 Herzlichen Glückwunsch! Ihre APP wird in Microsoft Teams gestartet.

## <a name="next-step"></a>Nächster Schritt

Erweitern Sie auf der persönlichen Registerkarte, die Sie gerade erstellt haben, oder erstellen Sie eine andere Art von Teams-app.

> [!div class="nextstepaction"]
> [Zu Ihrer persönlichen Registerkarte hinzufügen](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)
