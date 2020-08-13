---
title: Erstellen und Ausführen ihrer ersten Teams-App
author: heath-hamilton
description: Führen Sie Ihre erste Microsoft Teams-App aus.
ms.openlocfilehash: 98af8d8d6d89007e36c24bd34661ec21b33cbdf1
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652045"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a>Erstellen und Ausführen ihrer ersten Microsoft Teams-App

Sie können direkt in die Entwicklung auf der Microsoft Teams-Plattform wechseln, indem Sie schnell eine einfache APP erstellen und durchführen.

> [!NOTE]
> Bei der Befolgen dieser Lernprogramme ist es hilfreich, über funktionsfähige JavaScript-Kenntnisse (konkret reagieren) zu verfügen.

## <a name="set-up-your-development-account"></a>Einrichten Ihres entwicklungskontos

Um Apps für Teams zu erstellen, benötigen Sie ein Teams-Konto, das Sideloading zulässt (Ihr Konto kann dies möglicherweise bereits bereitstellen). Wenn dies nicht der Fall ist, registrieren Sie sich für ein Microsoft 365-Entwickler Abonnement, damit Sie einen Testmandanten erhalten können.

1. Überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:
    1. Wählen Sie im Microsoft Teams-Client **apps**aus.
    1. Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.
1. Wenn Sie diese Option verwenden, können Sie mit dem Erstellen beginnen. Wenn dies nicht der Fall ist, führen Sie die folgenden Schritte aus:
    1. Registrieren Sie sich für ein [Microsoft 365-Entwickler Abonnement](../doc-links/prepare-your-o365-tenant.md).
    1. [Aktivieren Sie benutzerdefinierte App-Sideloading](../doc-links/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) für Ihr Test Konto.

## <a name="get-your-development-tools"></a>Abrufen Ihrer Entwicklungstools

Sie können Microsoft Teams-apps mit Ihren bevorzugten Tools erstellen, aber hier erfahren Sie, wie Sie mit Visual Studio-Code und dem Microsoft Teams-Toolkit schnell loslegen müssen.

1. Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download).
1. Wählen Sie in Visual Studio Code die Option **Extensions** ![ Visual Studio Toolkit View in ](../doc-links/images/vs-code-extensions.png) der linken Aktivitäts Leiste aus, und installieren Sie das **Microsoft Teams-Toolkit**.
1. Installieren Sie [Node.js](https://nodejs.org/en/).

## <a name="create-an-app-project"></a>Erstellen eines App-Projekts

Das Microsoft Teams-Toolkit kann Ihnen helfen, ihr erstes App-Projekt einzurichten.

1. Öffnen Sie in Visual Studio Code das Toolkit, indem Sie das Symbol Teams auswählen. ![Teams-Symbol](../doc-links/images/favicon-16x16.png) in der linken Aktivitäts Leiste.
1. Wählen Sie **neue Teams-app erstellen**aus.
1. Wenn Sie dazu aufgefordert werden, geben Sie einen Namen für Ihre APP ein. Dies ist der Standardname für Ihre APP und auch der Name des Projektverzeichnisses auf Ihrem lokalen Computer.
1. Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter**aus.
1. Aktivieren Sie die Option **persönliche Registerkarte** , und wählen Sie **Fertig stellen** aus, um Ihr Projekt zu konfigurieren.

![Registerkartenansicht "Toolkit hinzufügen"](../doc-links/images/toolkit-add-tabs.PNG)

Nachdem Sie abgeschlossen haben, haben Sie die APP-Gerüst Komponenten zum Erstellen einer persönlichen Registerkarte.

## <a name="run-your-app"></a>Ausführen der APP

Führen Sie die `README.md` in Ihrem Projekt beschriebenen Schritte aus, um Ihre APP in Microsoft Teams zu erstellen, auszuführen und bereitzustellen. Im allgemeinen helfen Ihnen diese Anweisungen dabei, Folgendes zu tun:

* Hosten Ihrer APP auf `localhost` .
* [Richten Sie einen sicheren Tunnel mit ngrok ein](../doc-links/debug.md#locally-hosted) , damit Teams auf Ihre App zugreifen können. (Installieren Sie [ngrok](https://ngrok.com/download).)
* [Querladen Ihre APP](../doc-links/apps-upload.md) im Microsoft Teams-Client mithilfe der `Development.zip` im `.publish` -Ordner.

Nachdem Sie Ihre APP querladen haben, sollte Sie im Microsoft Teams-Client wie folgt aussehen.

![Beispielregisterkarte "Hello World"](../doc-links/images/tab-running.png)

## <a name="important-app-project-files"></a>Wichtige Dateien für das App-Projekt

Wenn Ihr App-Projekt und das Gerüstbau eingerichtet sind, nehmen Sie sich einige Zeit, um einige der wichtigsten Dateien zu verstehen, mit denen die Teams-App-Entwickler arbeiten.

### <a name="app-manifest-manifestjson"></a>App-Manifest ( `manifest.json` )

Im Verzeichnis befindet `.publish` sich das App-Manifest als Ausgangspunkt für ein beliebiges App-Projekt. Das Manifest definiert die grundlegenden Attribute Ihrer APP und verweist auf erforderliche Ressourcen. Wenn Sie eine App installieren, analysiert Microsoft Teams das Manifest, um zu verstehen, wie Ihre APP auf dem Client gerendert wird.

In den folgenden Lernprogrammen konzentrieren Sie sich auf die Abschnitte des App-Manifests zum Erstellen von persönlichen und Kanal Registerkarten.

### <a name="package-developmentzip"></a>Paket ( `Development.zip` )

Auch im Verzeichnis befindet `.publish` , benötigen Sie das App-Paket, um [Ihre APP](../../overview.md#how-can-you-share-your-teams-app) in Microsoft Teams querladen. Es wird auch verwendet, wenn im [App-Katalog Ihrer Organisation oder in](../../overview.md#how-can-you-share-your-teams-app) [AppSource](../../concepts/deploy-and-publish/appsource/publish.md)veröffentlicht wird.

Hier finden Sie einige Details zu den App-Paketdateien:

|Name|Typ|Größe|Speicherort des Manifests|Toolkit-Dateiname|
|---|---|:---:|:---:|-----|
|**App-Manifest**|`.json`| — | — |`.publish/manifest.json`|
|**Farb Logo**|`.png`|192 &times; 192 Pixel|`icon.color`|`.publish/color.png`|
|**Gliederungs Logo**|`.png`|32 &times; 32 Pixel|`icon.outline`|`.publish/outline.png`|

### <a name="scaffolding-src"></a>Gerüstbau ( `src` )

Das Toolkit erstellt automatisch ein Gerüst für Sie im `src` Verzeichnis basierend auf den Funktionen, die Sie während der Installation hinzugefügt haben.

Einige Dateien werden erstellt, unabhängig davon, welche Art von APP Sie haben, though. Beispielsweise ist die `App.js` Datei im `src/components` Verzeichnis wichtig, da Sie die Initialisierung und das Routing Ihrer APP übernimmt. Am wichtigsten ist, dass das [Microsoft Teams SDK](../doc-links/using-teams-client-sdk.md) aufgerufen wird, um die Kommunikation zwischen Ihrer APP und ihren Teams herzustellen.

Weitere Informationen zu Gerüsten finden Sie in den Lernprogrammen zum Erstellen von persönlichen und Kanal Registerkarten.

## <a name="next-step"></a>Nächster Schritt

🎉 Herzlichen Glückwunsch! Sie verfügen über eine laufende Teams-app. Wählen Sie die folgende Schaltfläche aus, um zu erfahren, wie Sie eine reale Funktion hinzufügen.

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte](add-personal-tab.md)
