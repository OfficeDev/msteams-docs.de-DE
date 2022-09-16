---
title: Erkunden des Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie mehr über das Erkunden des Teams-Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 0126953ac43b463460dcfd07c66354d39b53d690
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2022
ms.locfileid: "67781047"
---
# <a name="explore-teams-toolkit"></a>Erkunden des Teams-Toolkits

In diesem Dokument können Sie verschiedene UI-Elemente sowie beschreibung und grundlegende Verwendung im Teams-Toolkit für Visual Studio Code und Visual Studio verstehen.

::: zone pivot="visual-studio-code"

## <a name="teams-toolkit-for-visual-studio-code-basic-ui-elements"></a>Teams Toolkit für Visual Studio Code – grundlegende UI-Elemente

Nach der Installation des Teams-Toolkits wird die Benutzeroberfläche des Teams-Toolkits wie in der folgenden Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/overview1.png" alt-text="Übersicht über das Teams-Toolkit":::

| Seriennummer | UI-Elemente | Definition |
| --- | --- |
| 1 | **Erste Schritte** | Erkunden Sie das Teams-Toolkit. |
| &nbsp; | **Lernprogramme** | Greifen Sie auf verschiedene Lernprogramme zu. |
| &nbsp; | **Dokumentation** | Greifen Sie auf die Microsoft Teams-Entwicklerdokumentation zu. |
| 2 | **Erstellen einer neuen Teams-App** | Erstellen Sie eine neue Teams-App basierend auf Ihren Anforderungen. |
| 3 | **Beispiele anzeigen** | Erstellen Sie basierend auf vorhandenen Beispielen unterschiedliche App-Typen. |
| 4  | **Ordner öffnen** | Öffnen Sie die vorhandene Teams-App. |
| 5  | **Neue Datei** | Neue Datei erstellen. |
| &nbsp; | **Datei öffnen** | Öffnen Sie die vorhandene Datei. |
| &nbsp; | **Ordner öffnen** | Öffnen Sie den vorhandenen Ordner. |
| 6  | **Aktuell** | Zeigen Sie die zuletzt verwendeten Dateien an. |

### <a name="exploring-the-teams-toolkit-task-pane"></a>Erkunden des Aufgabenbereichs des Teams-Toolkits

Weitere UI-Elemente können Sie im Aufgabenbereich des Teams-Toolkits erkunden. Der Aufgabenbereich ist erst nach dem Erstellen einer App mithilfe des Teams-Toolkits sichtbar. Das folgende Video hilft Ihnen, mehr über den Prozess des Erstellens einer neuen Teams-App zu erfahren, und nach diesem Vorgang können Sie den Aufgabenbereich im Teams-Toolkit anzeigen.

   ![Erstellen einer Teams-App](~/assets/videos/javascript-tab-app1.gif)

Nach dem Erstellen einer neuen Teams-App sehen Sie die Verzeichnisstruktur der App im linken Bereich und die Infodatei im rechten Bereich.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/first-page.png" alt-text="Erste Seite des Teams-Toolkits":::

Machen wir eine Tour durch die Benutzeroberfläche des Teams-Toolkits.

 In der Visual Studio Code-Symbolleiste sind die folgenden Symbole für das Teams-Toolkit relevant:

| Symbol | Beschreibung |
| --- | --- |
| **Explorer** :::image type="icon" source="../assets/images/teams-toolkit-v2/file-explorer-icon.PNG":::  | So zeigen Sie die Verzeichnisstruktur der App an. |
| **Ausführen und Debuggen** :::image type="icon" source="../assets/images/teams-toolkit-v2/run-debug-icon.PNG":::  | So starten Sie den lokalen oder Remotedebuggingprozess. |
| **Teams Toolkit** :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: | So zeigen Sie den Aufgabenbereich im Teams-Toolkit an. |

Im Aufgabenbereich sehen Sie die folgenden Abschnitte:

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/accounts1.png" alt-text="Abschnitt &quot;Accounts&quot;":::
   :::column-end:::
   :::column span="":::

        Zum Entwickeln einer Teams-App benötigen Sie die folgenden Konten:
        
        * **Melden Sie sich bei M365 an**: Verwenden Sie Ihr Microsoft 365-Konto mit einem gültigen E5-Abonnement zum Erstellen Ihrer App.

        * **Melden Sie sich bei Azure an**: Verwenden Sie Ihr Azure-Konto für die Bereitstellung der App in Azure. Sie können ein [kostenloses Azure-Konto erstellen, bevor](https://azure.microsoft.com/free/) Sie beginnen.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/environment1.png" alt-text="Abschnitt &quot;Umgebung&quot;":::
   :::column-end:::
   :::column span="":::

        Um Ihre Teams-App bereitzustellen, benötigen Sie die folgenden Umgebungen:
        
       * **lokal**: Stellen Sie Ihre App in der lokalen Standardumgebung mit Konfigurationen der lokalen Computerumgebung bereit.

        * **dev**: Stellen Sie Ihre App in der Standardmäßigen Entwicklungsumgebung mit Remote- oder Cloudumgebungskonfigurationen bereit. Sie können nach Bedarf weitere Umgebungen erstellen.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/development.png" alt-text="Abschnitt &quot;Entwicklung&quot;":::
   :::column-end:::
   :::column span="":::

        Zum Erstellen und Anpassen Ihrer Teams-App benötigen Sie die folgenden Features:
        
       * **Erstellen einer neuen Teams-App**: Verwenden Sie den Toolkit-Assistenten, um das Projektgerüst für die App-Entwicklung vorzubereiten.

        * **Beispiele anzeigen**: Wählen Sie eine der Beispiel-Apps des Teams-Toolkits aus. Das Toolkit lädt den App-Code von GitHub herunter, und Sie können die Beispiel-App erstellen.
        
        * **Hinzufügen von Features**: Fügen Sie während des Entwicklungsprozesses weitere erforderliche Teams-Funktionen zur Teams-App hinzu, und fügen Sie optionale Cloudressourcen hinzu, die für Ihre App geeignet sind.
       
        * **Manifestdatei bearbeiten**: Bearbeiten Sie die Integration der Teams-App in den Teams-Client.
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deployment1.png" alt-text="Bereitstellungsabschnitt":::
   :::column-end:::
   :::column span="":::

        Um Ihre Teams-App bereitzustellen, bereitzustellen und zu veröffentlichen, benötigen Sie die folgenden Features:
        
        * **Bereitstellung in der Cloud**: Weisen Sie Azure-Ressourcen für Ihre Anwendung zu. Teams Toolkit ist in Azure Resource Manager integriert.

        * **Zip Teams-Metadatenpaket**: Erstellen Sie das App-Paket, das in Teams oder das Entwicklerportal hochgeladen werden kann. Es enthält das App-Manifest und App-Symbole.
        
        * **Bereitstellen in der Cloud**: Bereitstellen des Quellcodes in Azure.
       
        * **In Teams veröffentlichen**: Veröffentlichen Sie Ihre entwickelte App, und verteilen Sie sie in Bereiche wie Personal, Team, Kanal oder Organisation.
        
        * **Entwicklerportal für Teams**: Verwenden Sie das Entwicklerportal, um Ihre Teams-App zu konfigurieren und zu verwalten. 
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/help-and-feedback1.png" alt-text="Hilfe- und Feedbackabschnitt":::
   :::column-end:::
   :::column span="":::

        So greifen Sie auf weitere Informationen auf dem Teams-Toolkit zu. Sie benötigen die folgende Dokumentation und Ressourcen.
        
        * **Erste Schritte**: Anzeigen des Teams-Toolkits – Erste Schritte mit Hilfe in Visual Studio Code.

        * **Lernprogramme**: Wählen Sie diese Option aus, um auf verschiedene Lernprogramme zuzugreifen.
        
        * **Dokumentation**: Wählen Sie aus, um auf die Microsoft Teams-Entwicklerdokumentation zuzugreifen.
       
        * **Melden Sie Probleme auf GitHub**: Wählen Sie diese Option aus, um auf die GitHub-Seite zuzugreifen und probleme zu lösen.
   :::column-end:::
:::row-end:::

::: zone-end

::: zone pivot="visual-studio"

## <a name="explore-teams-toolkit-for-visual-studio"></a>Erkunden des Teams-Toolkits für Visual Studio

Nach der Installation des Teams-Toolkits können Sie die Optionen des Teams-Toolkits in zwei verschiedenen Methoden anzeigen:

# <a name="project"></a>[Projekt](#tab/prj)

Sie können unter **Project** auf das Teams-Toolkit zugreifen.

1. Wählen Sie **Project** > **Teams Toolkit** aus.
1. Sie können jetzt auf verschiedene Teams-Toolkit-Optionen zugreifen.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu_1.png" alt-text="Menü &quot;Teams-Toolkit-Vorgänge&quot;":::

# <a name="solution-explorer"></a>[Projektmappen-Explorer](#tab/solutionexplorer)

   Sie können unter **Projektmappen-Explorer** auf das Teams-Toolkit zugreifen.

1. Wählen Sie **"Ansicht** >  **Projektmappen-Explorer** aus, um Projektmappen-Explorer Bereich anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf Ihr **Projekt**.
1. Wählen Sie **das Teams-Toolkit** aus, um auf verschiedene Teams-Toolkit-Optionen zuzugreifen.

   :::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-operations-menu1_1.png" alt-text="Teams-Toolkit-Vorgänge aus Project":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname **"MyTeamsApp1**".

---

Nachdem Sie Ihr Teams-Projekt erstellt haben, können Sie die folgenden Funktionen im Teams-Toolkit für Visual Studio ausführen:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-menu-options.png"alt-text="Teams-Toolkit-Vorgänge über das Menü &quot;Projekt&quot;":::

|Funktion  |Beschreibung  |
|---------|---------|
|Vorbereiten von Abhängigkeiten von Teams-Apps     |Bevor Sie diesen Schritt mit einem lokalen Debuggen ausführen, können Sie die lokalen Debugabhängigkeiten einrichten und die Teams-App auf der Teams-Plattform registrieren. Sie benötigen ein Microsoft 365-Konto. Weitere Informationen finden Sie unter [Debuggen Ihrer Teams-App lokal mit Visual Studio](debug-teams-app-visual-studio.md)         |
|Manifestdatei öffnen     |Zum Öffnen der Teams-Manifestdatei können Sie mit der Maus auf die Parameter zeigen, um eine Vorschau der Werte anzuzeigen. Weitere Informationen finden [Sie unter Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)         |
|Updatemanifest im Teams-Entwicklerportal     |Wenn Sie die Manifestdatei aktualisieren, können Sie die Manifestdatei nur dann erneut in Azure bereitstellen, ohne das gesamte Projekt erneut bereitzustellen. Verwenden Sie diesen Befehl, um Ihre Änderungen auf remote zu aktualisieren. Weitere Informationen finden [Sie unter Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)       |
|Bereitstellung in der Cloud     |Diese Option hilft Ihnen beim Erstellen von Azure-Ressourcen, die Ihre Teams-App hosten. Weitere Informationen finden Sie unter [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)        |
|Bereitstellen in der Cloud     |Mit dieser Option können Sie Ihren Code in die Azure-Ressourcen kopieren, die bei der Bereitstellung in der Cloud erstellt wurden. Weitere Informationen finden [Sie unter Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)        |
|Vorschau in Teams     |Mit dieser Option wird der Teams-Webclient gestartet, und Sie können eine Vorschau der Teams-App in ihrem Browser anzeigen.         |
|Zip-App-Paket     |Diese Option generiert ein Teams-App-Paket im `Build` Ordner unter dem Projekt. Sie können das Paket auf den Teams-Client hochladen und die Teams-App ausführen.         |

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Installieren des Teams-Toolkits](install-Teams-Toolkit.md)
* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
* [Vorbereiten des Erstellens von Apps mit dem Microsoft Teams-Toolkit](build-environments.md)
* [Bereitstellen von Cloudressourcen mithilfe des Teams-Toolkits](provision.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)

<!--  
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ui-elements.png" alt-text="UI Elements":::

|Section|Features|Details
|---------|---------|--------|
| **1. ACCOUNTS** | &nbsp; | &nbsp; |
| &nbsp; |Microsoft 365 account|  Use your Microsoft 365 account with a valid E5 subscription for building your app.|
| &nbsp; | Azure Account |  Use your Azure account for deploying app on Azure. You can [create a free Azure account](https://azure.microsoft.com/free/) before you start.|
|**2.ENVIRONMENT** |  &nbsp; | &nbsp;|
| &nbsp; |Local |Deploy your app in the default local environment with local machine environment configurations.|
| &nbsp; | Dev |Deploy your app in the default dev environment with remote or cloud environment configurations. You can create more environments, as you need.|
| **3.DEVELOPMENT** | &nbsp; | &nbsp; |
| &nbsp; | Create a new Teams app | Teams Toolkit helps you to create and customize your Teams app project that makes the Teams app development work simpler. Create a new Teams app helps you to start with Teams app development by creating new Teams project using Teams Toolkit either by using **Create new project**|
| &nbsp; | View Samples | Select any of Teams Toolkit's sample apps. The toolkit downloads the app code from GitHub, and you can build the sample app.|
| &nbsp; | Add Features | It helps you to add additional Teams capabilities such as **Tab** or **Bot** or **Message extension** or **Command bot** or **Notification bot**, or **SSO enabled tab** optionally add Azure resources such as **Azure SQL Database** or **Azure Key Vault**, or **Azure function** or **Azure API Management** which fits your development needs to your current Teams app. You can also add **API connection** or **Single Sign-on** or **CI/CD workflows** for your Teams app.
| &nbsp; | Edit Manifest file | It helps you customize manifest file based on the app requirements |
| **4.DEPLOYMENT** | &nbsp; | &nbsp; |
| &nbsp;| Provision in the cloud | Allocate Azure resources for your application. Teams Toolkit is integrated with Azure Resource Manager.|
| &nbsp; | Zip Teams metadata package| Create the app package that can be uploaded to Teams or Developer Portal. It contains the app manifest and app icons. |
| &nbsp; | Deploy to the cloud| Deploy the source code to Azure.|
| &nbsp; | Publish to Teams| Publish your developed app and distribute it to scopes, such as personal, team, channel, or organization.|
| &nbsp; | Developer Portal for Teams| It is the primary tool for configuring, distributing, and managing your Microsoft Teams apps. You can collaborate with colleagues on your app, set up runtime environments, and much more. |
| **5.HELP AND FEEDBACK** | &nbsp; | &nbsp; |
| &nbsp; | Get Started |  View the Teams Toolkit Get started help within Visual Studio Code.|
| &nbsp; | Tutorials| Select to access different tutorials.|
| &nbsp; | Documentation| Select to access the Microsoft Teams Developer Documentation.|
| &nbsp; | Report issues on GitHub| It helps to get **Quick support** from product expert. Browse the existing issues before you create a new one, or visit [StackOverflow tag `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) to submit feedback.|
| **6.Explorer** | &nbsp; | &nbsp; |
 &nbsp; | &nbsp; | It helps to view the directory structure of your app.|
| **7.Run and Debug** | &nbsp; | &nbsp; |
 &nbsp; | &nbsp; | To start the local or remote debug process.|
-->
