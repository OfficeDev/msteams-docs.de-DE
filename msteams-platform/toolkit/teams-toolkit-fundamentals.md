---
title: Überblick über das Teams-Toolkit
author: zyxiaoyuer
description: Überblick über das Teams-Toolkit, die Installation des Teams-Toolkits und die Tour der Toolkit-Funktionen
ms.author: zhany
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: de249f060581c2d8e1f90408c8431fe451125ef2
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111423"
---
# <a name="teams-toolkit-overview"></a>Überblick über das Teams-Toolkit

> [!NOTE]
> Derzeit ist diese Funktion nur in **der öffentlichen Entwicklervorschau** verfügbar.

Das Teams-Toolkit für Microsoft Visual Studio Code unterstützt Sie beim Erstellen und Bereitstellen von Teams-Apps mit integrierter Identität, Zugriff auf Cloud-Speicher, Daten aus Microsoft Graph und anderen Diensten in Azure und Microsoft 365 ohne Konfiguration. Für die Entwicklung von Teams-Apps können Sie ähnlich wie beim Teams-Toolkit für Visual Studio das [CLI-Tool verwenden](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), das aus Toolkit besteht `teamsfx`.
Mit dem Teams-Toolkit können Sie Ihre Teams-App direkt aus Visual Studio Code erstellen, debuggen und bereitstellen. Die App-Entwicklung mit dem Toolkit hat folgende Vorteile:

* Integrierte Identität
* Zugriff auf Cloudspeicher
* Daten von Microsoft Graph
* Azure- und Microsoft 365-Dienste mit Zero-Configuration-Ansatz

Teams Toolkit bringt alle Tools, die zum Erstellen einer Teams-App benötigt werden, an einem Ort zusammen.

Für die Entwicklung von Teams-Apps können Sie ähnlich wie beim Teams-Toolkit für Visual Studio Code das [CLI-Tool verwenden](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md), das aus Toolkit besteht `teamsfx`.

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
1. Wählen Sie die Erweiterungsansicht (**Strg+Umschalt+X** / **⌘⇧-X** oder **Ansicht > Erweiterungen**):

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-1.png" alt-text="installieren":::

1. Geben Sie **Teams Toolkit** in das Suchfeld ein:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install toolkit-2.png" alt-text="Toolkit":::

1. Wählen Sie **Installieren** aus:
  
   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/install.png" alt-text="Installieren des Toolkits":::

> [!TIP]
> Sie können das Teams-Toolkit vom [Visual Studio Code Marketplace installieren](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

## <a name="take-a-tour-of-teams-toolkit"></a>Machen Sie eine Tour durch das Teams-Toolkit

Nach der Toolkit-Installation sehen Sie die Teams Toolkit-Benutzeroberfläche wie in der folgenden Abbildung gezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/teams toolkit.png" alt-text="minifunktionen":::

Sie können **Quick Start** auswählen, um das Teams-Toolkit zu erkunden, oder eine neue Teams-App **erstellen auswählen, um ein Team-Projekt** zu erstellen. Wenn Sie ein mit Teams Toolkit v2.+ erstelltes Teams-Projekt in Visual Studio Code geöffnet haben, sehen Sie die Teams Toolkit-Benutzeroberfläche mit allen Funktionen, wie in der folgenden Abbildung gezeigt: Sie können **Quick Start** auswählen, um das Teams Toolkit zu erkunden, oder **Create a neue Teams-App** zum Erstellen eines Teams-Projekts. Sie können eine Liste aller Toolkit-Features anzeigen, wenn Sie ein vorhandenes Projekt in der Visual Studio Code-Seitenleiste erstellen oder öffnen.

:::image type="content" source="../assets/images/teams-toolkit-v2/manual/toolkit functions.png" alt-text="Funktionen":::

Lassen Sie uns einen Rundgang durch die in diesem Dokument behandelten Themen machen:

## <a name="accounts"></a>Konten

Um eine Teams-App zu entwickeln, benötigen Sie mindestens ein Microsoft 365-Konto mit einem gültigen Abonnement. Wenn Sie Ihre Back-End-Ressourcen auf Azure hosten möchten, ist außerdem ein Azure-Konto erforderlich. Das Teams-Toolkit unterstützt die integrierte Erfahrung zum Anmelden, Bereitstellen und Bereitstellen von Azure-Ressourcen. Sie können ein [kostenloses Azure-Konto erstellen, bevor](https://azure.microsoft.com/free/) Sie beginnen.

## <a name="environment"></a>Umgebung

Das Teams-Toolkit unterstützt Sie beim Erstellen und Verwalten mehrerer Umgebungen sowie beim Bereitstellen und Bereitstellen von Artefakten in der Zielumgebung für die Teams-App.

### <a name="teamsfx-collaboration"></a>TeamsFx-Zusammenarbeit

Es ermöglicht Entwicklern und Projektinhabern, andere Mitarbeiter zum TeamsFx-Projekt einzuladen, um dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

## <a name="development"></a>Development

Das Teams-Toolkit unterstützt Sie beim Erstellen und Anpassen Ihres Teams-App-Projekts, das die Entwicklung der Teams-App vereinfacht.

### <a name="create-a-new-teams-app"></a>Erstellen einer neuen Teams-App

Es hilft Ihnen, mit der Entwicklung von Teams-Apps zu beginnen, indem Sie ein neues Teams-Projekt mit dem Teams-Toolkit erstellen, indem Sie entweder **Neues Projekt** erstellen **oder Aus Beispielen erstellen verwenden**.

### <a name="add-capabilities"></a>Fähigkeiten hinzufügen

Es hilft, während des Entwicklungsprozesses andere erforderliche Teams-Funktionen zur Teams-App hinzuzufügen.

### <a name="add-cloud-resources"></a>Fügen Sie Cloud-Ressourcen hinzu

Es hilft Ihnen, optional Cloud-Ressourcen hinzuzufügen, die Ihren Entwicklungsanforderungen entsprechen.

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

### <a name="cicd-guide"></a>CI/CD-Leitfaden

Es hilft bei der Automatisierung Ihres Entwicklungsworkflows beim Erstellen von Teams-Anwendungen. Der CI/CD-Leitfaden bietet Tools und Vorlagen für den Einstieg in die Einrichtung von CI- oder CD-Pipelines.

#### <a name="teamsfx-cli"></a>TeamsFx CLI

Es ist eine textbasierte Befehlszeilenschnittstelle, die die Entwicklung von Teams-Anwendungen beschleunigt und auch CI/CD-Szenarien ermöglicht, in denen Sie CLI in Skripts zur Automatisierung integrieren können.

#### <a name="teamsfx-sdk"></a>TeamsFx SDK

Es hilft Ihnen, die Aufgaben der Implementierung der Identität und des Zugriffs auf Cloud-Ressourcen auf einzeilige Anweisungen ohne Konfiguration zu reduzieren.

## <a name="help-and-feedback"></a>Hilfe und Feedback

In diesem Abschnitt finden Sie die Dokumentation und Ressourcen, die Sie benötigen. Sie können im Teams-Toolkit **Probleme auf GitHub** melden auswählen, um schnellen **Support vom** Produktexperten zu erhalten. Durchsuchen Sie das Problem, bevor Sie ein neues erstellen, oder [besuchen Sie das StackOverflow-Tag, um `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) Feedback zu senden.

Sehen wir uns die Funktionen des Teams-Toolkits an.

| Teams Toolkit-Features | Beinhaltet... | Mögliche Aktionen |
| --- | --- | --- |
| **Accounts** | &nbsp; | &nbsp; |
| &nbsp; | Microsoft 365 Konto | Verwenden Sie Ihr Microsoft 365-Konto mit einem gültigen E5-Abonnement zum Erstellen Ihrer App. |
| &nbsp; | Azure-Konto | Verwenden Sie Ihr Azure-Konto zum Bereitstellen von Apps in Azure. |
| **Umgebung** | &nbsp; | &nbsp; |
| &nbsp; | lokal | Stellen Sie Ihre App in der lokalen Standardumgebung mit Umgebungskonfigurationen für lokale Computer bereit. |
| &nbsp; | dev | Stellen Sie Ihre App in der standardmäßigen Entwicklungsumgebung mit Remote- oder Cloud-Umgebungskonfigurationen bereit. Sie können nach Bedarf weitere Umgebungen erstellen. |
| **Development** | &nbsp; | &nbsp; |
| &nbsp; | Erstellen einer neuen Teams-App | Verwenden Sie den Toolkit-Assistenten, um Projektgerüste für die App-Entwicklung vorzubereiten. |
| &nbsp; | Anzeigebeispiele | Wählen Sie eine der 12 Beispiel-Apps von Teams Toolkit aus. Das Toolkit lädt den App-Code von GitHub herunter, und Sie können die Beispiel-App erstellen. |
| &nbsp; | Fähigkeiten hinzufügen | Fügen Sie während des Entwicklungsprozesses weitere erforderliche Teams-Funktionen zur Teams-App hinzu. |
| &nbsp; | Fügen Sie Cloud-Ressourcen hinzu | Fügen Sie optionale Cloud-Ressourcen hinzu, die für Ihre App geeignet sind. |
| &nbsp; | Manifestdatei bearbeiten | Bearbeiten Sie die Teams-App-Integration mit dem Teams-Client. |
| **Bereitstellung** | &nbsp; | &nbsp; |
| &nbsp; | Bereitstellung in der Cloud | Weisen Sie Ihrer Anwendung Azure-Ressourcen zu. Teams Toolkit ist in Azure Resource Manager integriert. |
| &nbsp; | Zip Teams-Metadatenpaket | Erstellen Sie das App-Paket, das in Teams oder das Entwicklerportal hochgeladen werden kann. Es enthält das App-Manifest und App-Symbole.  |
| &nbsp; | Bereitstellen in die Cloud | Stellen Sie den Quellcode in Azure bereit. |
| &nbsp; | In Teams veröffentlichen | Veröffentlichen Sie Ihre entwickelte App, und verteilen Sie sie auf Bereiche wie "Persönlich", "Team", "Kanal" oder "Organisation". |
| &nbsp; | Entwicklerportal für Teams | Verwenden Sie das Developer Portal zur Konfiguration, Verwaltung und Bereitstellung Ihrer Anwendung. |
| &nbsp; | CI/CD-Leitfaden | Automatisieren Sie Ihren Entwicklungsworkflow beim Erstellen Teams Anwendung. |
| **Hilfe und Feedback** | &nbsp; | &nbsp; |
| &nbsp; | Schnellstart | Zeigen Sie die Schnellstarthilfe Teams Toolkit in Visual Studio Code an.  |
| &nbsp; | Dokumentation | Wählen Sie diese Option aus, um auf die Microsoft Teams-Entwicklerdokumentation zuzugreifen. |
| &nbsp; | Melden Sie Probleme auf GitHub | Wählen Sie diese Option aus, um auf die GitHub-Seite zuzugreifen und Probleme zu melden. |
|

> [!TIP]
> Durchsuchen Sie vorhandene Probleme, bevor Sie ein neues erstellen, oder besuchen Sie das [StackOverflow-Tag, `teams-toolkit`](https://stackoverflow.com/questions/tagged/teams-toolkit) um Feedback zu senden.

## <a name="see-also"></a>Siehe auch

* [Erstellen Sie ein neues Projekt mit dem Teams Toolkit](create-new-project.md)
* [Vorbereiten von Konten zum Erstellen von Teams-Apps](accounts.md)
* [Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits](publish.md)
* [Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen in die Cloud](deploy.md)
