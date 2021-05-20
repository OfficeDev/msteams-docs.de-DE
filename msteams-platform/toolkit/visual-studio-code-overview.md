---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Beginnen Sie mit dem Erstellen großartiger benutzerdefinierter Apps direkt innerhalb Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: efd0962e9c4c0d64dbac47caf29b2e56907937b3
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566558"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Erstellen Sie Apps mit dem Teams Toolkit und Visual Studio Code

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen. Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="installing-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Microsoft Teams Toolkit for Visual Studio Code steht im [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb Visual Studio Code zum Download zur Verfügung.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Aktivitätsleiste Visual Studio Code angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitätsleiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einen einfachen Zugriff anzuheften.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Importieren eines vorhandenen Projekts](#import-an-existing-teams-app-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Sie Ihre App](#package-your-app)
- [Führen Sie Ihre App lokal oder in Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekts

1. Erstellen Sie einen Arbeitsbereich oder Ordner für Ihr Projekt in Ihrer lokalen Umgebung.
1. Wählen Sie in Visual Studio Code das Teams-Symbol aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) aus der Aktivitätsleiste auf der linken Seite des Fensters.
1. Wählen Sie Microsoft Teams Toolkit im Befehlsmenü **öffnen** aus.
1. Wählen Sie im Befehlsmenü die Option **Neue Teams App erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein. Dies wird sowohl als Name des Ordners, in dem sich das Projekt befindet, als auch als Standardname Ihrer App verwendet.
1. Drücken Sie **die Eingabetaste,** und Sie gelangen zum Bildschirm **"Funktionen hinzufügen",** um die Eigenschaften für Ihre neue App zu konfigurieren.
1. Wählen Sie die Schaltfläche **Fertig stellen** aus, um den Konfigurationsvorgang abzuschließen.

## <a name="import-an-existing-teams-app-project"></a>Importieren eines vorhandenen Teams-App-Projekts

1. Wählen Sie in Visual Studio Code das Teams-Symbol aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) aus der Aktivitätsleiste auf der linken Seite des Fensters.
1. Wählen Sie **App-Paket** importieren aus dem Befehlsmenü aus.
1. Wählen Sie Ihre vorhandene [Teams App-Paket](../concepts/build-and-test/apps-package.md) ZIP-Datei.
1. Wählen Sie die Schaltfläche **Veröffentlichungspaket auswählen** aus. Die Konfigurationsregisterkarte des Toolkits sollte nun mit den Details Ihrer App aufgefüllt werden.
1. Wählen Sie in Visual Studio Code **Dateiordner** zum Arbeitsbereich hinzufügen aus,  ->   um das Quellcodeverzeichnis zum Visual Studio Code Arbeitsbereich hinzuzufügen.

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams-App drei Komponenten:

  1. Der Microsoft Teams Client (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden. Zum Beispiel HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.
  1. Ein Teams [App-Paket,](/concepts/build-and-test/apps-package.md) das aus drei Dateien besteht:

      > [!div class="checklist"]
      >
      > - Die manifest.jsweiter. 
      > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen oder Organisations-App-Katalog angezeigt werden soll.
      > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Teams Aktivitätsleiste.

Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter denen sich die Dienste befinden.

1. Um Ihre App zu konfigurieren, navigieren Sie zur Registerkarte **Microsoft Teams Toolkit** in Visual Studio Code.
1. Wählen Sie **App-Paket bearbeiten** aus, um die **App-Detailseite** anzuzeigen.
1. Durch das Bearbeiten der Felder auf der Seite App-Details wird der Inhalt der manifest.jsin der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. Weitere Informationen finden Sie im [App Studio-Manifesteditor](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Sie Ihre App

Wenn Sie die **App-Detailseite,** das **Manifest** oder **die .env-Dateien** im  **.publish-Ordner** Ihrer App ändern, werden automatisch Ihre **Development.zip** Datei generiert. Sie müssen zwei [Symbole](../concepts/build-and-test/apps-package.md#app-icons) in demselben Ordner einschließen.

## <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen Ihrer App lokal

## <a name="run-your-app"></a>Ausführen Ihrer App

### <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen Ihrer App lokal

Ausführliche Anweisungen zum Verpacken und Testen Ihrer App finden Sie auf der Projekthomepage zum **Erstellen und Ausführen** von Inhalten. Im Allgemeinen müssen Sie den Server Ihrer App installieren, ihn ausführen lassen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost ausgeführt werden.

### <a name="enable-development-from-localhost"></a>Ermöglichen der Entwicklung von localhost

Wenn Sie Ihre tabbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihren Browser anweisen, der von bereitgestellten App zu <https://localhost> vertrauen. Navigieren Sie zu <https://localhost:3000/tab>. Wenn eine Warnung angezeigt wird, die darauf hinweist, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um trotzdem fortzufahren. Auf Ihre App sollte jetzt vom Teams Client zugegriffen werden können.

### <a name="run-your-app-in-teams"></a>Führen Sie Ihre App in Teams

Voraussetzungen: [Aktivieren Teams Entwicklervorschaumodus](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Code Fensters.
1. Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen** anzuzeigen.
1. Sie können auch die Tastenkombination `Ctrl+Shift+D` verwenden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
