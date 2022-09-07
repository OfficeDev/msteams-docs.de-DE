---
title: Bereitstellen in die Cloud
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie die App in der Cloud, Azure oder SharePoint bereitstellen und Teams-Apps mithilfe des Teams-Toolkits bereitstellen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9ad2c9d16901990344ca521599b94b84b0e76217
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616926"
---
# <a name="deploy-teams-app-to-the-cloud"></a>Bereitstellen der Teams-App in der Cloud

Das Teams-Toolkit hilft Ihnen beim Bereitstellen oder Hochladen des Frontend- und Back-End-Codes in Ihrer Anwendung in Ihre bereitgestellten Cloudressourcen in Azure. Sie können Folgendes in der Cloud bereitstellen:

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

## <a name="see-also"></a>Siehe auch

* [Erstellen und Bereitstellen eines Azure-Clouddiensts](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
* [Erstellen von Teams-Apps mit mehreren Funktionen](add-capability.md)
* [Hinzufügen von Cloudressourcen zur Microsoft Teams-App](add-resource.md)
