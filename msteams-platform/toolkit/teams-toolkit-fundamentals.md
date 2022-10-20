---
title: Überblick über das Teams-Toolkit
author: zyxiaoyuer
description: Lernen Sie in diesem Modul das Teams-Toolkit, die Installation des Teams-Toolkits und die Benutzerreise des Teams-Toolkits kennen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 786bfd318f1cefa4329e54b5a19cba89a823bb5b
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615338"
---
# <a name="teams-toolkit-overview"></a>Überblick über das Teams-Toolkit

Das Teams-Toolkit erleichtert die ersten Schritte mit der App-Entwicklung für Microsoft Teams mit Visual Studio und Visual Studio Code.

* Beginnen mit einer Projektvorlage oder einem Beispiel
* Sparen von Setupzeit mit automatisierter App-Registrierung und -Konfiguration
* Ausführen und Debuggen in Teams direkt über vertraute Tools
* Smart defaults for hosting in Azure using infrastructure-as-code and Bicep
* Erstellen von eindeutigen Konfigurationen wie Dev, Test und Prod mithilfe des Features "Umgebungen"
* Bringen Sie Ihre App in Ihre Organisation oder die Teams-App Store mithilfe integrierter Veröffentlichungstools

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="User Journey des Teams-Toolkits" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

## <a name="available-for-visual-studio-and-visual-studio-code"></a>Verfügbar für Visual Studio und Visual Studio Code

Das Teams-Toolkit ist kostenlos für Visual Studio Code verfügbar und unterstützt Visual Studio 2022 Community, Professional und Enterprise. Weitere Informationen zur Installation und Einrichtung finden Sie in der [Dokumentation zum Installieren des Teams-Toolkits](./install-Teams-Toolkit.md) .

| Teams Toolkit | Visual Studio | Visual Studio Code |
| - | ------------- | ------------------ |
| Installation | Verfügbar im Visual Studio-Installer | Verfügbar im VS Marketplace |
| Erstellen mit | C#, .NET, ASP.NET, Blazor | JavaScript, TypeScript, React, SPFx |

## <a name="features"></a>Features

### <a name="project-templates"></a>Projektvorlagen

Das Teams-Toolkit reduziert die Komplexität der ersten Schritte mit Vorlagen für gängige Branchen-App-Szenarien und intelligente Standardeinstellungen, um Ihre Zeit bis zur Produktion zu beschleunigen. Wenn Sie bereits mit der Entwicklung von Teams-Apps vertraut sind, können Sie auch direkt mit funktionsorientierten Vorlagen beginnen. d. h. Registerkarte, Bot, Messaging-Erweiterung.

::: zone pivot="visual-studio-code"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app.png" alt-text="Erstellen eines neuen Teams-App-Menüs in VS Code":::
::: zone-end

::: zone pivot="visual-studio"
:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create-new-app-vs.png" alt-text="Erstellen eines neuen Teams-App-Menüs in VS Code":::
::: zone-end

### <a name="automatic-registration-and-configuration"></a>Automatische Registrierung und Konfiguration

Sparen Sie Zeit, und lassen Sie das Toolkit die App automatisch im Teams-Entwicklerportal registrieren und Einstellungen wie Azure Active Directory automatisch konfigurieren, wenn Sie die App zum ersten Mal ausführen oder debuggen. Melden Sie sich mit Ihrem Microsoft 365-Konto an, um zu steuern, wo die App konfiguriert ist, und passen Sie das enthaltene Azure AD-Manifest an, wenn Sie mehr Flexibilität benötigen.

::: zone pivot="visual-studio-code"

### <a name="multiple-environments"></a>Mehrere Umgebungen

Mit den Umgebungsfeatures können Sie verschiedene Gruppierungen von Cloudressourcen erstellen, um das Ausführen und Testen Ihrer App zu vereinfachen. Verwenden Sie die Entwicklungsumgebung mit Ihrem Azure-Abonnement, oder erstellen Sie eine neue Umgebung mit einem anderen Abonnement für Staging, Test und Produktion.

### <a name="quick-access-to-teams-developer-portal"></a>Schneller Zugriff auf das Teams-Entwicklerportal

Greifen Sie schnell auf das Teams-Entwicklerportal zu, in dem Sie Ihre App konfigurieren, verteilen und verwalten können. Weitere Informationen finden Sie unter [Verwalten Ihrer Teams-Apps mithilfe des Entwicklerportals](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Entwicklerportal":::

::: zone-end

::: zone pivot="visual-studio"

#### <a name="teamsfx-net-sdk-reference-docs"></a>TeamsFx .NET SDK-Referenzdokumente

* [Microsoft.Extensions.DependencyInjection-Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx-Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration-Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation-Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper-Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
