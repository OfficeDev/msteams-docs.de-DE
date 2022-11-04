---
title: Bereitstellen in die Cloud
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie eine App in der Cloud, In Azure oder SharePoint bereitstellen und Teams-Apps mithilfe des Teams-Toolkits bereitstellen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 17d4d1d80f9ffd634e2fdae815b8504bb6c0ca99
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833135"
---
# <a name="deploy-teams-app-to-the-cloud"></a>Bereitstellen der Teams-App in der Cloud

Teams Toolkit unterstützt Sie beim Bereitstellen oder Hochladen des Front-End- und Back-End-Codes in Ihrer Anwendung in Ihren bereitgestellten Cloudressourcen in Azure.

::: zone pivot="visual-studio-code"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio-code"></a>Bereitstellen der Teams-App in der Cloud mithilfe von Visual Studio Code

Sie können Folgendes in der Cloud bereitstellen:

* Die Registerkarte, z. B. Front-End-Anwendungen, werden in Azure Storage bereitgestellt und für statisches Webhosting oder eine SharePoint-Website konfiguriert.
* Die Back-End-APIs werden in Azure Functions bereitgestellt.
* Der Bot oder die Nachrichtenerweiterung wird in Azure App Service bereitgestellt.

  > [!NOTE]
  > Bevor Sie App-Code in der Azure-Cloud bereitstellen, müssen Sie die [Bereitstellung von Cloudressourcen](provision.md) erfolgreich abschließen.

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Bereitstellen von Teams-Apps mithilfe des Teams-Toolkits

Die Anleitungen zu den ersten Schritten helfen Ihnen bei der Bereitstellung mithilfe des Teams-Toolkits. Sie können Folgendes verwenden, um Ihre Teams-App bereitzustellen:

* [Bereitstellen Ihrer App in Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Bereitstellen Ihrer App in SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Details zur Teams-App-Workload

| Teams-App-Workload | Quellcode | Erstellen eines Artefakts| Zielressource |
|-------------|----------|---------------|---------------|
|Registerkarten mit React </br> Die Front-End-Workload| `yourProjectFolder/tabs`| `tabs/build` |Azure Storage |
|Registerkarten mit SharePoint </br> Die Front-End-Workload | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint-App-Katalog |
|APIs auf Azure Functions </br> Die Back-End-Workload | `yourProjectFolder/api`| Nicht zutreffend |Azure Functions |
|Bots und Nachrichtenerweiterungen </br> Die Back-End-Workload | `yourProjectFolder/bot` | Nicht zutreffend | Azure App Services |

> [!NOTE]
> Wenn Sie eine Azure API Management-Ressource in Ihr Projekt einschließen und die Bereitstellung auslösen, können Sie Ihre APIs in Azure Functions im Azure API Management-Dienst veröffentlichen.

::: zone-end

::: zone pivot="visual-studio"

## <a name="deploy-teams-app-to-the-cloud-using-visual-studio"></a>Bereitstellen der Teams-App in der Cloud mithilfe von Visual Studio

Die folgenden Apps können in Visual Studio bereitgestellt werden:

* Die Registerkarten-App, z. B. Front-End-Anwendungen, wird in Azure Storage bereitgestellt und für statisches Webhosting konfiguriert.
* Die Benachrichtigungsbot-App mit Azure Functions Triggern kann in Azure Functions bereitgestellt werden.
* Die Bot-App oder Nachrichtenerweiterung kann in Azure-App Services bereitgestellt werden.

Nach der Bereitstellung können Sie eine Vorschau der App im Teams-Client oder im Webbrowser anzeigen, bevor Sie mit der Verwendung beginnen können.

## <a name="deploy-teams-app-using-teams-toolkit"></a>Bereitstellen der Teams-App mithilfe des Teams-Toolkits

1. Öffnen Sie Visual Studio.
1. Wählen Sie **Neues Projekt erstellen** aus, oder öffnen Sie ein vorhandenes Projekt aus der Liste.
1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt **MyTeamsApp1** > **Teams Toolkit** > **In der Cloud bereitstellen**.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-cloud.png" alt-text="Bereitstellen in der Cloud":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname MyTeamsApp1.

1. Wählen Sie im Bestätigungsdialogfeld **Bereitstellen** aus.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-confirmation.png" alt-text="Bestätigungsdialogfeld für die Bereitstellung in der Cloud":::

   Nach Abschluss des Bereitstellungsprozesses wird ein Popupfenster mit der Bestätigung angezeigt, dass die Bereitstellung erfolgreich war. Sie können den Status auch im Ausgabefenster überprüfen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/VS-deploy-popup.png" alt-text="Popup für die Bereitstellung in der Cloud":::

### <a name="preview-your-app"></a>Vorschau ihrer App

Um eine Vorschau Ihrer App anzuzeigen, müssen Sie zunächst ein ZIP-App-Paket erstellen und in den Teams-Client querladen.

1. Wählen Sie **Project** > **Teams Toolkit** > **Zip App-Paket aus**.
1. Wählen Sie die Option **Für lokal** oder **Für Azure** aus, um das Teams-App-Paket zu generieren.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-ZipApp-package1.png" alt-text="Generieren eines Teams-App-Pakets":::

**So zeigen Sie eine Vorschau Ihrer App im Teams-Client an**

1. Wählen Sie **Project** > **Teams Toolkit** > **Preview in Teams** aus.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams2.png" alt-text="Vorschau der Teams-App im Teams-Client":::

   Jetzt wird Ihre App quer in Teams geladen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Querladen der Teams-App in den Teams-Client":::

Die andere Möglichkeit, eine Vorschau Ihrer App anzuzeigen:

1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt **MyTeamsApp1** unter **Projektmappen-Explorer**.
1. Wählen Sie **Teams Toolkit** > **Preview in Teams** aus, um die Teams-App im Webbrowser zu starten.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams.png" alt-text="Vorschau der Teams-App im Webbrowser":::

   > [!NOTE]
   > Die gleichen Menüoptionen sind im Menü Projekt verfügbar.

   Jetzt wird Ihre App quer in Teams geladen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/sideload-teams.png" alt-text="Querladen der Teams-App in den Teams-Client":::

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Erstellen und Bereitstellen eines Azure-Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Erstellen von Teams-Apps mit mehreren Funktionen](add-capability.md)
* [Hinzufügen von Cloudressourcen zur Microsoft Teams-App](add-resource.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-project.md#create-new-teams-app-in-visual-studio)
* [Bereitstellen von Cloudressourcen mithilfe von Visual Studio](provision-cloud-resources.md)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Lokales Debuggen Ihrer Teams-App mithilfe von Visual Studio](debug-local.md#debug-your-teams-app-locally-using-visual-studio)
