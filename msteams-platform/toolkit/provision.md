---
title: Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie Cloudressourcen mit Teams Toolkit bereitstellen, Ressourcen erstellen und die Ressourcenbereitstellung anpassen.
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 1c4232cfe51ae900414f474bcdd05c9a67d5c4c6
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144117"
---
# <a name="use-teams-toolkit-to-provision-cloud-resources"></a>Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen

TeamsFx lässt sich in Azure und Microsoft 365 Cloud integrieren, sodass Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen bereitstellen können, die Ihre Anwendung für den Code-Ansatz benötigt.  

## <a name="prerequisites"></a>Voraussetzungen

* Kontovoraussetzungen Zum Bereitstellen von Cloud-Ressourcen müssen Sie über die folgenden Konten verfügen:

  * Microsoft 365 Konto mit gültigem Abonnement.
  * Azure mit gültigem Abonnement.
  Weitere Informationen finden Sie unter [Vorbereiten von Konten für die Erstellung Teams App](accounts.md).

* [Installieren des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Sie das Teams-App-Projekt in VS-Code geöffnet haben.

## <a name="provision-using-teams-toolkit"></a>Bereitstellung mit Teams Toolkit

Die Bereitstellung erfolgt mit einem einzigen Befehl in Teams Toolkit für Visual Studio Code oder TeamsFx CLI wie folgt:

[Stellen Sie eine Azure-basierte App bereit](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8)

## <a name="resource-creation"></a>Ressourcenerstellung

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen erhalten:

* Microsoft Azure Active Directory (Azure AD)-Anwendung unter Ihrem Microsoft 365-Mandanten.
* Teams App-Registrierung unter der Teams Plattform Ihres Microsoft 365 Mandanten.
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement.

Wenn Sie ein neues Projekt erstellen, können Sie alle Azure-Ressourcen verwenden. Die ARM-Vorlage definiert alle Azure-Ressourcen und hilft beim Erstellen erforderlicher Azure-Ressourcen während der Bereitstellung. Wenn Sie einem vorhandenen Projekt [eine neue Funktionsressource hinzufügen](./add-resource.md), spiegelt die aktualisierte ARM-Vorlage die letzte Änderung wider.

> [!NOTE]
> Für Azure-Dienste fallen Kosten in Ihrem Abonnement an. Weitere Informationen zur Kostenschätzung finden Sie im [Preisrechner](https://azure.microsoft.com/pricing/calculator/).

### <a name="resource-creation-for-teams-tab-application"></a>Ressourcenerstellung für die Anwendung „Teams Tab“.

|Ressource|Zweck|Beschreibung |
|----------|--------------------------------|-----|
| Azure Storage | Hosten Ihrer Tab-App | Aktiviert die statische Web-App-Funktion zum Hosten Ihrer Tab-App |
| App Service-Plan für einfache Authentifizierung | Hosten Sie die Web-App von Simple Auth |Nicht zutreffend |
| Web-App für einfache Auth | Hosten Sie einen einfachen Authentifizierungsserver, um Zugriff auf andere Dienste in Ihrer Einzelseiten-App zu erhalten | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

### <a name="resource-creation-for-teams-bot-or-message-extension-application"></a>Ressourcenerstellung für Teams-Bot oder Nachrichtenerweiterungsanwendung

|Ressource|Zweck| Beschreibung |
|----------|--------------------------------|-----|
| Azure Bot-Dienst | Registriert Ihre App als Bot beim Bot-Framework | Verbindet den Bot mit Teams |
| App Service-Plan für Bot | Hosten Sie die Web-App von Bot |Nicht zutreffend |
| Web-App für Bot | Hosten Sie Ihre Bot-App | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

### <a name="resource-creation-for-azure-functions-in-the-project"></a>Ressourcenerstellung für Azure Functions im Projekt

|Ressource|Zweck| Beschreibung|
|----------|--------------------------------|-----|
| App Service-Plan für Function-App | Hosten Sie die Function-App |Nicht zutreffend |
| Function-App | Hosten Sie Ihre Azure-Function-APIs | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt eine CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anfragen von Ihrer Tab-App zuzulassen <br /> Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Azure-Speicher für die Function-App | Erforderlich zum Erstellen einer Function-App |Nicht zutreffend|
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

### <a name="resource-creation-for-azure-sql-in-the-project"></a>Ressourcenerstellung für Azure SQL im Projekt

|Ressource|Zweck | Beschreibung |
|----------|--------------------------------|-----|
| Azure SQL-Server | Hosten Sie die Azure SQL-Datenbankinstanz | Ermöglicht allen Azure-Diensten den Zugriff auf den Server |
| Azure SQL-Datenbank | Speichern Sie Daten für Ihre App | Gewährt dem Benutzer zugewiesene Identität, Lese- oder Schreibberechtigung für die Datenbank |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

### <a name="resource-creation-for-azure-api-management-in-the-project"></a>Ressourcenerstellung für Azure API Management im Projekt

|Ressource|Zweck|
|----------|--------------------------------|
| Azure AD-Anwendung für den API-Verwaltungsdienst | Ermöglicht Microsoft Power Platform den Zugriff auf APIs, die vom API-Verwaltungsdienst verwaltet werden |
| API-Verwaltungsdienst | Verwalten Sie Ihre in der Function-App gehosteten APIs |
| API-Verwaltungsprodukt | Gruppieren Sie Ihre APIs, definieren Sie Nutzungsbedingungen und Laufzeitrichtlinien |
| OAuth-Server für die API-Verwaltung | Ermöglicht Microsoft Power Platform den Zugriff auf Ihre in der Function-App gehosteten APIs |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen |

### <a name="resources-created-when-including-azure-key-vault-in-the-project"></a>Ressourcen, die beim Einschließen von Azure Key Vault in das Projekt erstellt wurden

|Ressourcen|Zweck dieser Ressource|
|----------|--------------------------------|
| Azure Key Vault-Dienst | Verwalten Sie Secrets (z. B. Azure AD-App-Clientschlüssel), die von anderen Azure-Diensten verwendet werden |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen |

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Teams Toolkit ermöglicht es Ihnen, einen Infrastructure-as-Code-Ansatz zu verwenden, um zu definieren, welche Azure-Ressourcen Sie bereitstellen und wie Sie sie konfigurieren möchten. Das Tool verwendet eine ARM-Vorlage, um Azure-Ressourcen zu definieren. Die ARM-Vorlage ist eine Reihe von Bicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie im [Bicep-Dokument](/azure/azure-resource-manager/bicep).

Die Bereitstellung mit ARM umfasst die Änderung der folgenden Sätze von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien (`azure.parameters.{your_env_name}.json`) im Ordner `.fx/configs` zum Übergeben von Parametern an Vorlagen.
* ARM-Vorlagendateien unter `templates/azure`, dieser Ordner enthält die folgenden Dateien:

| Datei | Funktion | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Bereitstellen eines Einstiegspunkts für die Azure-Ressourcenbereitstellung | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen | Ja |
| config.bicep | Hinzufügen erforderlicher TeamsFx-Konfigurationen zu Azure-Ressourcen | Ja |
| provision/xxx.bicep | Erstellen und Konfigurieren jeder von `provision.bicep` genutzten Azure-Ressource | Ja |
| teamsfx/xxx.bicep | Erforderliche TeamsFx-Konfigurationen zu jeder von `config.bicep` genutzten Azure-Ressource hinzufügen| Nein |

> [!NOTE]
> Wenn Sie Ihrem Projekt Ressourcen oder Fähigkeiten hinzufügen, wird `teamsfx/xxx.bicep` neu generiert, Sie können es nicht anpassen. Um die Biceps-Dateien zu ändern, können Sie Git verwenden, um Ihre Änderungen an `teamsfx/xxx.bicep`-Dateien nachzuverfolgen, was Ihnen hilft, keine Änderungen zu verlieren, während Sie Ressourcen oder Fähigkeiten hinzufügen.

### <a name="customize-arm-parameters-and-templates"></a>Passen Sie ARM-Parameter und -Vorlagen an

Sie können Azure-Ressourcen anpassen, indem Sie die Parameterdateien und die Biceps-Dateien anpassen.

#### <a name="customize-arm-template-parameter-files"></a>ARM-Vorlagenparameterdateien anpassen

Das Toolkit stellt eine Reihe vordefinierter Parameter bereit, mit denen Sie die Azure-Ressourcen anpassen können. Die Parameterdateien befinden sich unter `.fx/configs/azure.parameters.{env}.json` und alle verfügbaren Parameter sind in der Eigenschaft `provisionParameters` definiert. Es wird empfohlen, die Parameterdateien anzupassen, wenn die vordefinierten Parameter Ihren Anforderungen entsprechen.

Die folgende Tabelle enthält eine Liste der verfügbaren vordefinierten Parameter:

| Parametername | Standardwert | Was kann durch den Parameter angepasst werden | Wertbeschränkungen |
| --- | --- | --- | --- |
| resourceBaseName | Automatisch generiert für jede Umgebung | Standardname für alle Ressourcen | 2-20 Kleinbuchstaben und Zahlen |
| simpleAuthServerFarmsName | ${resourceBaseName}simpleAuth | Name des einfachen Authentifizierungs-App-Dienstplans | 1-40 alphanumerische Zeichen und Bindestriche |
| simpleAuthWebAppName | ${resourceBaseName}simpleAuth | Name der einfachen Authentifizierungs-Web-App | 2-60 alphanumerische Zeichen und Bindestriche <br /> Darf nicht mit Bindestrich beginnen oder enden |
| simpleAuthSku | F1 | SKU des einfachen Authentifizierungs-App-Dienstplans | Nicht zutreffend |
| frontendHostingStorageName | Registerkarte "${resourceBaseName}" | Name des Front-End-Hosting-Speicherkontos | 3-24 Kleinbuchstaben und Zahlen |
| frontendHostingStorageSku | StandardLRS | SKU des Front-End-Hosting-Speicherkontos |[Verfügbare Artikelnummern](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep)|
| functionServerfarmsName | ${resourceBaseName}api | Name des Dienstplans für Function-Apps | 1-40 alphanumerische Zeichen und Bindestriche |
| functionServerfarmsSku | Y1 | SKU des Serviceplans für Function-Apps | Nicht zutreffend|
| functionAppName | ${resourceBaseName}api | Name der Function-App | 2-60 alphanumerische Zeichen und Bindestriche <br /> Darf nicht mit Bindestrich beginnen oder enden |
| functionStorageName | ${resourceBaseName}api | Name des Speicherkontos der Function-App | 3-24 Kleinbuchstaben und Zahlen |
| functionStorageSku | StandardLRS | SKU des Speicherkontos der Function-App | [Verfügbare Artikelnummern](/azure/templates/microsoft.storage/storageaccounts?tabs=bicep) |
| botServiceName | ${resourceBaseName} | Name des Azure-Bot-Dienstes | 2-64 alphanumerische Zeichen, Unterstriche, Punkte und Bindestriche <br /> Mit alphanumerischem Zeichen beginnen |
| botServiceSku | F0 | SKU des Azure-Botdiensts | [Verfügbare Artikelnummern](/azure/templates/microsoft.botservice/2021-05-01-preview/botservices?tabs=bicep) |
| botDisplayName | ${resourceBaseName} | Anzeigename Ihres Bots | 1-42 Zeichen |
| botServerfarmsName | ${resourceBaseName}bot | Name des App-Dienstplans des Bots | 1-40 alphanumerische Zeichen und Bindestriche |
| botWebAppName | ${resourceBaseName}bot | Name der Web-App des Bots | 2-60 alphanumerische Zeichen und Bindestriche <br /> Darf nicht mit Bindestrich beginnen oder enden |
| botWebAppSKU | F1 | SKU des Bot App Service-Plans | Nicht zutreffend |
| userAssignedIdentityName | ${resourceBaseName} | Name der vom Benutzer zugewiesenen Identität | 3-128 alphanumerische Zeichen, Bindestriche und Unterstriche <br /> Beginnen Sie mit einem Buchstaben oder einer Zahl |
| sqlServerName | ${resourceBaseName} | Name des Azure SQL-Servers | 1-63 Kleinbuchstaben, Ziffern und Bindestriche <br /> Darf nicht mit Bindestrich beginnen oder enden |
| sqlDatabaseName | ${resourceBaseName} | Name der Azure SQL-Datenbank | 1-128 Zeichen, kann <>*%&:\/ nicht verwenden? oder Steuerzeichen <br /> Kann nicht mit Punkt oder Leerzeichen enden |
| sqlDatabaseSku | Standard | SKU der Azure SQL-Datenbank | Nicht zutreffend  |
| apimServiceName | ${resourceBaseName} | Name des APIM-Dienstes | 1-50 alphanumerische Zeichen und Bindestriche <br /> Mit Buchstaben beginnen und mit alphanumerischem Zeichen enden |
| apimServiceSku | Verbrauch | SKU des APIM-Dienstes | [Verfügbare Artikelnummern](/azure/templates/microsoft.apimanagement/service?tabs=bicep) |
| apimProductName | ${resourceBaseName} | Name des APIM-Produkts | 1-80 alphanumerische Zeichen und Bindestriche <br /> Mit Buchstaben beginnen und mit alphanumerischem Zeichen enden |
| apimOauthServerName | ${resourceBaseName} | Name des APIM-OAuth-Servers | 1-80 alphanumerische Zeichen und Bindestriche <br /> Mit Buchstaben beginnen und mit alphanumerischem Zeichen enden |
| keyVaultSkuName | standard | SKU-Name des Azure Key Vault-Diensts| |

In der Zwischenzeit sind die folgenden Parameter verfügbar, deren Werte während der Bereitstellung ausgefüllt werden. Der Zweck dieser Platzhalter besteht darin, sicherzustellen, dass wir in einer neuen Umgebung neue Ressourcen für Sie erstellen können. Die tatsächlichen Werte werden aus `.fx/states/state.{env}.json` aufgelöst.

##### <a name="azure-ad-application-related-parameters"></a>Anwendungsbezogene Azure AD-Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Azure AD-App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Das während der Bereitstellung erstellte Azure AD-App-Clientgeheimnis Ihrer App | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD-App Ihrer App | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der Azure AD-App Ihrer App | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Während der Bereitstellung erstellte Azure AD-App-Client-ID des Bots | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Während der Bereitstellung erstellter Clientschlüssel der Azure AD-App des Bots | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| apimClientId | {{state.fx-resource-apim.apimClientAADClientId}} | Die Client-ID der Azure AD-App von APIM, die während der Bereitstellung erstellt wurde | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |
| apimClientSecret | {{state.fx-resource-apim.apimClientAADClientSecret}} | Während der Bereitstellung erstellter geheimer Clientschlüssel der Azure AD-App von APIM | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |

##### <a name="azure-resource-related-parameters"></a>Azure-Ressourcenbezogene Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Server-Administratorkonto, das Sie während der Bereitstellung bereitgestellt haben | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Administratorkennwort für Azure SQL Server, das Sie während der Bereitstellung angegeben haben | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |
| apimPublisherEmail | {{state.fx-resource-apim.publisherEmail}} | Herausgeber-E-Mail-Adresse von APIM, Standardwert ist Ihr Azure-Konto | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |
| apimPublisherName | {{state.fx-resource-apim.publisherName}} | Herausgebername von APIM, Standardwert ist Ihr Azure-Konto | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |

#### <a name="referencing-environment-variables-in-parameter-files"></a>Referenzieren von Umgebungsvariablen in Parameterdateien

Wenn Sie die Werte in Parameterdateien nicht fest codieren möchten, z. B. wenn der Wert ein Geheimnis ist. Die Parameterdateien unterstützen das Referenzieren der Werte aus Umgebungsvariablen. Sie können die Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in Parameterwerten für das Tool verwenden, um die aktuelle Umgebungsvariable aufzulösen.

Das folgende Beispiel liest den Wert des Parameters `mySelfHostedDbConnectionString` aus der Umgebungsvariablen `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

#### <a name="customize-arm-template-files"></a>Passen Sie ARM-Vorlagendateien an

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderungen nicht erfüllen, können Sie die ARM-Vorlagen im Ordner `templates/azure` anpassen. Beispielsweise können Sie die ARM-Vorlage anpassen, um einige zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Sie müssen über Grundkenntnisse der Bicep-Sprache verfügen, die zum Erstellen von ARM-Vorlagen verwendet wird. Unter [Biceps-Dokumentation](/azure/azure-resource-manager/bicep/) können Sie mit dem Bicep beginnen.

> [!NOTE]
> Die ARM-Vorlage wird von allen Umgebungen gemeinsam genutzt. Sie können die [bedingte Bereitstellung](/azure/azure-resource-manager/bicep/conditional-resource-deployment) verwenden, wenn das Bereitstellungsverhalten zwischen Umgebungen unterschiedlich ist.

Um sicherzustellen, dass das TeamsFx-Tool ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie die ARM-Vorlage anpassen, die die folgende Anforderung erfüllt. Wenn Sie ein anderes Tool für die Weiterentwicklung verwenden, können Sie diese Anforderungen ignorieren.

* Lassen Sie die Ordnerstruktur und den Dateinamen unverändert. Das Tool fügt möglicherweise neue Inhalte an vorhandene Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Lassen Sie den Namen von automatisch generierten Parametern sowie seine Eigenschaftsnamen unverändert. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen oder Fähigkeiten hinzufügen.
* Lassen Sie die Ausgabe der automatisch generierten ARM-Vorlage unverändert. Sie können der ARM-Vorlage zusätzliche Ausgaben hinzufügen. Die Ausgabe ist `.fx/states/state.{env}.json` und kann in anderen Funktionen verwendet werden, z. B. Bereitstellen, Manifestdatei validieren.

### <a name="customization-scenarios"></a>Anpassungsszenarien

Sie können die folgenden Szenarien anpassen:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot

Sie können den folgenden Konfigurationsausschnitt zur Datei `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen selbst erstellte Azure AD-App für Ihre Teams-App zu verwenden. Informationen zum Erstellen einer Azure AD-App finden Sie unter <https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Nachdem Sie das Snippet hinzugefügt haben, fügen Sie Ihr Geheimnis der zugehörigen Umgebungsvariable hinzu, damit das Tool das eigentliche Geheimnis während der Bereitstellung auflösen kann.

> [!NOTE]
> Stellen Sie sicher, dass Sie dieselbe Azure AD-App nicht in mehreren Umgebungen freigeben. Wenn Sie keine Berechtigung zum Aktualisieren der Azure AD-App haben, können Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der Azure AD-App erhalten. Befolgen Sie die Anweisungen zum Aktualisieren Ihrer Azure AD-App nach der Bereitstellung.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App

Sie können das folgende Konfigurations-Snippet zur Datei `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen selbst erstellte Azure AD-App für Ihren Bot zu verwenden:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Nachdem Sie den vorangehenden Codeausschnitt hinzugefügt haben, fügen Sie Ihr Geheimnis der zugehörigen Umgebungsvariable hinzu, damit das Tool das eigentliche Geheimnis während der Bereitstellung auflösen kann.

#### <a name="skip-adding-user-for-sql-database"></a>Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank

Wenn beim Versuch des Tools, einen Benutzer zur SQL-Datenbank hinzuzufügen, der Fehler „Unzureichende Berechtigung“ angezeigt wird, können Sie das folgende Konfigurations-Snippet zur Datei `.fx/configs/config.{env}.json` hinzufügen, um das Hinzufügen eines SQL-Datenbankbenutzers zu überspringen:

```json
"skipAddingSqlUser": true
```

### <a name="specifying-the-name-of-function-app-instance"></a>Angeben des Namens der Function-App-Instanz

Sie können anstelle des Standardnamens `contosoteamsappapi` für die Function-App-Instanz verwenden.

> [!NOTE]
> Wenn Sie die Umgebung bereits bereitgestellt haben, kann durch Angabe des Namens eine neue Function-App-Instanz für Sie erstellt werden, anstatt die zuvor erstellte Instanz umzubenennen.

Die folgenden Schritte sind:

1. Öffnen Sie `.fx/configs/azure.parameters.{env}.json` für Ihre aktuelle Umgebung.
2. Fügen Sie dem Wert des Parameters `provisionParameters` eine neue Eigenschaft `functionAppName` hinzu.
3. Geben Sie `contosoteamsappapi` als Wert von ein `functionAppName`.
4. Die endgültige Parameterdatei wird im folgenden Snippet angezeigt:

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

So fügen Sie der Anwendung andere Azure-Ressourcen oder -Speicher hinzu:

Betrachten Sie das Szenario, in dem Sie Ihrem Azure-Function-Back-End Azure-Speicher hinzufügen möchten, um Blobdaten zu speichern. Es gibt keinen automatischen Ablauf zum Aktualisieren der Biceps-Vorlage mit Azure-Speicherunterstützung. Sie können jedoch die Bicep-Datei bearbeiten und die Ressource hinzufügen. Führen Sie dazu folgende Schritte aus:

1. Erstellen Sie ein Registerkartenprojekt.
2. Funktion zum Projekt hinzufügen. Weitere Informationen finden Sie unter [Ressourcen hinzufügen](./add-resource.md).
3. Deklarieren Sie das neue Speicherkonto in der ARM-Vorlage. Sie können die Ressource direkt unter `templates/azure/provision/function.bicep` deklarieren. Es steht Ihnen frei, die Ressourcen an anderen Stellen zu deklarieren.

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

4. Aktualisieren Sie die Einstellungen der Azure-Function-App mit der Azure-Speicherverbindungszeichenfolge in `templates/azure/provision/function.bicep`. Fügen Sie das folgende Snippet zum Array `appSettings` der Ressource `functionApp` hinzu:

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

<summary><b>Wie kann ich Fehler beheben?</b></summary>

Wenn Sie Fehler mit Teams Toolkit in Visual Studio Code erhalten, können Sie in der Fehlerbenachrichtigung **Hilfe erhalten** auswählen, um zum zugehörigen Dokument zu navigieren. Wenn Sie TeamsFx CLI verwenden, befindet sich am Ende der Fehlermeldung ein Hyperlink, der auf das Hilfedokument verweist. Sie können auch direkt das [Hilfedokument zur Bereitstellung](https://aka.ms/teamsfx-arm-help) anzeigen.

<br>

</details>

<details>

<summary><b>Wie kann ich während der Bereitstellung zu einem anderen Azure-Abonnement wechseln?</b></summary>

1. Wechseln Sie das Abonnement im aktuellen Konto oder melden Sie sich ab und wählen Sie ein neues Abonnement aus.
2. Wenn Sie die aktuelle Umgebung bereits bereitgestellt haben, müssen Sie eine neue Umgebung erstellen und die Bereitstellung durchführen, da ARM das Verschieben von Ressourcen nicht unterstützt.
3. Wenn Sie die aktuelle Umgebung nicht bereitgestellt haben, können Sie die Bereitstellung direkt auslösen.

<br>

</details>

<details>

<summary><b>Wie kann ich die Ressourcengruppe während der Bereitstellung ändern?</b></summary>

Vor der Bereitstellung werden Sie gefragt, ob Sie eine neue Ressourcengruppe erstellen oder eine vorhandene verwenden möchten. Sie können in diesem Schritt einen neuen Ressourcengruppennamen angeben oder einen vorhandenen auswählen.

<br>

</details>

<details>

<summary><b>Wie kann ich eine Sharepoint-basierte Anwendung bereitstellen?</b></summary>

Sie können [SharePoint-basierte Anwendungen bereitstellen](/microsoftteams/platform/sbs-gs-spfx?tabs=vscode%2Cviscode&tutorial-step=4).

> [!NOTE]
> Derzeit verfügt die Erstellung von Teams-Apps mit Sharepoint-Framework mit Teams Toolkit nicht über eine direkte Integration mit Azure, die Inhalte im Dokument gelten nicht für SPFx-basierte Apps.

<br>

</details>

## <a name="see-also"></a>Siehe auch

* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
