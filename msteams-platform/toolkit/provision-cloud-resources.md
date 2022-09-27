---
title: Verwenden des Teams-Toolkits zum Bereitstellen von Cloudressourcen mithilfe des Teams-Toolkits für Visual Studio
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie Cloudressourcen mithilfe des Teams-Toolkits bereitstellen. Auch zum Erstellen von Ressourcen und Anpassen der Ressourcenbereitstellung in Visual Studio
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 00e021e3e42eed6eeb5881d258a9884a7e579377
ms.sourcegitcommit: 65ae3ccc2312ddc6cdaa05096e30bdf9dca10c3f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2022
ms.locfileid: "68027472"
---
# <a name="provision-cloud-resources-using-visual-studio"></a>Bereitstellen von Cloudressourcen mit Visual Studio

TeamsFx lässt sich in Azure und die Microsoft 365-Cloud integrieren, mit der Sie Ihre Anwendung mit einem einzigen Befehl in Azure platzieren können. TeamsFx lässt sich in Azure Resource Manager integrieren, mit dem Sie Azure-Ressourcen bereitstellen können. Für den Codeansatz benötigt Ihre Anwendung die Cloudressourcen.

## <a name="prerequisites"></a>Voraussetzungen

Hier ist eine Liste der Tools, die Sie für die Bereitstellung Ihrer Cloudressourcen benötigen:

| &nbsp; | Installieren | Zum Benutzen... |
| --- | --- | --- |
| &nbsp; | **Required** | &nbsp; |
| &nbsp; | Visual Studio 2022, Version 17.3 | Sie können die Enterprise-Edition von Visual Studio und die "ASP.NET" Workload und Microsoft Teams-Entwicklungstools installieren. |
| &nbsp; | [Microsoft 365-Entwicklerkonto](https://developer.microsoft.com/en-us/microsoft-365/dev-program) | Zugriff auf das Teams-Konto mit den entsprechenden Berechtigungen zum Installieren einer App. |
| &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Microsoft Teams für die Zusammenarbeit mit allen, mit denen Sie zusammenarbeiten, über Apps für Chats, Besprechungen und Anrufe – alles an einem Ort. |
| &nbsp; | Teams Toolkit | Eine Visual Studio-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. |
| &nbsp; | [Azure-Konto](https://portal.azure.com/) | Azure-Konto mit einem gültigen Abonnement. |

## <a name="steps-to-provision-cloud-resources"></a>Schritte zum Bereitstellen von Cloudressourcen

Die folgenden Schritte helfen Ihnen bei der Bereitstellung von Cloudressourcen mit Visual Studio:

### <a name="sign-in-to-your-microsoft-365-account"></a>Anmelden bei Ihrem Microsoft 365-Konto

1. Visual Studio 2022.
2. Öffnen Sie das Microsoft Teams-App-Projekt.
3. Wählen Sie **"Projekt**" aus.
4. Wählen Sie **das Teams-Toolkit** aus.
5. Wählen Sie **"Teams-App-Abhängigkeiten vorbereiten" aus**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare-app-dependencies.png" alt-text="Vorbereiten von Abhängigkeiten von Teams-Apps":::

7. Wählen Sie **"Anmelden...** aus, um sich bei Ihrem Azure-Konto anzumelden.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-prepare1.png" alt-text="Bei Microsoft 365 anmelden":::

    > [!NOTE]
    > Wenn Sie bereits angemeldet sind, wird Ihr Benutzername angezeigt, oder Sie können dasselbe auswählen, um Ihr Konto zu wechseln.

8. Ihr Standardwebbrowser wird geöffnet, damit Sie [sich beim Konto anmelden](https://developer.microsoft.com/en-us/microsoft-365/dev-program) können.
9. Wählen Sie " **Weiter"** aus, nachdem Sie sich bei Ihrem Konto angemeldet haben.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-signin-M365.png" alt-text="Bestätigen Sie dies, indem Sie &quot;Weiter&quot; auswählen.":::

### <a name="sign-in-to-your-azure-account"></a>Anmelden bei Ihrem Azure-Konto

1. Öffnen Sie Visual Studio 2022.
2. Öffnen Sie das Teams-App-Projekt.
3. Wählen Sie **"Projekt**" aus.
4. Wählen Sie **das Teams-Toolkit** aus.
5. Wählen Sie **"In der Cloud bereitstellen" aus**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud.png" alt-text="Anmelden bei Azure-Konto":::

6. Wählen Sie **"Anmelden...** aus, um sich bei Ihrem Azure-Konto anzumelden.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-start.png" alt-text="Anmelden bei Ihrem Azure-Konto":::

   > [!NOTE]
   > Wenn Sie bereits angemeldet sind, wird Ihr Benutzername angezeigt, oder Sie haben die Möglichkeit, das Konto zu wechseln.

7. Melden Sie sich mit Ihren Anmeldeinformationen beim Azure-Konto an. Der Browser wird automatisch geschlossen.

### <a name="to-provision-cloud-resources"></a>So stellen Sie Cloudressourcen bereit

1. Nachdem Sie das Projekt in Visual Studio geöffnet haben, wählen Sie **"Projekt** auswählen" aus.
2. **Teams-Toolkit** auswählen
3. Wählen Sie **"In der Cloud bereitstellen" aus**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-in-cloud1.png" alt-text="Bereitstellung in der Cloud":::

4. Im Bereitstellungsdialogfeld können Sie eine Liste aller Abonnements in Ihrem Azure-Konto sehen.
5. Sie können entweder eine neue **Ressourcengruppe** auswählen oder erstellen.
6. Wählen Sie **"Bereitstellen" aus**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-select-subscription1.png" alt-text="Ressourcengruppe auswählen":::

7. Das Dialogfeld warnt Sie, dass Gebühren gemäß Azure-Nutzung hinzugefügt werden können. Wählen Sie **"Bereitstellen" aus**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-warning.png" alt-text="Bereitstellungswarnung":::

   Der Bereitstellungsprozess zum Erstellen der Ressourcen in der Azure-Cloud kann einige Zeit in Anspruch nehmen.

8. Überprüfen Sie das Ausgabefenster des Teams-Toolkits, um den Fortschritt zu überwachen.
9. Sie werden nach Abschluss der Bereitstellung aufgefordert. Wählen Sie **"Bereitgestellte Ressourcen anzeigen** " aus, um alle bereitgestellten Ressourcen anzuzeigen.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/Provision-cloud-resources-in-TTK-VS/teams-toolkit-vs-provision-provision-success.png" alt-text="Anzeigen bereitgestellter Ressourcen":::

### <a name="create-resources"></a>Erstellen von Ressourcen

Wenn Sie den Bereitstellungsbefehl in Teams Toolkit oder TeamsFx CLI auslösen, können Sie die folgenden Ressourcen erstellen:

* Microsoft Azure Active Directory (Azure AD)-Anwendung unter Ihrem Microsoft 365-Mandanten.
* Teams-App-Registrierung unter der Teams-Plattform Ihres Microsoft 365-Mandanten.
* Azure-Ressourcen unter Ihrem ausgewählten Azure-Abonnement.

Wenn Sie ein neues Projekt erstellen, müssen Sie auch Azure-Ressourcen erstellen. Die Azure Resource Manager-Vorlagen (ARM) definieren alle Azure-Ressourcen und helfen Ihnen, erforderliche Azure-Ressourcen während der Bereitstellung zu erstellen.

### <a name="create-resource-for-teams-tab-application"></a>Erstellen einer Ressource für die Registerkartenanwendung "Teams"

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| App-Serviceplan | Hostet Ihre Web-App der Registerkarte. | Nicht zutreffend |
| App-Dienst | Hostet Ihre Blazor-Registerkarten-App und einen einfachen Authentifizierungsserver, der ihnen hilft, Zugriff auf andere Dienste zu erhalten. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |

### <a name="create-resources-for-teams-message-extension-application"></a>Erstellen von Ressourcen für die Teams-Nachrichtenerweiterungsanwendung

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| App Service Plan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App Service | Hostet Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |

### <a name="create-resources-for-teams-command-bot-application"></a>Erstellen von Ressourcen für die Teams-Befehls-Bot-Anwendung

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| App-Serviceplan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App-Dienst | Hostet Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Identität verwalten | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |

### <a name="create-resources-for-teams-notification-bot-with-http-trigger-web-api-server-application"></a>Erstellen von Ressourcen für den Teams-Benachrichtigungs-Bot mit EINER HTTP-Triggeranwendung (Web-API-Server)

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| App-Serviceplan | Hostet Ihre Webbot-App. | Nicht zutreffend |
| App-Dienst | Hosten Sie Ihre Bot-App. | Fügt eine vom Benutzer zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen. |
| Verwaltete Identität | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |

### <a name="create-resource-for-teams-notification-bot-with-http-trigger-azure-function-application"></a>Erstellen einer Ressource für den Teams-Benachrichtigungs-Bot mit einer HTTP-Triggeranwendung (Azure-Funktion)

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| Identität verwalten | Authentifiziert Azure-Service-to-Service-Anforderungen. | Gemeinsam genutzt über verschiedene Funktionen und Ressourcen. |
| Speicherkonto | Hilft beim Erstellen der Funktions-App. | Nicht zutreffend |
| App-Serviceplan | Hostet die Funktions-Bot-App. | Nicht zutreffend |
| Function-App | Hostet Ihre Bot-App. | – Fügt dem Benutzer eine zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen.<br>– Fügt cors-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>– Fügt App-Einstellungen hinzu, die vom TeamsFx SDK erforderlich sind. |

### <a name="create-resource-for-teams-notification-bot-with-timer-trigger-azure-function-application"></a>Erstellen einer Ressource für den Teams-Benachrichtigungs-Bot mit Zeitgebertriggeranwendung (Azure-Funktion)

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| Identität verwalten | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |
| Speicherkonto | Hilft beim Erstellen der Funktions-App. | Nicht zutreffend. |
| App-Serviceplan | Hostet die Funktions-Bot-App. | Nicht zutreffend |
| Function-App | Hostet Ihre Bot-App. | – Fügt dem Benutzer eine zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen.<br>– Fügt cors-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>– Fügt App-Einstellungen hinzu, die vom TeamsFx SDK erforderlich sind. |

### <a name="create-resources-for-teams-notification-bot-with-http-trigger--timer-trigger-azure-function-application"></a>Erstellen von Ressourcen für den Teams-Benachrichtigungs-Bot mit der Anwendung HTTP-Trigger + Zeitgebertrigger (Azure-Funktion)

| Ressource | Zweck | Beschreibung |
| --- | --- | --- |
| Azure-Bot | Registriert Ihre App als Bot beim Bot-Framework. | Stellt eine Verbindung zwischen Bot und Teams her. |
| Identität verwalten | Authentifizieren von Azure Service-to-Service-Anforderungen. | Freigabe über verschiedene Funktionen und Ressourcen hinweg. |
| Speicherkonto | Hilft beim Erstellen der Funktions-App. | Nicht zutreffend |
| App-Serviceplan | Hostet die Funktions-Bot-App. | Nicht zutreffend |
| Funktions-App | Hostet Ihre Bot-App. | – Fügt dem Benutzer eine zugewiesene Identität hinzu, um auf andere Azure-Ressourcen zuzugreifen.<br>– Fügt cors-Regel (Cross-Origin Resource Sharing) hinzu, um Anforderungen von Ihrer Registerkarten-App zuzulassen.<br>– Fügt eine Authentifizierungseinstellung hinzu, die nur Anforderungen von Ihrer Teams-App zulässt.<br>– Fügt App-Einstellungen hinzu, die vom TeamsFx SDK erforderlich sind. |

### <a name="manage-your-resources"></a>Verwalten Ihrer Ressourcen

Sie können sich bei [Azure-Portal](https://portal.azure.com/) anmelden und alle ressourcen verwalten, die vom Teams-Toolkit erstellt wurden.

* Sie können die Ressourcengruppe aus der vorhandenen Liste oder der neuen Ressourcengruppe auswählen, die Sie erstellt haben.
* Die Details der ausgewählten Ressourcengruppe finden Sie im Abschnitt "Übersicht" des Inhaltsverzeichnisses.

### <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Mit dem Teams-Toolkit können Sie eine Infrastruktur für den Codeansatz verwenden, um die Azure-Ressourcen zu definieren, die Sie bereitstellen möchten. Sie können die Konfiguration im Teams-Toolkit entsprechend Ihren Anforderungen ändern.

Das Teams-Toolkit verwendet arm-Vorlage, um Azure-Ressourcen zu definieren. Die ARM-Vorlage ist eine Reihe von Bicep-Dateien, die die Infrastruktur und Konfiguration für Ihr Projekt definieren. Sie können Azure-Ressourcen anpassen, indem Sie die ARM-Vorlage ändern. Weitere Informationen finden Sie im [Bicep-Dokument](/azure/azure-resource-manager/bicep).

Die Bereitstellung mit ARM umfasst die Änderung der folgenden Sätze von Dateien, Parametern und Vorlagen:

* ARM-Parameterdateien (`azure.parameters.{your_env_name}.json`) im `.fx/configs` Ordner zum Übergeben von Parametern an Vorlagen.
* ARM-Vorlagendateien, die sich im `templates/azure` Ordner befinden, enthalten folgende Dateien:

| Datei | Funktion | Anpassung zulassen |
| --- | --- | --- |
| main.bicep | Stellen Sie den Einstiegspunkt für die Azure-Ressource bereit. Bereitstellung | Ja |
| provision.bicep | Erstellen und Konfigurieren von Azure-Ressourcen. | Ja |
| config.bicep | Fügen Sie erforderliche TeamsFx-Konfigurationen zu Azure-Ressourcen hinzu. | Ja |
| provision/xxx.bicep | Erstellen und konfigurieren Sie jede Azure-Ressource, die von verbraucht wird `provision.bicep`. | Ja |
| teamsfx/xxx.bicep | Fügen Sie die erforderlichen TeamsFx-Konfigurationen zu jeder Azure-Ressource hinzu, die von verbraucht wird `config.bicep`.| Nein |

> [!NOTE]
> Nachdem Sie Ihrem Projekt Ressourcen oder Funktionen hinzugefügt haben, `teamsfx/xxx.bicep` wird es neu generiert. Zum Ändern der Bicep-Dateien können Sie Git verwenden, um Ihre Änderungen an Dateien nachzuverfolgen `teamsfx/xxx.bicep` . Dadurch gehen beim Hinzufügen von Ressourcen oder Funktionen zu Ihrem Projekt keine Änderungen verloren.

Die ARM-Vorlagendateien verwenden Platzhalter für Parameter. Der Zweck der Platzhalter besteht darin, sicherzustellen, dass neue Ressourcen in der neuen Umgebung erstellt werden können. Die tatsächlichen Werte werden aus der `.fx/states/state.{env}.json` Datei aufgelöst.

### <a name="azure-ad-application-related-parameters"></a>Azure AD-Anwendungsbezogene Parameter

| Parametername | Standardwert-Platzhalter | Bedeutung des Platzhalters | So passen Sie es an |
| --- | --- | --- | --- |
| Microsoft 365 ClientId | {{state.fx-resource-aad-app-for-teams.clientId}} | Die Azure AD-App-Client-ID Ihrer App, die während der Bereitstellung erstellt wurde. | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app) |
| Microsoft 365 ClientSecret | {{state.fx-resource-aad-app-for-teams.clientSecret}} | Der geheime Azure AD-App-Clientschlüssel Ihrer App, der während der Bereitstellung erstellt wurde. | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 TenantId | {{state.fx-resource-aad-app-for-teams.tenantId}} | Mandanten-ID der Azure AD-App Ihrer App. | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app)  |
| Microsoft 365 OAuthAuthorityHost | {{state.fx-resource-aad-app-for-teams.oauthHost}} | OAuth-Autoritätshost der Azure AD-App Ihrer App. | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-teams-app) |
| botAadAppClientId | {{state.fx-resource-bot.botId}} | Die Azure AD-App-Client-ID des Bots, die während der Bereitstellung erstellt wurde. | [Anpassen des Werts](#use-an-existing-azure-ad-app-for-your-bot) |
| botAadAppClientSecret | {{state.fx-resource-bot.botPassword}} | Der geheime Azure AD-App-Clientschlüssel des Bots, der während der Bereitstellung erstellt wurde. | [Wert anpassen](#use-an-existing-azure-ad-app-for-your-bot) |

### <a name="reference-environment-variables-in-parameter-files"></a>Referenzumgebungsvariablen in Parameterdateien

Wenn der Wert geheim ist, müssen Sie sie nicht in der Parameterdatei hartcodieren. Die Parameterdateien unterstützen das Referenzieren der Werte aus Umgebungsvariablen. Sie können diese Syntax `{{$env.YOUR_ENV_VARIABLE_NAME}}` in den Parameterwerten für das Teams-Toolkit verwenden, um die Auflösung aus der aktuellen Umgebungsvariablen durchzuführen.

Das folgende Beispiel liest den Wert des Parameters `mySelfHostedDbConnectionString` aus der Umgebungsvariablen `DB_CONNECTION_STRING`:

```json
...
    "mySelfHostedDbConnectionString": "{{$env.DB_CONNECTION_STRING}}"
...
```

### <a name="customize-arm-template-files"></a>Passen Sie ARM-Vorlagendateien an

Wenn die vordefinierten Vorlagen Ihre Anwendungsanforderung nicht erfüllen, können Sie die ARM-Vorlagen unter `templates/azure` dem Ordner anpassen. Beispielsweise können Sie die ARM-Vorlage anpassen, um einige zusätzliche Azure-Ressourcen für Ihre App zu erstellen. Sie müssen über Grundkenntnisse der Bicep-Sprache verfügen, die zum Erstellen von ARM-Vorlagen verwendet wird.

Um sicherzustellen, dass das TeamsFx-Tool ordnungsgemäß funktioniert, passen Sie die ARM-Vorlage an, die die folgende Anforderung erfüllt:

* Stellen Sie sicher, dass die Ordnerstruktur und der Dateiname unverändert bleiben. Das Tool fügt möglicherweise neue Inhalte an die vorhandenen Dateien an, wenn Sie Ihrem Projekt weitere Ressourcen oder Funktionen hinzufügen.
* Stellen Sie sicher, dass der Name der automatisch generierten Parameter und dessen Eigenschaftsnamen nicht hängen bleiben. Die automatisch generierten Parameter können verwendet werden, wenn Sie Ihrem Projekt weitere Ressourcen oder Fähigkeiten hinzufügen.
* Stellen Sie sicher, dass auch die Ausgabe der automatisch generierten ARM-Vorlage unverändert bleibt. Sie können der ARM-Vorlage weitere Ausgaben hinzufügen. Die Ausgabe wird `.fx/states/state.{env}.json` und kann in anderen Features verwendet werden, z. B. bereitstellen und Überprüfen der Manifestdatei.

### <a name="customize-teams-app"></a>Anpassen der Teams-App

Sie können Ihren Bot oder die Teams-App anpassen, indem Sie Konfigurationsausschnitte hinzufügen, um eine von Ihnen erstellte Azure AD-App zu verwenden. Sie können folgendeRmaßen vorgehen:

#### <a name="use-an-existing-azure-ad-app-for-your-bot"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot

Sie können den folgenden Konfigurationsausschnitt `.fx/configs/config.{env}.json` hinzufügen, um eine von Ihnen erstellte Azure AD-App für Ihre Teams-App zu verwenden. Um eine Azure AD-App zu erstellen, folgen Sie dem Link <https://aka.ms/teamsfx-existing-aad-doc>.

```json
"auth": {
    "clientId": "<your Azure AD app client id>",
    "clientSecret": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}",
    "objectId": "<your Azure AD app object id>",
    "accessAsUserScopeId": "<id of the access_as_user scope>"
}
```

Fügen Sie nach dem Hinzufügen des Codeausschnitts Ihren geheimen Clientschlüssel zur zugehörigen Umgebungsvariable hinzu, damit das Teams-Toolkit den tatsächlichen geheimen Clientschlüssel während der Bereitstellung auflösen kann.

> [!NOTE]
> Stellen Sie sicher, dass Sie dieselbe Azure AD-App nicht in mehreren Umgebungen freigeben. Wenn Sie nicht über die Berechtigung zum Aktualisieren der Azure AD-App verfügen, erhalten Sie eine Warnung mit Anweisungen zum manuellen Aktualisieren der Azure AD-App. Befolgen Sie die folgenden Anweisungen, um Ihre Azure AD-App nach der Bereitstellung zu aktualisieren.

#### <a name="use-an-existing-azure-ad-app-for-your-teams-app"></a>Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App

Sie können den folgenden Konfigurationsausschnitt hinzufügen, um `.fx/configs/config.{env}.json` die für Ihren Bot erstellte Azure AD-App zu verwenden:

```json
"bot": {
    "appId": "<your Azure AD app client id>",
    "appPassword": "{{$env.ENV_NAME_THAT_STORES_YOUR_SECRET}}"
}
```

Fügen Sie nach dem Hinzufügen des Codeausschnitts Ihren geheimen Clientschlüssel zur zugehörigen Umgebungsvariablen für das Teams-Toolkit hinzu, um den tatsächlichen geheimen Clientschlüssel während der Bereitstellung aufzulösen.

#### <a name="skip-adding-user-for-sql-database"></a>Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank

Wenn beim Versuch des Teams-Toolkits, Benutzer zur SQL-Datenbank hinzuzufügen, ein unzureichender Berechtigungsfehler auftritt, können Sie den folgenden Konfigurationsausschnitt hinzufügen, um das Hinzufügen von SQL-Datenbankbenutzern zu `.fx/configs/config.{env}.json` überspringen:

```json
"skipAddingSqlUser": true
```

## <a name="see-also"></a>Siehe auch

* [Bereitstellen der Teams-App in der Cloud mit Visual Studio](deploy-teams-app.md)
* [Bearbeiten des Teams-App-Manifests mit Visual Studio](VS-TeamsFx-preview-and-customize-app-manifest.md)
* [Lokales Debuggen der Teams-App für Visual Studio](debug-teams-app-visual-studio.md)
