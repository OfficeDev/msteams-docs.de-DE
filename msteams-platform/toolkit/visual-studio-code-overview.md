---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Code Toolkit
ms.date: 06/30/2020
ms.openlocfilehash: 17f21d1656b32074318030b9df9e643200f58f80
ms.sourcegitcommit: ecf7ca8e77e77fe3f4cad1b13e3d31a825155555
ms.translationtype: Auto
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "45054252"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio-code"></a>Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code

Mit dem Microsoft Teams-Toolkit können Sie benutzerdefinierte Teams-apps direkt in der Visual Studio Code Umgebung erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie zum Erstellen, Debuggen und starten ihrer Teams-App benötigen.

## <a name="installing-the-teams-toolkit"></a>Installieren des Teams-Toolkits

Das Microsoft Teams-Toolkit für Visual Studio Code steht vom [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb Visual Studio Codes zum Download zur Verfügung.

> [!TIP]
> Nach der Installation sollte das Teams-Toolkit in der Leiste Visual Studio Code-Aktivität angezeigt werden. Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitäts Leiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu fixieren

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Importieren eines vorhandenen Projekts](#import-an-existing-teams-app-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Ihrer APP](#package-your-app)
- [Ausführen ihrer app in Microsoft Teams](#run-your-app-in-teams)
- [Überprüfen Ihrer APP](#validate-your-app)
- [Veröffentlichen Ihrer APP](#publish-your-app-to-teams)

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
1. Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. [Weitere Informationen](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Ihrer APP

Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest**oder **. env** -Dateien im Ordner " **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert. Sie müssen [zwei Symbole](../concepts/build-and-test/apps-package.md#icons) in den gleichen Ordner einschließen.

## <a name="install-and-run-your-app-locally"></a>Lokal installieren und Ausführen der APP

Ausführliche Anweisungen zum Verpacken und Testen Ihrer APP erhalten Sie im Abschnitt **Erstellen und ausführen* von Inhalten auf der Startseite des Projekts. Im Allgemeinen müssen Sie den Server Ihrer APP installieren, ihn ausführen lassen und dann eine Tunnellösung einrichten, damit Teams auf Inhalte zugreifen können, die von localhost aus gestartet werden.

## <a name="add-a-trusted-certificate-for-localhost"></a>Hinzufügen eines vertrauenswürdigen Zertifikats für localhost

Wenn Sie Ihre registerkartenbasierte App auf localhost mithilfe von HTTPS debuggen möchten, müssen Sie ein Zertifikat für localhost zum Katalog hinzufügen `Trusted Root Certification Authorities` . Sie müssen diesen Schritt nur einmal pro Computer ausführen.</br></br>

**Erstellen und Installieren eines vertrauenswürdigen Zertifikats:**
<details>
  <summary>Hier erweitern</summary>

* Erstellen und Ausführen der APP
  * Folgen Sie den Anweisungen im Abschnitt **Erstellen und ausführen** der Projekt-Readme-Datei, damit Sie von bereitgestellt wird https://localhost:3000/tab . Im allgemeinen umfasst dies die Ausführung von `npm install` Then`npm start`
  * Navigieren zu https://localhost:3000/tab von Google Chrome

* Erwerben Sie das SSL-Zertifikat:
  * Öffnen Sie das Fenster Chrome Developer Tools ( `ctrl + shift + i`  /  `cmd + option + i` ).
  * Klicken Sie auf die `Security` Registerkarte
  * Klicken Sie auf `View certificate` und Sie haben die Möglichkeit, das Zertifikat herunterzuladen – entweder durch Ziehen auf Ihren Desktop in OS X oder durch Klicken auf die `Details` Registerkarte in Windows und dann auf`Copy to File…`
  * Nennen Sie die Datei <*alles*>. CER, und speichern Sie Sie in einem Ordner, für den keine Zustimmung des Administrators erforderlich ist, um eine Schreibaktion auszuführen.
  
* Installieren des Zertifikats unter **Windows**
  * Wählen Sie die `DER encoded binary X.509 (.CER)` Option (die erste) aus, und speichern Sie Sie.
  * Doppelklicken Sie auf das Zertifikat, und installieren Sie es.
  * Wählen Sie`Local Machine`
  * Wählen Sie`Place all certificates in the following store`
  * Wählen Sie`Trusted Root Certification Authorities`
  * Bestätigen der Installation
  
* Installieren des Zertifikats **Mac OS X**
  * Öffnen Sie unter OS X das Dienstprogramm "Schlüsselbund-Access" und wählen Sie im `System` Menü auf der linken Seite. Klicken Sie auf das Schlosssymbol, um Änderungen zu aktivieren.
  * Klicken Sie auf die Schaltfläche Plus am unteren Rand, um ein neues Zertifikat hinzuzufügen, und wählen Sie die Datei aus, die `localhost.cer` Sie auf den Desktop gezogen haben. Klicken Sie `Always Trust` in das angezeigte Dialogfeld.
  * Nachdem Sie das Zertifikat dem System-Schlüsselbund hinzugefügt haben, doppelklicken Sie auf das Zertifikat, und erweitern Sie den `Trust` Abschnitt mit den Zertifikatdetails. Wählen Sie `Always Trust` für jede Option aus.

> [!IMPORTANT]
> Wenn Sie eine Sicherheitszertifikat Warnung erhalten, navigieren Sie zu https://localhost:3000/tab . Wenn die Website immer noch nicht vertrauenswürdig ist, starten Sie Ihren Computer neu, und localhost sollte als vertrauenswürdig akzeptiert werden.
</details>

## <a name="run-your-app-in-teams"></a>Ausführen ihrer app in Microsoft Teams
- Voraussetzungen:
  - [Aktivieren von Microsoft Teams Developer Preview Mode](https://aka.ms/teams-toolkit-enable-devpreview)

1. Navigieren Sie auf der linken Seite des Visual Studio Code Fensters zur Aktivitäts Leiste.
1. Wählen Sie das Symbol **Ausführen** aus, um die Ansicht **ausführen und Debuggen** anzuzeigen.
1. Sie können auch die Tastenkombination verwenden `Ctrl+Shift+D` .

## <a name="validate-your-app"></a>Überprüfen Ihrer APP

Auf der Seite über **prüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre APP an AppSource senden. Laden Sie einfach das Manifest-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen. Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können. Bei den Tests, die schwer zu automatisieren sind, werden in der **vorläufigen Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie Links zu einer vollständigen Übermittlungs Prüfliste aufgeführt.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer APP in Microsoft Teams

Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden. Ihr IT-Administrator prüft diese Übermittlungen. Sie können zur Seite *veröffentlichen* zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.

> [!div class="nextstepaction"]
> [Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
