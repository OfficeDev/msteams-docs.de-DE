---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter Apps direkt Visual Studio mit dem Microsoft Teams Toolkit
keywords: teams Visual Studio Toolkit
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

1. [Aktivieren der Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).

1. Stellen Sie sicher, **<span>dass ASP.NE</span>T-** und Webentwicklungsmodul zu Ihrer Visual Studio hinzugefügt wurde. Sie können dies überprüfen, indem Sie die Schritte in der Visual Studio ausführen, indem [Sie Arbeitsauslastungen und Komponentendokumentation](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) hinzufügen oder entfernen.

![Visual Studio asp.net Modul](../assets/images/visual-studio-web-dev-module.png)

3. Wenn Sie Ihre App testen möchten, indem Sie sie von Visual Studio bereitstellen, müssen Sie IIS (Internetinformationsdienste) in Ihrer Entwicklungsumgebung installiert haben. Visual Studio iiS ist nicht enthalten und nicht in der Standardkonfiguration Windows 10, Windows 8 oder Windows 7 enthalten. Sie können jedoch die neueste Version aus dem [Microsoft Download Center herunterladen.](https://www.microsoft.com/download/details.aspx?id=48264)

![IIS-Downloadseitenansicht](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a>Installieren des Teams Toolkits

Das Microsoft Teams Toolkit für Visual Studio steht im Visual Studio [Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) oder direkt über das  Menü Erweiterungen in Visual Studio.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Packen Ihrer App](#package-your-app)
- [Führen Sie Ihre App in Teams](#install-and-run-your-app-locally)
- [Validieren Ihrer App](#validate-your-app)
- [Veröffentlichen eigener Apps](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekt

1. Wählen **Sie Neues Projekt erstellen aus.**
1. Wählen **Microsoft Teams App aus,** und wählen Sie **Weiter aus.**
1. Sie gelangen zum Bildschirm **Konfigurieren Des** neuen Projekts, auf dem Sie den Namen **Project,** Standort **und** **Lösungsnamen auswählen können.**
1. Aktivieren Sie das Kontrollkästchen **Projekt und Projekt im gleichen Verzeichnis platzieren.**
1. In einem Popupfenster mit der Bezeichnung **Add Capabilities** können Sie eine oder mehrere Funktionen für Ihre Projekteinrichtung auswählen.
1. Wählen Sie die **Schaltfläche Weiter** aus, um den Konfigurationsprozess zu abschließen.
1. In einem Popupfenster mit der Bezeichnung **Add Capabilities** können Sie die Eigenschaften für jede ausgewählte Funktion auswählen.
1. Wählen **Sie Fertig** stellen aus, und Sie landen auf der Microsoft Teams Toolkit-Zielseite. 

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams drei Komponenten:

  1. Der Microsoft Teams (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anforderungen nach Inhalten reagiert, die in Teams angezeigt werden, z. B. HTML-Registerkarteninhalt oder eine adaptive Botkarte .
  1. Ein Teams-App-Paket besteht aus drei Dateien:

      > [!div class="checklist"]
      >
      > - The manifest.json
      > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen Oder Organisations-App-Katalog angezeigt werden soll
      > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige Teams Aktivitätsleiste.

Wenn eine App installiert ist, analysiert Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, in der sich die Dienste befinden.

> [!NOTE]
>Wenn Sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 oder Konto anmelden, um mit dem Entwicklungsprozess fortzufahren.
>
> Wenn Sie nicht über ein Microsoft 365 verfügen, können Sie sich für ein Microsoft 365 [Developer Program-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist *für* 90 Tage kostenlos und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio *Enterprise-* oder *Professional-Abonnement* verfügen, enthalten beide Programme ein kostenloses Microsoft 365-Entwicklerabonnement, das für die Lebensdauer Ihres Visual Studio ist. [](https://aka.ms/MyVisualStudioBenefits) Weitere Informationen finden Sie unter [Set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).
>

### <a name="configuration-steps"></a>Konfigurationsschritte 

1. Um Ihre App zu konfigurieren, wählen Sie **auf der Microsoft Teams Toolkit-Angebotsseite** **App-Paket bearbeiten aus.**
1. Wählen Sie **im Dropdownmenü** Meine Umgebungen die Option **Entwicklung aus.**
1. Sie landen auf der **Seite App-Details,** auf der Sie die Eigenschaftenfelder Ihrer App bearbeiten können.
1. Durch Bearbeiten der Felder auf der Seite App-Details werden die Inhalte der datei manifest.jsaktualisiert, die letztendlich als Teil des App-Pakets versandt werden. [Weitere Informationen](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Packen Ihrer App

Wenn Sie die **Seite** mit den App-Details ändern oder das  **Manifest aktualisieren,** oder **.env-Dateien** im Veröffentlichungsordner Ihrer App generieren Sie **Development.zip** Datei. Die Development.zip enthält drei erforderliche Dateien – die **manifest.jsund** [zwei Symbole](../concepts/build-and-test/apps-package.md#app-icons).

## <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen der App lokal

1. Wählen Sie **im Dropdownmenü Lösungskonfigurationen** die Option **Bereitstellen** aus, wie in der folgenden Abbildung dargestellt:

    ![Menü "Lösungskonfigurationen"](../assets/images/solution-configurations.png)

2. Wählen Sie **die Schaltfläche IIS Express + Teams** aus.

1. Teams wird gestartet, und der Dialog zur App-Installation sollte im Client Teams werden.

## <a name="validate-your-app"></a>Validieren Ihrer App

Auf **der Seite Überprüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre App an AppSource übermitteln. Laden Sie einfach das Manifestpaket hoch, und das Überprüfungstool überprüft Ihre App mit allen manifestbezogenen Testfällen. Für jeden fehlgeschlagenen Test enthält die Beschreibung einen Dokumentationslink, mit dem Sie den Fehler beheben können. Für die Tests, die schwer  zu automatisieren sind, enthält die vorläufige Prüfliste 7 der häufigsten fehlgeschlagenen Testfälle sowie einen Link zu einer vollständigen Übermittlungscheckliste.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

✔ Auf Ihrer Projekt-Homepage können Sie Ihre App in ein Team hochladen, Ihre App an Den benutzerdefinierten App-Store Ihres Unternehmens für Benutzer in Ihrer Organisation übermitteln oder Ihre App an die App-Quelle für alle benutzer Teams übermitteln.

✔ Ihr IT-Administrator überprüft diese Übermittlungen.

✔ Sie können zur Seite  Veröffentlichen zurückkehren, um ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App übermitteln oder derzeit aktive Übermittlungen abbrechen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
