---
title: Bereitstellen in die Cloud
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie die App in der Cloud, in Azure oder SharePoint bereitstellen und Teams Apps mit Teams Toolkit bereitstellen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: f7870a81c221182c98a0619d99c7cce255fcc170
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142052"
---
# <a name="deploy-to-the-cloud"></a>Bereitstellen in die Cloud

Teams Toolkit hilft Ihnen beim Bereitstellen oder Hochladen des Frontend- und Back-End-Codes in Ihrer Anwendung in Ihre bereitgestellten Cloudressourcen in Azure.

* Die Registerkarte, z. B. Frontend-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting oder eine SharePoint-Website konfiguriert.
* Die Back-End-APIs werden für Azure-Funktionen bereitgestellt.
* Der Bot oder die Nachrichtenerweiterung wird im Azure-App-Dienst bereitgestellt.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!NOTE]
>
> * Stellen Sie sicher, dass Sie das Teams-App-Projekt in VS-Code geöffnet haben.
> * Stellen Sie vor der Bereitstellung von Projektcode in [der Cloud die Cloudressourcen bereit](provision.md).

## <a name="deploy-teams-apps-using-teams-toolkit"></a>Bereitstellen Teams Apps mit Teams Toolkit

Die Anleitungen für die ersten Schritte helfen Ihnen bei der Bereitstellung mit Teams Toolkit. Sie können Folgendes verwenden, um Ihre Teams-App bereitzustellen:

* [Bereitstellen Ihrer App in Azure](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)
* [Bereitstellen Ihrer App für SharePoint](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch)

## <a name="details-on-teams-app-workload"></a>Details zu Teams App-Workload

| Teams App-Workload | Quellcode | Buildartefakte| Zielressource |
|-------------|----------|---------------|---------------|
|Registerkarten mit React </br> Die Frontend-Workload| `yourProjectFolder/tabs`| `tabs/build` |Azure Storage |
|Registerkarten mit SharePoint </br> Die Frontend-Workload | `yourProjectFolder/SPFx`| `SPFx/sharepoint/solution` |SharePoint App-Katalog |
|APIs für Azure-Funktionen </br> Die Back-End-Workload | `yourProjectFolder/api`| Nicht zutreffend |Azure-Funktionen |
|Bots und Nachrichtenerweiterungen </br> Die Back-End-Workload | `yourProjectFolder/bot` | Nicht zutreffend | Azure-App-Dienst |

> [!NOTE]
> Wenn Sie die Azure-API-Verwaltungsressource in Ihr Projekt einschließen und die Bereitstellung auslösen. Sie können Ihre APIs in Azure-Funktionen im Azure-API-Verwaltungsdienst veröffentlichen.

## <a name="see-also"></a>Siehe auch

* [Hinzufügen weiterer Cloudressourcen](add-resource.md)
* [Erstellen und Bereitstellen eines Azure-Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Hinzufügen weiterer Teams App-Funktionen](add-capability.md)
* [Bereitstellen von Projektcode mit CI/CD-Pipelines](use-CICD-template.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
