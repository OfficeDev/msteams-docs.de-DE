---
title: Erfahren Sie, wie Sie CI/CD-Pipelinevorlagen in GitHub, Azure DevOps und Jenkins für Microsoft Teams-Anwendungsentwickler verwenden.
author: MuyangAmigo
description: CI/CD-Vorlagen
ms.author: ruhe
ms.localizationpriority: high
ms.topic: overview
ms.date: 04/20/2022
ms.openlocfilehash: 2242f5820495cc3004b7fcbf9c65bce94e7220d1
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111563"
---
# <a name="set-up-cicd-pipelines"></a>Einrichten von CI/CD-Pipelines

TeamsFx hilft bei der Automatisierung Ihres Entwicklungsworkflows beim Erstellen von Teams-Anwendungen. Im Folgenden finden Sie die Tools und Vorlagen, mit denen Sie CI/CD-Pipelines einrichten, Workflowvorlagen erstellen und CI/CD-Workflows mit GitHub, Azure DevOps, Jenkins und anderen Plattformen anpassen können. Um Ressourcen bereitzustellen, können Sie Azure-Dienstprinzipale erstellen und die Microsoft Teams-App über das Microsoft Teams-Entwicklerportal veröffentlichen. Um eine Microsoft Teams-App manuell zu veröffentlichen, können Sie das [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com/home) nutzen.


|Tools und Vorlagen | Beschreibung |
|---|---|
|[TeamsFx CLI-Action](https://github.com/OfficeDev/teamsfx-cli-action)|GitHub-Aktion, die in TeamsFx CLI integriert ist.|
|[Microsoft Teams-Toolkit in Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Visual Studio Code-Erweiterung, mit der Sie Microsoft Teams-Apps sowie Automatisierungsworkflows für GitHub, Azure DevOps und Jenkins entwickeln können. |
|[TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli) | Befehlszeilentool, mit der Sie Microsoft Teams-Apps sowie Automatisierungsworkflows für GitHub, Azure DevOps und Jenkins entwickeln können.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) und [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Skriptvorlagen für die Automatisierung außerhalb von GitHub, Azure DevOps oder Jenkins. |


## <a name="set-up-pipelines"></a>Einrichten von Pipelines

Sie können Pipelines mit den folgenden Plattformen einrichten:

1. [Einrichten von Pipelines mit GitHub](#set-up-pipelines-with-github)
1. [Einrichten von Pipelines mit Azure DevOps](#set-up-pipelines-with-azure-devops)
1. [Einrichten von Pipelines mit Jenkins](#set-up-pipelines-with-jenkins)
1. [Einrichten von Pipelines für andere Plattformen](#set-up-pipelines-for-other-platforms)


### <a name="set-up-pipelines-with-github"></a>Einrichten von Pipelines mit GitHub

So richten Sie Pipelines mit GitHub für CI/CD ein:

1. Erstellen von Workflowvorlagen.

   * Visual Studio Code
   * TeamsFx CLI

1. Anpassen des CI/CD-Workflows.


## <a name="create-workflow-templates-with-github"></a>Erstellen von Workflowvorlagen mit GitHub

**Erstellen von Workflowvorlagen mit dem Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.
1. Wählen Sie das Symbol für das **Microsoft Teams-Toolkit** in der Visual Studio Code-Aktivitätsleiste aus.
1. Wählen Sie **CI/CD-Workflows hinzufügen** aus.
1. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
1. Wählen Sie **GitHub** als CI/CD-Anbieter aus.
1. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
1. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
1. Folgen Sie den README-Dateien unter`.github/workflows`, um den Workflow in GitHub einzurichten.

**Erstellen von Workflowvorlagen mithilfe von TeamsFx CLI**

1. Geben Sie `cd` in Ihr Microsoft Teams-App-Projektverzeichnis ein.
2. Geben Sie den Befehl `teamsfx add cicd` ein, um den interaktiven Befehlsprozess zu starten.
3. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
4. Wählen Sie **GitHub** als CI/CD-Anbieter aus.
5. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.github/workflows`, um den Workflow in GitHub einzurichten.

> [!NOTE]
> Wenn Sie zusätzliche Workflowvorlagen hinzufügen müssen, können Sie das gleiche Verfahren zum Erstellen von Workflowvorlagen in Visual Studio Code oder TeamsFx CLI ausführen.

### <a name="customize-cicd-workflow"></a>Anpassen des CI/CD-Workflows

Sie können die Testskripts zum Anpassen des CI/CD-Workflows ändern oder entfernen:

1. Standardmäßig wird der CD-Workflow ausgelöst, wenn neue Commits für die `main`-Verzweigung vorgenommen werden.
1. Ändern Sie bei Bedarf die Buildskripts.
1. Entfernen Sie bei Bedarf die Testskripts.

### <a name="set-up-pipelines-with-azure-devops"></a>Einrichten von Pipelines mit Azure DevOps

So richten Sie Pipelines mit Azure DevOps für CI/CD ein:

1. Erstellen von Workflowvorlagen.

   * Visual Studio Code
   * TeamsFx CLI

1. Anpassen des CI/CD-Workflows.


## <a name="create-workflow-templates-with-azure-devops"></a>Erstellen von Workflowvorlagen mit Azure DevOps

**Erstellen von Workflowvorlagen mit dem Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.
2. Wählen Sie das Symbol für das **Microsoft Teams-Toolkit** in der Visual Studio Code-Aktivitätsleiste aus.
3. Wählen Sie **CI/CD-Workflows hinzufügen** aus.
4. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
5. Wählen Sie **Azure DevOps** als CI/CD-Anbieter aus.
6. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung und Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.azure/pipelines`, um den Workflow in Azure DevOps einzurichten.

**Erstellen von Workflowvorlagen mithilfe der TeamsFx CLI**

1. Geben Sie `cd` in Ihr Microsoft Teams-App-Projektverzeichnis ein.
2. Geben Sie den Befehl `teamsfx add cicd` ein, um den interaktiven Befehlsprozess zu starten.
3. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
4. Wählen Sie **Azure DevOps** als CI/CD-Anbieter aus.
5. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.azure/pipelines`, um den Workflow in Azure DevOps einzurichten.

> [!NOTE]
> Wenn Sie zusätzliche Workflowvorlagen hinzufügen müssen, können Sie das gleiche Verfahren zum Erstellen von Workflowvorlagen in Visual Studio Code oder TeamsFx CLI ausführen.

### <a name="customize-ci-workflow"></a>Anpassen des CI-Workflows

Im Folgenden sind die Änderungen aufgeführt, die Sie am Skript oder an der Workflowdefinition vornehmen können:

1. Verwenden Sie das npm-Buildskript, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Verwenden Sie das npm-Testskript, das bei Erfolg 0 (null) zurückgibt, und ändern Sie die Testbefehle.

### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Im Folgenden sind die Änderungen aufgeführt, die Sie am Skript oder an der Workflowdefinition vornehmen können:

1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das bei Erfolg 0 (null) zurückgibt, oder ändern Sie die Testbefehle.

### <a name="set-up-pipelines-with-jenkins"></a>Einrichten von Pipelines mit Jenkins

So richten Sie Pipelines mit Jenkins für CI/CD ein:

1. Erstellen von Workflowvorlagen.

   * Visual Studio Code
   * TeamsFx CLI

1. Anpassen des CI/CD-Workflows.

## <a name="create-workflow-templates-with-jenkins"></a>Erstellen von Workflowvorlagen mit Jenkins

**Erstellen von Workflowvorlagen mit dem Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.
2. Wählen Sie das Symbol für das **Microsoft Teams-Toolkit** in der Visual Studio Code-Randleiste aus.
3. Wählen Sie **CI/CD-Workflows hinzufügen** aus.
4. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
5. Wählen Sie **Jenkins** als CI/CD-Anbieter aus.
6. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.jenkins/pipelines`, um den Workflow mit Jenkins einzurichten.

**Erstellen von Workflowvorlagen mithilfe von TeamsFx CLI**

1. Geben Sie `cd` in Ihr Microsoft Teams-App-Projektverzeichnis ein.
2. Geben Sie den Befehl `teamsfx add cicd` ein, um den interaktiven Befehlsprozess zu starten.
3. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
4. Wählen Sie **Jenkins** als CI/CD-Anbieter aus.
5. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.jenkins/pipelines`, um den Workflow mit Jenkins einzurichten.

> [!NOTE]
> Wenn Sie zusätzliche Workflowvorlagen hinzufügen müssen, können Sie das gleiche Verfahren zum Erstellen von Workflowvorlagen in Visual Studio Code oder TeamsFx CLI ausführen.

### <a name="customize-ci-workflow"></a>Anpassen des CI-Workflows

Im Folgenden sind einige der Änderungen aufgeführt, die Sie an Ihrem Projekt vornehmen können:

1. Ändern Sie die Art, wie der CI-Fluss ausgelöst wird. Standardmäßig werden die Trigger von **pollSCM** verwendet, wenn eine neue Änderung per Push in die **Dev**-Verzweigung verschoben wird.
1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das bei Erfolg 0 (null) zurückgibt, oder ändern Sie die Testbefehle.


### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Führen Sie die folgenden Schritte aus, um die CD-Pipeline anzupassen:

1. Ändern Sie den CD-Fluss. Standardmäßig werden die Trigger von `pollSCM` verwendet, wenn eine neue Änderung per Push in die `main`-Verzweigung verschoben wird.
1. Ändern Sie bei Bedarf die Buildskripts.
1. Entfernen Sie die Testskripts, wenn Sie keine Tests haben.


### <a name="set-up-pipelines-for-other-platforms"></a>Einrichten von Pipelines für andere Plattformen

Sie können den aufgeführten vordefinierten Bash-Beispielskripts folgen, um CI/CD-Pipelines auf den anderen Plattformen zu erstellen und anzupassen:

* [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Die Skripts basieren auf einem plattformübergreifenden TeamsFx-Befehlszeilentool: [TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli). Sie können es mit `npm install -g @microsoft/teamsfx-cli` installieren und der [Dokumentation](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) folgen, um die Skripts anzupassen.

> [!NOTE]
>
> * Um die Ausführung von `@microsoft/teamsfx-cli` im CI-Modus zu ermöglichen, aktivieren Sie `CI_ENABLED` durch `export CI_ENABLED=true`. Im CI-Modus ist `@microsoft/teamsfx-cli` für CI/CD geeignet.
> * Um die Ausführung von `@microsoft/teamsfx-cli` im nicht interaktiven Modus zu ermöglichen, legen Sie eine globale Konfiguration mit folgendem Befehl fest: `teamsfx config set -g interactive false`. Im nicht interaktiven Modus fordert `@microsoft/teamsfx-cli` keine Eingaben an..

Stellen Sie sicher, dass die Azure- und Microsoft 365-Anmeldeinformationen in Ihren Umgebungsvariablen sicher eingerichtet wurden. Wenn Sie beispielsweise GitHub als Quellcoderepository verwenden, lesen Sie [Github Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).


## <a name="provision-and-deploy-resources"></a>Bereitstellen von Ressourcen

Um Ressourcen für Azure innerhalb von CI/CD bereitzustellen, müssen Sie einen Azure-Dienstprinzipal erstellen und verwenden.

Führen Sie die folgenden Schritte aus, um Azure-Dienstprinzipale zu erstellen:

1. Registrieren Sie eine Microsoft Azure Active Directory (Azure AD)-Anwendung in einem einzelnen Einzelmandanten.
2. Weisen Sie Ihrer Azure AD-Anwendung eine Rolle zu, um auf Ihr Azure-Abonnement zuzugreifen. Die Rolle `Contributor` wird empfohlen.
3. Erstellen Sie ein neues Azure AD-Anwendungsgeheimnis.

> [!TIP]
> Speichern Sie Ihre Mandanten-ID, Anwendungs-ID (AZURE_SERVICE_PRINCIPAL_NAME) und den geheimen Schlüssel (AZURE_SERVICE_PRINCIPAL_PASSWORD) für die zukünftige Verwendung.

Weitere Informationen finden Sie in den [Richtlinien für Azure-Dienstprinzipale](/azure/active-directory/develop/howto-create-service-principal-portal). Es folgen die drei Möglichkeiten zum Erstellen von Dienstprinzipalen:

* [Microsoft Azure-Portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Microsoft Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Veröffentlichen einer Microsoft Teams-App mit dem Microsoft Teams-Entwicklerportal

Wenn Änderungen an der Manifestdatei der Microsoft Teams-App vorliegen, können Sie das Manifest aktualisieren und die Microsoft Teams-App erneut veröffentlichen.

Um eine Microsoft Teams-App manuell zu veröffentlichen, können Sie das [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com/home) nutzen.

Führen Sie die folgenden Schritte aus, um Ihre App zu veröffentlichen:

1. Melden Sie sich beim [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com) mit dem entsprechenden Konto an.
2. Importieren Sie Ihr App-Paket in eine ZIP-Datei, indem Sie `App -> Import app -> Replace` auswählen.
3. Wählen Sie die Ziel-App in der App-Liste aus.
4. Veröffentlichen Sie Ihre App, indem Sie `Publish -> Publish to your org`auswählen.

### <a name="see-also"></a>Siehe auch

* [Schnellstart für GitHub Actions](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Erstellen Ihrer ersten Azure DevOps-Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Erstellen Ihrer ersten Jenkins-Pipeline](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](/concepts/build-and-test/teams-developer-portal)
