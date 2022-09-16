---
title: Überblick über das Teams-Toolkit
author: zyxiaoyuer
description: Lernen Sie in diesem Modul das Teams-Toolkit, die Installation des Teams-Toolkits und die Benutzerreise des Teams-Toolkits kennen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/24/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 95a42e4bd2064bc1ce4b775f13ba990890bc6776
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2022
ms.locfileid: "67780730"
---
# <a name="teams-toolkit-overview"></a>Überblick über das Teams-Toolkit

Das Teams-Toolkit ist ein Funktionsfeature, mit dem Sie Multifunktionen sowohl in Microsoft Visual Studio Code als auch in Visual Studio ausführen können. Mithilfe des Teams-Toolkits können Sie den Prozess von der Erstellung bis zur Bereitstellung und Anpassung Ihrer App automatisieren. Die verschiedenen Features und Vorteile des Teams-Toolkits werden in der entsprechenden Dokumentation für die von Ihnen ausgewählten Umgebungen erläutert.

::: zone pivot="visual-studio-code"

## <a name="teams-toolkit-overview-for--visual-studio-code"></a>Übersicht über das Teams-Toolkit für Visual Studio Code

Mit dem Teams-Toolkit können Sie Ihre Teams-App direkt aus Visual Studio erstellen, debuggen und bereitstellen, Code.App Entwicklung mit dem Toolkit hat die folgenden Vorteile:

* Integrierte Identität
* Zugriff auf Cloudspeicher
* Daten von Microsoft Graph
* Azure- und Microsoft 365-Dienste mit Zero-Configuration-Ansatz.

Für die Entwicklung von Teams-Apps können Sie ähnlich wie beim Teams-Toolkit für Visual Studio das [CLI-Tool verwenden](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), das aus Toolkit besteht `teamsfx`.

## <a name="user-journey-of-teams-toolkit"></a>User Journey des Teams Toolkits

Teams Toolkit automatisiert manuelle Arbeit und bietet eine hervorragende Integration von Teams und Azure-Ressourcen. Das folgende Bild zeigt die Benutzerreise von Teams Toolkit:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png" alt-text="User Journey des Teams-Toolkits" lightbox="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey2.png":::

Die wichtigsten Meilensteine dieser Reise sind:

1. Beginnen Sie, indem Sie ein neues Projekt erstellen oder eine Beispiel-Teams-App ausprobieren.
1. Fügen Sie nach Bedarf Funktionen hinzu oder bearbeiten Sie die Manifestdatei.
1. Verwenden Sie das Microsoft 365-Konto, um Ihre Teams-App zu erstellen und zu debuggen.
1. Verwenden Sie das Azure-Konto zum Bereitstellen und Bereitstellen Ihrer App in der Cloud.
1. Veröffentlichen Sie Ihre App in Teams.

Die folgende Tabelle hilft Ihnen, den Überblick über das Teams-Toolkit in Visual Studio Code zu erhalten:

| Prozess | Beschreibung |
| ---- | ---- |
| Installieren des Teams-Toolkits | Sie können das Teams-Toolkit auf zwei Arten installieren: <br> - Verwenden von Visual Studio Code <br> – Verwenden von Visual Studio Code Marketplace|
| Unterstützung für Buildumgebungen | Es gibt zwei verschiedene Umgebungstypen: <br> - Javascript oder Typescript <br> - SPFx |
| Unterstützung für App-Typen und Azure-Funktion | Es gibt zwei verschiedene Arten von Apps: <br> – Funktionsbasierte App wie Registerkarte, Bot, Nachrichtenerweiterung  <br> – Szenariobasierte Teams-App wie Benachrichtigungs-Bot, Befehls-Bot und SSO-aktivierte persönliche Registerkarte |
| Entwickeln Ihrer Teams-App | Dazu zählen: <br> – Hinzufügen und Verwalten von Umgebungen <br> – Erstellen einer App mit mehreren Funktionen <br> – Erstellen von funktionsbasierten Cloudressourcen <br> – Integrieren der Drittanbieter-API <br> - Anpassen der Manifestdatei <br> – TeamsFx SDK |
| Debuggen Sie Ihre Teams-App | Dazu zählen: <br> – Lokales Debuggen Ihrer Teams-App <br> - Debuggen des Hintergrundprozesses|
| Hosten Ihrer Teams-App | Dazu zählen: <br> – Bereitstellen von Ressourcen in der Cloud <br> – Bereitstellen in der Cloud|
| Testen Ihrer Teams-App | Dazu zählen: <br> - Integrieren und Reduzieren <br> – Zip-Teams-Metadatenpaket <br> – Querladen und Testen der App in der Teams-Umgebung <br> – Testen des App-Verhaltens in unterschiedlichen Umgebungen|
| Veröffentlichen Ihrer Teams-App | Dazu zählen: <br> – Veröffentlichen Ihrer App <br> – Administratorgenehmigung verwalten <br> - Zum Speichern veröffentlichen <br> – Integration in das Entwicklerportal |

### <a name="entities-integrated-with-teams-toolkit"></a>In teams-Toolkit integrierte Entitäten

Teams Toolkit ist eine Erweiterung in Visual Studio Code. Es ist in die folgenden Entitäten in Teams Toolkit integriert, z. B. Azure AD und Microsoft 365, Developer Portal und Microsoft Graph. Alle Entitäten sind in das Teams-Toolkit integriert und helfen Benutzern beim Erstellen einer App.

| Entitäten | Beschreibung |
| ---- | ---- |
| Azure AD  | Azure Active Directory (Azure AD) ist ein cloudbasierter Identitäts- und Zugriffsverwaltungsdienst. Dieser Dienst hilft Ihren Mitarbeitern, auf externe Ressourcen wie Microsoft 365, die Azure-Portal und Tausende anderer SaaS-Anwendungen zuzugreifen. |
| Microsoft 365  | Teams-Entwicklerkonto beim Entwickeln einer App.|
| Entwicklerportal | Das Entwicklerportal für Teams ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps. Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr. |
| Microsoft Graph | Microsoft Graph ist das Gateway zu Daten und Informationen in Microsoft 365. Es bietet ein vereinheitlichtes Programmierbarkeitsmodell, mit dem Sie auf die enormen Datenmengen in Microsoft 365, Windows und Enterprise Mobility + Security zugreifen können. |

Teams Toolkit bringt alle Tools, die zum Erstellen einer Teams-App benötigt werden, an einem Ort zusammen.

## <a name="manage-your-apps-using-developer-portal"></a>Verwalten Ihrer Apps mithilfe des Entwicklerportals

Da das Teams-Toolkit in das Entwicklerportal integriert ist, können Sie Ihre App nach dem Erstellen einer App mithilfe des [Entwicklerportals für Teams](../concepts/build-and-test/teams-developer-portal.md) unter BEREITSTELLUNG konfigurieren, verteilen und verwalten. Weitere Informationen finden Sie unter [Verwalten Ihrer Teams-Apps mithilfe des Entwicklerportals](../concepts/build-and-test/manage-your-apps-in-developer-portal.md).

:::image type="content" source="../assets/images/teams-toolkit-v2/build-environment-developer-portal-1.png" alt-text="Entwicklerportal":::

::: zone-end

::: zone pivot="visual-studio"

## <a name="teams-toolkit-overview-for-visual-studio"></a>Übersicht über das Teams-Toolkit für Visual Studio

Das Teams-Toolkit für Visual Studio hilft Ihnen beim Erstellen, Debuggen und Bereitstellen von Microsoft Teams-Apps. Teams Toolkit für Visual Studio ist GA in Visual Studio 2022, Version 17.3. Die App-Entwicklung mit dem Teams-Toolkit bietet folgende Vorteile:

* Integrierte Identität
* Zugriff auf Cloudspeicher
* Daten von Microsoft Graph
* Azure- und Microsoft 365-Dienste mit Zero-Configuration-Ansatz

Für die Entwicklung von Teams-Apps können Sie auch [das CLI-Tool](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) verwenden, ähnlich dem Teams-Toolkit für Microsoft Visual Studio-Code, der das Toolkit `teamsfx`enthält.

Das Teams-Toolkit bietet alle Tools, die zum Erstellen einer Teams-App an einem zentralen Ort erforderlich sind.

> [!NOTE]
> Das Teams-Toolkit ist in anderen Versionen nicht verfügbar.

## <a name="user-journey-of-teams-toolkit"></a>User Journey of Teams Toolkit

Das Teams-Toolkit automatisiert manuelle Arbeit und bietet Ihnen eine großartige Integration von Teams- und Azure-Ressourcen. Die folgende Abbildung zeigt die Benutzerreise:

:::image type="content" source="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png" alt-text="Teams-Toolkit–Benutzerreise" lightbox="../assets/images/teams-toolkit-overview/teams-toolkit-user-journey.png":::

Die wichtigsten Meilensteine dieser Reise sind:

1. Sie können zunächst ein neues Projekt erstellen oder versuchen, eine Beispiel-Teams-App zu erstellen.
1. Anschließend können Sie Code oder die Manifestdatei nach Bedarf bearbeiten.
1. Zum Erstellen und Debuggen der Teams-App können Sie Ihr Microsoft 365-Konto verwenden.
1. Für die Bereitstellung und Bereitstellung Ihrer App in der Cloud können Sie Ihr Azure-Konto verwenden.
1. Sie können Ihre App endlich in Teams veröffentlichen.

Die folgenden Vorgänge werden im Teams-Toolkit für Visual Studio noch nicht unterstützt, im Vergleich zum Teams-Toolkit für Microsoft Visual Studio Code, sind jedoch in der zukünftigen Produktübersicht geplant.

* Fügen Sie Ihrer Teams-App weitere Teams-Funktionen hinzu.
* Hinzufügen weiterer Azure-Ressourcen zu Ihrer Teams-App
* Fügen Sie Ihrer Teams-App einmaliges Anmelden (Single Sign-On, SSO) hinzu.
* Fügen Sie Ihrer Teams-App eine API-Verbindung hinzu.
* Passen Sie Microsoft Azure Active Directory (Azure AD)-Manifest an.
* Fügen Sie CI/CD-Pipelines hinzu.
* Verwalten sie mehrere Cloudumgebungen.
* Zusammenarbeiten an Teams-Projekten.
* Veröffentlichen Sie die Teams-App.

### <a name="teamsfx-net-sdk-reference-docs"></a>TeamsFx .NET SDK-Referenzdokumente

* [Microsoft.Extensions.DependencyInjection-Namespace](/../dotnet/api/Microsoft.Extensions.DependencyInjection)
* [Microsoft.TeamsFx-Namespace](/../dotnet/api/Microsoft.TeamsFx)
* [Microsoft.TeamsFx.Configuration-Namespace](/../dotnet/api/Microsoft.TeamsFx.Configuration)
* [Microsoft.TeamsFx.Conversation-Namespace](/../dotnet/api/Microsoft.TeamsFx.Conversation)
* [Microsoft.TeamsFx.Helper-Namespace](/../dotnet/api/Microsoft.TeamsFx.Helper)

## <a name="see-also"></a>Siehe auch

* [Erstellen einer neuen Teams-App in Visual Studio](create-new-teams-app-for-Visual-Studio.md)
* [Bereitstellen von Cloudressourcen mit Visual Studio](provision-cloud-resources.md)
* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)

::: zone-end
