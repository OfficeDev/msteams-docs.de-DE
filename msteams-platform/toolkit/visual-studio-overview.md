---
title: Erstellen Sie Apps mit dem Microsoft Teams Toolkit und Visual Studio
description: Beginnen Sie mit dem Erstellen großartiger benutzerdefinierter Apps direkt innerhalb Visual Studio mit dem Microsoft Teams Toolkit
keywords: Teams visuelles Studio-Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: eb94a8de0355283344ebe890a6fa3a3050e243ea
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566551"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a>Erstellen von Apps mit dem Teams Toolkit und Visual Studio

Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen. Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.

## <a name="prerequisites"></a>Voraussetzungen

1. [Aktivieren Sie die Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).

1. Stellen Sie sicher, dass das **<span>ASP.NE</span>T- und Webentwicklungsmodul** zu Ihrer Visual Studio-Instanz hinzugefügt wurde. Sie können die folgenden Schritte im Visual Studio ändern ausführen, [indem Sie Workloads und Komponentendokumentation hinzufügen oder entfernen.](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true)

![Visual Studio asp.net Modul](../assets/images/visual-studio-web-dev-module.png)

3. Wenn Sie Ihre App testen möchten, indem Sie sie von Visual Studio bereitstellen, müssen Sie IIS (Internetinformationsdienste) in Ihrer Entwicklungsumgebung installiert haben. Visual Studio enthält iIS nicht und ist nicht in der Standardkonfiguration Windows 10, Windows 8 oder Windows 7 enthalten. Sie können jedoch die neueste Version aus dem [Microsoft-Downloadcenter](https://www.microsoft.com/download/details.aspx?id=48264)herunterladen.

![IIS-Downloadseite ansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Microsoft Teams Toolkit for Visual Studio steht im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt im Menü **Erweiterungen** innerhalb Visual Studio zum Download bereit.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Sie Ihre App](#package-your-app)
- [Führen Sie Ihre App in Teams](#install-and-run-your-app-locally)
- [Validieren Ihrer App](#validate-your-app)
- [Veröffentlichen eigener Apps](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekts

1. Wählen **Sie Erstellen eines neuen Projekts** aus.
1. Wählen Sie **Microsoft Teams App** und wählen Sie **Weiter**.
1. Sie gelangen zum **neuen Projektbildschirm Konfigurieren,** auf dem Sie den **Project Namen**, **Standort** und **Projektmappennamen** auswählen können.
1. Aktivieren Sie das Kontrollkästchen **Lösung und Projekt platzieren im selben Verzeichnis**.
1. In einem Popupfenster mit der Bezeichnung **"Funktionen hinzufügen"** können Sie eine oder mehrere Funktionen für ihre Projekteinrichtung auswählen.
1. Wählen Sie die Schaltfläche **Weiter** aus, um den Konfigurationsvorgang abzuschließen.
1. In einem Popupfenster mit der Bezeichnung **"Funktionen hinzufügen"** können Sie die Eigenschaften für jede ausgewählte Funktion auswählen.
1. Wählen Sie **Fertig stellen** und Sie werden auf der **Microsoft Teams Toolkit-Zielseite** landen.

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams-App drei Komponenten:

  1. Der Microsoft Teams Client (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anfragen nach Inhalten reagiert, die in Teams angezeigt werden, z. B. HTML-Registerkarteninhalt oder eine adaptive Bot-Karte .
  1. Ein Teams-App-Paket besteht aus drei Dateien:

      > [!div class="checklist"]
      >
      > - Die manifest.jsauf
      > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen oder Organisations-App-Katalog angezeigt werden soll
      > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Teams Aktivitätsleiste.

Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter denen sich die Dienste befinden.

> [!NOTE]
>Wenn Sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 oder Konto anmelden, um mit dem Entwicklungsprozess fortzufahren.
>
> Wenn Sie kein Microsoft 365 Konto haben, können Sie sich für ein [Abonnement des Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) anmelden. Es ist 90 Tage *lang kostenlos* und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio *Enterprise* oder *Professional* Abonnement verfügen, verfügen beide Programme über ein kostenloses Microsoft 365 [Entwicklerabonnement,](https://aka.ms/MyVisualStudioBenefits)das für die Dauer Ihres Visual Studio Abonnements aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements](/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Konfigurationsschritte 

1. Um Ihre App zu konfigurieren, wählen Sie auf der **Zielseite Microsoft Teams Toolkit** **App-Paket bearbeiten** aus.
1. Wählen Sie im Dropdown-Menü **Meine Umgebungen** die **Option Entwicklung** aus.
1. Sie landen auf der **App-Detailseite,** auf der Sie die Eigenschaftenfelder Ihrer App bearbeiten können.
1. Durch das Bearbeiten der Felder auf der Seite App-Details wird der Inhalt der manifest.jsin der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. [Weitere Informationen](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Sie Ihre App

Wenn Sie die **App-Detailseite** ändern oder die **Manifest-** oder **.env-Dateien** im  **.publish-Ordner** Ihrer App aktualisieren, werden automatisch Ihre **Development.zip** Datei generiert. Die Development.zip-Datei enthält drei erforderliche Dateien – die **manifest.jsein** und [zwei Symbole](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen Ihrer App lokal

1. Wählen Sie im Dropdownmenü **Lösungskonfigurationen** die Option **Bereitstellen** wie im folgenden Bild gezeigt aus:

    ![Menü für Lösungskonfigurationen](../assets/images/solution-configurations.png)

2. Wählen Sie die Schaltfläche **IIS Express + Teams** aus.

1. Teams wird gestartet, und der App-Installationsdialog sollte im Teams-Client angezeigt werden.

## <a name="validate-your-app"></a>Validieren Ihrer App

Auf der Seite **"Validieren"** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre App an AppSource senden. Laden Sie einfach das Manifestpaket hoch und das Validierungstool überprüft Ihre App mit allen manifesten Testfällen. Für jeden fehlgeschlagenen Test enthält die Beschreibung einen Dokumentationslink, mit dem Sie den Fehler beheben können. Für die schwer zu automatisierenden Tests werden in der **vorläufigen Checkliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie ein Link zu einer vollständigen Übermittlungs-Checkliste angezeigt.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

✔ Auf Ihrer Projekthomepage können Sie Ihre App in ein Team hochladen, Ihre App an den benutzerdefinierten App Store Ihres Unternehmens für Benutzer in Ihrer Organisation senden oder Ihre App an App Source für alle Teams Benutzer senden.

✔ Ihr IT-Administrator überprüft diese Einsendungen.

✔ Sie können zur **Seite Veröffentlichen** zurückkehren, um Ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier werden Sie auch kommen, um Updates an Ihre App zu senden oder alle derzeit aktiven Übermittlungen abzubrechen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
