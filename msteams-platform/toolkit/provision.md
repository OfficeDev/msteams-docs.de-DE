---
title: Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen
author: MuyangAmigo
description: Bereitstellen von Cloudressourcen
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 24b058957ab0db7ebd2ab9178ac95fe9473257e6
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104119"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen

TeamsFx lässt sich in Azure und Microsoft 365 Cloud integrieren, wodurch Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen bereitstellen können, die Ihre Anwendung für den Codeansatz benötigt.  

## <a name="prerequisites"></a>Voraussetzungen

* Kontovoraussetzungen Um Cloudressourcen bereitzustellen, müssen Sie über die folgenden Konten verfügen:

  * Microsoft 365 Konto mit gültigem Abonnement
  * Azure mit gültigem Abonnement Weitere Informationen finden Sie unter [Vorbereiten von Konten für die Erstellung Teams App](accounts.md).

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in VS-Code geöffnet ist.

## <a name="provision-using-teams-toolkit"></a>Bereitstellen mit Teams Toolkit

Die Bereitstellung erfolgt mit einem einzigen Befehl in Teams Toolkit für Visual Studio Code oder TeamsFx CLI wie folgt:

[Bereitstellen einer Azure-basierten App](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8)

## <a name="resource-creation"></a>Ressourcenerstellung

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen abrufen:

* Microsoft Azure Active Directory (Azure AD)-Anwendung unter Ihrem Microsoft 365 Mandanten
* Teams App-Registrierung unter der Teams Plattform Ihres Microsoft 365 Mandanten
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement

Wenn Sie ein neues Projekt erstellen, können Sie alle Azure-Ressourcen verwenden. Die ARM-Vorlage definiert alle Azure-Ressourcen und hilft beim Erstellen erforderlicher Azure-Ressourcen während der Bereitstellung. Wenn Sie einem vorhandenen Projekt [eine neue Funktionsressource hinzufügen](./add-resource.md) , spiegelt die aktualisierte ARM-Vorlage die neueste Änderung wider.

> [!NOTE]
> Azure-Dienste verursachen Kosten in Ihrem Abonnement. Weitere Informationen zur Kostenschätzung finden Sie [im Preisrechner](https://azure.microsoft.com/pricing/calculator/).

### <a name="resource-creation-for-teams-tab-application"></a>Ressourcenerstellung für Teams Tab-Anwendung

|Ressource|Zweck|Beschreibung |
|----------|--------------------------------|-----|
| Azure Storage | Hosten ihrer Registerkarten-App | Ermöglicht statischen Web-App-Features das Hosten Ihrer Registerkarten-App. |
| App-Serviceplan für einfache Authentifizierung | Hosten der Web-App von Simple Auth |Nicht zutreffend |
| Web-App für einfache Authentifizierung | Hosten eines einfachen Authentifizierungsservers, um Zugriff auf andere Dienste in Ihrer Einzelseitenanwendung zu erhalten | Fügt dem Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen | Gemeinsam genutzt über verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-teams-bot-or-message-extension-application"></a>Ressourcenerstellung für Teams Bot- oder Nachrichtenerweiterungsanwendung

|Ressource|Zweck| Beschreibung |
|----------|--------------------------------|-----|
| Azure-Bot-Dienst | Registriert Ihre App als Bot beim Bot-Framework | Stellt eine Verbindung zwischen Bot und Teams her. |
| App-Serviceplan für Bot | Hosten der Web-App von Bot |Nicht zutreffend |
| Web-App für Bot | Hosten Ihrer Bot-App | Fügt dem Benutzer eine zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind. |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen | Gemeinsam genutzt über verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-functions-in-the-project"></a>Ressourcenerstellung für Azure Functions im Projekt

|Ressource|Zweck| Beschreibung|
|----------|--------------------------------|-----|
| App-Serviceplan für Funktions-App | Hosten der Funktions-App |Nicht zutreffend |
| Funktions-App | Hosten Ihrer Azure-Funktionen-APIs | Fügt dem Benutzer eine zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen. <br /> Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams App zulässt. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind. |
| Azure Storage für Funktions-App | Erforderlich zum Erstellen der Funktions-App |Nicht zutreffend|
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen | Gemeinsam genutzt über verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-sql-in-the-project"></a>Ressourcenerstellung für Azure SQL im Projekt

|Ressource|Zweck | Beschreibung |
|----------|--------------------------------|-----|
| Azure SQL Server | Hosten der Azure SQL Datenbankinstanz | Ermöglicht allen Azure-Diensten den Zugriff auf den Server |
| Azure SQL-Datenbank | Store von Daten für Ihre App | Erteilt dem Benutzer zugewiesene Identitäts-, Lese- oder Schreibberechtigungen für die Datenbank. |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen | Gemeinsam genutzt über verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-api-management-in-the-project"></a>Erstellen von Ressourcen für Azure API Management im Projekt

|Ressource|Zweck|
|----------|--------------------------------|
| Azure AD Anwendung für den API-Verwaltungsdienst | Ermöglicht den Zugriff auf Microsoft Power Platform-APIs, die vom API-Verwaltungsdienst verwaltet werden. |
| API-Verwaltungsdienst | Verwalten Der in der Funktions-App gehosteten APIs |
| API-Verwaltungsprodukt | Gruppieren Ihrer APIs, Definieren von Nutzungsbedingungen und Laufzeitrichtlinien |
| API-Verwaltungs-OAuth-Server | Ermöglicht Microsoft Power Platform den Zugriff auf Ihre in der Funktions-App gehosteten APIs |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen |

### <a name="resources-created-when-including-azure-key-vault-in-the-project"></a>Ressourcen, die beim Einschließen von Azure Key Vault in das Projekt erstellt wurden

|Ressourcen|Zweck dieser Ressource|
|----------|--------------------------------|
| Azure Key Vault Service | Verwalten von geheimen Schlüsseln (z. B. Azure AD geheimen App-Clientschlüssel), die von anderen Azure-Diensten verwendet werden |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-to-Service-Anforderungen |

## <a name="customize-resource-provision"></a>Anpassen der Ressourcenbereitstellung

Teams Toolkit ermöglicht es Ihnen, eine Infrastruktur als Codeansatz zu verwenden, um zu definieren, welche Azure-Ressourcen Sie bereitstellen und wie Sie konfigurieren möchten. Das Tool verwendet ARM-Vorlage, um Azure-Ressourcen zu definieren. Bei der ARM-Vorlage handelt es sich um eine Reihe von Bicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie [im Bicep-Dokument](/azure/azure-resource-manager/bicep).

Die Bereitstellung mit ARM umfasst das Ändern der folgenden Gruppen von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien (`azure.parameters.{your_env_name}.json`), die sich im `.fx/configs` Ordner befinden, zum Übergeben von Parametern an Vorlagen.
* ARM-Vorlagendateien, die sich in `templates/azure`diesem Ordner befinden, enthält die folgenden Dateien:

| Datei | Funktion | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Bereitstellen eines Einstiegspunkts für die Bereitstellung von Azure-Ressourcen | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen | Ja |
| config.bicep | Hinzufügen von erforderlichen TeamsFx-Konfigurationen zu Azure-Ressourcen | Ja |
| provision/xxx.bicep | Erstellen und Konfigurieren jeder Azure-Ressource, die von `provision.bicep` | Ja |
| teamsfx/xxx.bicep | Hinzufügen von erforderlichen TeamsFx-Konfigurationen zu jeder Azure-Ressource, die von `config.bicep`| Nein |

> [!NOTE]
> Wenn Sie Ihrem Projekt Ressourcen oder Funktionen hinzufügen, `teamsfx/xxx.bicep` wird es neu generiert, sie können das nicht anpassen. Um die Bicep-Dateien zu ändern, können Sie Git verwenden, um Ihre Änderungen an Dateien nachzuverfolgen `teamsfx/xxx.bicep` , was Ihnen hilft, Änderungen beim Hinzufügen von Ressourcen oder Funktionen nicht zu verlieren.

### <a name="customize-arm-parameters-and-templates"></a>Anpassen von ARM-Parametern und -Vorlagen

Sie können Azure-Ressourcen anpassen, indem Sie die Parameterdateien anpassen und die Bicep-Dateien anpassen.

#### <a name="customize-arm-template-parameter-files"></a>Anpassen von ARM-Vorlagenparameterdateien

Das Toolkit stellt eine Reihe vordefinierter Parameter zum Anpassen der Azure-Ressourcen bereit. Die Parameterdateien befinden sich unter `.fx/configs/azure.parameters.{env}.json` und alle verfügbaren Parameter werden in der `provisionParameters` Eigenschaft definiert. Es wird empfohlen, die Parameterdateien anzupassen, wenn die vordefinierten Parameter Ihre Anforderung erfüllen.

Die folgende Tabelle enthält eine Liste der verfügbaren vordefinierten Parameter:

| Parametername | Standardwert | Was kann durch den Parameter angepasst werden? | Wertbeschränkungen |
| --- | --- | --- | --- |
| resourceBaseName | Automatisch generiert für jede Umgebung | Standardname für alle Ressourcen | 2-20 Kleinbuchstaben und Zahlen |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Name des Serviceplans für einfache Authentifizierungs-Apps | 1-40 alphanumerische Zeichen und Bindestriche |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Name der einfachen Authentifizierungs-Web-App | 2-60 alphanumerische Zeichen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| simpleAuthSku | F1 | SKU des Serviceplans für einfache Authentifizierungs-Apps | Nicht zutreffend |
| frontendHostingStorageName | Registerkarte "${resourceBaseName}" | Name des Frontend-Hostingspeicherkontos | 3-24 Kleinbuchstaben und Zahlen |
| frontendHostingStorageSku | Standard_LRS | SKU des Frontend-Hosting-Speicherkontos |[Verfügbare SKUs](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep)|
| functionServerfarmsName | ${resourceBaseName}api | Name des Dienstplans für Funktions-Apps | 1-40 alphanumerische Zeichen und Bindestriche |
| functionServerfarmsSku | Y1 | SKU des Dienstplans für Funktions-Apps | Nicht zutreffend|
| functionAppName | ${resourceBaseName}api | Name der Funktions-App | 2-60 alphanumerische Zeichen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| functionStorageName | ${resourceBaseName}api | Name des Speicherkontos der Funktions-App | 3-24 Kleinbuchstaben und Zahlen |
| functionStorageSku | Standard_LRS | SKU des Speicherkontos der Funktions-App | [Verfügbare SKUs](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep) |
| botServiceName | ${resourceBaseName} | Name des Azure-Botdiensts | 2-64 alphanumerische Zeichen, Unterstriche, Punkte und Bindestriche <br /> Beginnen mit alphanumerischer |
| botServiceSku | F0 | SKU des Azure-Botdiensts | [Verfügbare SKUs](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep) |
| botDisplayName | ${resourceBaseName} | Anzeigename Ihres Bots | 1-42 Zeichen |
| botServerfarmsName | ${resourceBaseName}bot | Name des App-Serviceplans des Bots | 1-40 alphanumerische Zeichen und Bindestriche |
| botWebAppName | ${resourceBaseName}bot | Name der Web-App des Bots | 2-60 alphanumerische Zeichen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| botWebAppSKU | F1 | SKU von Bot App Service Plan | Nicht zutreffend |
| userAssignedIdentityName | ${resourceBaseName} | Name der vom Benutzer zugewiesenen Identität | 3-128 alphanumerische Zeichen, Bindestriche und Unterstriche <br /> Beginnen mit Buchstabe oder Zahl |
| sqlServerName | ${resourceBaseName} | Name des Azure SQL Servers | 1-63 Kleinbuchstaben, Zahlen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| sqlDatabaseName | ${resourceBaseName} | Name der Azure SQL Datenbank | 1-128 Zeichen, kann <>*%&:\/? oder Steuerzeichen <br /> Kann nicht mit Punkt oder Leerzeichen enden |
| sqlDatabaseSku | Standard | SKU der Azure SQL Datenbank | Nicht zutreffend  |
| apimServiceName | ${resourceBaseName} | Name des APIM-Diensts | 1-50 alphanumerische Zeichen und Bindestriche <br /> Beginnen Sie mit Buchstaben und enden Sie mit alphanumerischer |
| apimServiceSku | Verbrauch | SKU des APIM-Diensts | [Verfügbare SKUs](/azure/templates/microsoft.apimanagement/service?tabs=bicep) |
| apimProductName | ${resourceBaseName} | Name des APIM-Produkts | 1-80 alphanumerische Zeichen und Bindestriche <br /> Beginnen Sie mit Buchstaben und enden Sie mit alphanumerischer |
| apimOauthServerName | ${resourceBaseName} | Name des APIM-OAuth-Servers | 1-80 alphanumerische Zeichen und Bindestriche <br /> Beginnen Sie mit Buchstaben und enden Sie mit alphanumerischer |
| keyVaultSkuName | Standard | SKU-Name des Azure Key Vault Service| |

In der Zwischenzeit sind die folgenden Parameter mit Werten verfügbar, die während der Bereitstellung aufgefüllt wurden. Der Zweck dieser Platzhalter besteht darin, sicherzustellen, dass wir neue Ressourcen für Sie in einer neuen Umgebung erstellen können. Die tatsächlichen Werte werden von `.fx/states/state.{env}.json`aufgelöst.

##### <a name="azure-ad-application-related-parameters"></a>Azure AD anwendungsbezogener Parameter

| Parametername | Standardwertplatzhalter | Bedeutung des Platzhalters | So wird's geht's: Anpassen |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Azure AD App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Der Azure AD geheimen App-Clientschlüssel, der während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD App | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der app Azure AD App | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Bots Azure AD App-Client-ID, die während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Bots Azure AD App-Clientschlüssel, der während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | APIM-Azure AD App-Client-ID, die während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | APIM-Azure AD App-Clientschlüssel, der während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

##### <a name="azure-resource-related-parameters"></a>Ressourcenbezogene Azure-Parameter

| Parametername | Standardwertplatzhalter | Bedeutung des Platzhalters | So wird's geht's: Anpassen |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Serveradministratorkonto, das Sie während der Bereitstellung bereitgestellt haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Azure SQL Serveradministratorkennwort, das Sie während der Bereitstellung angegeben haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | E-Mail-Adresse des APIM-Herausgebers, Standardwert ist Ihr Azure-Konto | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Name des Herausgebers der APIM, Standardwert ist Ihr Azure-Konto | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Verweisen auf Umgebungsvariablen in Parameterdateien

Wenn Sie die Werte nicht in Parameterdateien hartcodieren möchten, z. B. wenn der Wert ein geheimer Schlüssel ist. Die Parameterdateien unterstützen das Verweisen auf die Werte aus Umgebungsvariablen. Sie können die Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in Parameterwerten für das Tool verwenden, um aus der aktuellen Umgebungsvariablen aufzulösen.

Im folgenden Beispiel wird der Wert des Parameters aus der `mySelfHostedDbConnectionString` Umgebungsvariablen `DB_CONNECTION_STRING`gelesen:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Anpassen von ARM-Vorlagendateien

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderung nicht erfüllen, können Sie die ARM-Vorlagen im `templates/azure` Ordner anpassen. Sie können z. B. die ARM-Vorlage anpassen, um einige zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Sie benötigen Grundkenntnisse in der Bicep-Sprache, die zum Erstellen von ARM-Vorlagen verwendet wird. Sie können mit bicep in der [bicep-Dokumentation](/azure/azure-resource-manager/bicep/) beginnen.

> [!NOTE]
> Die ARM-Vorlage wird von allen Umgebungen gemeinsam verwendet. Sie können [die bedingte Bereitstellung](/azure/azure-resource-manager/bicep/conditional-resource-deployment) verwenden, wenn das Bereitstellungsverhalten zwischen Umgebungen unterschiedlich ist.

Um sicherzustellen, dass das TeamsFx-Tool ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie die ARM-Vorlage anpassen, die die folgende Anforderung erfüllt. Wenn Sie andere Tools für die Weiterentwicklung verwenden, können Sie diese Anforderungen ignorieren.

* Behalten Sie die Ordnerstruktur und den Dateinamen unverändert bei. Das Tool fügt möglicherweise neue Inhalte an vorhandene Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Lassen Sie den Namen der automatisch generierten Parameter sowie die Eigenschaftennamen unverändert. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Lassen Sie die Ausgabe der automatisch generierten ARM-Vorlage unverändert. Sie können der ARM-Vorlage zusätzliche Ausgaben hinzufügen. Die Ausgabe wird `.fx/states/state.{env}.json` und kann in anderen Features verwendet werden, z. B. bereitstellen, Manifestdatei überprüfen.

### <a name="customization-scenarios"></a>Anpassungsszenarien

Sie können die folgenden Szenarien anpassen:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden einer vorhandenen Azure AD-App für Ihren Bot

Sie können der Datei den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen selbst erstellte Azure AD-App für Ihre Teams-App zu verwenden. Informationen zum Erstellen einer Azure AD-App finden Sie <https://aka.ms/teamsfx-existing-aad-doc>unter .

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Nachdem Sie den Codeausschnitt hinzugefügt haben, fügen Sie Ihr Geheimnis der zugehörigen Umgebungsvariable hinzu, damit das Tool den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen kann.

> [!NOTE]
> Stellen Sie sicher, dass Sie nicht dieselbe Azure AD-App in mehreren Umgebungen freigeben. Wenn Sie nicht über die Berechtigung zum Aktualisieren der Azure AD-App verfügen, erhalten Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der Azure AD-App. Befolgen Sie die Anweisungen, um Ihre Azure AD App nach der Bereitstellung zu aktualisieren.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden einer vorhandenen Azure AD-App für Ihre Teams-App

Sie können der Datei den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen selbst erstellte Azure AD-App für Ihren Bot zu verwenden:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Nachdem Sie den vorherigen Codeausschnitt hinzugefügt haben, fügen Sie Ihr Geheimnis der zugehörigen Umgebungsvariable hinzu, damit das Tool den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen kann.

#### <a name="skip-adding-user-for-sql-database"></a>Hinzufügen von Benutzern für SQL Datenbank überspringen

Wenn sie nicht genügend Berechtigungsfehler haben, wenn das Tool versucht, benutzer zu SQL Datenbank hinzuzufügen, können Sie der Datei den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um das Hinzufügen SQL Datenbankbenutzers zu überspringen:

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Angeben des Namens der Function App-Instanz

Sie können die App-Instanz der Funktion anstelle des Standardnamens verwenden `contosoteamsappapi` .

> [!NOTE]
> Wenn Sie die Umgebung bereits bereitgestellt haben, kann durch Angeben des Namens eine neue Funktions-App-Instanz für Sie erstellt werden, anstatt die zuvor erstellte Instanz umzubenennen.

Die folgenden Schritte sind:

1. Für Ihre aktuelle Umgebung öffnen `.fx/configs/azure.parameters.{env}.json` .
2. Fügen Sie dem Wert des Parameters `provisionParameters`eine neue Eigenschaft `functionAppName` hinzu.
3. Geben Sie `contosoteamsappapi` als Wert von `functionAppName`
4. Die endgültige Parameterdatei wird im folgenden Codeausschnitt angezeigt:

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

So fügen Sie der Anwendung weitere Azure-Ressourcen oder -Speicher hinzu:

Betrachten Sie das Szenario: Sie möchten Azure-Speicher zu Ihrem Azure-Funktions-Back-End hinzufügen, um Blobdaten zu speichern. Es gibt keinen automatischen Fluss zum Aktualisieren der Bicep-Vorlage mit Azure Storage-Unterstützung. Sie können jedoch die Bicep-Datei bearbeiten und die Ressource hinzufügen. Führen Sie dazu folgende Schritte aus:

1. Erstellen Sie ein Registerkartenprojekt.
2. Fügen Sie dem Projekt eine Funktion hinzu. Weitere Informationen finden Sie [unter Hinzufügen von Ressourcen](./add-resource.md).
3. Deklarieren Sie das neue Speicherkonto in der ARM-Vorlage. Sie können die Ressource `templates/azure/provision/function.bicep` direkt deklarieren. Sie können die Ressourcen an anderen Stellen deklarieren.

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

4. Aktualisieren Sie die Einstellungen der Azure-Funktions-App mit der Azure Storage-Verbindungszeichenfolge in `templates/azure/provision/function.bicep`. Fügen Sie dem Array der `appSettings` Ressource den folgenden Codeausschnitt `functionApp` hinzu:

    ``````````````````bicep
    {
        name: 'MyAppStorageAccountConnectionString'
        value: 'DefaultEndpointsProtocol=https;AccountName=${applicationStorageAccount.name};AccountKey=${listKeys(applicationStorageAccount.id, '2021-06-01').keys[0].value}'
    }
    ```````````````````

5. Sie können Ihre Funktion mit Azure Storage-Ausgabebindungen aktualisieren.

## <a name="faq"></a>Häufig gestellte Fragen

<br>

<details>

<summary><b>Problembehandlung?</b></summary>

Wenn Sie Fehler mit Teams Toolkit in Visual Studio Code erhalten, können Sie **Hilfe** in der Fehlerbenachrichtigung auswählen, um zum zugehörigen Dokument zu navigieren. Wenn Sie TeamsFx CLI verwenden, wird am Ende der Fehlermeldung ein Link angezeigt, der auf das Hilfedokument verweist. Sie können das [Bereitstellungshilfedokument](https://aka.ms/teamsfx-arm-help) auch direkt anzeigen.

<br>

</details>

<details>

<summary><b>Wie kann ich während der Bereitstellung zu einem anderen Azure-Abonnement wechseln?</b></summary>

1. Wechseln Sie das Abonnement im aktuellen Konto, oder melden Sie sich ab, und wählen Sie ein neues Abonnement aus.
2. Wenn Sie die aktuelle Umgebung bereits bereitgestellt haben, müssen Sie eine neue Umgebung erstellen und die Bereitstellung ausführen, da ARM das Verschieben von Ressourcen nicht unterstützt.
3. Wenn Sie die aktuelle Umgebung nicht bereitgestellt haben, können Sie die Bereitstellung direkt auslösen.

<br>

</details>

<details>

<summary><b>Wie kann ich die Ressourcengruppe während der Bereitstellung ändern?</b></summary>

Vor der Bereitstellung werden Sie vom Tool gefragt, ob Sie eine neue Ressourcengruppe erstellen oder eine vorhandene verwenden möchten. Sie können einen neuen Ressourcengruppennamen angeben oder einen vorhandenen Namen in diesem Schritt auswählen.

<br>

</details>

<details>

<summary><b>Wie kann ich eine SharePoint-basierte App bereitstellen?</b></summary>

Sie können [der Bereitstellung SharePoint-basierten App](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4) folgen.

> [!NOTE]
> Derzeit verfügt das Erstellen Teams App mit SharePoint-Framework mit Teams Toolkit nicht über eine direkte Integration in Azure, der Inhalt im Dokument gilt nicht für SPFx-basierte Apps.

<br>

</details>

## <a name="see-also"></a>Siehe auch

* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
