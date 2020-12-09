---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Code Toolkit
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 350da030d15e72e2cad51c5967afab9b6f29fe9e
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604473"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Erstellen von apps mit dem Teams-Toolkit und Visual Studio Code

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der Visual Studio Code-Umgebung erstellen. Das Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="installing-the-teams-toolkit"></a>Installieren des Teams-Toolkits

Das Microsoft Teams-Toolkit für Visual Studio Code steht vom [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb Visual Studio Codes zum Download zur Verfügung.

> [!TIP]
> Nach der Installation sollte das Teams-Toolkit in der Leiste Visual Studio Code-Aktivität angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitäts Leiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu fixieren

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Importieren eines vorhandenen Projekts](#import-an-existing-teams-app-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Ihrer APP](#package-your-app)
- [Ausführen der APP lokal oder in Microsoft Teams](#run-your-app)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams-Projekts

1. Erstellen Sie in Ihrer lokalen Umgebung einen Arbeitsbereich/Ordner für Ihr Projekt.
1. Wählen Sie in Visual Studio Code das Symbol Teams aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) in der Aktivitäts Leiste auf der linken Seite des Fensters.
1. Wählen Sie im Menü Command **die Option Microsoft Teams Toolkit öffnen** aus.
1. Wählen Sie im Menü Command die Option **neue Teams-app erstellen** aus.
1. Wenn Sie dazu aufgefordert werden, geben Sie den Namen des Arbeitsbereichs ein. Dies wird sowohl als Name des Ordners, in dem sich Ihr Projekt befindet, als auch als Standardname Ihrer APP verwendet.
1. Drücken Sie die **EINGABETASTE** , und Sie gelangen auf den Bildschirm **Funktionen hinzufügen** , um die Eigenschaften ihrer neuen App zu konfigurieren.
1. Klicken Sie auf die Schaltfläche **Fertig stellen** , um den Konfigurationsprozess abzuschließen.

## <a name="import-an-existing-teams-app-project"></a>Importieren eines vorhandenen Teams-App-Projekts

1. Wählen Sie in Visual Studio Code das Symbol Teams aus. ![Teams-Symbol](../assets/icons/favicon-16x16.png) in der Aktivitäts Leiste auf der linken Seite des Fensters.
1. Wählen Sie im Menü Command die Option **App-Paket importieren** aus.
1. Wählen Sie die ZIP-Datei des vorhandenen [Teams-App-Pakets](../concepts/build-and-test/apps-package.md) aus.
1. Klicken Sie auf die Schaltfläche **veröffentlichungspaket auswählen** . Die Registerkarte Konfiguration des Toolkits sollte nun mit den Details Ihrer APP aufgefüllt werden.
1. Wählen Sie in Visual Studio Code **Datei**  ->  **Ordner zu Arbeitsbereich hinzufügen** aus, um das Quell Code Verzeichnis dem Arbeitsbereich Visual Studio Code hinzuzufügen.

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams-app drei Komponenten:

  1. Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.
  1. Ein Server, der auf Anforderungen für Inhalte reagiert, die in Microsoft Teams angezeigt werden, beispielsweise HTML-Registerkarteninhalte oder eine bot-Adaptive Karte.
  1. Ein Teams- [App-Paket](/concepts/build-and-test/apps-package.md) , bestehend aus drei Dateien:

  > [!div class="checklist"]
  >
  > - Die manifest.jsauf 
  > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre APP, das im öffentlichen oder im Organisations-App-Katalog angezeigt wird
 > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Microsoft Teams-Aktivitäts Leiste.

Wenn eine APP installiert ist, analysiert der Microsoft Teams-Client die Manifestdatei, um benötigte Informationen wie den Namen Ihrer APP und die URL zu ermitteln, in der sich die Dienste befinden.

1. Um Ihre APP zu konfigurieren, navigieren Sie in Visual Studio Code zur Registerkarte **Microsoft Teams Toolkit** .
1. Wählen Sie **App-Paket bearbeiten** aus, um die Seite **App-Details** anzuzeigen.
1. Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. *Siehe* [App Studio-Manifest-Editor](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Ihrer APP

Durch Ändern der **App-Detail** Seite, des **Manifests** oder der **env** -Dateien im Ordner "  **. Publish** " Ihrer APP wird die **Development.zip** Datei automatisch generiert. Sie müssen [zwei Symbole](../concepts/build-and-test/apps-package.md#app-icons) in den gleichen Ordner einschließen.

## <a name="install-and-run-your-app-locally"></a>Lokal installieren und Ausführen der APP

## <a name="run-your-app"></a>Ausführen der APP

### <a name="install-and-run-your-app-locally"></a>Lokal installieren und Ausführen der APP

Ausführliche Anweisungen zum Verpacken und Testen Ihrer APP erhalten Sie im Abschnitt **Erstellen und ausführen* von Inhalten auf der Startseite des Projekts. Im Allgemeinen müssen Sie den Server Ihrer APP installieren, ihn ausführen lassen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost aus gestartet werden.

### <a name="enable-development-from-localhost"></a>Aktivieren der Entwicklung von localhost

Wenn Sie Ihre registerkartenbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie Ihrem Browser mitteilen, dass der APP, von der bedient wird, Vertrauen muss <https://localhost> . Navigieren Sie zu <https://localhost:3000/tab>. Wenn eine Warnung angezeigt wird, die besagt, dass die Website nicht vertrauenswürdig ist, wählen Sie die Option aus, um den Vorgang fortzusetzen. Auf Ihre APP sollte nun über den Teams-Client zugegriffen werden.

### <a name="run-your-app-in-teams"></a>Ausführen ihrer app in Microsoft Teams

Voraussetzungen: Aktivieren von Microsoft [Teams Developer Preview Mode](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navigieren Sie auf der linken Seite des Visual Studio Code Fensters zur Aktivitäts Leiste.
1. Wählen Sie das Symbol **Ausführen** aus, um die Ansicht **ausführen und Debuggen** anzuzeigen.
1. Sie können auch die Tastenkombination verwenden `Ctrl+Shift+D` .

> [!div class="nextstepaction"]
> [Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
