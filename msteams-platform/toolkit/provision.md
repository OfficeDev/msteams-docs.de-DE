---
title: Verwenden von Teams Toolkit zum Bereitstellen von Cloudressourcen
author: MuyangAmigo
description: Bereitstellen von Cloudressourcen
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: c8899131876533fdd64913fb6790cff9f258e8f5
ms.sourcegitcommit: aede47694894d281f6b725083bc0b46ab0e4846d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2021
ms.locfileid: "61591785"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Verwenden von Teams Toolkit zum Bereitstellen von Cloudressourcen

TeamsFx bietet eine nahtlose Integration in Azure und Microsoft 365 Cloud, mit der Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen, die Ihre Anwendung benötigt, deklarativ mithilfe der Infrastruktur als Codeansatz bereitstellen können.  

## <a name="prerequisites"></a>Voraussetzungen

* Kontovoraussetzungen

    Um Cloudressourcen bereitzustellen, benötigen Sie die folgenden Konten mit den richtigen Berechtigungen. Weitere Informationen finden Sie unter [Vorbereiten von Konten zum Erstellen Teams App.](accounts.md)
    * Microsoft 365
    * Azure mit gültigem Abonnement

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Sie sollten bereits ein Teams App-Projekt in VS-Code geöffnet haben.

## <a name="provision-using-teams-toolkit"></a>Bereitstellung mit Teams Toolkit

Die Bereitstellung erfolgt mit einem einzigen Befehl im Teams Toolkit für Visual Studio Code oder TeamsFx CLI wie folgt:

[Bereitstellen einer Azure-basierten App](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8&branch)

## <a name="resource-creation"></a>Erstellen von Ressourcen

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen abrufen:

* AAD Anwendung unter Ihrem Microsoft 365 Mandanten
* Teams App-Registrierung unter der Teams-Plattform Ihres Microsoft 365 Mandanten
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement

Wenn Sie ein neues Projekt erstellen, erhalten Sie alle zu erstellenden Azure-Ressourcen. Die generierte ARM-Vorlage definiert alle Azure-Ressourcen und hilft bei der Erstellung der erforderlichen Azure-Ressourcen während der Bereitstellung. Wenn Sie einem vorhandenen Projekt [neue Funktionen/Ressourcen hinzufügen,](./add-resource.md) spiegelt die aktualisierte ARM-Vorlage die aktuelle Änderung wider.

> [!NOTE]
> Azure-Dienste verursachen Kosten in Ihrem Abonnement. Eine Schätzung finden Sie im [Preisrechner.](https://azure.microsoft.com/pricing/calculator/)

### <a name="resource-creation-for-teams-tab-application"></a>Erstellen von Ressourcen für Teams Registerkartenanwendung

|Ressourcen|Zweck dieser Ressource| Anmerkungen |
|----------|--------------------------------|-----|
| Azure Storage | Hosten Der Registerkarten-App | Ermöglicht der statischen Web-App das Hosten Ihrer Registerkarten-App |
| App-Dienstplan für einfache Authentifizierung | Hosten der Web-App der einfachen Authentifizierung | |
| Web App für einfache Authentifizierung | Hosten eines einfachen Authentifizierungsservers, der Ihnen den Zugriff auf andere Dienste in Ihrer Einzelseitenanwendung erleichtert | Fügt eine vom Benutzer zugewiesene Identität hinzu, um den Zugriff auf andere Azure-Ressourcen zu vereinfachen. |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resources-created-for-teams-bot-or-messaging-extension-application"></a>Ressourcen, die für Teams Bot- oder Messaging-Erweiterungsanwendung erstellt wurden

|Ressourcen|Zweck dieser Ressource| Anmerkungen |
|----------|--------------------------------|-----|
| Azure Bot Service | Registriert Ihre App als Bot beim Bot Framework | Verbindet den Bot mit Teams |
| App-Dienstplan für Bot | Hosten der Web-App von Bot | |
| Web App für Bot | Hosten Ihrer Bot-App | Fügt eine vom Benutzer zugewiesene Identität hinzu, um den Zugriff auf andere Azure-Ressourcen zu vereinfachen. <br /> Fügt App-Einstellungen hinzu, die für [das TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resources-created-when-including-azure-functions-in-the-project"></a>Ressourcen, die erstellt werden, wenn Azure-Funktionen in das Projekt eingeschlossen werden

|Ressourcen|Zweck dieser Ressource| Anmerkungen |
|----------|--------------------------------|-----|
| App-Dienstplan für Funktions-App | Hosten der Funktions-App | |
| Funktions-App | Hosten Ihrer Azure Functions-APIs | Fügt eine vom Benutzer zugewiesene Identität hinzu, um den Zugriff auf andere Azure-Ressourcen zu vereinfachen. <br /> Fügt eine CORS-Regel hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen. <br /> Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt. <br /> Fügt App-Einstellungen hinzu, die für [das TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Azure Storage für Funktions-App | Erforderlich beim Erstellen einer Funktions-App | |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resources-created-when-including-azure-sql-in-the-project"></a>Ressourcen, die erstellt werden, wenn Azure SQL in das Projekt eingeschlossen werden

|Ressourcen|Zweck dieser Ressource| Anmerkungen |
|----------|--------------------------------|-----|
| Azure SQL Server | Hosten der Azure SQL-Datenbank Instanz | Ermöglicht allen Azure-Diensten den Zugriff auf den Server |
| Azure SQL-Datenbank | Store Daten für Ihre App | Gewährt der Benutzeridentität Lese-/Schreibberechtigung für die Datenbank |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resources-created-when-including-azure-api-management-in-the-project"></a>Ressourcen, die erstellt werden, wenn Azure API Management in das Projekt eingeschlossen wird

|Ressourcen|Zweck dieser Ressource|
|----------|--------------------------------|
| Azure Active Directory-Anwendung für den API-Verwaltungsdienst | Ermöglicht Microsoft Power Platform-Zugriffs-APIs, die vom API-Verwaltungsdienst verwaltet werden |
| API-Verwaltungsdienst | Verwalten Der in der Funktions-App gehosteten APIs |
| API-Verwaltungsprodukt | Gruppieren Sie Ihre APIs, definieren Sie Nutzungsbedingungen und Laufzeitrichtlinien |
| API-Verwaltung OAuth Server | Ermöglicht Microsoft Power Platform den Zugriff auf Ihre in der Funktions-App gehosteten APIs. |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen |

## <a name="customize-resource-provision"></a>Anpassen der Ressourcenbereitstellung

Teams Toolkit ermöglicht es Ihnen, eine Infrastruktur als Codeansatz zu verwenden, um zu definieren, welche Azure-Ressourcen Sie bereitstellen und wie Sie diese konfigurieren möchten. Die Tools verwenden die ARM-Vorlage, um Azure-Ressourcen zu definieren. Bei der ARM-Vorlage handelt es sich um eine Reihe von Biicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können erstellte Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie unter [Bicep-Dokument.](/azure/azure-resource-manager/bicep.md) Die Bereitstellung mit ARM umfasst das Ändern der folgenden beiden Sätze von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien ( `azure.parameters.{your_env_name}.json` ) befinden sich im `.fx/configs` Ordner, um Parameter an Vorlagen zu übergeben.
* ARM-Vorlagendateien befinden sich unter `templates/azure` , dieser Ordner enthält die folgenden Dateien:

| Datei | Was bewirkt dies? | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Bereitstellen eines Einstiegspunkts für die Azure-Ressourcenbereitstellung | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen | Ja |
| config.bicep | Hinzufügen der erforderlichen TeamsFx-Konfigurationen zu Azure-Ressourcen | Ja |
| provision/xxx.bicep | Erstellen und Konfigurieren jeder azure-Ressource, die von `provision.bicep` | Ja |
| teamsfx/xxx.bicep | Hinzufügen der erforderlichen TeamsFx-Konfigurationen zu jeder Azure-Ressource, die von `config.bicep`| Nein |

> [!NOTE]
> wenn Sie Ressourcen oder Funktionen zu Ihrem Projekt hinzufügen, `teamsfx/xxx.bicep` wird neu generiert. Aus diesem Grund wird es als nicht anpassbar gekennzeichnet. Wenn Sie diese Biicep-Dateien wirklich ändern müssen, empfehlen wir die Verwendung von Git, um Ihre Änderungen an Dateien nachzuverfolgen, `teamsfx/xxx.bicep` damit Sie Ihre Änderungen beim Hinzufügen von Ressourcen oder Funktionen nicht verlieren.

### <a name="customize-arm-parameters-and-templates"></a>Anpassen von ARM-Parametern und -Vorlagen

Sie können Azure-Ressourcen anpassen, indem Sie die Parameterdateien und die Biicep-Dateien anpassen.

#### <a name="customize-arm-template-parameter-files"></a>Anpassen von ARM-Vorlagenparameterdateien

Das Toolkit bietet eine Reihe vordefinierter Parameter, mit denen Sie die Azure-Ressourcen anpassen können. Die Parameterdateien befinden sich `.fx/configs/azure.parameters.{env}.json` an, und alle verfügbaren Parameter werden in der `provisionParameters` Eigenschaft definiert. Es wird bevorzugt, die Parameterdateien anzupassen, wenn die vordefinierten Parameter Ihre Anforderung erfüllen.

Hier ist eine Liste der verfügbaren vordefinierten Parameter:

| Parametername | Standardwert | Was kann durch den Parameter angepasst werden? | Werteinschränkungen |
| --- | --- | --- | --- |
| resourceBaseName | Automatisch generiert für jede Umgebung | Standardname für alle Ressourcen | 2 bis 20 Kleinbuchstaben und Zahlen |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Name des Dienstplans für einfache Authentifizierungs-Apps | 1-40 Alphanumerics und Bindestriche |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Name der einfachen Auth Web App | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| simpleAuthSku | F1 | SKU des Einfachen Authentifizierungs-App-Serviceplans |  |
| frontendHostingStorageName | Registerkarte "${resourceBaseName}" | Name des Front-End-Hosting-Storage-Kontos | 3-24 Kleinbuchstaben und Zahlen |
| frontendHostingStorageSku | Standard_LRS | SKU des Front-End-Hosting-Storage-Kontos | Verfügbare SKUs finden Sie auf dieser [Seite.](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch) |
| functionServerfarmsName | ${resourceBaseName}-API | Name des App-Serviceplans der Funktions-App | 1-40 Alphanumerics und Bindestriche |
| functionServerfarmsSku | Y1 | SKU des App-Serviceplans der FUnction-App |
| functionAppName | ${resourceBaseName}-API | Name der Funktions-App | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| functionStorageName | ${resourceBaseName}-API | Name des Storage-Kontos der Funktions-App | 3-24 Kleinbuchstaben und Zahlen |
| functionStorageSku | Standard_LRS | SKU des Storage-Kontos der Funktions-App | Verfügbare SKUs finden Sie auf dieser [Seite.](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep&branch=pr-en-us-4713) |
| botServiceName | ${resourceBaseName} | Name des Azure Bot-Diensts | 2-64 Alphanumerics, Unterstriche, Punkte und Bindestriche <br /> Beginnen Sie mit alphanumerisch |
| botServiceSku | F0 | SKU des Azure Bot-Diensts | Verfügbare SKUs finden Sie auf dieser [Seite.](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep&branch) |
| botDisplayName | ${resourceBaseName} | Anzeigename Ihres Bots | 1 bis 42 Zeichen |
| botServerfarmsName | ${resourceBaseName}-Bot | Name des Bot-App-Serviceplans | 1-40 Alphanumerics und Bindestriche |
| botWebAppName | ${resourceBaseName}-Bot | Name der Bot-Web-App | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| botWebAppSKU | F1 | SKU des Bot-App-Serviceplans |  |
| userAssignedIdentityName | ${resourceBaseName} | Name der vom Benutzer zugewiesenen Identität | 3-128 Alphanumerics, Bindestriche und Unterstriche <br /> Mit Buchstabe oder Zahl beginnen |
| sqlServerName | ${resourceBaseName} | Name von Azure SQL Server | 1 bis 63 Kleinbuchstaben, Zahlen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| sqlDatabaseName | ${resourceBaseName} | Name der Azure SQL-Datenbank | 1 bis 128 Zeichen, kann <>*%& nicht verwendet werden: \/ ? oder Steuerelementzeichen <br /> Kann nicht mit Punkt oder Leerzeichen enden |
| sqlDatabaseSku | Standard | SKU von Azure SQL-Datenbank |  |
| apimServiceName | ${resourceBaseName} | Name des APIM-Diensts | 1-50 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |
| apimServiceSku | Verbrauch | SKU des APIM-Diensts | Verfügbare SKUs finden Sie auf dieser [Seite.](/azure/templates/microsoft.apimanagement/service?tabs=bicep&branch) |
| apimProductName | ${resourceBaseName} | Name des APIM-Produkts | 1-80 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |
| apimOauthServerName | ${resourceBaseName} | Name des APIM-OAuth-Servers | 1-80 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |

In der Zwischenzeit sind die folgenden Parameter mit Werten verfügbar, die während der Bereitstellung aufgefüllt werden. Der Zweck dieser Platzhalter besteht darin, sicherzustellen, dass wir neue Ressourcen für Sie erstellen können, wenn Sie eine neue Umgebung erstellen. Die tatsächlichen Werte werden von `.fx/states/state.{env}.json` aufgelöst.

##### <a name="aad-application-related-parameters"></a>AAD anwendungsbezogener Parameter

| Parametername | Platzhalter für Standardwerte | Bedeutung des Platzhalters | Anpassen |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die AAD App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Der AAD clientschlüssel Ihrer App, der während der Bereitstellung erstellt wurde | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-teams-app) |
| Microsoft 365TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der AAD App Ihrer App | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-teams-app) |
| Microsoft 365 OauthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der AAD App Ihrer App | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Bots AAD App-Client-ID, die während der Bereitstellung erstellt wurde | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Bots AAD Geheimen App-Clientschlüssel, der während der Bereitstellung erstellt wurde | Informationen zum Anpassen des Werts finden Sie [in diesem Abschnitt.](#use-an-existing-aad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | APIM-AAD App-Client-ID, die während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | APIM-AAD App-Clientschlüssel, der während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

##### <a name="azure-resource-related-parameters"></a>Ressourcenbezogene Azure-Parameter

| Parametername | Platzhalter für Standardwerte | Bedeutung des Platzhalters | Anpassen |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Server Administratorkonto, das Sie während der Bereitstellung bereitgestellt haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Azure SQL Server Administratorkennwort, das Sie während der Bereitstellung angegeben haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | DIE HERAUSGEBER-E-Mail von APIM. Der Standardwert ist Ihr Azure-Konto. | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Der Herausgebername von APIM. Der Standardwert ist Ihr Azure-Konto. | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Verweisen auf Umgebungsvariablen in Parameterdateien

Manchmal möchten Sie die Werte in Parameterdateien möglicherweise nicht hartcodieren. Beispiel: Wenn der Wert ein geheimer Schlüssel ist. Die Parameterdateien unterstützen das Verweisen auf die Werte aus Umgebungsvariablen. Sie können die Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in Parameterwerten verwenden, um den Tools mitzuteilen, dass der Wert aus der aktuellen Umgebungsvariable aufgelöst werden muss.

Im folgenden Beispiel wird der Wert des Parameters aus der `mySelfHostedDbConnectionString` Umgebungsvariablen `DB_CONNECTION_STRING` gelesen:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Anpassen von ARM-Vorlagendateien

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderung nicht erfüllen, können Sie die ARM-Vorlagen im `templates/azure` Ordner anpassen. Beispielsweise können Sie die ARM-Vorlage anpassen, um einige zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Dies ist ein Vorausszenario und erfordert Grundlegendes über Biicep-Sprache, die zum Erstellen der ARM-Vorlage verwendet wird. Sie können mit Bicep in [der Bicep-Dokumentation](/azure/azure-resource-manager/bicep/?branch)beginnen.
> [!NOTE]
> Die ARM-Vorlage wird von allen Umgebungen gemeinsam verwendet. Sie können die [bedingte Bereitstellung](/azure/azure-resource-manager/bicep/conditional-resource-deployment?branch) verwenden, wenn das Bereitstellungsverhalten zwischen Umgebungen unterschiedlich ist.

Um sicherzustellen, dass die TeamsFx-Tools ordnungsgemäß funktionieren, stellen Sie sicher, dass Ihre angepasste ARM-Vorlage die folgende Anforderung erfüllt. Wenn Sie andere Tools für die weitere Entwicklung verwenden, können Sie diese Anforderungen ignorieren.

* Lassen Sie die Ordnerstruktur und den Dateinamen unverändert. Das Tool fügt möglicherweise neue Inhalte an vorhandene Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen/Funktionen hinzufügen.
* Lassen Sie den Namen der automatisch generierten Parameter sowie die Eigenschaftsnamen unverändert. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen/Funktionen hinzufügen.
* Lassen Sie die Ausgabe der automatisch generierten ARM-Vorlage unverändert. Sie können der ARM-Vorlage zusätzliche Ausgaben hinzufügen. Die Ausgabe wird beibehalten `.fx/states/state.{env}.json` und in anderen Features wie bereitstellen, Manifestdatei überprüfen usw. verwendet.

### <a name="customization-scenarios"></a>Anpassungsszenarien

Dies sind einige häufige Szenarien, in denen Sie das Bereitstellungsverhalten anpassen können.

#### <a name="use-an-existing-aad-app-for-your-teams-app"></a>Verwenden einer vorhandenen AAD-App für Ihre Teams-App

Sie können den folgenden Konfigurationsausschnitt zur `.fx/configs/config.{env}.json` Datei hinzufügen, um eine AAD-App zu verwenden, die Sie selbst für Ihre Teams-App erstellt haben. Informationen zum Erstellen einer AAD-App finden Sie unter <https://aka.ms/teamsfx-existing-aad-doc> .

```json
"auth": {
    "clientId": "<your AAD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your AAD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Nachdem Sie den obigen Codeausschnitt hinzugefügt haben, fügen Sie Ihren geheimen Schlüssel der zugehörigen Umgebungsvariablen hinzu, damit die Tools den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen können.

> [!NOTE]
> Sie sollten keine AAD App in mehreren Umgebungen freigeben. Wenn Sie nicht über die Berechtigung zum Aktualisieren der AAD-App verfügen, erhalten Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der AAD-App. Befolgen Sie die Anweisungen, um Ihre AAD-App nach der Bereitstellung zu aktualisieren.

#### <a name="use-an-existing-aad-app-for-your-bot"></a>Verwenden einer vorhandenen AAD-App für Ihren Bot

Sie können den folgenden Konfigurationsausschnitt zur `.fx/configs/config.{env}.json` Datei hinzufügen, um eine AAD App zu verwenden, die Sie selbst für Ihren Bot erstellt haben.

```json
"bot": {
    "appId": "<your AAD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Nachdem Sie den obigen Codeausschnitt hinzugefügt haben, fügen Sie Ihren geheimen Schlüssel der zugehörigen Umgebungsvariablen hinzu, damit die Tools den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen können.

> [!NOTE]
> Sie sollten keine AAD App in mehreren Umgebungen freigeben.

#### <a name="skip-adding-user-for-sql-database"></a>Überspringen des Hinzufügens von Benutzern für SQL Datenbank

Manchmal erhalten Sie möglicherweise einen Fehler aufgrund unzureichender Berechtigungen, wenn das Tool versucht, SQL Datenbank Einen Benutzer hinzuzufügen. Sie können der Datei den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um das Hinzufügen SQL Datenbankbenutzers zu überspringen.

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Angeben des Namens der Function App-Instanz

In diesem Beispiel werde ich einen anderen Namen für die Function App-Instanz angeben, `contosoteamsappapi` anstatt den Standardnamen zu verwenden.

> [!NOTE]
> Wenn Sie die Umgebung bereits bereitgestellt haben, wird durch Angeben des Namens eine neue Funktions-App-Instanz für Sie erstellt, anstatt die zuvor erstellte Instanz umzubenennen.

Die folgenden Schritte sind:

1. Für `.fx/configs/azure.parameters.{env}.json` Ihre aktuelle Umgebung geöffnet.
2. Fügen Sie dem Wert des Parameters eine neue Eigenschaft `functionAppName` `provisionParameters` hinzu.
3. Füllen Sie "contosoteamsappapi" als Wert von `functionAppName`
4. Die endgültige Parameterdatei wird wie folgt dargestellt:

    ```json
    {
        "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameters.json#",
        "contentVersion": "1.0.0.0",
        "parameters": {
            "provisionParameters": {
            "value": {
                "functionAppName": "contosoteamsappapi"
                ...
                }
            }
        }
    }
    ```

### <a name="scenerio"></a>Scenerio 

**So fügen Sie der Anwendung eine andere Azure-Ressource (Azure-Speicher) hinzu**

Betrachten Sie das Szenario, sie möchten Ihrem Azure Function-Back-End Azure Storage hinzufügen, um einige Blobdaten zu speichern. Es gibt keinen automatischen Fluss zum Aktualisieren der Biicep-Vorlage mit Azure Storage Unterstützung. Sie können jedoch die Biicep-Datei bearbeiten und die Ressource hinzufügen. Die Schritte sind wie folgt:

1. Erstellen eines Registerkartenprojekts
2. Fügen Sie dem Projekt eine Funktion hinzu. Weitere Informationen zum Hinzufügen von Ressourcen finden Sie unter ["Ressourcen hinzufügen".](./add-resource.md)
3. Deklarieren Sie das neue Storage Konto in der ARM-Vorlage. Zur Vereinfachung deklarieren wir die Ressource `templates/azure/provision/function.bicep` direkt. Sie können die Ressourcen an anderen Stellen deklarieren.

    `````````bicep
    var applicationStorageAccountName = 'myapp${uniqueString(resourceGroup().id)}'
    resource applicationStorageAccount 'Microsoft.Storage/storageAccounts@2021-06-01' = {
        name: applicationStorageAccountName
        location: resourceGroup().location
        kind: 'Storage'
        sku: {
            name: 'Standard_LRS'
        }
    }
    `````````

4. Aktualisieren Sie die Azure Function App-Einstellungen mit Azure Storage Verbindungszeichenfolge in `templates/azure/provision/function.bicep` , bei der es sich um dieselbe Datei in Schritt 3 handelt. Fügen Sie dem Ressourcenarray den folgenden Codeausschnitt `functionApp` `appSettings` hinzu.

    ``````````````````bicep
    {
        name: 'MyAppStorageAccountConnectionString'
        value: 'DefaultEndpointsProtocol=https;AccountName=${applicationStorageAccount.name};AccountKey=${listKeys(applicationStorageAccount.id, '2021-06-01').keys[0].value}'
    }
    ```````````````````

5. Jetzt können Sie Ihre Funktion mit Azure Storage Ausgabebindungen aktualisieren.

## <a name="faq"></a>Häufig gestellte Fragen

<br>

<details>

<summary><b>Problembehandlung</b></summary>

Wenn Teams Toolkit in Visual Studio Code Fehler aufgetreten sind, können Sie auf die `Get Help` Schaltfläche in der Fehlerbenachrichtigung klicken, um zum zugehörigen Hilfedokument zu navigieren. Wenn Sie TeamsFx CLI verwenden, wird am Ende der Fehlermeldung ein Hyperlink angezeigt, der auf das Hilfedokument verweist. Sie können das [Bereitstellungshilfedokument](https://aka.ms/teamsfx-arm-help) auch direkt anzeigen.

<br>

</details>

<details>

<summary><b>Wie kann ich während der Bereitstellung zu einem anderen Azure-Abonnement wechseln?</b></summary>

1. Wechseln Sie im aktuellen Konto zum Abonnement, oder melden Sie sich ab, und wählen Sie ein neues Abonnement aus.
2. Wenn Sie bereits eine aktuelle Umgebung bereitgestellt haben, müssen Sie eine neue Umgebung erstellen und die Bereitstellung durchführen, da ARM das Verschieben von Ressourcen nicht unterstützt.
3. Wenn Sie die aktuelle Umgebung nicht bereitgestellt haben, können Sie die Bereitstellung direkt auslösen.

<br>

</details>

<details>

<summary><b>Wie kann ich die Ressourcengruppe während der Bereitstellung ändern?</b></summary>

Vor der Bereitstellung werden Sie vom Tool gefragt, ob Sie eine neue Ressourcengruppe erstellen oder eine vorhandene verwenden möchten. In diesem Schritt können Sie einen neuen Ressourcengruppennamen angeben oder einen vorhandenen auswählen.

<br>

</details>

<details>

<summary><b>Wie kann ich SharePoint-basierte App bereitstellen?</b></summary>

Sie können der [Bereitstellung SharePoint-basierten App](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4&branch) folgen, um SharePoint-basierte App bereitzustellen.

> [!NOTE]
> Derzeit verfügt das Erstellen Teams App mit SharePoint-Framework mit Teams Toolkit nicht über eine direkte Integration in Azure. Die Inhalte in diesem Dokument gelten nicht für SPFx-basierte Apps.


<br>

</details>

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Bereitstellen Teams App in der Cloud](deploy.md)

> [!div class="nextstepaction"]
> [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)

> [!div class="nextstepaction"]
> [Zusammenarbeit mit anderen Entwicklern an Teams Projekt](TeamsFx-collaboration.md)
