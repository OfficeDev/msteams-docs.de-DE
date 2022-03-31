---
title: Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen
author: MuyangAmigo
description: Bereitstellen von Cloudressourcen
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0528654b2867552af802fb95e3a6e47ca3228414
ms.sourcegitcommit: 52af681132e496a57b18f468c5b73265a49a5f44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64590647"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen

TeamsFx lässt sich in Azure und Microsoft 365 Cloud integrieren, sodass Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen bereitstellen können, die Ihre Anwendung für den Codeansatz benötigt.  

## <a name="prerequisites"></a>Voraussetzungen

* Kontovoraussetzungen Zum Bereitstellen von Cloudressourcen benötigen Sie die folgenden Konten:

  * Microsoft 365 Konto mit gültigem Abonnement
  * Azure mit gültigem Abonnement Weitere Informationen finden Sie unter [Vorbereiten von Konten für das Erstellen Teams App](accounts.md).

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt im VS-Code geöffnet ist.

## <a name="provision-using-teams-toolkit"></a>Bereitstellung mit Teams Toolkit

Die Bereitstellung erfolgt mit einem einzigen Befehl im Teams Toolkit für Visual Studio Code oder TeamsFx CLI wie folgt:

[Bereitstellen einer Azure-basierten App](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8)

## <a name="resource-creation"></a>Erstellen von Ressourcen

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen abrufen:

* Microsoft Azure Active Directory anwendung (Azure AD) unter Ihrem Microsoft 365 Mandanten
* Teams App-Registrierung unter der Teams-Plattform Ihres Microsoft 365 Mandanten
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement

Wenn Sie ein neues Projekt erstellen, können Sie alle Azure-Ressourcen verwenden. Die ARM-Vorlage definiert alle Azure-Ressourcen und hilft beim Erstellen der erforderlichen Azure-Ressourcen während der Bereitstellung. Wenn Sie einem vorhandenen Projekt [eine neue Funktionsressource hinzufügen](./add-resource.md) , spiegelt die aktualisierte ARM-Vorlage die aktuelle Änderung wider.

> [!NOTE]
> Azure-Dienste verursachen Kosten in Ihrem Abonnement. Weitere Informationen zur Kostenberechnung finden Sie [im Preisrechner](https://azure.microsoft.com/pricing/calculator/).

### <a name="resource-creation-for-teams-tab-application"></a>Erstellen von Ressourcen für Teams Registerkartenanwendung

|Ressource|Zweck|Beschreibung |
|----------|--------------------------------|-----|
| Azure-Speicher | Hosten Der Registerkarten-App | Ermöglicht der statischen Web-App das Hosten Ihrer Registerkarten-App |
| App-Dienstplan für einfache Authentifizierung | Hosten der Web-App der einfachen Authentifizierung |Nicht zutreffend |
| Web-App für einfache Authentifizierung | Hosten eines einfachen Authentifizierungsservers für den Zugriff auf andere Dienste in Ihrer Einzelseitenanwendung | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-teams-bot-or-messaging-extension-application"></a>Ressourcenerstellung für Teams Bot- oder Messaging-Erweiterungsanwendung

|Ressource|Zweck| Beschreibung |
|----------|--------------------------------|-----|
| Azure-Bot-Dienst | Registriert Ihre App als Bot beim Bot-Framework | Verbindet den Bot mit Teams |
| App-Dienstplan für Bot | Hosten der Web-App des Bots |Nicht zutreffend |
| Web-App für Bot | Hosten Ihrer Bot-App | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt App-Einstellungen hinzu, die für [das TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-functions-in-the-project"></a>Erstellen von Ressourcen für Azure Functions im Projekt

|Ressource|Zweck| Beschreibung|
|----------|--------------------------------|-----|
| App-Dienstplan für Funktions-App | Hosten der Funktions-App |Nicht zutreffend |
| Funktions-App | Hosten Ihrer Azure-Funktions-APIs | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt eine CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen. <br /> Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt. <br /> Fügt App-Einstellungen hinzu, die für [das TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Azure-Speicher für Funktions-App | Erforderlich zum Erstellen einer Funktions-App |Nicht zutreffend|
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-sql-in-the-project"></a>Erstellen von Ressourcen für Azure SQL im Projekt

|Ressource|Zweck | Beschreibung |
|----------|--------------------------------|-----|
| Azure SQL Server | Hosten der Azure SQL Datenbankinstanz | Ermöglicht allen Azure-Diensten den Zugriff auf den Server |
| Azure SQL-Datenbank | Store Daten für Ihre App | Gewährt dem Benutzer zugewiesene Identität, Lese- oder Schreibberechtigung für die Datenbank |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen | Gemeinsam genutzt für verschiedene Funktionen und Ressourcen |

### <a name="resource-creation-for-azure-api-management-in-the-project"></a>Erstellen von Ressourcen für Azure API Management im Projekt

|Ressource|Zweck|
|----------|--------------------------------|
| Azure AD-Anwendung für den API-Verwaltungsdienst | Ermöglicht Microsoft Power Platform-Zugriffs-APIs, die vom API-Verwaltungsdienst verwaltet werden |
| API-Verwaltungsdienst | Verwalten Der in der Funktions-App gehosteten APIs |
| API-Verwaltungsprodukt | Gruppieren Sie Ihre APIs, definieren Sie Nutzungsbedingungen und Laufzeitrichtlinien |
| API-Verwaltungs-OAuth-Server | Ermöglicht Microsoft Power Platform den Zugriff auf Ihre in der Funktions-App gehosteten APIs. |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen |

### <a name="resources-created-when-including-azure-key-vault-in-the-project"></a>Ressourcen, die erstellt werden, wenn Azure Key Vault in das Projekt eingeschlossen werden

|Ressourcen|Zweck dieser Ressource|
|----------|--------------------------------|
| Azure Key Vault-Dienst | Verwalten von geheimen Schlüsseln (z. B. Azure AD geheimen App-Clientschlüssel), die von anderen Azure-Diensten verwendet werden |
| Benutzer zugewiesene Identität | Authentifizieren von Azure Service-zu-Service-Anforderungen |

## <a name="customize-resource-provision"></a>Anpassen der Ressourcenbereitstellung

mit Teams Toolkit können Sie eine Infrastruktur als Codeansatz verwenden, um zu definieren, welche Azure-Ressourcen Sie bereitstellen und wie Sie sie konfigurieren möchten. Das Tool verwendet die ARM-Vorlage, um Azure-Ressourcen zu definieren. Bei der ARM-Vorlage handelt es sich um eine Reihe von Biicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie im [Biicep-Dokument](/azure/azure-resource-manager/bicep).

Die Bereitstellung mit ARM umfasst das Ändern der folgenden Sätze von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien (`azure.parameters.{your_env_name}.json`) im `.fx/configs` Ordner zum Übergeben von Parametern an Vorlagen.
* ARM-Vorlagendateien befinden sich unter `templates/azure`, dieser Ordner enthält die folgenden Dateien:

| Datei | Funktion | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Bereitstellen eines Einstiegspunkts für die Azure-Ressourcenbereitstellung | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen | Ja |
| config.bicep | Hinzufügen der erforderlichen TeamsFx-Konfigurationen zu Azure-Ressourcen | Ja |
| provision/xxx.bicep | Erstellen und Konfigurieren jeder azure-Ressource, die von `provision.bicep` | Ja |
| teamsfx/xxx.bicep | Hinzufügen der erforderlichen TeamsFx-Konfigurationen zu jeder Azure-Ressource, die von `config.bicep`| Nein |

> [!NOTE]
> Wenn Sie Ressourcen oder Funktionen zu Ihrem Projekt hinzufügen, `teamsfx/xxx.bicep` werden sie erneut generiert, sie können dies nicht anpassen. Um die Biicep-Dateien zu ändern, können Sie Git verwenden, um Ihre Änderungen an Dateien nachzuverfolgen `teamsfx/xxx.bicep` . Dadurch können Sie beim Hinzufügen von Ressourcen oder Funktionen keine Änderungen verlieren.

### <a name="customize-arm-parameters-and-templates"></a>Anpassen von ARM-Parametern und -Vorlagen

Sie können Azure-Ressourcen anpassen, indem Sie die Parameterdateien und die Biicep-Dateien anpassen.

#### <a name="customize-arm-template-parameter-files"></a>Anpassen von ARM-Vorlagenparameterdateien

Das Toolkit bietet eine Reihe vordefinierter Parameter, mit denen Sie die Azure-Ressourcen anpassen können. Die Parameterdateien befinden sich an `.fx/configs/azure.parameters.{env}.json` , und alle verfügbaren Parameter werden in der `provisionParameters` Eigenschaft definiert. Es wird empfohlen, die Parameterdateien anzupassen, wenn die vordefinierten Parameter Ihren Anforderungen entsprechen.

Die folgende Tabelle enthält eine Liste der verfügbaren vordefinierten Parameter:

| Parametername | Standardwert | Was kann durch den Parameter angepasst werden? | Werteinschränkungen |
| --- | --- | --- | --- |
| resourceBaseName | Automatisch generiert für jede Umgebung | Standardname für alle Ressourcen | 2 bis 20 Kleinbuchstaben und Zahlen |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Name des Dienstplans für eine einfache Authentifizierungs-App | 1-40 Alphanumerics und Bindestriche |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Name einer einfachen Authentifizierungs-Web-App | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| simpleAuthSku | F1 | SKU eines einfachen Authentifizierungs-App-Dienstplans | Nicht zutreffend |
| frontendHostingStorageName | Registerkarte "${resourceBaseName}" | Name des Front-End-Hostingspeicherkontos | 3-24 Kleinbuchstaben und Zahlen |
| frontendHostingStorageSku | Standard_LRS | SKU des Front-End-Hostingspeicherkontos |[Verfügbare SKUs](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep)|
| functionServerfarmsName | ${resourceBaseName}-API | Name des Dienstplans für Funktions-Apps | 1-40 Alphanumerics und Bindestriche |
| functionServerfarmsSku | Y1 | SKU des Dienstplans für Funktions-Apps | Nicht zutreffend|
| functionAppName | ${resourceBaseName}-API | Name der Funktions-App | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| functionStorageName | ${resourceBaseName}-API | Name des Speicherkontos der Funktions-App | 3-24 Kleinbuchstaben und Zahlen |
| functionStorageSku | Standard_LRS | SKU des Speicherkontos der Funktions-App | [Verfügbare SKUs](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep) |
| botServiceName | ${resourceBaseName} | Name des Azure-Bot-Diensts | 2-64 Alphanumerics, Unterstriche, Punkte und Bindestriche <br /> Beginnen Sie mit alphanumerisch |
| botServiceSku | F0 | SKU des Azure-Botdiensts | [Verfügbare SKUs](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep) |
| botDisplayName | ${resourceBaseName} | Anzeigename Ihres Bots | 1 bis 42 Zeichen |
| botServerfarmsName | ${resourceBaseName}-Bot | Name des App-Serviceplans des Bots | 1-40 Alphanumerics und Bindestriche |
| botWebAppName | ${resourceBaseName}-Bot | Name der Web-App des Bots | 2-60 Alphanumerics und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| botWebAppSKU | F1 | SKU des Bot-App Service-Plans | Nicht zutreffend |
| userAssignedIdentityName | ${resourceBaseName} | Name der vom Benutzer zugewiesenen Identität | 3-128 Alphanumerics, Bindestriche und Unterstriche <br /> Mit Buchstabe oder Zahl beginnen |
| sqlServerName | ${resourceBaseName} | Name Azure SQL Servers | 1 bis 63 Kleinbuchstaben, Zahlen und Bindestriche <br /> Kann nicht mit Bindestrich beginnen oder enden |
| sqlDatabaseName | ${resourceBaseName} | Name der Azure SQL Datenbank | 1 bis 128 Zeichen, kann <>*%&:\/? oder Steuerelementzeichen <br /> Kann nicht mit Punkt oder Leerzeichen enden |
| sqlDatabaseSku | Standard | SKU der Azure SQL-Datenbank | Nicht zutreffend  |
| apimServiceName | ${resourceBaseName} | Name des APIM-Diensts | 1-50 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |
| apimServiceSku | Verbrauch | SKU des APIM-Diensts | [Verfügbare SKUs](/azure/templates/microsoft.apimanagement/service?tabs=bicep) |
| apimProductName | ${resourceBaseName} | Name des APIM-Produkts | 1-80 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |
| apimOauthServerName | ${resourceBaseName} | Name des APIM-OAuth-Servers | 1-80 Alphanumerics und Bindestriche <br /> Mit Buchstaben beginnen und mit Alphanumerisch enden |
| keyVaultSkuName | Standard | SKU-Name des Azure Key Vault-Diensts| |

In der Zwischenzeit sind die folgenden Parameter mit Werten verfügbar, die während der Bereitstellung aufgefüllt werden. Der Zweck dieser Platzhalter besteht darin, sicherzustellen, dass wir neue Ressourcen für Sie in einer neuen Umgebung erstellen können. Die tatsächlichen Werte werden von `.fx/states/state.{env}.json`aufgelöst.

##### <a name="azure-ad-application-related-parameters"></a>Azure AD anwendungsbezogener Parameter

| Parametername | Platzhalter für Standardwerte | Bedeutung des Platzhalters | Anpassen |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Azure AD App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Der Azure AD clientschlüssel Ihrer App, der während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD App Ihrer App | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der Azure AD-App Ihrer App | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Bots Azure AD App-Client-ID, die während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Bots Azure AD geheimer App-Clientschlüssel, der während der Bereitstellung erstellt wurde | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | APIM-Azure AD App-Client-ID, die während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | DER AZURE AD clientschlüssel der APIM, der während der Bereitstellung erstellt wurde | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

##### <a name="azure-resource-related-parameters"></a>Ressourcenbezogene Azure-Parameter

| Parametername | Platzhalter für Standardwerte | Bedeutung des Platzhalters | Anpassen |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Serveradministratorkonto, das Sie während der Bereitstellung bereitgestellt haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Azure SQL Serveradministratorkennwort, das Sie während der Bereitstellung angegeben haben | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | DIE HERAUSGEBER-E-Mail von APIM. Der Standardwert ist Ihr Azure-Konto. | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Der Herausgebername von APIM. Der Standardwert ist Ihr Azure-Konto. | Löschen des Platzhalters und Ausfüllen des tatsächlichen Werts |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Verweisen auf Umgebungsvariablen in Parameterdateien

Wenn Sie die Werte in Parameterdateien nicht hartcodieren möchten, z. B. wenn der Wert ein geheimer Schlüssel ist. Die Parameterdateien unterstützen das Verweisen auf die Werte aus Umgebungsvariablen. Sie können die Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in Parameterwerten verwenden, damit das Tool aus der aktuellen Umgebungsvariable aufgelöst wird.

Im folgenden Beispiel wird der Wert des Parameters aus der `mySelfHostedDbConnectionString` Umgebungsvariablen gelesen `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Anpassen von ARM-Vorlagendateien

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderung nicht erfüllen, können Sie die ARM-Vorlagen im `templates/azure` Ordner anpassen. Beispielsweise können Sie die ARM-Vorlage anpassen, um einige zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Sie benötigen Grundkenntnisse der Biicep-Sprache, die zum Erstellen der ARM-Vorlage verwendet wird. Sie können mit Bicep in [der Bicep-Dokumentation](/azure/azure-resource-manager/bicep/) beginnen.

> [!NOTE]
> Die ARM-Vorlage wird von allen Umgebungen gemeinsam verwendet. Sie können die [bedingte Bereitstellung](/azure/azure-resource-manager/bicep/conditional-resource-deployment) verwenden, wenn das Bereitstellungsverhalten zwischen umgebungen unterschiedlich ist.

Um sicherzustellen, dass das TeamsFx-Tool ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie die ARM-Vorlage anpassen, die die folgende Anforderung erfüllt. Wenn Sie ein anderes Tool für die weitere Entwicklung verwenden, können Sie diese Anforderungen ignorieren.

* Lassen Sie die Ordnerstruktur und den Dateinamen unverändert. Das Tool fügt möglicherweise neue Inhalte an vorhandene Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Lassen Sie den Namen der automatisch generierten Parameter sowie die Eigenschaftsnamen unverändert. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Lassen Sie die Ausgabe der automatisch generierten ARM-Vorlage unverändert. Sie können der ARM-Vorlage zusätzliche Ausgaben hinzufügen. Die Ausgabe wird `.fx/states/state.{env}.json` und kann in anderen Features verwendet werden, z. B. bereitstellen, Manifestdatei überprüfen.

### <a name="customization-scenarios"></a>Anpassungsszenarien

Sie können die folgenden Szenarien anpassen:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden einer vorhandenen Azure AD-App für Ihren Bot

Sie können der Datei den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um eine Azure AD App zu verwenden, die Sie selbst für Ihre Teams-App erstellt haben. Informationen zum Erstellen einer Azure AD-App finden Sie unter <https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Nachdem Sie den Codeausschnitt hinzugefügt haben, fügen Sie Ihren geheimen Schlüssel der zugehörigen Umgebungsvariablen hinzu, damit das Tool den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen kann.

> [!NOTE]
> Stellen Sie sicher, dass Sie nicht dieselbe Azure AD App in mehreren Umgebungen freigeben. Wenn Sie nicht über die Berechtigung zum Aktualisieren der Azure AD-App verfügen, erhalten Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der Azure AD-App. Befolgen Sie die Anweisungen, um Ihre Azure AD-App nach der Bereitstellung zu aktualisieren.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden einer vorhandenen Azure AD-App für Ihre Teams-App

Sie können den folgenden Konfigurationsausschnitt zur `.fx/configs/config.{env}.json` Datei hinzufügen, um eine Azure AD-App zu verwenden, die Sie selbst für Ihren Bot erstellt haben:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Nachdem Sie den vorherigen Codeausschnitt hinzugefügt haben, fügen Sie Ihren geheimen Schlüssel der zugehörigen Umgebungsvariablen hinzu, damit das Tool den tatsächlichen geheimen Schlüssel während der Bereitstellung auflösen kann.

#### <a name="skip-adding-user-for-sql-database"></a>Überspringen des Hinzufügens eines Benutzers für SQL Datenbank

Wenn beim Versuch des Tools, benutzer zu SQL Datenbank hinzuzufügen, nicht genügend Berechtigungsfehler auftreten, können Sie der Datei den folgenden Konfigurationsausschnitt hinzufügen, um das Hinzufügen SQL Datenbankbenutzers zu `.fx/configs/config.{env}.json` überspringen:

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Angeben des Namens der Function App-Instanz

Sie können die App-Instanz der Funktion anstelle des Standardnamens verwenden `contosoteamsappapi` .

> [!NOTE]
> Wenn Sie die Umgebung bereits bereitgestellt haben, kann die Angabe des Namens eine neue Funktions-App-Instanz für Sie erstellen, anstatt die zuvor erstellte Instanz umzubenennen.

Die folgenden Schritte sind:

1. Für Ihre aktuelle Umgebung geöffnet `.fx/configs/azure.parameters.{env}.json` .
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

So fügen Sie der Anwendung weitere Azure-Ressourcen oder Speicher hinzu:

Betrachten Sie das Szenario, in dem Sie Ihrem Azure-Funktions-Back-End Azure-Speicher hinzufügen möchten, um Blobdaten zu speichern. Es gibt keinen automatischen Fluss, um die Biicep-Vorlage mit Azure-Speicherunterstützung zu aktualisieren. Sie können jedoch die Biicep-Datei bearbeiten und die Ressource hinzufügen. Führen Sie dazu folgende Schritte aus:

1. Erstellen Sie ein Registerkartenprojekt.
2. Fügen Sie dem Projekt eine Funktion hinzu. Weitere Informationen finden Sie unter ["Hinzufügen von Ressourcen"](./add-resource.md).
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

4. Aktualisieren Sie die Einstellungen der Azure-Funktions-App mit der Azure-Speicherverbindungszeichenfolge in `templates/azure/provision/function.bicep`. Fügen Sie dem Ressourcenarray `appSettings` den folgenden Codeausschnitt `functionApp` hinzu:

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

<summary><b>Problembehandlung</b></summary>

Wenn in Visual Studio Code Fehler mit Teams Toolkit auftreten, können Sie in der Fehlerbenachrichtigung **Hilfe** auswählen, um zum zugehörigen Dokument zu navigieren. Wenn Sie TeamsFx CLI verwenden, wird am Ende der Fehlermeldung ein Link angezeigt, der auf das Hilfedokument verweist. Sie können das [Bereitstellungshilfedokument](https://aka.ms/teamsfx-arm-help) auch direkt anzeigen.

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

<summary><b>Wie kann ich sharepointbasierte Apps bereitstellen?</b></summary>

Sie können die [Bereitstellung SharePoint-basierten App](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4) befolgen.

> [!NOTE]
> Derzeit verfügt das Erstellen Teams App mit SharePoint-Framework mit Teams Toolkit nicht über eine direkte Integration in Azure, der Inhalt des Dokuments gilt nicht für SPFx-basierte Apps.

<br>

</details>

## <a name="see-also"></a>Weitere Informationen

* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
