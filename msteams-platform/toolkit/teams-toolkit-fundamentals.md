---
title: Übersicht über Teams Toolkit
author: zyxiaoyuer
description: 'Übersicht über Teams Toolkit, Installation von Teams Toolkit und Tour of Toolkit-Features'
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
---

# <a name="teams-toolkit-overview"></a>Übersicht über Teams Toolkit

> [!NOTE]
> Derzeit ist dieses Feature nur in der **öffentlichen Entwicklervorschau** verfügbar.

mit Teams Toolkit können Sie Ihre Teams-App direkt aus Visual Studio Code erstellen, debuggen und bereitstellen. Die App-Entwicklung mit dem Toolkit hat folgende Vorteile:

- Integrierte Identität
- Zugriff auf Cloudspeicher
- Daten von Microsoft Graph
- Azure- und Microsoft 365-Dienste mit Nullkonfigurationsansatz

Teams Toolkit vereint alle Tools, die zum Erstellen einer Teams-App erforderlich sind.

Für Teams App-Entwicklung, ähnlich wie Teams Toolkit für Visual Studio Code, können Sie [das CLI-Tool](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) verwenden, das aus Toolkit `teamsfx`besteht.

## <a name="user-journey-of-teams-toolkit"></a>User Journey of Teams Toolkit

Teams Toolkit automatisiert manuelle Arbeit und bietet eine hervorragende Integration von Teams und Azure-Ressourcen. Die folgende Abbildung zeigt Teams Toolkit-User Journey:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-toolkit-user-journey.png" alt-text="Teams Toolkit User Journey" border="true":::

Die wichtigsten Meilensteine dieser Reise sind:

1. Beginnen Sie, indem Sie ein neues Projekt erstellen oder ein Beispiel Teams App ausprobieren.
1. Fügen Sie Funktionen hinzu, oder bearbeiten Sie die Manifestdatei nach Bedarf.
1. Verwenden Sie Microsoft 365 Konto, um Ihre Teams-App zu erstellen und zu debuggen.
1. Verwenden Sie das Azure-Konto, um Ihre App in der Cloud bereitzustellen und bereitzustellen.
1. Veröffentlichen Sie Ihre App in Teams.

## <a name="install-teams-toolkit-for-visual-studio-code"></a>Installieren Teams Toolkit für Visual Studio Code

1. Öffnen **Sie Visual Studio Code.**
1. Wählen Sie die Erweiterungsansicht (**STRG+UMSCHALT+X** / **⌘⇧-X** oder **> Erweiterungen anzeigen**):

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="Installieren":::

1. Geben Sie **Teams Toolkit** in das Suchfeld ein:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-2.png" alt-text="Toolkit":::

1. Wählen Sie **"Installieren" aus**:
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install.png" alt-text="Install Toolkit":::

> [!TIP]
> Sie können Teams Toolkit über [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) installieren.

## <a name="take-a-tour-of-teams-toolkit"></a>Machen Sie eine Tour durch Teams Toolkit

Nach der Toolkit-Installation wird die Teams Toolkit-Benutzeroberfläche wie in der folgenden Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teams toolkit.png" alt-text="Minifunktionen":::

Sie können **den Schnellstart** auswählen, um das Teams Toolkit zu erkunden, oder wählen **Sie "Neue Teams-App** erstellen" aus, um ein Teams Projekt zu erstellen. Sie können eine Liste aller Toolkit-Features anzeigen, wenn Sie ein vorhandenes Projekt in Visual Studio Code Sidebar erstellen oder öffnen.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/toolkit functions.png" alt-text="Funktionen":::

Sehen wir uns die Themen an, die in diesem Dokument behandelt werden:

## <a name="accounts"></a>Konten

Zum Entwickeln einer Teams-App benötigen Sie mindestens ein Microsoft 365 Konto mit einem gültigen Abonnement. Wenn Sie Ihre Back-End-Ressourcen in Azure hosten möchten, ist auch ein Azure-Konto erforderlich. Teams Toolkit unterstützt die integrierte Erfahrung bei der Anmeldung, Bereitstellung und Bereitstellung für Azure-Ressourcen. Sie können [ein kostenloses Azure-Konto erstellen](https://azure.microsoft.com/free/) , bevor Sie beginnen.

## <a name="environment"></a>Umgebung

Teams Toolkit hilft Ihnen beim Erstellen und Verwalten mehrerer Umgebungen, bei der Bereitstellung und Bereitstellung von Artefakten in der Zielumgebung für Teams App.

### <a name="teamsfx-collaboration"></a>TeamsFx-Zusammenarbeit

Entwickler und Projektbesitzer können andere Mitarbeiter zum TeamsFx-Projekt einladen, dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

## <a name="development"></a>Development

Teams Toolkit hilft Ihnen, Ihr Teams App-Projekt zu erstellen und anzupassen, wodurch die Teams App-Entwicklung einfacher wird.

### <a name="create-a-new-teams-app"></a>Erstellen einer neuen Teams-App

Sie können mit Teams App-Entwicklung beginnen, indem Sie neue Teams Projekt mit Teams Toolkit erstellen, indem **Sie entweder ein neues Projekt erstellen** oder **anhand von Beispielen erstellen**.

### <a name="add-capabilities"></a>Hinzufügen von Funktionen

Es hilft, Teams App während des Entwicklungsprozesses weitere erforderliche Teams Funktionen hinzuzufügen.

### <a name="add-cloud-resources"></a>Hinzufügen von Cloudressourcen

Es hilft Ihnen, optional Cloudressourcen hinzuzufügen, die Ihren Entwicklungsanforderungen entsprechen.

### <a name="edit-manifest-file"></a>Bearbeiten der Manifestdatei 

Es hilft Ihnen, die Teams App-Integration mit Teams Client zu bearbeiten.

## <a name="deployment"></a>Bereitstellung)

Stellen Sie während oder nach der Entwicklung sicher, dass Sie Teams App bereitstellen, bereitstellen und veröffentlichen, bevor Benutzer darauf zugriffen können.

### <a name="provision-in-the-cloud"></a>Bereitstellung in der Cloud

Es wird in den Azure-Ressourcen-Manager integriert, mit dem Sie Azure-Ressourcen bereitstellen können, die Ihre Anwendung für den Codeansatz benötigt.

### <a name="deploy-to-the-cloud"></a>Bereitstellen in der Cloud

 Es hilft Ihnen, den Quellcode in Azure bereitzustellen.

### <a name="publish-to-teams"></a>Veröffentlichen in Teams

Nach dem Erstellen der App können Sie Ihre App auf einen anderen Bereich verteilen, z. B. einzeln, team, organisation oder jeder. Veröffentlichen auf Teams hilft Ihnen beim Veröffentlichen Ihrer entwickelten App.

### <a name="cicd-guide"></a>CI/CD-Leitfaden

Es hilft Ihnen, Ihren Entwicklungsworkflow beim Erstellen Teams Anwendung zu automatisieren. Der CI/CD-Leitfaden enthält Tools und Vorlagen für die ersten Schritte beim Einrichten von CI- oder CD-Pipelines.

#### <a name="teamsfx-cli"></a>TeamsFx CLI

Es handelt sich um eine textbasierte Befehlszeilenschnittstelle, die Teams Anwendungsentwicklung beschleunigt und auch CI/CD-Szenarien ermöglicht, in denen Sie CLI in Skripts zur Automatisierung integrieren können.

#### <a name="teamsfx-sdk"></a>TeamsFx SDK

Es hilft Ihnen, die Aufgaben der Implementierung von Identität und Zugriff auf Cloudressourcen auf einzeilige Anweisungen mit Nullkonfiguration zu reduzieren.

## <a name="help-and-feedback"></a>Hilfe und Feedback

In diesem Abschnitt finden Sie die dokumentation und ressourcen, die Sie benötigen. Sie können im Teams Toolkit "**Probleme melden" auf GitHub** auswählen, um **schnellen Support** von Produktexperten zu erhalten. Durchsuchen Sie das Problem, bevor Sie ein neues erstellen, oder besuchen Sie das [StackOverflow-Tag `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) , um Feedback zu übermitteln.

Sehen wir uns nun Teams Toolkit-Features an.

| Features des Teams Toolkits | Enthält... | Mögliche Aktionen |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Microsoft 365 Konto | Verwenden Sie Ihr Microsoft 365-Konto mit einem gültigen E5-Abonnement zum Erstellen Ihrer App. |
| &nbsp; | Azure-Konto | Verwenden Sie Ihr Azure-Konto für die Bereitstellung der App in Azure. |
| **Umgebung** | &nbsp; | &nbsp; |
| &nbsp; | lokal | Stellen Sie Ihre App in der lokalen Standardumgebung mit Lokalen Computerumgebungskonfigurationen bereit. |
| &nbsp; | Dev | Stellen Sie Ihre App in der standardmäßigen Entwicklungsumgebung mit Remote- oder Cloudumgebungskonfigurationen bereit. Sie können nach Bedarf weitere Umgebungen erstellen. |
| **Development** | &nbsp; | &nbsp; |
| &nbsp; | Erstellen einer neuen Teams-App | Verwenden Sie den Toolkit-Assistenten, um das Projektgerüst für die App-Entwicklung vorzubereiten. |
| &nbsp; | Beispiele anzeigen | Wählen Sie eine der 12 Beispiel-Apps des Teams Toolkits aus. Das Toolkit lädt den App-Code aus GitHub herunter, und Sie können die Beispiel-App erstellen. |
| &nbsp; | Hinzufügen von Funktionen | Fügen Sie während des Entwicklungsprozesses weitere erforderliche Teams Funktionen zu Teams App hinzu. |
| &nbsp; | Hinzufügen von Cloudressourcen | Fügen Sie optionale Cloudressourcen hinzu, die für Ihre App geeignet sind. |
| &nbsp; | Bearbeiten der Manifestdatei | Bearbeiten Sie die Teams App-Integration mit Teams Client. |
| **Bereitstellung** | &nbsp; | &nbsp; |
| &nbsp; | Bereitstellung in der Cloud | Weisen Sie Azure-Ressourcen für Ihre Anwendung zu. Teams Toolkit ist in Azure Resource Manager integriert. |
| &nbsp; | Zip-Teams-Metadatenpaket | Erstellen Sie das App-Paket, das in Teams oder entwicklerportal hochgeladen werden kann. Es enthält das App-Manifest und App-Symbole.  |
| &nbsp; | Bereitstellen in der Cloud | Stellen Sie den Quellcode in Azure bereit. |
| &nbsp; | Veröffentlichen in Teams | Veröffentlichen Sie Ihre entwickelte App, und verteilen Sie sie auf Bereiche, z. B. persönlich, Team, Kanal oder Organisation. |
| &nbsp; | Entwicklerportal für Teams | Verwenden Sie das Entwicklerportal, um Ihre Teams App zu konfigurieren und zu verwalten. |
| &nbsp; | CI/CD-Leitfaden | Automatisieren Sie Ihren Entwicklungsworkflow beim Erstellen Teams Anwendung. |
| **Hilfe und Feedback** | &nbsp; | &nbsp; |
| &nbsp; | Schnellstart | Sehen Sie sich die Teams Toolkit-Schnellstarthilfe in Visual Studio Code an.  |
| &nbsp; | Dokumentation | Wählen Sie diese Option aus, um auf die Microsoft Teams Entwicklerdokumentation zuzugreifen. |
| &nbsp; | Melden von Problemen bei GitHub | Wählen Sie diese Option aus, um auf GitHub Seite zuzugreifen und Probleme auszulösen. |
|

> [!TIP]
> Durchsuchen Sie vorhandene Probleme, bevor Sie ein neues erstellen, oder besuchen Sie das [StackOverflow-Tag `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) , um Feedback zu übermitteln.

## <a name="see-also"></a>Siehe auch

* [Erstellen eines neuen Projekts mit Teams Toolkit](create-new-project.md)
* [Vorbereiten von Konten zum Erstellen Teams Apps](accounts.md)
* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
* [Verwenden Teams Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in der Cloud](deploy.md)
