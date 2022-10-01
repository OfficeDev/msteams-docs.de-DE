---
title: Installieren des Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie mehr über die Installation des Teams-Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 03d101df114d3f7564c78c433d01191172e180c9
ms.sourcegitcommit: 3aaccc48906fc6f6fbf79916af5664bf55537250
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68295984"
---
# <a name="install-teams-toolkit"></a>Installieren des Teams-Toolkits

In diesem Artikel wird beschrieben, wie Die Teams Toolkit-Erweiterung installiert wird.

## <a name="prerequisites"></a>Voraussetzungen

::: zone pivot="visual-studio-code"

Vor der Installation des Teams-Toolkits für Visual Studio Code müssen Sie [Visual Studio Code herunterladen und installieren](https://code.visualstudio.com/Download).

::: zone-end

::: zone pivot="visual-studio"

Vor der Installation des Teams-Toolkits für Visual Studio müssen Sie [Visual Studio 2022](https://aka.ms/VSDownload) mithilfe der Visual Studio-Installer herunterladen und installieren.

::: zone-end

::: zone pivot="visual-studio-code"

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Installieren Sie das Teams-Toolkit für Visual Studio Code

Sie können das Teams-Toolkit über das Fenster "Erweiterungen" in Visual Studio Code oder über den Visual Studio Marketplace installieren.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Starten Sie **Visual Studio Code**.
1. Öffnen Des Fensters Erweiterungen (**STRG+UMSCHALT+X** / **⌘⇧-X** oder **Ansicht > Erweiterungen**).

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="Screenshot zeigt, wie Sie installieren.":::

1. Geben Sie das **Teams-Toolkit** in das Suchfeld ein.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Screenshot des Toolkits.":::

1. Wählen Sie **Installieren** aus.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Screenshot der Installation von Toolkit 4.0.0.":::

   Nach der erfolgreichen Installation des Teams-Toolkits in Visual Studio Code wird auf der Visual Studio Code-Symbolleiste ein Symbol für das Teams-Toolkit angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Screenshot der Nachinstallationsansicht.":::

# <a name="marketplace"></a>[Markt](#tab/marketplace)

1. Wechseln Sie in einem Webbrowser zu [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-ttk-marketplace.png" alt-text="Screenshot der Installation von TTK Marketplace.":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Install-ttk.png" alt-text="Der Screenshot zeigt, wie TTK installiert wird.":::

1. Wählen Sie im Popupfenster " **Öffnen** " aus, um Visual Studio Code zu starten.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-open.png" alt-text="Screenshot zum Auswählen des geöffneten Bildschirms.":::

   Die Erweiterungsseite des Teams-Toolkits wird in Visual Studio Code angezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ttk-in-vsc.png" alt-text="Screenshot zeigt, wie Sie TTK in VSC auswählen.":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Der Screenshot zeigt, wie Sie &quot;TTK in VSC installieren&quot; auswählen.":::

   Nach der erfolgreichen Installation des Teams-Toolkits in Visual Studio Code wird auf der Visual Studio Code-Symbolleiste ein Symbol für das Teams-Toolkit angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Screenshot der Ansicht &quot;Nach der Installation&quot;.":::

---

## <a name="installing-a-different-release-version"></a>Installieren einer anderen Version

Visual Studio Code hält das Teams-Toolkit standardmäßig automatisch auf dem neuesten Stand. Wenn Sie eine andere Version installieren möchten, führen Sie die folgenden Schritte aus:

* Wählen Sie auf der Visual Studio Code-Symbolleiste das Symbol "Erweiterungen (:::image type="icon" source="../assets/images/teams-toolkit-v2/extension icon.PNG":::)" aus.
* Geben Sie das **Teams-Toolkit**  in das Suchfeld ein.
* Wählen Sie auf der Seite "Teams-Toolkit" den Dropdownpfeil neben der Schaltfläche " **Deinstallieren** " aus.
* Wählen Sie im Menü " **Andere Version installieren...** " aus, und wählen Sie aus, welche Version installiert werden soll.

## <a name="installing-a-pre-release-version"></a>Installieren einer Vorabversion

Die Erweiterung "Teams Toolkit für Visual Studio Code" ist auch auf GitHub verfügbar. Um Vorabversionen herunterzuladen, wechseln Sie [auf GitHub zur Seite "Releases"](https://github.com/OfficeDev/TeamsFx/releases) , und suchen Sie nach Erweiterungsdownloads, die als Vorabversion gekennzeichnet sind.

::: zone-end

::: zone pivot="visual-studio"

## <a name="install-teams-toolkit-for-visual-studio"></a>Installieren Sie das Teams-Toolkit für Visual Studio

   > [!IMPORTANT]
   > Wir empfehlen die Verwendung von Visual Studio 2022, Version 17.3.3 oder höher für das Teams-Toolkit, das die neueste Version ist, um mehrere bekannte Probleme in früheren Versionen von Visual Studio zu beheben.

1. [Laden Sie das Visual Studio-Installationsprogramm herunter](https://aka.ms/VSDownload), oder öffnen Sie es, wenn es bereits installiert ist.
2. Wählen Sie **"Installieren"** oder **"Ändern** " aus, wenn Visual Studio bereits installiert ist.
3. Wählen Sie die Registerkarte **"Workloads** " und dann die **ASP.NET- und Webentwicklungsworkload** aus.
4. Wählen Sie auf der rechten Seite im Abschnitt **"Optional**" im Bereich "**Installationsdetails**" die **Microsoft Teams-Entwicklungstools** aus.
5. Wählen Sie **"Ändern"** oder " **Installieren** " aus, um die Installation abzuschließen.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install_1.png" alt-text="Der Screenshot zeigt, wie Visual Studio installiert wird.":::

6. Wählen Sie nach Abschluss der Installation **"Starten** " aus, um Visual Studio zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch_1.png" alt-text="Screenshot zeigt, wie Visual Studio gestartet wird.":::

::: zone-end

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Teams-Toolkit installiert wurde, besuchen [Sie "Erstellen eines neuen Teams-Projekts](create-new-project.md) ", um zu beginnen.

## <a name="see-also"></a>Siehe auch

* [Erkunden des Teams-Toolkits](explore-Teams-Toolkit.md)
* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
* [Vorbereiten des Erstellens von Apps mit dem Microsoft Teams-Toolkit](build-environments.md)
* [Bereitstellen von Cloudressourcen mithilfe des Teams-Toolkits](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
