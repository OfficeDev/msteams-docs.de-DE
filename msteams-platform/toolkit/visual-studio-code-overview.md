---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter Apps direkt Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 59f2943f37856c42346b2ffad4e01d88910679ae
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020261"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Erstellen von Apps mit dem Teams Toolkit und Visual Studio Code

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen. Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="installing-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Microsoft Teams Toolkit für Visual Studio Code steht im [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb des Visual Studio zur Verfügung.

> [!TIP]
> Nach der Installation sollte das Teams Toolkit in der Visual Studio Code-Aktivitätsleiste angezeigt werden. Wenn nicht, klicken Sie mit der rechten Maustaste in der Aktivitätsleiste, und wählen **Sie Microsoft Teams aus,** um das Toolkit für den einfachen Zugriff anheften.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Importieren eines vorhandenen Projekts](#import-an-existing-teams-app-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Packen Ihrer App](#package-your-app)
- [Ausführen Ihrer App lokal oder in Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams-Projekts

1. Erstellen Sie einen Arbeitsbereich/Ordner für Ihr Projekt in Ihrer lokalen Umgebung.
1. Wählen Visual Studio In code das Symbol Teams aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) aus der Aktivitätsleiste auf der linken Seite des Fensters.
1. Wählen **Sie im Befehlsmenü Microsoft Teams Toolkit** öffnen aus.
1. Wählen **Sie im Befehlsmenü Erstellen** einer neuen Teams-App aus.
1. Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein. Dies wird sowohl als Name des Ordners verwendet, in dem sich Ihr Projekt befindet, als auch als Standardname Ihrer App.
1. Drücken **Sie die** EINGABETASTE, und Sie gelangen zum Bildschirm Funktionen hinzufügen, um die Eigenschaften für Ihre neue App zu konfigurieren. 
1. Wählen Sie die **Schaltfläche Fertig** stellen aus, um den Konfigurationsprozess zu beenden.

## <a name="import-an-existing-teams-app-project"></a>Importieren eines vorhandenen Teams-App-Projekts

1. Wählen Visual Studio In code das Symbol Teams aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) aus der Aktivitätsleiste auf der linken Seite des Fensters.
1. Wählen **Sie im Befehlsmenü App-Paket** importieren aus.
1. Wählen Sie Ihre vorhandene [Zip-Datei für Teams-App-Pakete](../concepts/build-and-test/apps-package.md) aus.
1. Wählen Sie die **Schaltfläche Veröffentlichungspaket auswählen** aus. Die Konfigurationsregisterkarte des Toolkits sollte nun mit den Details Ihrer App gefüllt werden.
1. Wählen Visual Studio Code die Option Ordner zum Arbeitsbereich hinzufügen aus, um das Quellcodeverzeichnis dem arbeitsbereich  ->   Visual Studio hinzuzufügen.

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams-App drei Komponenten:

  1. Der Microsoft Teams-Client (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anfragen nach Inhalten reagiert, die in Teams angezeigt werden, z. B. HTML-Registerkarteninhalt oder eine adaptive Botkarte.
  1. Ein [Teams-App-Paket,](/concepts/build-and-test/apps-package.md) das aus drei Dateien besteht:

  > [!div class="checklist"]
  >
  > - The manifest.json 
  > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen Oder Organisations-App-Katalog angezeigt werden soll
 > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams-Aktivitätsleiste.

Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, in der sich die Dienste befinden.

1. Um Ihre App zu konfigurieren, navigieren Sie zur **Registerkarte Microsoft Teams Toolkit** in Visual Studio Code.
1. Wählen **Sie App-Paket bearbeiten aus,** um die **Seite App-Details anzuzeigen.**
1. Durch Bearbeiten der Felder auf der Seite App-Details werden die Inhalte der datei manifest.jsaktualisiert, die letztendlich als Teil des App-Pakets versandt werden. *Siehe* [App Studio-Manifest-Editor](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Packen Ihrer App

Wenn Sie die **App-Details-,**  **Manifest-** oder **ENV-Dateien** im Veröffentlichungsordner Ihrer App ändern, wird ihreDevelopment.zip **generiert.** Sie müssen zwei Symbole [in](../concepts/build-and-test/apps-package.md#app-icons) denselben Ordner hinzufügen.

## <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen der App lokal

## <a name="run-your-app"></a>Ausführen Ihrer App

### <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen der App lokal

Ausführliche Anweisungen zum Packen und Testen Ihrer App finden Sie unter **Erstellen* und Ausführen von Inhalten in Ihrer Projekthomepage. Im Allgemeinen müssen Sie den Server Ihrer App installieren, ausführen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen kann, die von localhost ausgeführt werden.

### <a name="enable-development-from-localhost"></a>Aktivieren der Entwicklung von localhost

Wenn Sie Ihre registerkartenbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihrem Browser mitteilen, dass er der App vertraut, von der sie bedient <https://localhost> wird. Navigieren Sie zu <https://localhost:3000/tab>. Wenn eine Warnung angezeigt wird, die angibt, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um trotzdem fortzufahren. Auf Ihre App sollte nun über den Teams-Client zugegriffen werden können.

### <a name="run-your-app-in-teams"></a>Ausführen Ihrer App in Teams

Voraussetzungen: [Aktivieren des Vorschaumodus für Teams-Entwickler](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Codefensters.
1. Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen anzeigen.**
1. Sie können auch die Tastenkombination `Ctrl+Shift+D` verwenden.

> [!div class="nextstepaction"]
> [Nächster Schritt: Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
