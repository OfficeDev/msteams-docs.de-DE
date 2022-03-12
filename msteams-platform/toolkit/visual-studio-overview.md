---
title: Erstellen von Apps mit dem Teams Toolkit und Visual Studio
description: Erste Schritte beim Erstellen von großartigen benutzerdefinierten Apps direkt in Visual Studio mit dem Microsoft Teams Toolkit. Erfahren Sie, wie Sie Ihre App in Visual Studio konfigurieren, ihre App überprüfen und über Visual Studio und das Entwicklerportal veröffentlichen.
keywords: Visual Studio-Toolkit für Teams
ms.localizationpriority: medium
ms.topic: overview
ms.date: 1/13/2022
ms.author: johmil
ms.openlocfilehash: c34f1113cd4da5f1b416dba6bc950b3588accecf
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453430"
---
# <a name="teams-toolkit-for-visual-studio"></a>Microsoft Teams-Toolkit-Erweiterung für Visual Studio

Erstellen, Testen und Entwickeln für Teams in Ihrer IDE.

Teams Toolkit-Erweiterung für Visual Studio erleichtert das Erstellen neuer Projekte für Teams, das automatische Einrichten von Apps im Teams Entwicklerportal, das Ausführen und Debuggen in Teams, das Konfigurieren von Cloudhosting und die Verwendung von [TeamsFx](https://github.com/OfficeDev/teamsfx) aus Ihrer IDE.

## <a name="install-teams-toolkit-for-visual-studio"></a>Installieren von Teams Toolkit für Visual Studio

>[!NOTE]
> Stellen Sie als Voraussetzung sicher, dass Sie Visual Studio 2022 17.1 Preview 2 oder höher verwenden, um die folgenden Anweisungen zu befolgen.

1. Wenn Sie bereits Visual Studio 2022 17.1 Preview 2 installiert haben, fahren Sie mit dem nächsten Schritt fort. Installieren Sie andernfalls [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/).
2. Öffnen Sie die Visual Studio-Installer.
3. Wählen Sie " **Ändern** " für die vorhandene VS 2022-Vorschauinstallation aus.
4. Wählen Sie die **Arbeitsauslastung für ASP.NET- und Webentwicklung** aus.
5. Erweitern Sie auf der rechten Seite den Abschnitt **ASP.NET und Webentwicklung**, und wählen Sie in der optionalen Liste der Komponenten **Microsoft Teams Entwicklungstools** aus.
6. Wählen Sie "**Installieren**" oder **"Ändern**" im Visual Studio-Installer aus, um den Installationsvorgang abzuschließen.

![Auswählen der Microsoft Teams Entwicklungstools im installierten Visual Studio-Installationsprogramm.)](images/teams-development-tools-vs-installer.png)

## <a name="get-started-quickly-with-a-new-project"></a>Erste Schritte schnell mit einem neuen Projekt

Teams Toolkit-Projektvorlagen enthalten den gesamten Code, die Dateien und die Konfiguration, die Sie für die ersten Schritte mit einem Teams App-Projekt benötigen.

Mit der Projektvorlage Microsoft Teams App können Sie ein Microsoft 365 Konto angeben, das erforderlich ist, um Ihre neue Teams-App automatisch zu registrieren und zu konfigurieren.

> [!NOTE]
> Wenn Sie nicht über ein Microsoft 365 Konto verfügen, können Sie sich für ein [Abonnement Microsoft 365 Entwicklerprogramms](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist 90 Tage kostenlos und wird verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise oder Professional Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits), das für die Lebensdauer Ihres Visual Studio Abonnements aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements](/office/developer-program/office-365-developer-program-get-started).

1. Starten Sie Visual Studio 2022.
1. Wählen Sie im Startfenster " **Neues Projekt erstellen**" aus.
1. Geben Sie im Feld **"Nach Vorlagen suchen**" Microsoft Teams App ein.
1. Wählen Sie die **Vorlage Microsoft Teams App** aus, und wählen Sie **"Weiter**" aus.
1. Geben **Sie im Fenster "Neues Projekt konfigurieren**" _HelloTeams_ in das **Feld Project Namen** ein, oder geben Sie es ein. Wählen Sie dann " **Erstellen" aus**.
1. Wählen **Sie im Fenster "Neue Teams Anwendung erstellen**" die Option "**Kontoauswahl auswählen**" aus, oder melden Sie sich bei einem Microsoft 365 Konto an. Wählen Sie dann " **Erstellen" aus**.

![Erstellen eines neuen Microsoft Teams App-Projekts in Visual Studio.](images/teams-toolkit-vs-new-project.png)

Visual Studio öffnet Ihr neues Projekt, und Teams Toolkit richtet Das neue Projekt im Teams Entwicklerportal ein. Das Projekt wird für die Teams Organisation hinzugefügt, die mit dem Microsoft 365 Konto verknüpft ist, das Sie in den obigen Schritten ausgewählt haben, und eine neue Azure Active Directory Registrierung erstellen. Dies ist erforderlich, damit die App in Teams ausgeführt werden kann.

## <a name="run-and-debug-your-app-in-teams"></a>Ausführen und Debuggen Ihrer App in Teams

Sie können Ihr App-Projekt lokal über Visual Studio starten.

1. Öffnen oder [erstellen Sie ein Teams App-Projekt](#get-started-quickly-with-a-new-project).
2. Drücken Sie **F5**, oder wählen Sie **Debuggen aus, > Debuggen** in Visual Studio starten.

Visual Studio startet Ihr Teams-App-Projekt in einem Browser und startet das Debuggen.

## <a name="host-your-teams-app-in-the-cloud-and-preview-it"></a>Hosten Ihrer Teams-App in der Cloud und Anzeigen einer Vorschau

Sie können Cloudressourcen für das Hosten Ihrer App in Azure mit Teams Toolkit erstellen und automatisch konfigurieren.

1. Wählen Sie im **Menü "Cloud" die option Project > Teams Toolkit > Bereitstellung** aus.
2. Wählen Sie im Fenster "Abonnement auswählen" das Azure-Abonnement aus, mit dem Sie Ressourcen erstellen möchten.

Teams Toolkit erstellt Azure-Ressourcen in diesem Abonnement, aber während dieses Schritts wird kein Code bereitgestellt. So stellen Sie Das Projekt für diese neuen Ressourcen bereit:

1. Wählen Sie im Menü **"Cloud" das Project > Teams Toolkit > Bereitstellen aus**.

## <a name="preview-your-app-running-from-cloud-resources"></a>Anzeigen einer Vorschau Ihrer App, die über Cloudressourcen ausgeführt wird

Sie können Ihre App in einem Browser mithilfe der Remoteressourcen ausführen, um zu überprüfen, ob alles funktioniert. In diesem Szenario ist das Debuggen noch nicht möglich.

1. Wählen Sie das **Menü Project > Teams Toolkit > Vorschau Teams App** aus.

Ihre App wird in einem Browser geöffnet und verwendet die Ressourcen, die durch die Schritte "Bereitstellen" und "Bereitstellen" erstellt wurden.

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

Im [Teams Entwicklerportal](https://dev.teams.microsoft.com/home) können Sie Ihre App in ein Team hochladen, Ihre App an den benutzerdefinierten App-Store Ihres Unternehmens für Benutzer in Ihrer Organisation übermitteln oder Ihre App für alle Teams Benutzer an App Source übermitteln.

- Ihr IT-Administrator wird diese Übermittlungen überprüfen.
- Sie können zur **Veröffentlichungsseite** zurückkehren, um ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App übermitteln oder alle derzeit aktiven Übermittlungen abbrechen.
