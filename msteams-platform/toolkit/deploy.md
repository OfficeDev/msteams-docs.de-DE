---
title: Bereitstellen in die Cloud
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie die App in der Cloud, Azure oder SharePoint bereitstellen und Teams-Apps mithilfe des Teams-Toolkits bereitstellen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 179a3002533e296e03dc0bb367b43880e95c3a1f
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2022
ms.locfileid: "67781104"
---
# <a name="deploy-teams-app-to-the-cloud"></a>Bereitstellen der Teams-App in der Cloud

Das Teams-Toolkit hilft Ihnen beim Bereitstellen oder Hochladen des Frontend- und Back-End-Codes in Ihrer Anwendung in Ihre bereitgestellten Cloudressourcen in Azure.

::: zone pivot="visual-studio-code"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio-code"></a>Bereitstellen der Teams-App in der Cloud mit Visual Studio Code

Sie können Folgendes in der Cloud bereitstellen:

* Die Registerkarte, z. B. Frontend-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting oder eine SharePoint-Website konfiguriert.
* Die Back-End-APIs werden für Azure-Funktionen bereitgestellt.
* Der Bot oder die Nachrichtenerweiterung wird im Azure-App-Dienst bereitgestellt.

  > [!NOTE]
  > Bevor Sie App-Code in der Azure-Cloud bereitstellen, müssen Sie die [Bereitstellung von Cloudressourcen](provision.md) erfolgreich abschließen.

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Bereitstellen von Teams-Apps mithilfe des Teams-Toolkits

Die Anleitungen "Erste Schritte" helfen Ihnen bei der Bereitstellung mithilfe des Teams-Toolkits. Sie können Folgendes verwenden, um Ihre Teams-App bereitzustellen:

* [Bereitstellen Ihrer App in Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Bereitstellen Ihrer App in SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Details zur Arbeitsauslastung der Teams-App

| Teams-App-Workload | Quellcode | Buildartefakte| Zielressource |
|-------------|----------|---------------|---------------|
|Registerkarten mit React </br> Die Frontend-Workload| `yourProjectFolder/tabs`| `tabs/build` |Azure Storage |
|Registerkarten mit SharePoint </br> Die Frontend-Workload | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint-App-Katalog |
|APIs für Azure-Funktionen </br> Die Back-End-Workload | `yourProjectFolder/api`| Nicht zutreffend |Azure-Funktionen |
|Bots und Nachrichtenerweiterungen </br> Die Back-End-Workload | `yourProjectFolder/bot` | Nicht zutreffend | Azure-App-Dienst |

> [!NOTE]
> Wenn Sie die Azure-API-Verwaltungsressource in Ihr Projekt einbeziehen und die Bereitstellung auslösen, können Sie Ihre APIs in Azure-Funktionen im Azure-API-Verwaltungsdienst veröffentlichen.

::: zone-end

::: zone pivot="visual-studio"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio"></a>Bereitstellen der Teams-App in der Cloud mit Visual Studio

Die folgenden Apps können in Visual Studio bereitgestellt werden:

* Die Registerkarten-App, z. B. Frontend-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting konfiguriert.
* Die Benachrichtigungs-Bot-App mit Azure-Funktionstriggern kann für Azure-Funktionen bereitgestellt werden.
* Die Bot-App oder Nachrichtenerweiterung kann für Azure-App-Dienste bereitgestellt werden.

Nach der Bereitstellung können Sie eine Vorschau der App im Teams-Client oder im Webbrowser anzeigen, bevor Sie mit der Verwendung beginnen können.

## <a name="deploy-teams-app-using-teams-toolkit"></a>Bereitstellen der Teams-App mithilfe des Teams-Toolkits

1. Öffnen Sie Visual Studio.
1. Wählen Sie **"Neues Projekt erstellen** " aus, oder öffnen Sie ein vorhandenes Projekt aus der Liste.
1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt **"MyTeamsApp1** > **Teams Toolkit** > **Deploy to the cloud**".

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-cloud.png" alt-text="Bereitstellen in der Cloud":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname "MyTeamsApp1".

1. Wählen Sie im Bestätigungsdialogfeld " **Bereitstellen** " aus.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-confirmation.png" alt-text="Bestätigungsdialogfeld für die Bereitstellung in der Cloud":::

   Nach Abschluss des Bereitstellungsprozesses wird ein Popup mit der Bestätigung angezeigt, dass es erfolgreich bereitgestellt wurde. Sie können den Status auch im Ausgabefenster überprüfen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/VS-deploy-popup.png" alt-text="Popupmenü &quot;Bereitstellen in der Cloud&quot;":::

### <a name="preview-your-app"></a>Anzeigen einer Vorschau Ihrer App

Um eine Vorschau Ihrer App anzuzeigen, müssen Sie zuerst ein Zip-App-Paket erstellen und in den Teams-Client querladen.

1. Wählen Sie Das **Zip-App-Paket** des **Project** > **Teams-Toolkits** >  aus.
1. Wählen Sie die Option **"Für lokal** " oder **"Für Azure** " aus, um das Teams-App-Paket zu generieren.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-ZipApp-package1.png" alt-text="Generieren des Teams-App-Pakets":::

**So zeigen Sie eine Vorschau Ihrer App im Teams-Client an**

1. Wählen Sie **Project** > **Teams Toolkit** > **Preview in Teams** aus.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams2.png" alt-text="Vorschau der Teams-App im Teams-Client":::

   Jetzt wird Ihre App in Teams quergeladen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Querladen der Teams-App im Teams-Client":::

Die andere Möglichkeit, eine Vorschau Ihrer App anzuzeigen:

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt **"MyTeamsApp1**" unter **Projektmappen-Explorer**.
1. Wählen Sie **"Teams Toolkit** > **Preview" in Teams** aus, um die Teams-App im Webbrowser zu starten.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams.png" alt-text="Vorschau der Teams-App im Webbrowser":::

   > [!NOTE]
   > Die gleichen Menüoptionen stehen im Menü "Projekt" zur Verfügung.

   Jetzt wird Ihre App in Teams quergeladen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Querladen der Teams-App im Teams-Client":::

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Erstellen und Bereitstellen eines Azure-Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Erstellen von Teams-Apps mit mehreren Funktionen](add-capability.md)
* [Hinzufügen von Cloudressourcen zur Microsoft Teams-App](add-resource.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Lokales Debuggen Ihrer Teams-App mit Visual Studio](debug-teams-app-visual-studio.md)
