---
title: Installieren des Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie mehr über die Installation des Teams-Toolkits.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 07/29/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: e079f023d931af48d5c06151c585a059c3f7f803
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833079"
---
# <a name="install-teams-toolkit"></a>Installieren des Teams-Toolkits

In diesem Artikel wird beschrieben, wie Sie die Teams Toolkit-Erweiterung installieren.

## <a name="prerequisites"></a>Voraussetzungen

::: zone pivot="visual-studio-code"

Vor der Installation von Teams Toolkit für Visual Studio Code müssen Sie [Visual Studio Code herunterladen und installieren](https://code.visualstudio.com/Download).

::: zone-end

::: zone pivot="visual-studio"

Vor der Installation des Teams-Toolkits für Visual Studio müssen Sie [Visual Studio 2022 mithilfe des Visual Studio-Installer herunterladen und installieren](https://aka.ms/VSDownload).

::: zone-end

::: zone pivot="visual-studio-code"

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Installieren Sie das Teams-Toolkit für Visual Studio Code

Sie können das Teams-Toolkit über das Fenster Erweiterungen in Visual Studio Code oder über den Visual Studio Marketplace installieren.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Starten Sie **Visual Studio Code**.
1. Öffnen Sie das Fenster Erweiterungen (**STRG+UMSCHALT+X** / **⌘⇧-X** oder **Ansicht > Erweiterungen**).

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="Screenshot: Installation":::

1. Geben Sie **Teams Toolkit** in das Suchfeld ein.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Screenshot: Toolkit":::

1. Wählen Sie **Installieren** aus.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Screenshot: Installieren des Toolkits 4.0.0":::

   Nach erfolgreicher Installation des Teams-Toolkits in Visual Studio Code wird auf der Visual Studio Code-Symbolleiste ein Teams-Toolkit-Symbol angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Screenshot: Ansicht nach der Installation":::

# <a name="marketplace"></a>[Markt](#tab/marketplace)

1. Navigieren Sie in einem Webbrowser zum [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-ttk-marketplace.png" alt-text="Screenshot: Installation von TTK Marketplace":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Install-ttk.png" alt-text="Screenshot: Installieren von TTK":::

1. Wählen Sie im Popupfenster **Öffnen** aus, um Visual Studio Code zu starten.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-open.png" alt-text="Screenshot: Auswählen des geöffneten":::

   Die Erweiterungsseite des Teams-Toolkits wird in Visual Studio Code angezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/ttk-in-vsc.png" alt-text="Screenshot: Auswählen von TTK in VSC":::

1. Wählen Sie **Installieren** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-install-ttk.png" alt-text="Screenshot: Auswählen von &quot;TTK in VSC installieren&quot;":::

   Nach erfolgreicher Installation des Teams-Toolkits in Visual Studio Code wird auf der Visual Studio Code-Symbolleiste ein Teams-Toolkit-Symbol angezeigt.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/after-install.png" alt-text="Screenshot: Ansicht nach der Installation":::

---

## <a name="installing-a-different-release-version"></a>Installieren einer anderen Releaseversion

Standardmäßig hält Visual Studio Code das Teams Toolkit automatisch auf dem neuesten Stand. Wenn Sie eine andere Version installieren möchten, führen Sie die folgenden Schritte aus:

* Wählen Sie auf der Visual Studio Code-Symbolleiste das Symbol Erweiterungen (:::image type="icon" source="../assets/images/teams-toolkit-v2/extension icon.PNG":::) aus.
* Geben Sie **Teams Toolkit**  in das Suchfeld ein.
* Wählen Sie auf der Seite Teams Toolkit den Dropdownpfeil neben der Schaltfläche **Deinstallieren** aus.
* Wählen Sie im Menü **Weitere Version installieren...** aus, und wählen Sie die zu installierende Version aus.

## <a name="installing-a-pre-release-version"></a>Installieren einer Vorabversion

Die Erweiterung Teams Toolkit für Visual Studio Code ist auch auf GitHub verfügbar. Um Vorabversionen herunterzuladen, wechseln Sie auf [GitHub zur Seite Releases](https://github.com/OfficeDev/TeamsFx/releases) , und suchen Sie nach Erweiterungsdownloads, die als Vorabversion gekennzeichnet sind.

::: zone-end

::: zone pivot="visual-studio"

## <a name="install-teams-toolkit-for-visual-studio"></a>Installieren Sie das Teams-Toolkit für Visual Studio

   > [!IMPORTANT]
   > Es wird empfohlen, Visual Studio 2022 Version 17.3.3 oder höher für das Teams Toolkit zu verwenden. Dies ist die neueste Version, um mehrere bekannte Probleme in früheren Versionen von Visual Studio zu beheben.

1. [Laden Sie das Visual Studio-Installationsprogramm herunter](https://aka.ms/VSDownload), oder öffnen Sie es, wenn es bereits installiert ist.
2. Wählen **Sie Installieren** oder **Ändern** aus, wenn Visual Studio bereits installiert ist.
3. Wählen Sie die Registerkarte **Workloads** und dann die **Workload ASP.NET und Webentwicklung** aus.
4. Wählen Sie auf der rechten Seite im Bereich **Installationsdetails** im Abschnitt **Optional** die **Microsoft Teams-Entwicklungstools** aus.
5. Wählen Sie **Ändern** oder **Installieren** aus, um die Installation abzuschließen.

   :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-install_1.png" alt-text="Screenshot: Installieren von Visual Studio":::

6. Klicken Sie nach Abschluss der Installation auf **Starten** , um Visual Studio zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-overview/visual-studio-launch_1.png" alt-text="Screenshot: Starten von Visual Studio":::

::: zone-end

## <a name="next-steps"></a>Nächste Schritte

Nachdem Das Teams-Toolkit nun installiert wurde, besuchen [Sie Erstellen eines neuen Teams-Projekts](create-new-project.md) , um zu beginnen.

## <a name="see-also"></a>Siehe auch

* [Erkunden des Teams-Toolkits](explore-Teams-Toolkit.md)
* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
* [Vorbereiten der Erstellung von Apps mithilfe des Microsoft Teams-Toolkits](build-environments.md)
* [Bereitstellen von Cloudressourcen mithilfe des Teams Toolkits](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Erstellen einer neuen Teams-App in Visual Studio](create-new-project.md#create-new-teams-app-in-visual-studio)
* [Bereitstellen von Cloudressourcen mithilfe von Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mithilfe von Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)
