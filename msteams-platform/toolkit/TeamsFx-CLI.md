---
title: TeamsFx-Befehlszeilenschnittstelle
author: MuyangAmigo
description: In diesem Modul lernen Sie die TeamsFx-Bibliothek, die TeamsFx-Befehlszeilenschnittstelle, unterstützte Befehle und ihre Szenarien kennen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d269da398280f51a3225414f279a25fcd5d9d7cf
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142073"
---
# <a name="teamsfx-library"></a>TeamsFx-Bibliothek

Microsoft Teams Framework (TeamsFx) ist eine Bibliothek, die allgemeine Funktionalitäts- und Integrationsmuster kapselt, z. B. den vereinfachten Zugriff auf Microsoft Identity. Sie können Apps für Microsoft Teams ohne Konfiguration erstellen.

Im Folgenden finden Sie eine Liste der wichtigsten TeamsFx-Features:

* **TeamsFx-Zusammenarbeit**: Ermöglicht Entwicklern und Projektbesitzern, andere Mitarbeiter zum TeamsFx-Projekt einzuladen. Sie können zusammenarbeiten, um ein TeamsFx-Projekt zu debuggen und bereitzustellen.

* **TeamsFx CLI**: Beschleunigt Teams Anwendungsentwicklung. Außerdem wird ein CI/CD-Szenario ermöglicht, in dem Sie die CLI zur Automatisierung in Skripts integrieren können.

* **TeamsFx SDK**: Bietet Zugriff auf Datenbank, z. B. die primäre TeamsFx-Codebibliothek, die einfache Authentifizierung für client- und serverseitigen Code enthält, der auf Teams Entwickler zugeschnitten ist.

## <a name="teamsfx-command-line-interface"></a>TeamsFx-Befehlszeilenschnittstelle

Die TeamsFx-CLI ist eine textbasierte Befehlszeilenschnittstelle, die die Entwicklung von Teams-Anwendungen beschleunigt. Das Ziel besteht darin, beim Erstellen von Teams-Anwendungen eine tastaturzentrierte Erfahrung zu bieten. Außerdem wird ein CI/CD-Szenario ermöglicht, in dem Sie die CLI zur Automatisierung in Skripts integrieren können.

Weitere Informationen finden Sie unter:

* [Quellcode](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli)
* [Paket (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx-cli)

## <a name="get-started"></a>Erste Schritte

Installieren Sie `teamsfx-cli` über `npm`, und führen Sie `teamsfx -h` aus, um alle verfügbaren Befehle zu überprüfen:

```bash
  npm install -g @microsoft/teamsfx-cli
  teamsfx -h
```

## <a name="supported-commands"></a>Unterstützte Befehle

| Befehl | Beschreibung |
|----------------|-------------|
| `teamsfx new`| Erstellen Sie eine neue Teams Anwendung.|
| `teamsfx add`| Fügt Ihrer Teams-Anwendung Features hinzu.|
| `teamsfx account`| Verwalten Sie Clouddienstkonten. Die unterstützten Clouddienste sind „Azure“ und „Microsoft 365“. |
| `teamsfx env` | Verwalten Sie Umgebungen. |
| `teamsfx provision` | Stellen Sie Cloudressourcen in der aktuellen Anwendung bereit.|
| `teamsfx deploy` | Stellen Sie die aktuelle Anwendung bereit.  |
| `teamsfx package` | Erstellen Sie Ihre Teams-App in einem Paket für die Veröffentlichung.|
| `teamsfx validate` | Überprüfen Sie die aktuelle Anwendung.|
| `teamsfx publish` | Veröffentlichen Sie die App in Teams.|
| `teamsfx preview` | Zeigen Sie eine Vorschau der aktuellen Anwendung an. |
| `teamsfx config`  | Verwalten Sie die Konfigurationsdaten. |
| `teamsfx permission`| Arbeiten Sie mit anderen Entwicklern im selben Projekt zusammen.|

## `teamsfx new`

Ist standardmäßig `teamsfx new` im interaktiven Modus und führt zum Erstellen neuer Teams Anwendung. Sie können im nicht interaktiven Modus arbeiten, indem Sie die Kennzeichnung auf `false`festlegen`--interactive`.

| Befehl | Beschreibung |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Erstellen einer App aus einer vorhandenen Vorlage |
| `teamsfx new template list`     | Auflisten aller verfügbaren Vorlagen |

### <a name="parameters-for-teamsfx-new"></a>Parameter für `teamsfx new`

| Parameter | Anforderung | Beschreibung |
|:---------------- |:-------------|:-------------|
|`--app-name` | Ja| Name Ihrer Teams-Anwendung.|
|`--interactive`| Nein | Wählen Sie die Optionen interaktiv aus. Die Optionen sind `true` und `false`, und der Standardwert ist `true`.|
|`--capabilities`| Nein| Wählen Sie Teams Anwendungsfunktionen aus. Die Optionen sind `tab`, `tab-non-sso`, `tab-spfx`, `bot`, `message-extension`, `notification`, `command-bot`, `sso-launch-page``search-app`. Der Standardwert ist `tab`.|
|`--programming-language`| Nein| Programmiersprache für das Projekt. Die Optionen sind `javascript` oder `typescript`, und der Standardwert ist `javascript`.|
|`--folder`| Nein | Projektverzeichnis. Unter diesem Verzeichnis wird ein Unterordner mit Ihrem App-Namen erstellt. Der Standardwert ist `./`.|
|`--spfx-framework-type`| Nein| Gilt, wenn die Funktion `SPFx tab` ausgewählt ist. Front-End-Framework. Die Optionen sind `none`, `react` und `minimal`der Standardwert ist `none`.|
|`--spfx-web part-name`| Nein | Gilt, wenn die Funktion `SPFx tab` ausgewählt ist. Der Standardwert ist „helloworld“.|
|`--bot-host-type-trigger`| Nein | Gilt, wenn die Funktion `Notification bot` ausgewählt ist. Die Optionen sind `http-restify`, `http-functions`und `timer-functions`. Der Standardwert ist `http-restify`.|

### <a name="scenarios-for-teamsfx-new"></a>Szenarien für `teamsfx new`

Sie können den interaktiven Modus verwenden, um eine Teams-App zu erstellen. Die folgende Liste enthält Szenarien zum Steuern aller Parameter mit `teamsfx new`:

* HTTP-ausgelöster Benachrichtigungs-Bot mit Restify-Server

  ```bash
  teamsfx new --interactive false --capabilities "notification" --bot-host-type-trigger "http-restify" --programming-language "typescript" --folder "./" --app-name       MyAppName
  ```

* Teams Befehls- und Antwort-Bot

  ```bash
  teamsfx new --interactive false --capabilities "command-bot" --programming-language "typescript" --folder "./" --app-name myAppName
  ```

* Registerkarten-App, die auf SPFx mithilfe von React gehostet wird

  ```bash
  teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
  ```

## `teamsfx add`

In der folgenden Tabelle sind die verschiedenen Features ihrer Teams Anwendung sowie deren Beschreibung aufgeführt.

| Befehl | Beschreibung |
|:----------------  |:-------------|
| `teamsfx add notification` | Senden Sie Benachrichtigungen über verschiedene Trigger an Microsoft Teams. |
| `teamsfx add command-and-response` | Reagieren Sie auf einfache Befehle in Microsoft Teams Chat.|
| `teamsfx add sso-tab` | Teams identitätsabhängige Webseiten, die in Microsoft Teams eingebettet sind.|
| `teamsfx add tab` | In Microsoft Teams eingebettete Hello World-Webseiten.|
| `teamsfx add bot` | Hello world chatbot to run simple and repetitive tasks by user. |
| `teamsfx add message-extension` | Die Nachrichtenerweiterung "Hello World" ermöglicht Interaktionen über Schaltflächen und Formulare. |
| `teamsfx add azure-function`| Eine serverlose, ereignisgesteuerte Computelösung, mit der Sie weniger Code schreiben können. |
| `teamsfx add azure-apim` | Eine hybride Multicloud-Verwaltungsplattform für APIs in allen Umgebungen.|
| `teamsfx add azure-sql` | Ein stets aktueller relationaler Datenbankdienst, der für die Cloud erstellt wurde. |
| `teamsfx add azure-keyvault` | Ein Clouddienst zum sicheren Speichern und Zugreifen auf geheime Schlüssel. |
| `teamsfx add sso` | Entwickeln Sie ein einzelnes Sign-On-Feature für Teams Startseiten und Bot-Funktionen. |
| `teamsfx add api-connection [auth-type]` | Verbinden zu einer API mit Authentifizierungsunterstützung mithilfe des TeamsFx SDK. |
| `teamsfx add cicd` | Fügen Sie CI/CD-Workflows für GitHub, Azure DevOps oder Jenkins hinzu.|

## `teamsfx account`

In der folgenden Tabelle sind die Clouddienstkonten wie Azure und Microsoft 365 aufgeführt.

| Befehl | Beschreibung |
|:----------------  |:-------------|
| `teamsfx account login <service>`  | Melden Sie sich beim ausgewählten Clouddienst an. Dienstoptionen sind Microsoft 365 oder Azure. |
| `teamsfx account logout <service>`  | Melden Sie sich beim ausgewählten Clouddienst ab. Dienstoptionen sind Microsoft 365 oder Azure. |
| `teamsfx account set --subscription` | Aktualisieren Sie die Kontoeinstellungen, um eine Abonnement-ID festzulegen. |

## `teamsfx env`

In der folgenden Tabelle sind die verschiedenen Umgebungen aufgeführt.

|  Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Fügen Sie eine neue Umgebung hinzu, indem Sie sie aus der angegebenen Umgebung kopieren. |
| `teamsfx env list` | Listen Sie alle Umgebungen auf. |

### <a name="scenarios-for-teamsfx-env"></a>Szenarien für `teamsfx env`

Erstellen Sie eine neue Umgebung, indem Sie sie aus der vorhandenen Entwicklungsumgebung kopieren:

```bash
teamsfx env add staging --env dev
```

## `teamsfx provision`

Stellen Sie die Cloudressourcen in der aktuellen Anwendung bereit.

| Befehl `teamsFx provision` | Beschreibung |
|:----------------  |:-------------|
| `teamsfx provision manifest` | Stellen Sie eine Teams-App im Teams Entwicklerportal mit entsprechenden Informationen bereit, die in der angegebenen Manifestdatei angegeben sind. |

### <a name="parameters-for-teamsfx-provision"></a>Parameter für `teamsfx provision`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine Umgebung für das Projekt aus. |
|`--subscription`| Nein | Geben Sie eine Azure-Abonnement-ID an. |
|`--resource-group`| Nein | Legen Sie den Namen einer vorhandenen Ressourcengruppe fest. |
|`--sql-admin-name`| Nein | Anwendbar, wenn SQL Ressource im Projekt vorhanden ist. Administratorname von SQL.|
|`--sql-password`| Nein| Anwendbar, wenn SQL Ressource im Projekt vorhanden ist. Administratorkennwort von SQL.|

## `teamsfx deploy`

Dieser Befehl wird verwendet, um die aktuelle Anwendung bereitzustellen. Standardmäßig wird das gesamte Projekt bereitgestellt, aber es ist auch möglich, es nur teilweise bereitzustellen. Die Optionen sind `frontend-hosting`, `function`, `apim`, `bot`, `spfx``aad-manifest` und `manifest`.

### <a name="parameters-for-teamsfx-deploy"></a>Parameter für `teamsfx deploy`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--open-api-document`| Nein | Anwendbar, wenn im Projekt eine APIM-Ressource vorhanden ist. Der Pfad der geöffneten API-Dokumentdatei. |
|`--api-prefix`| Nein | Anwendbar, wenn im Projekt eine APIM-Ressource vorhanden ist. Das API-Namenspräfix. Der eindeutige Standardname der API ist `{api-prefix}-{resource-suffix}-{api-version}`. |
|`--api-version`| Nein | Anwendbar, wenn im Projekt eine APIM-Ressource vorhanden ist. Die API-Version. |
|`--include-app-manifest`| Nein | Gibt an, ob das App-Manifest auf Teams Plattform bereitgestellt werden soll. Optionen sind `yes` und `not`. Der Standardwert ist `no`. |
|`--include-aad-manifest`| Nein | Gibt an, ob ein aad-Manifest bereitgestellt werden soll. Optionen sind `yes` und `not`. Der Standardwert ist `no`. |

## `teamsfx validate`

Überprüfen Sie die aktuelle Anwendung. Mit diesem Befehl wird die Manifestdatei Ihrer Anwendung überprüft.

### <a name="parameters-for-teamsfx-validate"></a>Parameter für `teamsfx validate`

`--env`: Wählen Sie eine vorhandene Umgebung für das Projekt aus.

## `teamsfx publish`

Veröffentlichen Sie die App in Teams.

### <a name="parameters-for-teamsfx-publish"></a>Parameter für `teamsfx publish`

`--env`: Wählen Sie eine vorhandene Umgebung für das Projekt aus.

## `teamsfx package`

Erstellen Sie Ihre Teams-App in einem Paket für die Veröffentlichung.

## `teamsfx preview`

Zeigen Sie eine Vorschau der aktuellen Anwendung lokal oder remote an.

### <a name="parameters-for-teamsfx-preview"></a>Parameter für `teamsfx preview`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--local`| Nein | Zeigen Sie eine Vorschau der Anwendung lokal an. `--local` und `--remote` schließen sich aus. |
|`--remote`| Nein | Zeigen Sie eine Vorschau der Anwendung remote an. `--remote` und `--local` schließen sich aus. |
|`--env`| Nein | Wählen Sie eine vorhandene Umgebung für das Projekt aus, wenn der Parameter `--remote` angefügt wird. |
|`--folder`| Nein | Stammverzeichnis des Projekts. Der Standardwert ist `./`. |
|`--browser`| Nein | Der Browser zum Öffnen des Teams-Webclients. Die Optionen sind `chrome`, `edge` und `default`, z. B. der Standardbrowser des Systems, und der Wert ist `default`. |
|`--browser-arg`| Nein | Das Argument, das an den Browser übergeben werden soll, erfordert „--browser“ und kann mehrmals verwendet werden, z. B.: --browser-args="--guest". |
|`--sharepoint-site`| Nein | SharePoint-Website-URL, z. B. `{your-tenant-name}.sharepoint.com` für die SPFx-Projektremotevorschau. |
|`--m365-host`| Zeigen Sie eine Vorschau der Anwendung in Teams, Outlook oder Office an. Optionen sind `teams`und `outlook` `office`. Der Standardwert ist `teams`. |

### <a name="scenarios-for-teamsfx-preview"></a>Szenarien für `teamsfx preview`

Die folgende Liste enthält die allgemeinen Szenarien für die Vorschau von TeamsFx:

* Lokale Vorschau

  Abhängigkeiten:

  * Node.js
  * .NET SDK
  * Azure Functions Core Tools

  ```bash
  teamsfx preview --local
  teamsfx preview --local --browser chrome
  ```

* Remotevorschau

  ```bash
  teamsfx preview --remote
  teamsfx preview --remote --browser edge
  ```

  > [!NOTE]
  > Die Protokolle der Hintergrunddienste, z. B. React, werden in `~/.fx/cli-log/local-preview/` gespeichert.

## `teamsfx config`

Die Konfigurationsdaten befinden sich entweder im Benutzerbereich oder im Projektbereich.

|  Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Anzeigen des Konfigurationswerts der Option |
| `teamsfx config set <option> <value>` | Aktualisieren des Konfigurationswerts der Option |

### <a name="parameters-for-teamsfx-config"></a>Parameter für `teamsfx config`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--folder`| Nein | Project Verzeichnis, das zum Abrufen oder Festlegen der Projektkonfiguration verwendet wird. Der Standardwert ist `./`. |
|`--global`| Nein | Bereich der Konfiguration. Bei "true" ist der Bereich auf den Benutzerbereich und nicht auf den Projektbereich beschränkt. Der Standardwert ist `false`. Zu den unterstützten globalen Konfigurationen gehören `telemetry`jetzt , `validate-dotnet-sdk`, `validate-func-core-tools`, `validate-node`. |

### <a name="scenarios-for-teamsfx-config"></a>Szenarien für `teamsfx config`

Die geheimen Schlüssel in der `.userdata` Datei sind verschlüsselt und können Ihnen helfen, `teamsfx config` erforderliche Werte anzuzeigen oder zu aktualisieren.

* Senden von Telemetriedaten beenden

  ```bash
  teamsfx config set telemetry off
  ```

* Deaktivieren der Umgebungsprüfung

  Es gibt drei Konfigurationen zum Aktivieren oder Deaktivieren von Node.js, .NET SDK und Azure Functions Core Tools-Überprüfung, und alle sind standardmäßig aktiviert. Sie können die Konfiguration auf „Aus“ festlegen, wenn Sie die Abhängigkeitsüberprüfung nicht benötigen und die Abhängigkeiten selbst installieren möchten. Überprüfen Sie die folgenden Handbücher:

  * [Node.js-Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)
  * [.NET SDK-Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk)
  * [Azure Functions Installationshandbuch für Kerntools](<https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure>- functions-core-tools).

  Zum Deaktivieren der .NET SDK-Überprüfung können Sie den folgenden Befehl verwenden:

  ```bash
  teamsfx config set validate-dotnet-sdk off
  ```

  Zum Aktivieren der .NET SDK-Überprüfung können Sie den folgenden Befehl verwenden:

  ```bash
  teamsfx config set validate-dotnet-sdk on
  ```

* Anzeigen der gesamten Konfiguration des Benutzerbereichs

  ```bash
  teamsfx config get -g
  ```

* Anzeigen der gesamten Konfiguration im Projekt

  Das Geheimnis wird automatisch entschlüsselt:

    ```bash
    teamsfx config get --env dev
    ```

* Aktualisieren der Geheimniskonfiguration im Projekt

  ```bash
  teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
  ```

## `teamsfx permission`

TeamsFx CLI bietet `teamsFx permission` Befehle für Zusammenarbeitsszenarien.

|  Befehl | Beschreibung |
|:------------------------------|-------------|
| `teamsfx permission grant --env --email` | Erteilen Sie die Berechtigung für das Microsoft 365-Konto des Mitarbeiters für das Projekt einer angegebenen Umgebung. |
| `teamsfx permission status` | Berechtigungsstatus für das Projekt anzeigen |

### <a name="parameters-for-teamsfx-permission-grant"></a>Parameter für `teamsfx permission grant`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Geben Sie den Namen einer Umgebung an. |
|`--email`| Ja | Geben Sie die Microsoft 365-E-Mail-Adresse des Mitarbeiters an. Stellen Sie sicher, dass sich das Konto des Mitarbeiters im selben Mandanten wie der Ersteller befindet. |

### <a name="parameters-for-teamsfx-permission-status"></a>Parameter für `teamsfx permission status`

| Parameter | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Geben Sie den Namen einer Umgebung an. |
|`--list-all-collaborators` | Nein | Mit diesem Flag druckt die Teams-Toolkit-CLI alle Mitarbeiter für dieses Projekt. |

### <a name="scenarios-for-teamsfx-permission"></a>Szenarien für `teamsfx permission`

Die folgende Liste enthält erforderliche Berechtigungen für `TeamsFx` Projekte:

* Erteilen von Berechtigungen

  Projektersteller und Mitarbeiter können den Befehl `teamsfx permission grant` verwenden, um dem Projekt einen neuen Mitarbeiter hinzuzufügen:

  ```bash
  teamsfx permission grant --env dev --email user-email@user-tenant.com
  ```

  Nach erhalt der erforderlichen Berechtigung können Projektersteller und Projektmitarbeiter das Projekt mit dem neuen Mitarbeiter durch GitHub teilen, und der neue Mitarbeiter kann über alle Berechtigungen für Microsoft 365 Konto verfügen.

* Anzeigen des Berechtigungsstatus

  Project Ersteller und Mitarbeiter können den Befehl verwenden`teamsfx permission status`, um Microsoft 365 Kontoberechtigung für bestimmte env anzuzeigen:

  ```bash
  teamsfx permission status --env dev
  ```

* Auflisten aller Mitarbeiter

  Projektersteller und Mitarbeiter können den Befehl `teamsfx permission status` verwenden, um alle Mitarbeiter für eine bestimmte Umgebung anzuzeigen:

  ```bash
  teamsfx permission status --env dev --list-all-collaborators
  ```

* Workflow der E2E-Zusammenarbeit in CLI

  * Als Projektersteller:

    * So erstellen Sie ein neues TeamsFx-Registerkarten- oder -Bot-Projekt und wählen Azure als Hosttyp aus

      ```bash
      teamsfx new --interactive false --app-name newapp --host-type azure
      ```

    * So melden Sie sich bei Microsoft 365- und Azure-Konto an:

      ```bash
      teamsfx account login azure
      teamsfx account login Microsoft 365
      ```

    * So stellen Sie Ihr Projekt bereit

      ```bash
      teamsfx provision
      ```

    * So zeigen Sie Mitarbeiter an

      ```bash
      teamsfx permission status --env dev --list-all-collaborators
      ```

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-status-all-1.png" alt-text="permission-1":::

    * So fügen Sie ein weiteres Konto als Mitarbeiter hinzu. Stellen Sie sicher, dass sich das hinzugefügte Konto unter demselben Mandanten befindet:

      ```bash
      teamsfx permission grant --env dev --email user-email@user-tenant.com
      ```

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-grant-1.png" alt-text="permission":::

    * So übertragen Sie Ihr Projekt auf GitHub

  * Als Projektmitarbeiter:

    * Klonen Sie das Projekt von GitHub.
    * Melden Sie sich bei Microsoft 365 Konto an. Stellen Sie sicher, dass dasselbe Microsoft 365-Konto hinzugefügt wird:

      ```bash
      teamsfx account login Microsoft 365
      ```

    * Melden Sie sich mit der Berechtigung "Mitwirkender" für alle Azure-Ressourcen beim Azure-Konto an.

      ```bash
      teamsfx account login azure
      ```

    * Überprüfen Sie den Berechtigungsstatus. Sie sollten über die Berechtigung „Besitzer“ für das Projekt verfügen:

      ```bash
      teamsfx permission status --env dev
      ```

      ![Berechtigungsstatus](./images/permission-status.png)

    * Aktualisieren Sie den Registerkartencode, und stellen Sie das Projekt remote bereit.
    * Starten Sie remote, und das Projekt sollte einwandfrei funktionieren.

## <a name="see-also"></a>Siehe auch

* [TeamsFx SDK für TypeScript oder JavaScript](TeamsFx-SDK.md)
* [Verwalten mehrerer Umgebungen im Teams-Toolkit](TeamsFx-multi-env.md)
* [Zusammenarbeiten an Teams-Projekten mit dem Teams-Toolkit](TeamsFx-collaboration.md)
* [Übersicht über das Teams-Toolkit](teams-toolkit-fundamentals.md)
