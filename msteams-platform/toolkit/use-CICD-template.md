---
title: CI/CD-Vorlagen
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie CI/CD-Pipelinevorlagen in GitHub-, Azure DevOps- und Jenkins für Teams-AnwendungsentwicklerCI/CD-Vorlagen verwenden.
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 04/20/2022
ms.openlocfilehash: 1b2f7258b661a2b194f2072c9ad8fd920d58983d
ms.sourcegitcommit: c7fbb789b9654e9b8238700460b7ae5b2a58f216
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485397"
---
# <a name="set-up-cicd-pipelines"></a>Einrichten von CI/CD-Pipelines

TeamsFx hilft bei der Automatisierung Ihres Entwicklungsworkflows beim Erstellen von Teams-Anwendungen. Im Folgenden finden Sie die Tools und Vorlagen, mit denen Sie CI/CD-Pipelines einrichten, Workflowvorlagen erstellen und CI/CD-Workflows mit GitHub, Azure DevOps, Jenkins und anderen Plattformen anpassen können. Um Ressourcen bereitzustellen, können Sie Azure-Dienstprinzipale erstellen und die Microsoft Teams-App über das Microsoft Teams-Entwicklerportal veröffentlichen. Um eine Microsoft Teams-App manuell zu veröffentlichen, können Sie das [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com/home) nutzen.

|Tools und Vorlagen | Beschreibung |
|---|---|
|[TeamsFx CLI-Action](https://github.com/OfficeDev/teamsfx-cli-action)|GitHub-Aktion, die in TeamsFx CLI integriert ist.|
|[Microsoft Teams-Toolkit in Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)| Visual Studio Code-Erweiterung, die Sie bei der Entwicklung von Teams-Apps und Automatisierungsworkflows für GitHub, Azure DevOps und Jenkins unterstützt. |
|[TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli) | Kommandozeilen-Tool, das Sie bei der Entwicklung von Teams-Apps und Automatisierungsworkflows für GitHub, Azure DevOps und Jenkins unterstützt.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) und [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Skriptvorlagen für die Automatisierung außerhalb von GitHub, Azure DevOps oder Jenkins. |

## <a name="set-up-pipelines"></a>Einrichten von Pipelines

Sie können Pipelines mit den folgenden Plattformen einrichten:

1. [Einrichten von Pipelines mit GitHub](#set-up-pipelines-with-github)
1. [Einrichten von Pipelines mit Azure DevOps](#set-up-pipelines-with-azure-devops)
1. [Einrichten von Pipelines mit Jenkins](#set-up-pipelines-with-jenkins)
1. [Einrichten von Pipelines für andere Plattformen](#set-up-pipelines-for-other-platforms)

## <a name="set-up-pipelines-with-github"></a>Einrichten von Pipelines mit GitHub

So richten Sie Pipelines mit GitHub für CI/CD ein:

* Erstellen von Workflowvorlagen.

  * Visual Studio Code
  * TeamsFx CLI

* Anpassen des CI/CD-Workflows.

### <a name="create-workflow-templates"></a>Erstellen von Workflowvorlagen

Sie können die folgenden Workflowvorlagen mit GitHub erstellen:

**Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.

1. Wählen Sie im linken Bereich das Symbol " **Teams-Toolkit** " :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png"::: aus.

1. Wählen Sie **"Features hinzufügen" aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/add-feature.png" alt-text="Hinzufügen von Features":::

1. Wählen Sie **CI/CD-Workflows hinzufügen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/toolkit-ci-cd-workflow.png" alt-text="Ci/CD-Workflow auswählen":::

1. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
1. Wählen Sie **GitHub** als CI/CD-Anbieter aus.
1. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
1. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
1. Folgen Sie den README-Dateien unter`.github/workflows`, um den Workflow in GitHub einzurichten.

**TeamsFx CLI**

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

## <a name="set-up-pipelines-with-azure-devops"></a>Einrichten von Pipelines mit Azure DevOps

So richten Sie Pipelines mit Azure DevOps für CI/CD ein:

* Erstellen von Workflowvorlagen.

  * Visual Studio Code
  * TeamsFx CLI

* Anpassen des CI/CD-Workflows.

### <a name="create-workflow-templates"></a>Erstellen von Workflowvorlagen

Sie können die folgenden Workflowvorlagen mit Azure DevOps erstellen:

**Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.
2. Wählen Sie im linken Bereich das Symbol " **Teams-Toolkit** " :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png"::: aus.
1. Wählen Sie **CI/CD-Workflows hinzufügen** aus.
1. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
1. Wählen Sie **Azure DevOps** als CI/CD-Anbieter aus.
1. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung und Veröffentlichen in Microsoft Teams.
1. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
1. Folgen Sie den README-Dateien unter`.azure/pipelines`, um den Workflow in Azure DevOps einzurichten.

**TeamsFx CLI**

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

Sie können die folgenden Änderungen für das Skript oder die Workflowdefinition vornehmen:

1. Verwenden Sie das npm-Buildskript, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Verwenden Sie npm test script, das bei Erfolg Null zurückgibt, und ändern Sie die Testbefehle.

### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Sie können die folgenden Änderungen für das Skript oder die Workflowdefinition vornehmen:

1. Stellen Sie sicher, dass Sie ein npm-Build-Skript haben oder passen Sie die Art und Weise der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie ein npm-Testskript haben, das bei Erfolg Null zurückgibt oder ändern Sie die Testbefehle.

## <a name="set-up-pipelines-with-jenkins"></a>Einrichten von Pipelines mit Jenkins

So richten Sie Pipelines mit Jenkins für CI/CD ein:

* Erstellen von Workflowvorlagen.

  * Visual Studio Code
  * TeamsFx CLI

* Anpassen des CI/CD-Workflows.

### <a name="create-workflow-templates"></a>Erstellen von Workflowvorlagen

Sie können die folgenden Workflowvorlagen mit Jenkins erstellen:

**Microsoft Teams-Toolkit in Visual Studio Code**

1. Erstellen Sie eine neue Microsoft Teams-App mit dem Microsoft Teams-Toolkit.
2. Wählen Sie im linken Bereich das Symbol " **Teams-Toolkit** " :::image type="icon" source="../assets/images/teams-toolkit-v2/add-API/api-add-icon.png"::: aus.
3. Wählen Sie **CI/CD-Workflows hinzufügen** aus.
4. Wählen Sie in der Eingabeaufforderung eine Umgebung aus.
5. Wählen Sie **Jenkins** als CI/CD-Anbieter aus.
6. Wählen Sie aus diesen Optionen mindestens eine Vorlage aus: CI, CD, Bereitstellung oder Veröffentlichen in Microsoft Teams.
7. Öffnen Sie die Vorlage, und passen Sie die Workflows an, die in Ihre Szenarien passen.
8. Folgen Sie den README-Dateien unter`.jenkins/pipelines`, um den Workflow mit Jenkins einzurichten.

**TeamsFx CLI**

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

Sie können die folgenden Änderungen an Ihrem Projekt vornehmen:

1. Ändern Sie, wie der CI-Flow ausgelöst wird. Die Standardeinstellung ist, die Auslöser von **pollSCM** zu verwenden, wenn eine neue Änderung in den **Entwicklungszweig** verschoben wird.
1. Stellen Sie sicher, dass Sie ein npm-Build-Skript haben oder passen Sie die Art und Weise der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie ein npm-Testskript haben, das bei Erfolg Null zurückgibt oder ändern Sie die Testbefehle.

### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Führen Sie die folgenden Schritte aus, um die CD-Pipeline anzupassen:

1. Ändern Sie den CD-Ablauf. Die Standardeinstellung ist, die Auslöser zu verwenden,`pollSCM`wenn eine neue Änderung in den`main`Zweig verschoben wird.
1. Ändern Sie bei Bedarf die Buildskripts.
1. Entfernen Sie die Testskripts, wenn Sie keine Tests haben.

## <a name="set-up-pipelines-for-other-platforms"></a>Einrichten von Pipelines für andere Plattformen

Sie können den aufgeführten vordefinierten Bash-Beispielskripts folgen, um CI/CD-Pipelines auf den anderen Plattformen zu erstellen und anzupassen:

* [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Die Skripts basieren auf einem plattformübergreifenden TeamsFx-Befehlszeilentool: [TeamsFx CLI](https://www.npmjs.com/package/@microsoft/teamsfx-cli). Sie können es mit `npm install -g @microsoft/teamsfx-cli` installieren und der [Dokumentation](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) folgen, um die Skripts anzupassen.

> [!NOTE]
>
> * Um die Ausführung von `@microsoft/teamsfx-cli` im CI-Modus zu ermöglichen, aktivieren Sie `CI_ENABLED` durch `export CI_ENABLED=true`. Im CI-Modus ist `@microsoft/teamsfx-cli` für CI/CD geeignet.
> * Um die Ausführung von `@microsoft/teamsfx-cli` im nicht interaktiven Modus zu ermöglichen, legen Sie eine globale Konfiguration mit folgendem Befehl fest: `teamsfx config set -g interactive false`. Im nicht interaktiven Modus fordert `@microsoft/teamsfx-cli` keine Eingaben an..

Stellen Sie sicher, dass die Azure- und Microsoft 365-Anmeldeinformationen in Ihren Umgebungsvariablen sicher eingerichtet wurden. Wenn Sie zum Beispiel GitHub als Quellcode-Repository verwenden, lesen Sie bitte[GitHub Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).

## <a name="provision-and-deploy-resources"></a>Bereitstellen von Ressourcen

Um Ressourcen für Azure innerhalb von CI/CD bereitzustellen, müssen Sie einen Azure-Dienstprinzipal erstellen und verwenden.

Führen Sie die folgenden Schritte aus, um Azure-Dienstprinzipale zu erstellen:

1. Registrieren Sie eine Microsoft Azure Active Directory (Azure AD)-Anwendung in einem einzelnen Einzelmandanten.
2. Weisen Sie Ihrer Azure AD-Anwendung eine Rolle zu, um auf Ihr Azure-Abonnement zuzugreifen. Die`Contributor`Rolle wird empfohlen.
3. Erstellen Sie ein neues Azure AD-Anwendungsgeheimnis.

> [!TIP]
> Speichern Sie Ihre Mandanten-ID, Anwendungs-ID (AZURE_SERVICE_PRINCIPAL_NAME) und den geheimen Schlüssel (AZURE_SERVICE_PRINCIPAL_PASSWORD) für die zukünftige Verwendung.

Weitere Informationen finden Sie in den [Richtlinien für Azure-Dienstprinzipale](/azure/active-directory/develop/howto-create-service-principal-portal). Es folgen die drei Möglichkeiten zum Erstellen von Dienstprinzipalen:

* [Microsoft Azure-Portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [Windows PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Microsoft Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Veröffentlichen einer Microsoft Teams-App mit dem Microsoft Teams-Entwicklerportal

Wenn Änderungen an der Manifestdatei der Microsoft Teams-App vorliegen, können Sie das Manifest aktualisieren und die Microsoft Teams-App erneut veröffentlichen. Um eine Microsoft Teams-App manuell zu veröffentlichen, können Sie das [Entwicklerportal für Microsoft Teams](https://dev.teams.microsoft.com/home) nutzen.

Führen Sie die folgenden Schritte aus, um Ihre App zu veröffentlichen:

1. Melden Sie sich mit dem entsprechenden Konto beim [Entwicklerportal für Teams](https://dev.teams.microsoft.com) an.
2. Importieren Sie Ihr App-Paket in ZIP, wählen Sie `App -> Import app -> Replace`aus.
3. Wählen Sie die Ziel-App in der App-Liste aus.
4. Veröffentlichen Sie Ihre App, wählen Sie `Publish -> Publish to your org`.

### <a name="see-also"></a>Siehe auch

* [Schnellstart für GitHub Actions](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Erstellen Ihrer ersten Azure DevOps-Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Erstellen Ihrer ersten Jenkins-Pipeline](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md)
