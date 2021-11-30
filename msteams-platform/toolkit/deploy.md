---
title: Bereitstellen in der Cloud
author: MuyangAmigo
description: Bereitstellen in der Cloud
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 3f7dc4b320bccfa8a6017f87045b27a37d8199f7
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61227737"
---
# <a name="deploy-to-the-cloud"></a>Bereitstellen in der Cloud

Teams Toolkit hilft Ihnen, den Front-End- und Back-End-Code in Ihrer Anwendung bereitzustellen oder in Ihre bereitgestellten Cloudressourcen in Azure hochzuladen.

* Die Registerkarte, z. B. Front-End-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting oder eine SharePoint Website konfiguriert.
* Die Back-End-APIs werden in Azure-Funktionen bereitgestellt.
* Die Bot- oder Messaging-Erweiterung wird im Azure App Service bereitgestellt.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Sie sollten bereits ein Teams App-Projekt in VS-Code geöffnet haben.

> [!NOTE]
> Bevor Sie Projektcode in der Cloud bereitstellen, führen Sie zuerst die Schritte zur Bereitstellung von [Cloudressourcen](provision.md) aus.


## <a name="deploy-teams-apps-using-teams-toolkit"></a>Bereitstellen Teams Apps mit Teams Toolkit

In Lernprogrammen für die ersten Schritte finden Sie schrittweise Anleitungen zur Bereitstellung mit Teams Toolkit. Sie können Folgendes verwenden, um Ihre Teams-App bereitzustellen:

* [Bereitstellen Ihrer App in Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Bereitstellen Ihrer App für SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workloads"></a>Details zu Teams App-Workloads

| Teams App-Workloads| Quellcode | Erstellen Artifacts| Zielressourcen |
|-------------|----------|---------------|---------------|
|Registerkarten mit React </br> Die Front-End-Workload| `yourProjectFolder/tabs`| `tabs/build` |Azure Storage |
|Registerkarten mit SharePoint </br> Die Front-End-Workload | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint App-Katalog |
|APIs für Azure-Funktionen </br> Die Back-End-Workload | `yourProjectFolder/api`| Nicht zutreffend |Azure Functions |
|Bots und Messaging-Erweiterungen </br> Die Back-End-Workload | `yourProjectFolder/bot` | Nicht zutreffend | Azure App Service |

> [!NOTE]
> Wenn Sie die Azure-API-Verwaltungsressource in Ihr Projekt einschließen und die Bereitstellung auslösen. Sie können Ihre APIs in Azure Functions im Azure API Management Service veröffentlichen.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Hinzufügen weiterer Cloudressourcen](add-resource.md)

> [!div class="nextstepaction"]
> [Hinzufügen weiterer Teams App-Funktionen](add-capability.md)

> [!div class="nextstepaction"]
> [Bereitstellen von Projektcode mit CI/CD-Pipelines](use-CICD-template.md)

> [!div class="nextstepaction"]
> [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)

> [!div class="nextstepaction"]
> [Zusammenarbeit mit anderen Entwicklern an Teams Projekt](TeamsFx-collaboration.md)
