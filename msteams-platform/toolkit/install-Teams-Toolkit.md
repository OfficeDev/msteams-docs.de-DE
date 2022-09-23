---
title: Installieren des Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie mehr über die Installation des Teams-Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 9b6492efed353e2f3228a04da292141679401e66
ms.sourcegitcommit: ef545fac5c0dbe970d81f53b1631930e9196eba3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2022
ms.locfileid: "67991656"
---
# <a name="install-teams-toolkit"></a>Installieren des Teams-Toolkits

Das Teams-Toolkit ist eine Erweiterung in Visual Studio und Visual Studio Code. In diesem Dokument erfahren Sie, wie Sie das Teams-Toolkit installieren.

::: zone pivot="visual-studio-code"

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Installieren Sie das Teams-Toolkit für Visual Studio Code

Bevor Sie mit der Installation beginnen, müssen Visual Studio Code und der Teams-Client installiert sein.

## <a name="steps-to-install-teams-toolkit"></a>Schritte zum Installieren des Teams-Toolkits

Sie können das Teams-Toolkit aus einer Erweiterung in Visual Studio Code und von Visual Studio Code Marketplace installieren. Die folgenden Schritte helfen Ihnen beim Installieren des Teams-Toolkits:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie **Visual Studio Code**.
1. Wählen Sie die Ansicht "Erweiterungen" (**STRG+UMSCHALT+X** / **⌘⇧-X** oder **Ansicht > Erweiterungen**) aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="installieren":::

1. Geben Sie das **Teams-Toolkit** in das Suchfeld ein.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Toolkit":::

1. Wählen Sie **Installieren** aus.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Installieren von Toolkit 4.0.0":::

   Nach der erfolgreichen Installation des Teams-Toolkits in Visual Studio Code wird das Symbol des Teams-Toolkits auf der Visual Studio Code-Symbolleiste angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Nach der Installation":::

# <a name="marketplace"></a>[Markt](#tab/marketplace)

1. Öffnen Sie [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

   Die folgende Seite wird angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-ttk-marketplace.png" alt-text="TTK Marketplace installieren":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Install-ttk.png" alt-text="TTK installieren":::

1. Wählen Sie im Popupfenster " **Öffnen**" aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-open.png" alt-text="Wählen Sie &quot;Öffnen&quot; aus.":::

   Die folgende Visual Studio Code-Seite wird angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ttk-in-vsc.png" alt-text="Auswählen von TTK in VSC":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Wählen Sie &quot;TTK in VSC installieren&quot; aus.":::

   Nach der erfolgreichen Installation des Teams-Toolkits in Visual Studio Code wird das Symbol des Teams-Toolkits auf der Visual Studio Code-Symbolleiste angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Nach der Installation":::

---

#### <a name="upgrade-teams-toolkit"></a>Aktualisieren des Teams-Toolkits

Das Teams-Toolkit wird standardmäßig auf die neueste Version aktualisiert. Mit den folgenden Schritten können Sie unterschiedliche Versionen installieren:

* Wählen Sie das Symbol "Erweiterungen :::image type="icon" source="../assets/images/teams-toolkit-v2/extension icon.PNG"::: " aus.
* Geben Sie das **Teams-Toolkit**  in das Suchfeld ein.
* Wählen Sie in der Erweiterung des Teams-Toolkits das Symbol aus :::image type="icon" source="../assets/images/teams-toolkit-v2/setting icon.PNG"::: .
* Wählen Sie **"Andere Version installieren** " aus, um auf die neueste Version des Teams-Toolkits zu aktualisieren.

::: zone-end

::: zone pivot="visual-studio"

## <a name="install-teams-toolkit-for-visual-studio"></a>Installieren Sie das Teams-Toolkit für Visual Studio

Bevor Sie mit der Installation beginnen, müssen Sie Visual Studio-Installer installieren.

Sie können die neuesten Visual Studio-Installer von der [Visual Studio-Downloadseite](https://visualstudio.microsoft.com) herunterladen.

## <a name="steps-to-install-teams-toolkit"></a>Schritte zum Installieren des Teams-Toolkits

Nachdem Sie die Visual Studio-Installer geöffnet haben, gehen Sie im Popupfenster "Workloads" wie folgt vor:

1. Wählen Sie die Workload **ASP.NET und Webentwicklung** aus.
1. Wählen Sie im Bereich "**Installationsdetails**" die **Microsoft Teams-Entwicklungstools** aus.
1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install_1.png" alt-text="Visual Studio-Installation":::

1. Wählen Sie **"Starten"** aus, um Visual Studio zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch_1.png" alt-text="Starten von Visual Studio":::

   > [!IMPORTANT]
   > Es wird empfohlen, Visual Studio 2022, Version 17.3.3, herunterzuladen, da teams Toolkit für Visual Studio ga in dieser Version ist. Dieser Artikel wurde für Visual Studio 2022, Version 17.3.3, geschrieben. Teams Toolkit Version 17.3.* oder höher.

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Erkunden des Teams-Toolkits](explore-Teams-Toolkit.md)
* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
* [Vorbereiten des Erstellens von Apps mit dem Microsoft Teams-Toolkit](build-environments.md)
* [Bereitstellen von Cloudressourcen mithilfe des Teams-Toolkits](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
