---
title: CI- oder CD-Unterstützung für Teams Anwendungsentwickler
author: MuyangAmigo
description: CICD-Vorlagen
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 5ca5f81fd857296f2e81dbce97673f5a10c66ab7
ms.sourcegitcommit: 2d5bdda6c52693ed682bbd543b0aa66e1feb3392
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2022
ms.locfileid: "61768573"
---
# <a name="cicd-guide"></a>CI/CD-Leitfaden

TeamsFx hilft beim Automatisieren Ihres Entwicklungsworkflows beim Erstellen Teams Anwendung. Das Dokument enthält Tools und Vorlagen für die ersten Schritte beim Einrichten von CI- oder CD-Pipelines mit GitHub, Azure Devops und Jenkins.

|Tools und Vorlagen|Beschreibung| 
|---|---|
|[teamsfx-cli-action](https://github.com/OfficeDev/teamsfx-cli-action)|GitHub Aktion, die in TeamsFx CLI integriert ist.|
|[github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) und [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml)| GitHub CI- oder CD-Vorlagen für Teams App. |
|[jenkin-ci-template. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) und [jenkin-cd-template. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile)|Jenkin CI- oder CD-Vorlagen für eine Teams-App.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) und [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Skriptvorlagen für die Automatisierung außerhalb von GitHub. |

## <a name="ci-or-cd-workflow-templates-in-github"></a>CI- oder CD-Workflowvorlagen in GitHub

**So schließen Sie CI- oder CD-Workflows ein, um Teams App-Entwicklungsprozess in GitHub zu automatisieren:**

1. Ordner erstellen unter `.github/workflows`
1. Kopieren Sie eine der folgenden Vorlagendateien:
    * [github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) für CI-Workflow.
    * [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml) für CD-Workflow.
1. Passen Sie die Workflows an, die ihren Szenarien entsprechen.

### <a name="customize-ci-workflow"></a>Anpassen des CI-Workflows

Führen Sie die folgenden Schritte aus, um den Workflow für Ihr Projekt anzupassen:

1. Ändern Sie den CI-Fluss. 
1. Verwenden Sie das npm-Buildskript, oder passen Sie die Art und Weise an, wie Sie das Projekt im Automatisierungscode erstellen.
1. Verwenden Sie npm test script which returns zero for success, and change the test commands.

### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Führen Sie die folgenden Schritte aus, um den CD-Workflow anzupassen:

1. Standardmäßig wird der CD-Workflow ausgelöst, wenn neue Commits für die `main` Verzweigung ausgeführt werden.
1. Erstellen Sie GitHub [geheimen Repositoryschlüssel](https://docs.github.com/en/actions/reference/encrypted-secrets) nach Umgebung, um Anmeldeinformationen für Azure-Dienstprinzipale und M365-Konten zu speichern. Weitere Informationen finden Sie unter [GitHub Aktionen](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md).
1. Ändern Sie ggf. die Buildskripts.
1. Entfernen Sie die Testskripts nach Bedarf.

> [!NOTE]
> Der Bereitstellungsschritt ist nicht in der CD-Vorlage enthalten, da er normalerweise nur einmal ausgeführt wird. Sie können die Bereitstellung entweder in Teams Toolkit, TeamsFx CLI oder mithilfe eines separaten Workflows ausführen. Stellen Sie sicher, dass nach der Bereitstellung ein Commit ausgeführt wird. Die Ergebnisse der Bereitstellung werden im `.fx` Ordner abgelegt.

### <a name="github-secrets"></a>Github secrets

In der folgenden Tabelle sind alle geheimen Schlüssel aufgeführt, die Sie zum Erstellen einer Umgebung in GitHub benötigen:

1. Wählen Sie **Einstellungen** aus.
1. Wechseln Sie zum Abschnitt **"Umgebungen".**
1. Wählen Sie **"Neue Umgebung"** aus.
1. Geben Sie einen Namen für Ihre Umgebung ein. Der in der Vorlage bereitgestellte Standardumgebungsname lautet `test_environment` . 
1. Wählen Sie **"Umgebung konfigurieren" aus.**
1. Wählen **Sie "Geheimen Schlüssel hinzufügen" aus.**

In der folgenden Tabelle sind alle geheimen Schlüssel aufgeführt, die zum Erstellen einer Umgebung erforderlich sind:

|Name|Beschreibung|
|---|---|
|AZURE_SERVICE_PRINCIPAL_NAME|Der Dienstprinzipalname von Azure, der zur Bereitstellung von Ressourcen verwendet wird.|
|AZURE_SERVICE_PRINCIPAL_PASSWORD|Das Kennwort des Azure-Dienstprinzipals.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|M365_ACCOUNT_NAME|Das M365-Konto zum Erstellen und Veröffentlichen Teams App.|
|M365_ACCOUNT_PASSWORD|Das Kennwort des M365-Kontos.|
|M365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Weitere Informationen finden Sie unter [Suchen Ihrer M365-Mandanten-ID.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

> [!NOTE]
> Derzeit wird der nicht interaktive Authentifizierungsstil für M365 in CI- oder CD-Workflows verwendet. Stellen Sie sicher, dass Ihr M365-Konto über ausreichende Berechtigungen in Ihrem Mandanten verfügt und keine mehrstufige Authentifizierung oder andere erweiterte Sicherheitsfeatures aktiviert ist. Weitere Informationen finden Sie unter [Konfigurieren von M365-Anmeldeinformationen,](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md#configure-m365azure-credentials-as-github-secret) um sicherzustellen, dass Sie die mehrstufige Authentifizierung und Die Sicherheitsstandards für die im Workflow verwendeten Anmeldeinformationen deaktiviert haben.

> [!NOTE]
> Derzeit wird der Dienstprinzipal für Azure in CI/CD-Workflows verwendet. Weitere Informationen finden Sie unter[Erstellen von Azure-Dienstprinzipien.](#create-azure-service-principals)

## <a name="set-up-ci-or-cd-pipelines-with-azure-devops"></a>Einrichten von CI- oder CD-Pipelines mit Azure DevOps

Sie können automatisierte Pipelines in Azure DevOps einrichten und einen Verweis auf die Skripts erstellen.

Führen Sie die folgenden Schritte aus, um zu beginnen:

* [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

### <a name="set-up-ci-pipeline"></a>Einrichten der CI-Pipeline

1. Fügen Sie [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) zu Ihrem Azure DevOps-Repository hinzu, und führen Sie die erforderlichen Anpassungen aus, wie Sie aus den Kommentaren in der Skriptdatei ableiten können.
1. Führen Sie die [Schritte aus, um Ihre Azure DevOps Pipeline für CI zu erstellen.](/azure/devops/pipelines/create-first-pipeline)
Hier sehen Sie ein Szenario mit gängigen CI-Pipelineskripts:

```yml
trigger:
- dev 

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.17.0'
    checkLatest: true
  
- task: Bash@3
  inputs:
    filePath: './others-script-ci-template.sh'
```

Es folgen die Änderungen, die Sie für das Skript oder die Workflowdefinition vornehmen können:

1. Ändern Sie den CI-Fluss. Standardmäßig wird ein neuer Commit in die `dev` Verzweigung verschoben.
1. Ändern Sie die Art und Weise, wie Knoten und npm installiert werden.
1. Verwenden Sie npm build script, oder passen Sie die Art und Weise an, wie Sie im Automatisierungscode erstellen.
1. Verwenden Sie npm test script which returns zero for success, and change the test commands.

### <a name="set-up-cd-pipeline"></a>Einrichten der CD-Pipeline

1. Fügen Sie [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) zu Ihrem Azure DevOps-Repository hinzu, und führen Sie die erforderlichen Anpassungen aus, wie Sie aus den Kommentaren in der Skriptdatei ableiten können.
1. Erstellen Sie Ihre Azure DevOps-Pipeline für CD. Weitere Informationen finden Sie unter [Erstellen der ersten Pipeline.](/azure/devops/pipelines/create-first-pipeline) Auf die Definition der Pipeline kann auf die folgende Beispieldefinition für die CI-Pipeline verwiesen werden.
1. Fügen Sie die erforderlichen Variablen durch Definieren von [Variablen](/azure/devops/pipelines/process/variables)hinzu, und machen Sie sie bei Bedarf als geheime Schlüssel.

```yml
trigger:
- main 

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.17.0'
    checkLatest: true
  
- task: Bash@3
  env:
    SP_NAME: $(AZURE_SERVICE_PRINCIPAL_NAME)
    SP_PASSWORD: $(AZURE_SERVICE_PRINCIPAL_PASSWORD)
    TENANT_ID: $(AZURE_TENANT_ID)
    AZURE_SUBSCRIPTION_ID: $(AZURE_SUBSCRIPTION_ID)
    M365_ACCOUNT_NAME: $(M365_ACCOUNT_NAME)
    M365_ACCOUNT_PASSWORD: $(M365_ACCOUNT_PASSWORD)
  inputs:
    filePath: './others-script-cd-template.sh'
```

Es folgen die Änderungen, die Sie für das Skript oder die Workflowdefinition vornehmen können:

1. Wie der CD-Fluss ausgelöst wird. Standardmäßig geschieht dies, wenn neue  Commits für die Hauptverzweigung ausgeführt werden.
1. Ändern Sie die Art und Weise, wie Knoten und npm installiert werden.
1. Ändern Sie den Umgebungsnamen, standardmäßig dessen **Staging.**
1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das null zurückgibt, um erfolgreich zu sein, und/oder ändern Sie die Testbefehle.

### <a name="pipeline-variables-for-azure-devops"></a>Pipelinevariablen für Azure DevOps

Führen Sie die folgenden Schritte aus, um Pipelinevariablen in Azure DevOps zu erstellen:

1. Wählen Sie auf der Bearbeitungsseite "Pipeline" **variablen** aus, und wählen Sie **"Neue Variable"** aus.
1. Geben Sie name or value pair for your variable.
1. Aktivieren Sie bei Bedarf das Kontrollkästchen **"Diesen Wert geheim halten".**
1. Wählen Sie **"OK"** aus, um die Variable zu erstellen.

|Name|Beschreibung|
|---|---|
|AZURE_SERVICE_PRINCIPAL_NAME|Der Dienstprinzipalname von Azure, der zur Bereitstellung von Ressourcen verwendet wird.|
|AZURE_SERVICE_PRINCIPAL_PASSWORD|Das Kennwort des Azure-Dienstprinzipals.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|M365_ACCOUNT_NAME|Das M365-Konto zum Erstellen und Veröffentlichen der Teams-App.|
|M365_ACCOUNT_PASSWORD|Das Kennwort des M365-Kontos.|
|M365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Erfahren Sie mehr [darüber, wie Sie Ihre M365-Mandanten-ID finden.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

## <a name="ci-or-cd-pipeline-templates-in-jenkins"></a>CI- oder CD-Pipelinevorlagen in Jenkins

Um diese Vorlagen zu Ihrem Repository hinzuzufügen, fragen Sie die Versionen der [Jenkin-ci-Vorlage ab. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) und  [jenkin-cd-template. Jenkinfile,](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile) um sich in Ihrem Repository nach Verzweigung zu befinden.

Außerdem müssen Sie CI- oder CD-Pipelines in Jenkin erstellen, die entsprechend auf die jeweilige **Jenkinfile** verweisen.

Führen Sie die Schritte aus, um zu überprüfen, wie Sie Jenkin mit verschiedenen SCM-Plattformen verbinden:

1. [Jenkin mit GitHub](https://www.jenkins.io/solutions/github/)
2. [Jenkin mit Azure DevOps](https://www.dragonspears.com/blog/ci-cd-with-jenkins-and-azure-devops-services)
3. [Jenkin mit GitLab](https://docs.gitlab.com/ee/integration/jenkins.html)
4. [Jenkin mit Bitbucket](https://medium.com/ampersand-academy/integrate-bitbucket-jenkins-c6e51103d0fe)

### <a name="customize-ci-pipeline"></a>Anpassen der CI-Pipeline

Es folgen einige der Änderungen, die Sie vornehmen können, um Ihr Projekt anzupassen:

1. Benennen Sie die Vorlagendatei in **Jenkinfile** um, und platzieren Sie sie unter der Zielverzweigung, z. B. der **Dev** Branch.
1. Ändern Sie, wie der CI-Fluss ausgelöst wird. Wir verwenden standardmäßig die Trigger von **pollSCM,** wenn eine neue Änderung in den **Dev** Branch verschoben wird.
1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das null zurückgibt, um erfolgreich zu sein, und/oder ändern Sie die Testbefehle.

### <a name="customize-cd-pipeline"></a>Anpassen der CD-Pipeline

Führen Sie die folgenden Schritte aus, um die CD-Pipeline anzupassen:

1. Benennen Sie die Vorlagendatei in **Jenkinsfile** um, und platzieren Sie sie unter der Zielverzweigung, z. B. der Hauptverzweigung. 
1. Ändern Sie den CD-Fluss. Wir verwenden standardmäßig die Trigger von **pollSCM,** wenn eine neue Änderung in die **Hauptverzweigung** verschoben wird.
1. Erstellen Sie [Jenpipelineanmeldeinformationen,](https://www.jenkins.io/doc/book/using/using-credentials/) um Anmeldeinformationen für Azure-Dienstprinzipale und M365-Konten zu speichern.
1. Ändern Sie ggf. die Buildskripts.
1. Entfernen Sie die Testskripts, wenn Sie keine Tests haben.

### <a name="credentials-for-jenkins"></a>Anmeldeinformationen für Jenkins

Folgen Sie ["using-credentials",](https://www.jenkins.io/doc/book/using/using-credentials/) um Anmeldeinformationen für Jenkin zu erstellen.

|Name|Beschreibung|
|---|---|
|AZURE_SERVICE_PRINCIPAL_NAME|Der Dienstprinzipalname von Azure, der zur Bereitstellung von Ressourcen verwendet wird.|
|AZURE_SERVICE_PRINCIPAL_PASSWORD|Das Kennwort des Azure-Dienstprinzipals.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|M365_ACCOUNT_NAME|Das M365-Konto zum Erstellen und Veröffentlichen der Teams-App.|
|M365_ACCOUNT_PASSWORD|Das Kennwort des M365-Kontos.|
|M365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Erfahren Sie mehr [darüber, wie Sie Ihre M365-Mandanten-ID finden.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

## <a name="get-started-guide-for-other-platforms"></a>Leitfaden für die ersten Schritte für andere Plattformen

Sie können den aufgeführten vordefinierten Beispiel-Bash-Skripts folgen, um CI- oder CD-Pipelines auf anderen Plattformen zu erstellen und anzupassen:

* [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)

Die Skripts basieren auf einem plattformübergreifenden TeamsFx-Befehlszeilentool [TeamsFx-CLI.](https://www.npmjs.com/package/@microsoft/teamsfx-cli) Sie können es installieren `npm install -g @microsoft/teamsfx-cli` und der [Dokumentation](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) folgen, um die Skripts anzupassen.

> [!NOTE]
> * Um `@microsoft/teamsfx-cli` die Ausführung im CI-Modus zu aktivieren, aktivieren Sie `CI_ENABLED` nach `export CI_ENABLED=true` . Im CI-Modus `@microsoft/teamsfx-cli` ist für CI oder CD geeignet.
> * Um `@microsoft/teamsfx-cli` die Ausführung im nicht interaktiven Modus zu aktivieren, legen Sie eine globale Konfiguration mit folgendem Befehl fest: `teamsfx config set -g interactive false` . Im nicht interaktiven Modus `@microsoft/teamsfx-cli` werden eingabeinteraktiv keine Fragen gestellt.

Stellen Sie sicher, dass Azure- und M365-Anmeldeinformationen in Ihren Umgebungsvariablen sicher festgelegt werden. Wenn Sie beispielsweise GitHub als Quellcode-Repository verwenden. Weitere Informationen finden Sie unter [Github Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets).

## <a name="create-azure-service-principals"></a>Erstellen von Azure-Dienstprinzipalen

Um Ressourcen für Azure innerhalb von CI/CD bereitzustellen und bereitzustellen, müssen Sie einen Azure-Dienstprinzipal für die Verwendung erstellen.

Führen Sie die folgenden Schritte aus, um Azure-Dienstprinzipale zu erstellen:
1. Registrieren Sie eine Azure AD Anwendung in einem einzelnen Mandanten.
2. Weisen Sie Ihrer Azure AD-Anwendung eine Rolle für den Zugriff auf Ihr Azure-Abonnement zu, und `Contributor` die Rolle wird empfohlen. 
3. Erstellen Sie einen neuen Azure AD Anwendungsschlüssel.

> [!TIP]
> Speichern Sie Ihre Mandanten-ID, Anwendungs-ID(AZURE_SERVICE_PRINCIPAL_NAME) und den geheimen Schlüssel (AZURE_SERVICE_PRINCIPAL_PASSWORD) für die zukünftige Verwendung.

Weitere Informationen finden Sie in den [Richtlinien für Azure-Dienstprinzipale.](/azure/active-directory/develop/howto-create-service-principal-portal) Es folgen die drei Methoden zum Erstellen des Dienstprinzipals: 
* [Azure-Portal](/azure/active-directory/develop/howto-create-service-principal-portal)
* [PowerShell](/azure/active-directory/develop/howto-authenticate-service-principal-powershell)
* [Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli)

## <a name="publish-teams-app-using-teams-developer-portal"></a>Veröffentlichen Teams App mit Teams Entwicklerportal
Wenn Änderungen im Zusammenhang mit Teams Manifestdatei der App vorgenommen werden, sollten Sie die Teams-App erneut veröffentlichen, um das Manifest zu aktualisieren.

Um Teams App manuell zu veröffentlichen, können Sie [das Entwicklerportal für Teams](https://dev.teams.microsoft.com/home)verwenden.

Führen Sie die folgenden Schritte aus, um Ihre App zu veröffentlichen:
1. Melden Sie sich beim [Entwicklerportal für Teams](https://dev.teams.microsoft.com) mit dem entsprechenden Konto an.
2. Importieren Sie Ihr App-Paket in ZIP, indem Sie `App -> Import app -> Replace` .
3. Wählen Sie die Ziel-App in der App-Liste aus.
4. Veröffentlichen Sie Ihre App, indem Sie `Publish -> Publish to your org`

### <a name="see-also"></a>Siehe auch

* [Schnellstart für GitHub-Aktionen](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Erstellen Der ersten Azure DevOps Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Erstellen Ihrer ersten Jenpipeline](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
* [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](/concepts/build-and-test/teams-developer-portal)
