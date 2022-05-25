---
title: Überblick über das Teams-Toolkit
author: zyxiaoyuer
description: Überblick über das Teams-Toolkit, die Installation des Teams-Toolkits und die Tour der Toolkit-Funktionen
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/17/2022
ms.openlocfilehash: 1b65fedbc34cb00771dde279a19ab1d6b4d8b16a
ms.sourcegitcommit: 929391b6c04d53ea84a93145e2f29d6b96a64d37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2022
ms.locfileid: "65673013"
---
# <a name="teams-toolkit-overview"></a>Überblick über das Teams-Toolkit

Das Teams-Toolkit für Microsoft Visual Studio Code unterstützt Sie beim Erstellen und Bereitstellen von Teams-Apps mit integrierter Identität, Zugriff auf Cloud-Speicher, Daten aus Microsoft Graph und anderen Diensten in Azure und Microsoft 365 ohne Konfiguration. Für die Entwicklung von Teams-Apps können Sie ähnlich wie beim Teams-Toolkit für Visual Studio das [CLI-Tool verwenden](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), das aus Toolkit besteht `teamsfx`.
Mit dem Teams-Toolkit können Sie Ihre Teams-App direkt aus Visual Studio Code erstellen, debuggen und bereitstellen. Die App-Entwicklung mit dem Toolkit hat folgende Vorteile:

* Integrierte Identität
* Zugriff auf Cloudspeicher
* Daten von Microsoft Graph
* Azure- und Microsoft 365-Dienste mit Zero-Configuration-Ansatz

Teams Toolkit bringt alle Tools, die zum Erstellen einer Teams-App benötigt werden, an einem Ort zusammen.

## <a name="user-journey-of-teams-toolkit"></a>User Journey des Teams Toolkits

Teams Toolkit automatisiert manuelle Arbeit und bietet eine hervorragende Integration von Teams und Azure-Ressourcen. Das folgende Bild zeigt die Benutzerreise von Teams Toolkit:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey.png" alt-text="Teams Toolkit User Journey" border="true":::

Die wichtigsten Meilensteine dieser Reise sind:

1. Beginnen Sie, indem Sie ein neues Projekt erstellen oder eine Beispiel-Teams-App ausprobieren.
1. Fügen Sie nach Bedarf Funktionen hinzu oder bearbeiten Sie die Manifestdatei.
1. Verwenden Sie das Microsoft 365-Konto, um Ihre Teams-App zu erstellen und zu debuggen.
1. Verwenden Sie das Azure-Konto zum Bereitstellen und Bereitstellen Ihrer App in der Cloud.
1. Veröffentlichen Sie Ihre App in Teams.

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Installieren Sie das Teams-Toolkit für Visual Studio Code

1. Öffnen Sie **Visual Studio Code.**
1. Wählen Sie die Ansicht "Erweiterungen" (**STRG+UMSCHALT+X** / **⌘⇧-X** oder **Ansicht > Erweiterungen**) aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="installieren":::

1. Geben Sie **Teams Toolkit** in das Suchfeld ein.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit2.png" alt-text="Toolkit":::

1. Wählen Sie **Installieren** aus.
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install-toolkit.png" alt-text="Installieren von Toolkit 4.0.0":::

> [!TIP]
> Sie können das Teams-Toolkit vom [Visual Studio Code Marketplace installieren](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="take-a-tour-of-teams-toolkit"></a>Machen Sie eine Tour durch das Teams-Toolkit

Nach der Toolkit-Installation sehen Sie die Teams Toolkit-Benutzeroberfläche wie in der folgenden Abbildung gezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/Teams-toolkit.png" alt-text="minifunktionen":::

Sie können **Erste Schritte** auswählen, um das Teams Toolkit zu erkunden, oder **eine neue Teams-App** erstellen, um ein Teams Projekt zu erstellen. Wenn Sie ein Teams Projekt, das von Teams Toolkit erstellt wurde, in Visual Studio Code geöffnet haben, wird Teams Toolkit-Benutzeroberfläche mit allen Funktionen angezeigt, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamstookit1.png" alt-text="Screenshot des Teams-Toolkits":::

Lassen Sie uns eine Tour durch die in diesem Dokument behandelten Themen unternehmen.

## <a name="accounts"></a>Konten

Um eine Teams-App zu entwickeln, benötigen Sie mindestens ein Microsoft 365-Konto mit einem gültigen Abonnement. Wenn Sie Ihre Back-End-Ressourcen auf Azure hosten möchten, ist außerdem ein Azure-Konto erforderlich. Teams Toolkit unterstützt die integrierte Erfahrung bei der Anmeldung, Bereitstellung und Bereitstellung für Azure-Ressourcen. Sie können ein [kostenloses Azure-Konto erstellen, bevor](https://azure.microsoft.com/free/) Sie beginnen.

## <a name="environment"></a>Umgebung

Das Teams-Toolkit unterstützt Sie beim Erstellen und Verwalten mehrerer Umgebungen sowie beim Bereitstellen und Bereitstellen von Artefakten in der Zielumgebung für die Teams-App.

### <a name="teamsfx-collaboration"></a>TeamsFx-Zusammenarbeit

Es ermöglicht Entwicklern und Projektinhabern, andere Mitarbeiter zum TeamsFx-Projekt einzuladen, um dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teamsfx.png" alt-text="Teamsfx-Projekt":::

## <a name="development"></a>Development

Das Teams-Toolkit unterstützt Sie beim Erstellen und Anpassen Ihres Teams-App-Projekts, das die Entwicklung der Teams-App vereinfacht.

### <a name="create-a-new-teams-app"></a>Erstellen einer neuen Teams-App

Es hilft Ihnen, mit Teams App-Entwicklung zu beginnen, indem Sie ein neues Teams Projekt mit Teams Toolkit erstellen, indem Sie entweder ein **neues Projekt erstellen** oder **anhand eines Beispiels starten**.

### <a name="add-features"></a>Features hinzufügen

Es hilft Ihnen, zusätzliche Teams-Funktionen wie **Tab** oder **Bot** inkrementell hinzuzufügen oder optional Azure-Ressourcen wie **Azure SQL-Datenbank** oder **Azure Key Vault** hinzuzufügen, was Ihren Entwicklungsanforderungen an Ihre aktuelle Teams-App entspricht. Sie können auch **Workflows für einmaliges Anmelden** oder **CI/CD** für Ihre Teams-App hinzufügen. 

### <a name="edit-manifest-file"></a>Manifestdatei bearbeiten

Es hilft Ihnen, die Teams-App-Integration mit dem Teams-Client zu bearbeiten.

## <a name="deployment"></a>Bereitstellung)

Stellen Sie während oder nach der Entwicklung sicher, dass die Teams-App bereitgestellt, bereitgestellt und veröffentlicht wird, bevor sie für Benutzer zugänglich ist.

### <a name="provision-in-the-cloud"></a>Bereitstellung in der Cloud

Es lässt sich in den Azure-Ressourcen-Manager integrieren, der es Ihnen ermöglicht, Azure-Ressourcen bereitzustellen, die Ihre Anwendung für den Code-Ansatz benötigt.

### <a name="deploy-to-the-cloud"></a>Bereitstellen in die Cloud

 Es hilft Ihnen, den Quellcode in Azure bereitzustellen.

### <a name="publish-to-teams"></a>In Teams veröffentlichen

Nachdem Sie die App erstellt haben, können Sie Ihre App an verschiedene Bereiche verteilen, z. B. Einzelpersonen, Teams, Organisationen oder alle. In Teams veröffentlichen hilft Ihnen, Ihre entwickelte App zu veröffentlichen.

#### <a name="teamsfx-cli"></a>TeamsFx CLI

Es ist eine textbasierte Befehlszeilenschnittstelle, die die Entwicklung von Teams-Anwendungen beschleunigt und auch CI/CD-Szenarien ermöglicht, in denen Sie CLI in Skripts zur Automatisierung integrieren können.

#### <a name="teamsfx-sdk"></a>TeamsFx SDK

Es hilft Ihnen, die Aufgaben der Implementierung der Identität und des Zugriffs auf Cloud-Ressourcen auf einzeilige Anweisungen ohne Konfiguration zu reduzieren.

## <a name="help-and-feedback"></a>Hilfe und Feedback

In diesem Abschnitt finden Sie die Dokumentation und Ressourcen, die Sie benötigen. Sie können im Teams-Toolkit **Probleme auf GitHub** melden auswählen, um schnellen **Support vom** Produktexperten zu erhalten. Durchsuchen Sie das Problem, bevor Sie ein neues erstellen, oder [besuchen Sie das StackOverflow-Tag, um `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) Feedback zu senden.
<!--  
Let's explore Teams Toolkit features.

| Teams Toolkit Features | Includes | What you can do |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Microsoft 365 account | Use your Microsoft 365 account with a valid E5 subscription for building your app. |
| &nbsp; | Azure account | Use your Azure account for deploying app on Azure. |
| **Environment** | &nbsp; | &nbsp; |
| &nbsp; | local | Deploy your app in the default local environment with local machine environment configurations. |
| &nbsp; | dev | Deploy your app in the default dev environment with remote or cloud environment configurations. You can create more environments, as you need. |
| **Development** | &nbsp; | &nbsp; |
| &nbsp; | Create a new Teams app | Use the toolkit wizard to prepare project scaffolding for app development. |
| &nbsp; | View samples | Select any of Teams Toolkit's 12 sample apps. The toolkit downloads the app code from GitHub, and you can build the sample app. |
| &nbsp; | Add Features | - Add other required Teams capabilities to Teams app during development process. </br> - Add optional cloud resources suitable for your app. |
| &nbsp; | Edit manifest file | Edit the Teams app integration with Teams client. |
| **Deployment** | &nbsp; | &nbsp; |
| &nbsp; | Provision in the cloud | Allocate Azure resources for your application. Teams Toolkit is integrated with Azure Resource Manager. |
| &nbsp; | Zip Teams metadata package | Create the app package that can be uploaded to Teams or Developer Portal. It contains the app manifest and app icons.  |
| &nbsp; | Deploy to the cloud | Deploy the source code to Azure. |
| &nbsp; | Publish to Teams | Publish your developed app and distribute it to scopes, such as personal, team, channel, or organization. |
| &nbsp; | Developer Portal for Teams | Use Developer Portal to configure and manage your Teams app. |
| **Help and Feedback** | &nbsp; | &nbsp; |
| &nbsp; | Quick start | View the Teams Toolkit Quick start help within Visual Studio Code.  |
| &nbsp; | Tutorial | Select to access different tutorials. |
| &nbsp; | Documentation | Select to access the Microsoft Teams Developer Documentation. |
| &nbsp; | Report issues on GitHub | Select to access GitHub page and raise any issues. |

-->
> [!TIP]
> Durchsuchen Sie vorhandene Probleme, bevor Sie ein neues erstellen, oder besuchen Sie das [StackOverflow-Tag, `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) um Feedback zu senden.

## <a name="see-also"></a>Siehe auch

* [Erstellen Sie ein neues Projekt mit dem Teams Toolkit](create-new-project.md)
* [Vorbereiten von Konten zum Erstellen von Teams-Apps](accounts.md)
* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in die Cloud](deploy.md)
