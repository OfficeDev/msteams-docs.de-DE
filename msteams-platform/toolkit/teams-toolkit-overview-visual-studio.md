---
title: Übersicht über das Teams-Toolkit für Visual Studio
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Übersicht über das Teams-Toolkit für Visual Studio
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
ms.openlocfilehash: 3685d105f13024507b880c35040b9d798a6d845f
ms.sourcegitcommit: b9ec2a17094cb8b24c3017815257431fb0a679d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2022
ms.locfileid: "67990917"
---
# <a name="teams-toolkit-overview-for-visual-studio"></a>Übersicht über das Teams-Toolkit für Visual Studio

Das Teams-Toolkit für Visual Studio hilft Ihnen beim Erstellen, Debuggen und Bereitstellen von Microsoft Teams-Apps. Teams Toolkit für Visual Studio ist GA in Visual Studio 2022, Version 17.3. Die App-Entwicklung mit dem Teams-Toolkit bietet folgende Vorteile:

* Integrierte Identität
* Zugriff auf Cloudspeicher
* Daten von Microsoft Graph
* Azure- und Microsoft 365-Dienste mit Zero-Configuration-Ansatz

Für die Entwicklung von Teams-Apps können Sie auch [das CLI-Tool](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) verwenden, ähnlich dem Teams-Toolkit für Microsoft Visual Studio-Code, der das Toolkit `teamsfx`enthält.

Das Teams-Toolkit bietet alle Tools, die zum Erstellen einer Teams-App an einem zentralen Ort erforderlich sind.

> [!NOTE]
> Das Teams-Toolkit ist in anderen Versionen nicht verfügbar.

## <a name="user-journey-of-teams-toolkit"></a>User Journey of Teams Toolkit

Das Teams-Toolkit automatisiert manuelle Arbeit und bietet Ihnen eine großartige Integration von Teams- und Azure-Ressourcen. Die folgende Abbildung zeigt die Benutzerreise:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png" alt-text="Teams-Toolkit–Benutzerreise":::

Die wichtigsten Meilensteine dieser Reise sind:

1. Sie können zunächst ein neues Projekt erstellen oder versuchen, eine Beispiel-Teams-App zu erstellen.
1. Anschließend können Sie Code oder die Manifestdatei nach Bedarf bearbeiten.
1. Zum Erstellen und Debuggen der Teams-App können Sie Ihr Microsoft 365-Konto verwenden.
1. Für die Bereitstellung und Bereitstellung Ihrer App in der Cloud können Sie Ihr Azure-Konto verwenden.
1. Sie können Ihre App endlich in Teams veröffentlichen.

## <a name="install-teams-toolkit-for-visual-studio"></a>Installieren Sie das Teams-Toolkit für Visual Studio

Sie können das neueste Visual Studio-Installationsprogramm von der [Visual Studio-Downloadseite](https://visualstudio.microsoft.com) herunterladen.

> [!NOTE]
> Sie müssen zuerst das Visual Studio-Installationsprogramm installieren, bevor Sie Visual Studio installieren.

Nachdem Sie das Visual Studio-Installationsprogramm geöffnet haben, im Popupfenster "Workloads".

1. Aktivieren Sie das Kontrollkästchen **ASP.NET- und Webentwicklungsworkload** .
1. Aktivieren Sie das Feld **"Microsoft Teams-Entwicklungstools** " im Bereich "Installationsdetails".
1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install1.png" alt-text="Visual Studio-Installation":::

1. Wählen Sie **"Starten"** aus, um Visual Studio zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch.png" alt-text="Starten von Visual Studio":::

   > [!IMPORTANT]
   > Es wird empfohlen, Visual Studio 2022, Version 17.3.0, herunterzuladen, da Teams Toolkit für Visual Studio ga in dieser Version ist. Dieser Artikel wurde für Visual Studio 2022, Version 17.3.0, geschrieben. Teams Toolkit Version 17.3.* oder höher.

## <a name="take-a-tour-of-teams-toolkit"></a>Machen Sie eine Tour durch das Teams-Toolkit

Nachdem Sie das Teams-Toolkit installiert haben, können Sie sich die verschiedenen Menüoptionen des Teams-Toolkits kurz ansehen:

1. Wählen Sie **"Projekt**" aus.
1. Wählen Sie **das Teams-Toolkit** aus.
1. Sie können jetzt auf die **Menüoptionen des Teams-Toolkits** zugreifen.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu.png" alt-text="Menü &quot;Teams-Toolkit-Vorgänge&quot;":::

   Sie können auch über Projektmappen-Explorer auf das Menü des Teams-Toolkits zugreifen.

4. Klicken Sie mit der rechten Maustaste auf Ihr **Projekt**.
5. Wählen Sie **die Menüoptionen** des **Teams Toolkit** >  Teams Toolkit aus.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu1.png" alt-text="Teams-Toolkit-Vorgänge aus Project":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname **"MyTeamsApp1**".

Sie können die folgenden Funktionen im Teams-Toolkit für Visual Studio ausführen:

|Funktion  |Beschreibung  |
|---------|---------|
|Teams-Projekt erstellen     |Erstellen eines Teams-Projekts mithilfe der Teams-Vorlage in Visual Studio         |
|Vorbereiten von Abhängigkeiten von Teams-Apps     |Bevor Sie diesen Schritt mit einem lokalen Debuggen ausführen, können Sie die lokalen Debugabhängigkeiten einrichten und die Teams-App auf der Teams-Plattform registrieren. Sie benötigen ein Microsoft 365-Konto. Weitere Informationen finden Sie unter [Debuggen Ihrer Teams-App lokal mit Visual Studio](debug-teams-app-visual-studio.md)         |
|Manifestdatei öffnen     |Zum Öffnen der Teams-Manifestdatei können Sie mit der Maus auf die Parameter zeigen, um eine Vorschau der Werte anzuzeigen. Weitere Informationen finden [Sie unter Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)         |
|Updatemanifest im Teams-Entwicklerportal     |Wenn Sie die Manifestdatei aktualisieren, können Sie die Manifestdatei nur dann erneut in Azure bereitstellen, ohne das gesamte Projekt erneut bereitzustellen. Verwenden Sie diesen Befehl, um Ihre Änderungen auf remote zu aktualisieren. Weitere Informationen finden [Sie unter Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)       |
|Bereitstellung in der Cloud     |Diese Option hilft Ihnen beim Erstellen von Azure-Ressourcen, die Ihre Teams-App hosten. Weitere Informationen finden Sie unter [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)        |
|Bereitstellen in der Cloud     |Mit dieser Option können Sie Ihren Code in die Azure-Ressourcen kopieren, die bei der Bereitstellung in der Cloud erstellt wurden. Weitere Informationen finden [Sie unter Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)        |
|Vorschau in Teams     |Mit dieser Option wird der Teams-Webclient gestartet, und Sie können eine Vorschau der Teams-App in ihrem Browser anzeigen.         |
|Zip-App-Paket     |Diese Option generiert ein Teams-App-Paket im `Build` Ordner unter dem Projekt. Sie können das Paket auf den Teams-Client hochladen und die Teams-App ausführen.         |

Die folgenden Vorgänge werden im Teams-Toolkit für Visual Studio noch nicht unterstützt, im Vergleich zum Teams-Toolkit für Visual Studio Code, sind jedoch in der zukünftigen Produktübersicht geplant.

* Fügen Sie Ihrer Teams-App weitere Teams-Funktionen hinzu.
* Hinzufügen weiterer Azure-Ressourcen zu Ihrer Teams-App
* Fügen Sie Ihrer Teams-App einmaliges Anmelden hinzu.
* Fügen Sie Ihrer Teams-App eine API-Verbindung hinzu.
* Anpassen des Azure AD-Manifests.
* Fügen Sie CI/CD-Pipelines hinzu.
* Verwalten sie mehrere Cloudumgebungen.
* Zusammenarbeiten an Teams-Projekten.
* Veröffentlichen Sie die Teams-App.

### <a name="teamsfx-net-sdk-reference-docs"></a>TeamsFx .NET SDK-Referenzdokumente

* [Microsoft.Extensions.DependencyInjection-Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx-Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration-Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation-Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper-Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

## <a name="see-also"></a>Siehe auch

* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
