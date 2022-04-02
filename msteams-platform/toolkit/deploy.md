---
title: Bereitstellen in die Cloud
author: MuyangAmigo
description: Bereitstellen der App in der Cloud, Azure oder SharePoint
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 35a60e718bb97cdcc24de66729e3929b2d21a59f
ms.sourcegitcommit: 2236204ff710f4eca606ceffb233572981f6edbe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2022
ms.locfileid: "64614530"
---
# <a name="deploy-to-the-cloud"></a>Bereitstellen in die Cloud

Teams Toolkit hilft Ihnen, den Front-End- und Back-End-Code in Ihrer Anwendung bereitzustellen oder in Ihre bereitgestellten Cloudressourcen in Azure hochzuladen.

* Die Registerkarte, z. B. Front-End-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting oder eine SharePoint-Website konfiguriert.
* Die Back-End-APIs werden in Azure-Funktionen bereitgestellt.
* Der Bot oder die Messaging-Erweiterung wird im Azure-App-Dienst bereitgestellt.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!NOTE]
>
> * Stellen Sie sicher, dass Teams App-Projekt im VS-Code geöffnet ist.
> * Bevor Sie Projektcode in der Cloud bereitstellen, [stellen Sie die Cloudressourcen bereit](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Bereitstellen Teams Apps mit Teams Toolkit

Die Anleitungen für die ersten Schritte helfen Ihnen bei der Bereitstellung mit Teams Toolkit. Sie können Folgendes verwenden, um Ihre Teams-App bereitzustellen:

* [Bereitstellen Ihrer App in Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Bereitstellen Ihrer App für SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Details zu Teams App-Workload

| Teams App-Workload | Quellcode | Buildartefakt| Zielressource |
|-------------|----------|---------------|---------------|
|Registerkarten mit React </br> Die Front-End-Workload| `yourProjectFolder/tabs`| `tabs/build` |Azure-Speicher |
|Registerkarten mit SharePoint </br> Die Front-End-Workload | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint App-Katalog |
|APIs für Azure-Funktionen </br> Die Back-End-Workload | `yourProjectFolder/api`| Nicht zutreffend |Azure-Funktionen |
|Bots und Messaging-Erweiterungen </br> Die Back-End-Workload | `yourProjectFolder/bot` | Nicht zutreffend | Azure-App-Dienst |

> [!NOTE]
> Wenn Sie die Azure-API-Verwaltungsressource in Ihr Projekt einschließen und die Bereitstellung auslösen. Sie können Ihre APIs in Azure-Funktionen im Azure-API-Verwaltungsdienst veröffentlichen.

## <a name="see-also"></a>Weitere Informationen

* [Hinzufügen weiterer Cloudressourcen](add-resource.md)
* [Erstellen und Bereitstellen eines Azure-Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Hinzufügen weiterer Teams App-Funktionen](add-capability.md)
* [Bereitstellen von Projektcode mit CI/CD-Pipelines](use-CICD-template.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
