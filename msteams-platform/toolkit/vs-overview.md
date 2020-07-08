---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Toolkit
ms.date: 06/30/2020
ms.openlocfilehash: e5715cf23cfd221b65afe0e6258ce06ff98770aa
ms.sourcegitcommit: 694babb79d379360a20cf928a9d2b88dd6d3bdd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "45051722"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio"></a>Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio

Mit dem Microsoft Teams-Toolkit können Sie benutzerdefinierte Teams-apps direkt in der Visual Studio Umgebung erstellen. Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie zum Erstellen, Debuggen und starten ihrer Teams-App benötigen.

## <a name="installing-the-teams-toolkit"></a>Installieren des Teams-Toolkits

Das Microsoft Teams-Toolkit für Visual Studio steht vom [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb von Visual Studio zum Download bereit.

## <a name="using-the-toolkit"></a>Verwenden des Toolkits

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Verpacken Ihrer APP](#package-your-app)
- [Ausführen ihrer app in Microsoft Teams](#install-and-run-your-app-locally)
- [Überprüfen Ihrer APP](#validate-your-app)
- [Veröffentlichen Ihrer APP](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams-Projekts

1. Erstellen Sie ein neues Projekt, und wählen Sie die Vorlage Microsoft Terams Toolkit aus.
1. Sie gelangen auf den Bildschirm **Funktionen hinzufügen** Konfigurieren der Eigenschaften für Ihre neue APP.
1. Klicken Sie auf die Schaltfläche **Fertig stellen** , um den Konfigurationsprozess abzuschließen.

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

1. Um Ihre APP zu konfigurieren, navigieren Sie zum **Microsoft Teams Toolkit** -Erweiterungsfenster.
1. Wählen Sie **App-Paket bearbeiten** aus, um die Seite **App-Details** anzuzeigen.
1. Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird. [Weitere Informationen](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Verpacken Ihrer APP

Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest**oder **. env** -Dateien im Ordner " **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert. Sie müssen [zwei Symbole](../concepts/build-and-test/apps-package.md#icons) in den gleichen Ordner einschließen.

## <a name="install-and-run-your-app-locally"></a>Lokal installieren und Ausführen der APP

Wählen Sie im Dropdownmenü *Lösungs Konfigurationen* die Option *Bereitstellen*aus. Drücken Sie die Schaltfläche *ISS Express + Teams* . Microsoft Teams wird gestartet, und der APP-Installationsdialog sollte im Microsoft Teams-Client angezeigt werden.

## <a name="validate-your-app"></a>Überprüfen Ihrer APP

Auf der Seite über **prüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre APP an AppSource senden. Laden Sie einfach das Manifest-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen. Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können. Bei den Tests, die schwer zu automatisieren sind, werden in der **vorläufigen Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie Links zu einer vollständigen Übermittlungs Prüfliste aufgeführt.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer APP in Microsoft Teams

Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden. Ihr IT-Administrator prüft diese Übermittlungen. Sie können zur Seite *veröffentlichen* zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.

> [!div class="nextstepaction"]
> [Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
