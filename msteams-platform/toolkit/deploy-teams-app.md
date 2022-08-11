---
title: Bereitstellen der Teams-App in der Cloud mit Visual Studio
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Apps in der Cloud, Azure oder SharePoint bereitstellen und Teams-Apps mithilfe des Teams-Toolkits in Visual Studio bereitstellen.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: be4eeb10e16b0dda4d789e4607ac8ffbc302b0e1
ms.sourcegitcommit: f192d7685ee3ddf4a55dc9787d56744403c3f8f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2022
ms.locfileid: "67302444"
---
# <a name="deploy-teams-app-to-the-cloud-using-visual-studio"></a>Bereitstellen der Teams-App in der Cloud mit Visual Studio

Das Teams-Toolkit hilft Ihnen beim Bereitstellen oder Hochladen des Front-End- und Back-End-Codes Ihrer Anwendung in die bereitgestellten Cloudressourcen in Ihrem Azure-Abonnement. Nach der Bereitstellung können Sie eine Vorschau der App im Teams-Client oder im Webbrowser anzeigen, bevor Sie mit der Verwendung beginnen können. Die folgenden Apps können in Visual Studio bereitgestellt werden:

* Die Registerkarten-App, z. B. Frontend-Anwendungen, wird im Azure-Speicher bereitgestellt und für statisches Webhosting konfiguriert.
* Die Benachrichtigungs-Bot-App mit Azure-Funktionstriggern kann für Azure-Funktionen bereitgestellt werden.
* Die Bot-App oder Nachrichtenerweiterung kann für Azure-App-Dienste bereitgestellt werden.

## <a name="prerequisite"></a>Voraussetzungen

Hier ist eine Liste der Tools, die Sie zum Erstellen und Bereitstellen Ihrer Apps benötigen.

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022, Version 17.3 | Sie können die Enterprise-Edition von Visual Studio und die "ASP.NET" Workload und Microsoft Teams-Entwicklungstools installieren. |
| &nbsp; | Teams Toolkit | Eine Visual Studio-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
| &nbsp; | Azure-Tools und [Microsoft Azure CLI](/cli/azure/install-azure-cli) | Azure-Tools für den Zugriff auf gespeicherte Daten oder die Bereitstellung eines cloudbasierten Back-End für Ihre Teams-App in Azure. |

  > [!NOTE]
  > Bevor Sie Projektcode in der Cloud bereitstellen, [stellen Sie Cloudressourcen für TTK Visual Studio](provision VS.md) bereit.

## <a name="deploy-teams-app-using-teams-toolkit"></a>Bereitstellen der Teams-App mithilfe des Teams-Toolkits

1. Starten Sie Visual Studio.
1. Wählen Sie **"Neues Projekt erstellen** " aus, oder öffnen Sie ein vorhandenes Projekt aus der Liste.
1. Klicken Sie mit der rechten Maustaste auf Ihr Projekt **"MyTeamsApp1**".
1. Wählen Sie **das Teams-Toolkit** aus.
1. Wählen Sie **"In der Cloud bereitstellen" aus...**

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-cloud.png" alt-text="Bereitstellen in der Cloud":::

   > [!NOTE]
   > In diesem Szenario lautet der Projektname "MyTeamsApp1".

1. Wählen Sie im Bestätigungsdialogfeld " **Bereitstellen** " aus.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-confirmation.png" alt-text="Bestätigungsdialogfeld für die Bereitstellung in der Cloud":::

1. Nachdem der Bereitstellungsprozess ausgelöst und abgeschlossen wurde, wird ein Popup mit der Bestätigung angezeigt, dass er erfolgreich bereitgestellt wurde. Sie können den Status auch im Ausgabefenster überprüfen.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/VS-deploy-popup.png" alt-text="Popupmenü &quot;Bereitstellen in der Cloud&quot;":::

Nachdem Ihr Projekt erfolgreich in Azure bereitgestellt wurde, gibt es verschiedene Möglichkeiten, eine Vorschau Ihrer App im Teams-Toolkit anzuzeigen:

1. Wählen Sie Das **Zip-App-Paket** des **Project** > **Teams-Toolkits** >  aus, um das Teams-App-Paket zu generieren.
1. Wählen Sie die Option **"Lokal"** oder **"Für Azure** " aus, und laden Sie sie in den Teams-Client hoch.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-ZipApp-package.png" alt-text="Generieren des Teams-App-Pakets":::

  **So zeigen Sie eine Vorschau Ihrer App im Teams-Client an**

3. Wählen Sie **"Projekt**" aus.
4. Wählen Sie **das Teams-Toolkit** aus.
5. Wählen Sie **"Vorschau" in Teams aus**.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams1.png" alt-text="Vorschau der Teams-App im Teams-Client":::

Die andere Möglichkeit, eine Vorschau Ihrer App anzuzeigen:

1. Klicken Sie im Bereich Průzkumník řešení mit der rechten Maustaste auf Ihr Projekt **"MyTeamsApp1**".
1. Wählen Sie **das Teams-Toolkit** aus.
1. Wählen Sie **"Vorschau" in Teams** aus, um die Teams-App im Webbrowser zu starten.

   :::image type="content" source="../assets/images/deploy-teams-app-cloud-vs/vs-deploy-preview-teams.png" alt-text="Vorschau der Teams-App im Webbrowser":::

   > [!NOTE]
   > Die gleichen Menüoptionen stehen im Menü "Projekt" zur Verfügung.

## <a name="see-also"></a>Siehe auch

* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Lokales Debuggen Ihrer Teams-App mit Visual Studio](debug-teams-app-visual-studio.md)
