---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Toolkit
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 5ba3cd8b5714876a96595aec295ff6d0066e115f
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "49476986"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Erstellen von apps mit dem Teams-Toolkit und Visual Studio

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen. Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="prerequisites"></a>Voraussetzungen

1. [Entwicklervorschau aktivieren](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. Stellen Sie sicher, dass das **<span>ASP.ne</span>T-und das Webentwicklungs Modul** zu Ihrer Visual Studio-Instanz hinzugefügt wurde. Sie können überprüfen, indem Sie die Schritte im [Visual Studio ändern durch Hinzufügen oder Entfernen von Arbeitslasten und Komponenten](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) Dokumentation durchführen.

![Visual Studio-ASP.NET-Modul](../assets/images/visual-studio-web-dev-module.png)

3. Wenn Sie Ihre APP testen möchten, indem Sie Sie aus Visual Studio bereitstellen, müssen Sie IIS (Internet Information Services) in Ihrer Entwicklungsumgebung installiert haben. Visual Studio enthält IIS nicht und ist nicht in der standardmäßigen Windows 10-, Windows 8-oder Windows 7-Konfiguration enthalten; Sie können die neueste Version jedoch aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=48264)herunterladen.

![IIS-Downloadseiten Ansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Installieren des Teams-Toolkits

Das Microsoft Teams-Toolkit für Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt im Menü " **Erweiterungen** " in Visual Studio zum Download bereit.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Ihrer APP](#package-your-app)
- [Ausführen ihrer app in Microsoft Teams](#install-and-run-your-app-locally)
- [Überprüfen Ihrer APP](#validate-your-app)
- [Veröffentlichen Ihrer APP](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams-Projekts

1. Wählen Sie **Neues Projekt erstellen** aus.
1. Klicken Sie auf **Microsoft Teams-App** , und wählen Sie **weiter** aus.
1. Sie gelangen auf den Bildschirm **configure your New Project** , in dem Sie den **Projektnamen**, den **Speicherort** und den **Lösungsnamen** auswählen können.
1. Aktivieren Sie das Kontrollkästchen **Projektmappe und Projekt in demselben Verzeichnis platzieren**.
1. Mit einem Popupfenster mit der Bezeichnung **Add-Funktionen** können Sie eine oder mehrere Funktionen für Ihr Projekt-Setup auswählen.
1. Klicken Sie auf die Schaltfläche **weiter** , um den Konfigurationsprozess abzuschließen.
1. Mit einem Popupfenster mit der Bezeichnung **Add-Funktionen** können Sie die Eigenschaften für jede ausgewählte Funktion auswählen.
1. Wählen Sie **Fertig stellen** aus, und Sie werden auf der Startseite von **Microsoft Teams Toolkit** landen.

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

> [!NOTE]
>Wenn Sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 oder-Konto anmelden, damit der Entwicklungsprozess fortgesetzt werden kann.
>
> Wenn Sie kein Microsoft 365-Konto haben, können Sie sich für ein [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) Abonnement anmelden. Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365- [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist. *Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Konfigurationsschritte 

1. Um Ihre APP zu konfigurieren, wählen Sie auf der Startseite des **Microsoft Teams Toolkit** die Option **App-Paket bearbeiten** aus.
1. Wählen Sie im Dropdownmenü **meine Umgebungen** die Option **Entwicklung** aus.
1. Sie landen auf der Seite mit den **App-Details** , auf der Sie die Eigenschaften Felder Ihrer APP bearbeiten können.
1. Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. [Weitere Informationen](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Ihrer APP

Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest** oder **. env** -Dateien im Ordner "  **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert. Die Development.zip Datei enthält drei erforderliche Dateien – die Dateien **manifest.js** und [zwei Symboldateien](../concepts/build-and-test/apps-package.md#icons).

## <a name="install-and-run-your-app-locally"></a>Lokal installieren und Ausführen der APP

1. Wählen Sie im Dropdownmenü **Lösungs Konfigurationen** die Option **Bereitstellen** aus.

![Menü "Lösungs Konfigurationen"](../assets/images/solution-configurations.png)

2. Wählen Sie die Schaltfläche **ISS Express + Teams** aus.

1. Microsoft Teams wird gestartet, und der APP-Installationsdialog sollte im Microsoft Teams-Client angezeigt werden.

## <a name="validate-your-app"></a>Überprüfen Ihrer APP

Auf der Seite über **prüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre APP an AppSource senden. Laden Sie einfach das Manifest-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen. Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können. Bei den Tests, die schwer zu automatisieren sind, werden in der **vorläufigen Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie Links zu einer vollständigen Übermittlungs Prüfliste aufgeführt.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer APP in Microsoft Teams

✔ Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden.

✔ Ihr IT-Administrator diese Übermittlungen prüft.

✔ Können Sie zur Seite **veröffentlichen** zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.

> [!div class="nextstepaction"]
> [Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
