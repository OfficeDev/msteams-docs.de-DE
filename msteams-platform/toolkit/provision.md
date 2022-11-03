---
title: Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie Cloudressourcen mithilfe des Teams-Toolkits bereitstellen, Ressourcen erstellen und die Ressourcenbereitstellung anpassen.
ms.author: shenwe
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: 6c3e44de4d63911dff5481ab859019aea37559d1
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833198"
---
# <a name="provision-cloud-resources"></a>Bereitstellen von Cloudressourcen

TeamsFx lässt sich in Azure und Microsoft 365 Cloud integrieren, sodass Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen bereitstellen können, die Ihre Anwendung für den Code-Ansatz benötigt.

::: zone pivot="visual-studio-code"

## <a name="provision-using-teams-toolkit-in-visual-studio-code"></a>Bereitstellen mithilfe des Teams-Toolkits in Visual Studio Code

Die Bereitstellung erfolgt mit einem einzelnen Befehl in Teams Toolkit for Visual Studio Code oder TeamsFx CLI. Weitere Informationen finden Sie unter [Bereitstellen einer Azure-basierten App](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=8).

## <a name="create-resources"></a>Ressourcen erstellen

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen erhalten:

* Microsoft Azure Active Directory (Azure AD)-Anwendung unter Ihrem Microsoft 365-Mandanten.
* Teams-App-Registrierung unter der Teams-Plattform Ihres Microsoft 365-Mandanten.
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement.

Wenn Sie ein neues Projekt erstellen, können Sie alle Azure-Ressourcen verwenden. Die ARM-Vorlage definiert alle Azure-Ressourcen und hilft beim Erstellen erforderlicher Azure-Ressourcen während der Bereitstellung. Wenn Sie einem vorhandenen Projekt [eine neue Funktionsressource hinzufügen](./add-resource.md), spiegelt die aktualisierte ARM-Vorlage die letzte Änderung wider.

> [!NOTE]
> Für Azure-Dienste fallen Kosten in Ihrem Abonnement an. Weitere Informationen zur Kostenschätzung finden Sie im [Preisrechner](https://azure.microsoft.com/pricing/calculator/).

Die folgende Liste zeigt die Ressourcenerstellung für verschiedene Arten von App- und Azure-Ressourcen:
<br>

<details>
<summary><b>Ressourcenerstellung für die Anwendung „Teams Tab“.</b></summary>

|Ressource|Zweck|Beschreibung |
|----------|--------------------------------|-----|
| Azure Storage | Hosten Ihrer Tab-App | Aktiviert die statische Web-App-Funktion zum Hosten Ihrer Tab-App |
| App Service-Plan für einfache Authentifizierung | Hosten Sie die Web-App von Simple Auth |Nicht zutreffend |
| Web-App für einfache Auth | Hosten Sie einen einfachen Authentifizierungsserver, um Zugriff auf andere Dienste in Ihrer Einzelseiten-App zu erhalten | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für Teams-Bot oder Nachrichtenerweiterungsanwendung</b></summary>

|Ressource|Zweck| Beschreibung |
|----------|--------------------------------|-----|
| Azure Bot-Dienst | Registriert Ihre App als Bot beim Bot-Framework | Verbindet den Bot mit Teams |
| App Service-Plan für Bot | Hosten Sie die Web-App von Bot |Nicht zutreffend |
| Web-App für Bot | Hosten Sie Ihre Bot-App | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für Azure Functions im Projekt</b></summary>

|Ressource|Zweck| Beschreibung|
|----------|--------------------------------|-----|
| App Service-Plan für Function-App | Hosten Sie die Function-App |Nicht zutreffend |
| Function-App | Hosten Sie Ihre Azure-Function-APIs | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. <br /> Fügt eine CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anfragen von Ihrer Tab-App zuzulassen <br /> Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt. <br /> Fügt App-Einstellungen hinzu, die vom [TeamsFx SDK](https://www.npmjs.com/package/@microsoft/teamsfx) erforderlich sind |
| Azure-Speicher für die Function-App | Erforderlich zum Erstellen einer Function-App |Nicht zutreffend|
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für Azure SQL im Projekt</b></summary>

|Ressource|Zweck | Beschreibung |
|----------|--------------------------------|-----|
| Azure SQL-Server | Hosten Sie die Azure SQL-Datenbankinstanz | Ermöglicht allen Azure-Diensten den Zugriff auf den Server |
| Azure SQL-Datenbank | Speichern Sie Daten für Ihre App | Gewährt dem Benutzer zugewiesene Identität, Lese- oder Schreibberechtigung für die Datenbank |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen | Wird von verschiedenen Funktionen und Ressourcen gemeinsam genutzt |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für Azure API Management im Projekt</b></summary>

|Ressource|Zweck|
|----------|--------------------------------|
| Azure AD-Anwendung für den API-Verwaltungsdienst | Ermöglicht Microsoft Power Platform den Zugriff auf APIs, die vom API-Verwaltungsdienst verwaltet werden |
| API-Verwaltungsdienst | Verwalten Sie Ihre in der Function-App gehosteten APIs |
| API-Verwaltungsprodukt | Gruppieren Sie Ihre APIs, definieren Sie Nutzungsbedingungen und Laufzeitrichtlinien |
| OAuth-Server für die API-Verwaltung | Ermöglicht Microsoft Power Platform den Zugriff auf Ihre in der Function-App gehosteten APIs |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen |

</details>
<br>

<details>
<summary><b>Ressourcen, die beim Einschließen von Azure Key Vault in das Projekt erstellt wurden</b></summary>

|Ressourcen|Zweck dieser Ressource|
|----------|--------------------------------|
| Azure Key Vault-Dienst | Verwalten Sie Secrets (z. B. Azure AD-App-Clientschlüssel), die von anderen Azure-Diensten verwendet werden |
| Vom Benutzer zugewiesene Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen |

</details>
<br>

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Mit dem Teams-Toolkit können Sie einen Infrastructure-as-Code-Ansatz verwenden, um Azure-Ressourcen zu definieren, die Sie bereitstellen möchten, und wie Sie konfigurieren möchten. Das Tool verwendet eine ARM-Vorlage, um Azure-Ressourcen zu definieren. Die ARM-Vorlage ist eine Reihe von Bicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie im [Bicep-Dokument](/azure/azure-resource-manager/bicep).

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

### <a name="azure-ad-parameters"></a>Azure AD-Parameter

Die ARM-Vorlagendateien verwenden Platzhalter für Parameter. Der Zweck dieser Platzhalter besteht darin, die Erstellung neuer Ressourcen für Sie in einer neuen Umgebung sicherzustellen. Die tatsächlichen Werte werden aus `.fx/states/state.{env}.json` aufgelöst.

Es gibt zwei Arten von Parametern, z. B. anwendungsbezogene Azure AD-Parameter und Azure-ressourcenbezogene Parameter.

##### <a name="azure-ad-application-related-parameters"></a>Anwendungsbezogene Azure AD-Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Azure AD-App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](#use-an-existing-azure-ad-app-for-your-bot) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Das während der Bereitstellung erstellte Azure AD-App-Clientgeheimnis Ihrer App | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD-App Ihrer App | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der Azure AD-App Ihrer App | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Während der Bereitstellung erstellte Azure AD-App-Client-ID des Bots | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Während der Bereitstellung erstellter Clientschlüssel der Azure AD-App des Bots | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](#use-an-existing-azure-ad-app-for-your-bot) |

##### <a name="azure-resource-related-parameters"></a>Azure-Ressourcenbezogene Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| azureSqlAdmin | {{state.fx-resource-azure-sql.admin}} | Azure SQL Server-Administratorkonto, das Sie während der Bereitstellung bereitgestellt haben | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |
| azureSqlAdminPassword | {{state.fx-resource-azure-sql.adminPassword}} | Administratorkennwort für Azure SQL Server, das Sie während der Bereitstellung angegeben haben | Löschen Sie den Platzhalter und füllen Sie den tatsächlichen Wert aus |

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

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App

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

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot

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
2. Fügen Sie beispielsweise `functionAppName` eine neue Eigenschaft unter dem `provisionParameters` Abschnitt hinzu.
3. Geben Sie den Wert ein `functionAppName`, z. B `contosoteamsappapi`. .
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

So fügen Sie der Anwendung andere Azure-Ressourcen oder -Speicher hinzu:

Stellen Sie sich folgendes Szenario vor:

Sie möchten Ihrem Azure-Funktions-Back-End Azure Storage hinzufügen, um Blobdaten zu speichern. Es gibt keinen automatischen Ablauf zum Aktualisieren der Biceps-Vorlage mit Azure-Speicherunterstützung. Sie können jedoch die Bicep-Datei bearbeiten und die Ressource hinzufügen. Führen Sie dazu folgende Schritte aus:

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

::: zone-end

::: zone pivot="visual-studio"

## <a name="provision-using-teams-toolkit-in-visual-studio"></a>Bereitstellen mithilfe des Teams-Toolkits in Visual Studio

Die folgenden Schritte helfen Ihnen beim Bereitstellen von Cloudressourcen mithilfe von Visual Studio:

### <a name="sign-in-to-your-microsoft-365-account"></a>Anmelden bei Ihrem Microsoft 365-Konto

1. Öffnen Sie Visual Studio 2022.
1. Öffnen Sie das Microsoft Teams-App-Projekt.
1. Wählen Sie Project **Teams Toolkit** > **Prepare Teams App Dependencies (Teams-App-Abhängigkeiten** >  vorbereiten) aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare-app-dependencies1.png" alt-text="Vorbereiten von Teams-App-Abhängigkeiten":::

1. Wählen Sie **Anmelden** aus, um sich bei Ihrem Azure-Konto anzumelden.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare1.png" alt-text="Bei Microsoft 365 anmelden":::

    > [!NOTE]
    > Wenn Sie bereits angemeldet sind, wird Ihr Benutzername angezeigt, oder Sie können denselben auswählen, um Ihr Konto zu wechseln.

1. Ihr Standardwebbrowser wird geöffnet, damit Sie [sich beim Konto anmelden](https://developer.microsoft.com/en-us/microsoft-365/dev-program) können.

1. Wählen Sie **Weiter** aus, nachdem Sie sich bei Ihrem Konto angemeldet haben.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-signin-M365.png" alt-text="Bestätigen Sie, indem Sie Weiter auswählen.":::

### <a name="sign-in-to-your-azure-account"></a>Anmelden bei Ihrem Azure-Konto

1. Öffnen Sie Visual Studio 2022.
1. Öffnen Sie das Projekt Teams-App.
1. Wählen Sie **Project** > **Teams Toolkit** > **Bereitstellen in der Cloud** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud2.png" alt-text="Anmelden beim Azure-Konto":::

1. Wählen Sie **Anmelden...** aus, um sich bei Ihrem Azure-Konto anzumelden.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-start.png" alt-text="Anmelden bei Ihrem Azure-Konto":::

   > [!NOTE]
   > Wenn Sie bereits angemeldet sind, wird Ihr Benutzername angezeigt, oder Sie haben die Möglichkeit, das Konto zu wechseln.

   Nachdem Sie sich mit Ihren Anmeldeinformationen bei Ihrem Azure-Konto angemeldet haben, wird der Browser automatisch geschlossen.

### <a name="to-provision-cloud-resources"></a>So stellen Sie Cloudressourcen bereit

Nachdem Sie Ihr Projekt in Visual Studio geöffnet haben:

1. Wählen Sie **Project** > **Teams Toolkit** > **Bereitstellen in der Cloud** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud2.png" alt-text="Bereitstellen in der Cloud":::

   Das Fenster **Bereitstellen** wird angezeigt.

1. Geben Sie die folgenden Details ein, um Ihre Ressourcen bereitzustellen.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-select-subscription1.png" alt-text="Ressourcengruppe auswählen":::

   1. Wählen Sie in der Dropdownliste Ihren **Abonnementnamen** aus.
   1. Wählen Sie Ihre **Ressourcengruppe** aus der Dropdownliste aus.
   1. Wählen Sie in der Dropdownliste Ihre **Region** aus.

      > [!NOTE]
      > Sie können eine neue Ressourcengruppe erstellen, indem Sie **Neu** auswählen.

   1. Wählen Sie **Bereitstellen** aus.

1. Das Dialogfeld wird mit dem Hinweis angezeigt, dass Gebühren gemäß Azure-Nutzung hinzugefügt werden können. Wählen Sie **Bereitstellen** aus.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-warning.png" alt-text="Bereitstellungswarnung":::

   Beim Bereitstellungsprozess werden Ressourcen in der Azure-Cloud erstellt. Sie können den Fortschritt überwachen, indem Sie das Ausgabefenster des Teams-Toolkits beobachten.

1. Sie werden nach Abschluss der Bereitstellung aufgefordert. Wählen Sie **Bereitgestellte Ressourcen anzeigen** aus, um alle bereitgestellten Ressourcen anzuzeigen.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-provision-success.png" alt-text="Anzeigen bereitgestellter Ressourcen":::

## <a name="create-resources"></a>Erstellen von Ressourcen

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen erstellen:

* Microsoft Azure Active Directory (Azure AD)-Anwendung unter Ihrem Microsoft 365-Mandanten.
* Teams-App-Registrierung unter der Teams-Plattform Ihres Microsoft 365-Mandanten.
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement.

Wenn Sie ein neues Projekt erstellen, müssen Sie auch Azure-Ressourcen erstellen. Die ARM-Vorlagen (Azure Resource Manager) definieren alle Azure-Ressourcen und helfen Ihnen beim Erstellen der erforderlichen Azure-Ressourcen während der Bereitstellung.

Die folgende Liste zeigt die Ressourcenerstellung für verschiedene Arten von App- und Azure-Ressourcen:
<br>

<details>
<summary><b>Ressourcenerstellung für die Anwendung „Teams Tab“.</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| App Service-Plan | Hostet Ihre Web-App der Registerkarte. | Nicht zutreffend |
| App Service | Hosten Ihrer Blazor-Registerkarten-App und eines einfachen Authentifizierungsservers, mit dem Sie Zugriff auf andere Dienste erhalten können. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für die Microsoft Teams-Nachrichtenerweiterungsanwendung</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| App Service Plan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App Service | Hostet Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für die Teams-Befehlsbotanwendung</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| App Service-Plan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App Service | Hostet Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für den Teams-Benachrichtigungsbot mit HTTP-Triggeranwendung (Web-API-Server)</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| App Service-Plan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App Service | Hosten Sie Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Verwaltete Identität | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für einen Teams-Benachrichtigungsbot mit HTTP-Triggeranwendung (Azure-Funktion)</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| Identität verwalten | Authentifiziert Azure Service-to-Service-Anforderungen. | Gemeinsame Nutzung über verschiedene Funktionen und Ressourcen hinweg. |
| Speicherkonto | Hilft beim Erstellen einer Funktions-App. | Nicht zutreffend |
| App Service-Plan | Hostet die Funktionsbot-App. | Nicht zutreffend |
| Function-App | Hostet Ihre Bot-App. | : Fügt eine benutzerseitig zugewiesene Identität für den Zugriff auf andere Azure-Ressourcen hinzu.<br>– Fügt CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>: Fügt App-Einstellungen hinzu, die für das TeamsFx SDK erforderlich sind. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für teams-Benachrichtigungsbots mit Timertriggeranwendung (Azure-Funktion)</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| Identität verwalten | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |
| Speicherkonto | Hilft beim Erstellen einer Funktions-App. | Nicht zutreffend. |
| App Service-Plan | Hostet die Funktionsbot-App. | Nicht zutreffend |
| Function-App | Hostet Ihre Bot-App. | : Fügt eine benutzerseitig zugewiesene Identität für den Zugriff auf andere Azure-Ressourcen hinzu.<br>– Fügt CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>: Fügt App-Einstellungen hinzu, die für das TeamsFx SDK erforderlich sind. |

</details>
<br>

<details>
<summary><b>Ressourcenerstellung für den Teams-Benachrichtigungsbot mit HTTP-Trigger und Timertriggeranwendung (Azure-Funktion)</b></summary>

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Verbindet den Bot mit Teams. |
| Identität verwalten | Authentifizieren von Azure-Dienst-zu-Dienst-Anforderungen. | Freigaben für verschiedene Funktionen und Ressourcen. |
| Speicherkonto | Hilft beim Erstellen einer Funktions-App. | Nicht zutreffend |
| App Service-Plan | Hostet die Funktionsbot-App. | Nicht zutreffend |
| Funktions-App | Hostet Ihre Bot-App. | : Fügt eine benutzerseitig zugewiesene Identität für den Zugriff auf andere Azure-Ressourcen hinzu.<br>– Fügt CORS-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>: Fügt App-Einstellungen hinzu, die für das TeamsFx SDK erforderlich sind. |

</details>
<br>

### <a name="manage-your-resources"></a>Verwalten Ihrer Ressourcen

Sie können sich bei [Azure-Portal](https://portal.azure.com/) anmelden und alle ressourcen verwalten, die von Teams Toolkit erstellt wurden.

* Sie können eine Ressourcengruppe aus der vorhandenen Liste oder der neuen Ressourcengruppe auswählen, die Sie erstellt haben.
* Die Details der ausgewählten Ressourcengruppe finden Sie im Abschnitt "Übersicht" des Inhaltsverzeichnisses.

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Mit dem Teams-Toolkit können Sie eine Infrastruktur für den Codeansatz verwenden, um die Azure-Ressourcen zu definieren, die Sie bereitstellen möchten. Sie können die Konfiguration im Teams-Toolkit gemäß Ihren Anforderungen ändern.

Das Teams-Toolkit verwendet eine ARM-Vorlage, um Azure-Ressourcen zu definieren. Die ARM-Vorlage ist eine Reihe von Bicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie im [Bicep-Dokument](/azure/azure-resource-manager/bicep).

Die Bereitstellung mit ARM umfasst die Änderung der folgenden Sätze von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien (`azure.parameters.{your_env_name}.json`) im `.fx/configs` Ordner zum Übergeben von Parametern an Vorlagen.
* ARM-Vorlagendateien, die sich im `templates/azure` Ordner befinden, enthalten die folgenden Dateien:

| Datei | Funktion | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Geben Sie einen Einstiegspunkt für die Azure-Ressource an. Bereitstellung | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen | Ja |
| config.bicep | Fügen Sie erforderliche TeamsFx-Konfigurationen zu Azure-Ressourcen hinzu. | Ja |
| provision/xxx.bicep | Erstellen und konfigurieren Sie jede azure-Ressource, die von genutzt wird `provision.bicep`. | Ja |
| teamsfx/xxx.bicep | Fügen Sie die erforderlichen TeamsFx-Konfigurationen zu jeder Azure-Ressource hinzu, die von genutzt wird `config.bicep`.| Nein |

> [!NOTE]
> Nachdem Sie Ihrem Projekt Ressourcen oder Funktionen hinzugefügt haben, `teamsfx/xxx.bicep` wird neu generiert. Um die Bicep-Dateien zu ändern, können Sie Git verwenden, um Ihre Änderungen an Dateien nachzuverfolgen `teamsfx/xxx.bicep` . Dadurch verlieren Sie beim Hinzufügen von Ressourcen oder Funktionen zu Ihrem Projekt keine Änderungen.

Die ARM-Vorlagendateien verwenden Platzhalter für Parameter. Der Zweck der Platzhalter besteht darin, sicherzustellen, dass neue Ressourcen in der neuen Umgebung erstellt werden können. Die tatsächlichen Werte werden aus der `.fx/states/state.{env}.json` Datei aufgelöst.

### <a name="azure-ad-application-related-parameters"></a>Azure AD-anwendungsbezogene Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Während der Bereitstellung erstellte Azure AD-App-Client-ID Ihrer App. | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Der geheime Azure AD-App-Clientschlüssel Ihrer App, der während der Bereitstellung erstellt wurde. | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD-App Ihrer App. | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der Azure AD-App Ihrer App. | [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Die Während der Bereitstellung erstellte Client-ID der Azure AD-App des Bots. | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Der geheime Clientschlüssel der Azure AD-App des Bots, der während der Bereitstellung erstellt wurde. | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](#use-an-existing-azure-ad-app-for-your-bot) |

### <a name="reference-environment-variables-in-parameter-files"></a>Verweisen auf Umgebungsvariablen in Parameterdateien

Wenn der Wert geheimnis ist, müssen Sie sie nicht in der Parameterdatei hartcodieren. Die Parameterdateien unterstützen das Referenzieren der Werte aus Umgebungsvariablen. Sie können diese Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in den Parameterwerten für Teams Toolkit verwenden, um die Auflösung aus der aktuellen Umgebungsvariablen zu ermöglichen.

Das folgende Beispiel liest den Wert des Parameters `mySelfHostedDbConnectionString` aus der Umgebungsvariablen `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

### <a name="customize-arm-template-files"></a>Passen Sie ARM-Vorlagendateien an

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderung nicht erfüllen, können Sie die ARM-Vorlagen unter dem `templates/azure` Ordner anpassen. Beispielsweise können Sie die ARM-Vorlage anpassen, um zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Sie müssen über Grundkenntnisse der Bicep-Sprache verfügen, die zum Erstellen von ARM-Vorlagen verwendet wird.

Um sicherzustellen, dass das TeamsFx-Tool ordnungsgemäß funktioniert, passen Sie die ARM-Vorlage an, die die folgenden Anforderungen erfüllt:

* Stellen Sie sicher, dass die Ordnerstruktur und der Dateiname unverändert bleiben. Das Tool fügt möglicherweise neue Inhalte an die vorhandenen Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Stellen Sie sicher, dass der Name der automatisch generierten Parameter und die zugehörigen Eigenschaftennamen nicht hängen bleiben. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen oder Fähigkeiten hinzufügen.
* Stellen Sie sicher, dass auch die Ausgabe der automatisch generierten ARM-Vorlage unverändert ist. Sie können der ARM-Vorlage weitere Ausgaben hinzufügen. Die Ausgabe ist `.fx/states/state.{env}.json` und kann in anderen Features wie bereitstellen und überprüfen der Manifestdatei verwendet werden.

### <a name="customize-teams-app"></a>Anpassen der Teams-App

Sie können Ihren Bot oder die Teams-App anpassen, indem Sie Konfigurationsausschnitte hinzufügen, um eine von Ihnen erstellte Azure AD-App zu verwenden. Sie haben folgende Möglichkeiten:

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App

Sie können den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen für Ihre Teams-App erstellte Azure AD-App zu verwenden. Um eine Azure AD-App zu erstellen, folgen Sie dem Link <https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Nachdem Sie den Codeausschnitt hinzugefügt haben, fügen Sie Ihren geheimen Clientschlüssel der zugehörigen Umgebungsvariablen hinzu, damit teams Toolkit den tatsächlichen geheimen Clientschlüssel während der Bereitstellung auflösen kann.

> [!NOTE]
> Stellen Sie sicher, dass Sie dieselbe Azure AD-App nicht in mehreren Umgebungen freigeben. Wenn Sie nicht über die Berechtigung zum Aktualisieren der Azure AD-App verfügen, erhalten Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der Azure AD-App. Befolgen Sie diese Anweisungen, um Ihre Azure AD-App nach der Bereitstellung zu aktualisieren.

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot

Sie können den folgenden Konfigurationsausschnitt hinzufügen, um die für Ihren Bot erstellte Azure AD-App zu `.fx/configs/config.{env}.json` verwenden:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Fügen Sie nach dem Hinzufügen des Codeausschnitts Ihren geheimen Clientschlüssel zur zugehörigen Umgebungsvariablen für Teams Toolkit hinzu, um den tatsächlichen geheimen Clientschlüssel während der Bereitstellung aufzulösen.

#### <a name="skip-adding-user-for-sql-database"></a>Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank

Wenn beim Versuch des Teams-Toolkits, benutzer zur SQL-Datenbank hinzuzufügen, ein Fehler aufgrund unzureichender Berechtigungen angezeigt wird, können Sie den folgenden Konfigurationsausschnitt zu hinzufügen, um `.fx/configs/config.{env}.json` das Hinzufügen eines SQL-Datenbankbenutzers zu überspringen:

```json
"skipAddingSqlUser": true
```

::: zone-end

## <a name="see-also"></a>Siehe auch

* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
* [Bereitstellen der Teams-App in der Cloud mithilfe von Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Lokales Debuggen der Teams-App für Visual Studio](debug-local.md#debug-your-teams-app-locally-using-visual-studio)
