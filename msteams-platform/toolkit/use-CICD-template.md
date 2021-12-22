---
title: CI- oder CD-Unterstützung für Teams Anwendungsentwickler
author: MuyangAmigo
description: CICD-Vorlagen
ms.author: ruhe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: acd12a96365bf97bd419045c415e71efd3a118e2
ms.sourcegitcommit: aede47694894d281f6b725083bc0b46ab0e4846d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2021
ms.locfileid: "61591778"
---
# <a name="ci-or-cd-support-for-teams-application-developers"></a>CI- oder CD-Unterstützung für Teams Anwendungsentwickler

TeamsFx hilft beim Automatisieren Ihres Entwicklungsworkflows beim Erstellen Teams Anwendung. Das Dokument bietet Tools und vorgefertigte Vorlagen für die ersten Schritte beim Einrichten von CI- oder CD-Pipelines mit den beliebtesten Entwicklungsplattformen wie GitHub, Azure Devops und Jenops.

|Tools und Vorlagen|Beschreibung|
|---|---|
|[teamsfx-cli-action](https://github.com/OfficeDev/teamsfx-cli-action)|Eine sofort einsatzbereite GitHub-Aktion, die in TeamsFx CLI integriert ist.|
|[github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) und [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml)| GitHub CI- oder CD-Vorlagen für eine Teams-App. |
|[jenkin-ci-template. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) und [jenkin-cd-template. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile)|Jenkin CI- oder CD-Vorlagen für eine Teams-App.|
|[script-ci-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh) und [script-cd-template.sh](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh)| Skriptvorlagen für die Automatisierung überall außerhalb von GitHub. |

## <a name="ci-or-cd-workflow-templates-in-github"></a>CI- oder CD-Workflowvorlagen in GitHub

**So schließen Sie CI- oder CD-Workflows ein, um Teams App-Entwicklungsprozess in GitHub zu automatisieren:**

1. Erstellen eines Ordners unter `.github/workflows`
1. Kopieren Sie die Vorlagendateien (entweder eine oder beide):
    * [github-ci-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-ci-template.yml) für CI-Workflow.
    * [github-cd-template.yml](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/github-cd-template.yml) für CD-Workflow.
1. Passen Sie diese Workflows an Ihre Szenarien an.

### <a name="customize-ci-workflow"></a>Anpassen des CI-Workflows

Sie können die folgenden Änderungen vornehmen, um den Workflow für Ihr Projekt anzupassen:

1. Ändern Sie, wie der CI-Fluss ausgelöst wird. Standardmäßig wird eine Pullanforderung für die `dev` Verzweigung erstellt.
1. Verwenden Sie ein npm-Buildskript, oder passen Sie die Art und Weise an, wie Sie das Projekt im Automatisierungscode erstellen.
1. Verwenden Sie ein npm-Testskript, das null zurückgibt, um erfolgreich zu sein, und/oder ändern Sie die Testbefehle.

### <a name="customize-cd-workflow"></a>Anpassen des CD-Workflows

Die folgenden Schritte zum Anpassen des CD-Workflows:

1. Standardmäßig wird der CD-Workflow ausgelöst, wenn neue Commits für die `main` Verzweigung ausgeführt werden.
1. Erstellen Sie GitHub [geheimen Repositoryschlüssel](https://docs.github.com/en/actions/reference/encrypted-secrets) nach Umgebung, um Azure- oder Microsoft 365 Anmeldeinformationen zu speichern. In der folgenden Tabelle sind alle geheimen Schlüssel aufgeführt, die Sie für GitHub erstellen müssen. Eine detaillierte Verwendung finden Sie in den GitHub Aktionen [README.md.](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md)
1. Ändern Sie ggf. die Buildskripts.
1. Entfernen Sie die Testskripts, wenn Sie keine Tests haben.

> [!Note]
> Der Bereitstellungsschritt ist nicht in der CD-Vorlage enthalten, da er normalerweise nur einmal ausgeführt wird. Sie können entweder die Bereitstellung in Teams Toolkit, TeamsFx CLI oder mithilfe eines separaten Workflows ausführen. Denken Sie daran, nach der Bereitstellung einen Commit auszuführen (Ergebnisse der Bereitstellung werden innerhalb des `.fx` Ordners abgelegt), und speichern Sie den Dateiinhalt `.fx/states/{YOUR_ENV_NAME}.userdata` in GitHub [Repositoryschlüssel](https://docs.github.com/en/actions/reference/encrypted-secrets) mit Namen `USERDATA_CONTENT` für die zukünftige Verwendung.

### <a name="environment-variables"></a>Umgebungsvariablen

Schritte zum Erstellen von Umgebungsvariablen in GitHub:

1. Navigieren Sie auf der Projekt **Einstellungen** Seite zum Abschnitt **"Umgebungen",** und wählen Sie **"Neue Umgebung"** aus.
1. Geben Sie einen Namen für Ihre Umgebung ein. Der in der Vorlage bereitgestellte Standardumgebungsname lautet `test_environment` . Wählen Sie **"Umgebung konfigurieren"** aus, um fortzufahren.
1. Wählen Sie auf der nächsten Seite **"Geheimen Schlüssel hinzufügen"** aus, um geheime Schlüssel für jedes der in der folgenden Tabelle aufgeführten Elemente hinzuzufügen.

|Name|Beschreibung|
|---|---|
|AZURE_ACCOUNT_NAME|Der Kontoname von Azure, der zum Bereitstellen von Ressourcen verwendet wird.|
|AZURE_ACCOUNT_PASSWORD|Das Kennwort des Azure-Kontos.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|Microsoft 365_ACCOUNT_NAME|Das Microsoft 365 Konto zum Erstellen und Veröffentlichen der Teams-App.|
|Microsoft 365_ACCOUNT_PASSWORD|Das Kennwort des Microsoft 365 Kontos.|
|Microsoft 365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Erfahren Sie mehr [darüber, wie Sie Ihre Microsoft 365 Mandanten-ID finden.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

> [!NOTE]
> Lesen Sie die Informationen unter ["Konfigurieren Microsoft 365/Azure-Anmeldeinformationen",](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md#configure-m365azure-credentials-as-github-secret) um sicherzustellen, dass Sie die mehrstufige Authentifizierung und die Sicherheitsstandards für die im Workflow verwendeten Anmeldeinformationen deaktiviert haben.

## <a name="set-up-ci-or-cd-pipelines-with-azure-devops"></a>Einrichten von CI- oder CD-Pipelines mit Azure DevOps

Sie können automatisierte Pipelines in Azure DevOps einrichten und einen Verweis auf die Skripts erstellen. Führen Sie die unten aufgeführten Schritte aus, um zu beginnen:

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

Die möglichen Änderungen, die Sie für das Skript oder die Workflowdefinition vornehmen können:

1. Ändern Sie, wie der CI-Fluss ausgelöst wird. Standardmäßig wird ein neuer Commit in die `dev` Verzweigung verschoben.
1. Ändern Sie die Art und Weise, wie Knoten und npm installiert werden.
1. Verwenden Sie npm build script, oder passen Sie die Art und Weise an, wie Sie im Automatisierungscode erstellen.
1. Verwenden Sie npm test script which returns zero for success, and/or change the test commands.

### <a name="set-up-cd-pipeline"></a>Einrichten der CD-Pipeline

1. Fügen Sie [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) zu Ihrem Azure DevOps-Repository hinzu, und führen Sie die erforderlichen Anpassungen aus, wie Sie aus den Kommentaren in der Skriptdatei ableiten können.
1. Erstellen Sie Ihre Azure DevOps Pipeline für CD, wie Sie auf [diesen Link](/azure/devops/pipelines/create-first-pipeline)verweisen können. Auf die Definition der Pipeline kann auf die folgende Beispieldefinition für die CI-Pipeline verwiesen werden.
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

- task: DownloadSecureFile@1
  name: userdata
  inputs:
    secureFile: 'staging.userdata'
- task: Bash@3
  inputs:
    targetType: 'inline'
    script: |
      mkdir -p .fx/states/
      cp $(userdata.secureFilePath) .fx/states/staging.userdata
  
- task: Bash@3
  env:
    AZURE_ACCOUNT_NAME: $(AZURE_ACCOUNT_NAME)
    AZURE_ACCOUNT_PASSWORD: $(AZURE_ACCOUNT_PASSWORD)
    AZURE_TENANT_ID: $(AZURE_TENANT_ID)
    Microsoft 365_ACCOUNT_NAME: $(Microsoft 365_ACCOUNT_NAME)
    Microsoft 365_ACCOUNT_PASSWORD: $(Microsoft 365_ACCOUNT_PASSWORD)
  inputs:
    filePath: './others-script-cd-template.sh'
```

Die möglichen Änderungen, die Sie für das Skript oder die Workflowdefinition vornehmen können:

1. Wie der CD-Fluss ausgelöst wird. Standardmäßig geschieht dies, wenn neue  Commits für die Hauptverzweigung ausgeführt werden.
1. Ändern Sie die Art und Weise, wie Knoten und npm installiert werden.
1. Ändern Sie den Umgebungsnamen, standardmäßig dessen **Staging.**
1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das null zurückgibt, um erfolgreich zu sein, und/oder ändern Sie die Testbefehle.

> [!Note]
> Der Bereitstellungsschritt ist nicht in der CD-Vorlage enthalten, da er normalerweise nur einmal ausgeführt wird. Sie können entweder die Bereitstellung in Teams Toolkit, TeamsFx CLI oder mithilfe eines getrennten Workflows ausführen. Denken Sie daran, nach der Bereitstellung einen Commit auszuführen (Ergebnisse der Bereitstellung werden im `.fx` Ordner abgelegt) und in Azure DevOps sichere `.fx/states/{YOUR_ENV_NAME}.userdata` [Dateien](/azure/devops/pipelines/library/secure-files) für die zukünftige Verwendung hochzuladen.

### <a name="environment-variables-for-azure-devops"></a>Umgebungsvariablen für Azure DevOps

Schritte zum Erstellen von Pipelinevariablen in Azure DevOps:

1. Wählen Sie auf der Seite "Pipelinebearbeitung" oben rechts **"Variablen"** und dann **"Neue Variable"** aus.
1. Geben Sie das Name/Wert-Paar für Ihre Variable ein.
1. Aktivieren Sie bei Bedarf das Kontrollkästchen **"Diesen Wert geheim halten".**
1. Wählen Sie **"OK"** aus, um die Variable zu erstellen.

|Name|Beschreibung|
|---|---|
|AZURE_ACCOUNT_NAME|Der Kontoname von Azure, der zum Bereitstellen von Ressourcen verwendet wird.|
|AZURE_ACCOUNT_PASSWORD|Das Kennwort des Azure-Kontos.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|Microsoft 365_ACCOUNT_NAME|Das Microsoft 365-Konto zum Erstellen und Veröffentlichen der Teams-App.|
|Microsoft 365_ACCOUNT_PASSWORD|Das Kennwort des Microsoft 365 Kontos.|
|Microsoft 365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Erfahren Sie mehr [darüber, wie Sie Ihre Microsoft 365 Mandanten-ID finden.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|

> [!NOTE]
> Der Bereitstellungsschritt ist nicht in der CD-Vorlage enthalten, da er normalerweise nur einmal ausgeführt wird. Sie können entweder die Bereitstellung in Teams Toolkit, TeamsFx CLI oder mithilfe eines getrennten Workflows ausführen. Denken Sie daran, nach der Bereitstellung einen Commit auszuführen (Ergebnisse der Bereitstellung werden im `.fx` Ordner abgelegt) und speichern Sie den Dateiinhalt `.fx/states/{YOUR_ENV_NAME}.userdata` in Jenkins-Anmeldeinformationen für die zukünftige Verwendung.

## <a name="ci-or-cd-pipeline-templates-in-jenkins"></a>CI- oder CD-Pipelinevorlagen in Jenkins

Um diese Vorlagen zu Ihrem Repository hinzuzufügen, benötigen Sie Ihre Versionen der [Jenkin-Ci-Vorlage. Jenkinfile](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-ci-template.Jenkinsfile) und  [jenkin-cd-template. Jenkinfile,](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/jenkins-cd-template.Jenkinsfile) um sich in Ihrem Repository nach Verzweigung zu befinden.

Außerdem müssen Sie CI- oder CD-Pipelines in Jenkin erstellen, die entsprechend auf die jeweilige **Jenkinfile** verweisen.

Führen Sie die Schritte aus, um zu überprüfen, wie Sie Jenkin mit verschiedenen SCM-Plattformen verbinden:

1. [Jenkin mit GitHub](https://www.jenkins.io/solutions/github/)
2. [Jenkin mit Azure DevOps](https://www.dragonspears.com/blog/ci-cd-with-jenkins-and-azure-devops-services)
3. [Jenkin mit GitLab](https://docs.gitlab.com/ee/integration/jenkins.html)
4. [Jenkin mit Bitbucket](https://medium.com/ampersand-academy/integrate-bitbucket-jenkins-c6e51103d0fe)

### <a name="customize-ci-pipeline"></a>Anpassen der CI-Pipeline

Es gibt einige potenzielle Änderungen, die Sie vornehmen können, um Ihr Projekt anzupassen:

1. Benennen Sie die Vorlagendatei in **Jenkinsfile** um, da es sich um eine gängige Vorgehensweise handelt, und setzen Sie sie unter die Zielverzweigung, z. B. den **Dev** Branch.
1. Ändern Sie, wie der CI-Fluss ausgelöst wird. Wir verwenden standardmäßig die Trigger von **pollSCM,** wenn eine neue Änderung in den **Dev** Branch verschoben wird.
1. Stellen Sie sicher, dass Sie über ein npm-Buildskript verfügen, oder passen Sie die Art der Erstellung im Automatisierungscode an.
1. Stellen Sie sicher, dass Sie über ein npm-Testskript verfügen, das null zurückgibt, um erfolgreich zu sein, und/oder ändern Sie die Testbefehle.

### <a name="customize-cd-pipeline"></a>Anpassen der CD-Pipeline

Ändern Sie die folgenden Schritte, um die CD-Pipeline anzupassen:

1. Benennen Sie die Vorlagendatei in **Jenkinfile** um, da es sich um eine gängige Vorgehensweise handelt, und setzen Sie sie unter die Zielverzweigung, z. B. die Hauptverzweigung. 
1. Wie der CD-Fluss ausgelöst wird. Wir verwenden standardmäßig die Trigger von **pollSCM,** wenn eine neue Änderung in die **Hauptverzweigung** verschoben wird.
1. Erstellen Sie [Anmeldeinformationen](https://www.jenkins.io/doc/book/using/using-credentials/) für die Jenpipeline, um Azure/Microsoft 365 Anmeldeinformationen zu speichern. In der folgenden Tabelle sind alle Anmeldeinformationen aufgeführt, die Sie für Jenkins erstellen müssen.
1. Ändern Sie ggf. die Buildskripts.
1. Entfernen Sie die Testskripts, wenn Sie keine Tests haben.

> [!Note]
 Der Bereitstellungsschritt ist nicht in der CD-Vorlage enthalten, da er normalerweise nur einmal ausgeführt wird. Sie können entweder die Bereitstellung in Teams Toolkit, TeamsFx CLI oder mithilfe eines separaten Workflows ausführen. Denken Sie daran, nach der Bereitstellung einen Commit auszuführen (Ergebnisse der Bereitstellung werden im `.fx` Ordner abgelegt) und speichern Sie den Dateiinhalt `.fx/states/{YOUR_ENV_NAME}.userdata` in Jenkins-Anmeldeinformationen für die zukünftige Verwendung.

### <a name="environment-variables-for-jenkins"></a>Umgebungsvariablen für Jenkins

Folgen Sie ["using-credentials",](https://www.jenkins.io/doc/book/using/using-credentials/) um Anmeldeinformationen für Jenkin zu erstellen.

|Name|Beschreibung|
|---|---|
|AZURE_ACCOUNT_NAME|Der Kontoname von Azure, der zum Bereitstellen von Ressourcen verwendet wird.|
|AZURE_ACCOUNT_PASSWORD|Das Kennwort des Azure-Kontos.|
|AZURE_SUBSCRIPTION_ID|So identifizieren Sie das Abonnement, in dem die Ressourcen bereitgestellt werden.|
|AZURE_TENANT_ID|So identifizieren Sie den Mandanten, in dem sich das Abonnement befindet.|
|Microsoft 365_ACCOUNT_NAME|Das M3icrosoft 365-Konto zum Erstellen und Veröffentlichen der Teams-App.|
|Microsoft 365_ACCOUNT_PASSWORD|Das Kennwort des Microsoft 365 Kontos.|
|Microsoft 365_TENANT_ID|Um den Mandanten zu identifizieren, in dem die Teams App erstellt/veröffentlicht wird. Dieser Wert ist optional, es sei denn, Sie verfügen über ein mehrinstanzenfähiges Konto und möchten einen anderen Mandanten verwenden. Erfahren Sie mehr [darüber, wie Sie Ihre Microsoft 365 Mandanten-ID finden.](/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)|
> Hinweis: Lesen Sie die Informationen unter ["Konfigurieren Microsoft 365/Azure-Anmeldeinformationen",](https://github.com/OfficeDev/teamsfx-cli-action/blob/main/README.md#configure-m365azure-credentials-as-github-secret) um sicherzustellen, dass Sie die mehrstufige Authentifizierung und die Sicherheitsstandards für die in der Pipeline verwendeten Anmeldeinformationen deaktiviert haben.

## <a name="get-started-guide-for-other-platforms"></a>Leitfaden für die ersten Schritte für andere Plattformen

Sie können den aufgeführten vordefinierten Beispiel-Bash-Skripts folgen, um CI- oder CD-Pipelines auf anderen Plattformen zu erstellen und anzupassen:

* [CI-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-ci-template.sh)
* [CD-Skripts](https://github.com/OfficeDev/TeamsFx/blob/main/docs/cicd_insider/others-script-cd-template.sh) Die Skripts sind ziemlich einfach, und die meisten Teile davon sind plattformübergreifende CLI, sodass es einfach ist, sie in andere Arten von Skripts zu transformieren, z. B. PowerShell.

Die Skripts basieren auf einem plattformübergreifenden TeamsFx-Befehlszeilentool [TeamsFx-CLI.](https://www.npmjs.com/package/@microsoft/teamsfx-cli) Sie können es installieren `npm install -g @microsoft/teamsfx-cli` und der [Dokumentation](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/cli/user-manual.md) folgen, um die Skripts anzupassen.

> [!Note]
> Um `@microsoft/teamsfx-cli` die Ausführung im CI-Modus zu aktivieren, aktivieren Sie `CI_ENABLED` nach `export CI_ENABLED=true` . Im CI-Modus `@microsoft/teamsfx-cli` ist für CI oder CD geeignet.

Stellen Sie sicher, dass Azure- und M365-Anmeldeinformationen in Ihren Umgebungsvariablen sicher festgelegt werden. Wenn Sie beispielsweise GitHub als Quellcoderepository verwenden, können Sie die [Github Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets) verwenden, um Ihre Umgebungsvariablen sicher zu speichern.

## <a name="publish-teams-app-using-teams-developer-portal"></a>Veröffentlichen Teams App mit Teams Entwicklerportal

Wenn Änderungen im Zusammenhang mit Teams Manifestdatei der App vorgenommen werden, sollten Sie die Teams-App erneut veröffentlichen, um das Manifest zu aktualisieren.

Um Teams App manuell zu veröffentlichen, können Sie [das Entwicklerportal für Teams](https://dev.teams.microsoft.com/home)verwenden.

**So veröffentlichen Sie Ihre App**

1. Melden Sie sich im [Entwicklerportal für Teams](https://dev.teams.microsoft.com) mit dem entsprechenden Konto an.
2. Importieren Sie Ihr App-Paket in ZIP, indem Sie `App -> Import app -> Replace` .
3. Wählen Sie die Ziel-App in der App-Liste aus, und wechseln Sie zur Übersichtsseite.
4. Veröffentlichen Sie Ihre App, indem Sie `Publish -> Publish to your org`

### <a name="see-also"></a>Siehe auch

* [Schnellstart für GitHub-Aktionen](https://docs.github.com/en/actions/quickstart#creating-your-first-workflow)
* [Erstellen Ihrer ersten Azure DevOps-Pipeline](/azure/devops/pipelines/create-first-pipeline)
* [Erstellen Ihrer ersten Jenpipeline](https://www.jenkins.io/doc/pipeline/tour/hello-world/)
