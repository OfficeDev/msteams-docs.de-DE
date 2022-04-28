---
title: TeamsFx-Befehlszeilenschnittstelle
author: MuyangAmigo
description: Beschreibt die TeamsFx-Befehlszeilenschnittstelle
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 5fde7e94c198bfe76810a52ede78d0be7270ba0c
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104518"
---
# <a name="teamsfx-library"></a>TeamsFx-Bibliothek

Microsoft Teams Framework (TeamsFx) ist eine Bibliothek, die allgemeine Funktionalitäts- und Integrationsmuster (z. B. den vereinfachten Zugriff auf Microsoft Identity) kapselt. Sie können Apps für Microsoft Teams mit Nullkonfiguration erstellen.

Hier ist eine Liste der wichtigsten TeamsFx-Features:

* **TeamsFx-Zusammenarbeit**: Entwicklern und Projektbesitzern erlauben, andere Mitarbeiter zum TeamsFx-Projekt einzuladen. Sie können zusammenarbeiten, um ein TeamsFx-Projekt zu debuggen und bereitzustellen.

* **TeamsFx CLI**: Es beschleunigt Teams Anwendungsentwicklung. Es ermöglicht auch CI/CD-Szenario, in dem Sie CLI in Skripts für die Automatisierung integrieren können.

* **TeamsFx SDK**: TeamsFx Software Development Kit (SDK) ist die Hauptcodebibliothek von TeamsFx, die die einfache Authentifizierung sowohl für clientseitigen als auch für serverseitigen Code kapselt, der auf Teams Entwickler zugeschnitten ist.

## <a name="teamsfx-command-line-interface"></a>TeamsFx-Befehlszeilenschnittstelle

TeamsFx CLI ist eine textbasierte Befehlszeilenschnittstelle, die Teams Anwendungsentwicklung beschleunigt. Es zielt darauf ab, tastaturzentrierte Erfahrung beim Erstellen Teams Anwendungen bereitzustellen. Es ermöglicht auch CI/CD-Szenario, in dem Sie CLI in Skripts für die Automatisierung integrieren können.

Weitere Informationen finden Sie unter:

* [Quellcode](https://github.com/OfficeDev/TeamsFx/tree/dev/packages/cli)
* [Paket (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx-cli)

## <a name="get-started"></a>Erste Schritte

Installieren Von `teamsfx-cli` `npm` und Ausführen `teamsfx -h` , um alle verfügbaren Befehle zu überprüfen:

```bash
  npm install -g @microsoft/teamsfx-cli
  teamsfx -h
```

## <a name="supported-commands"></a>Unterstützte Befehle

| Befehl | Beschreibung |
|----------------|-------------|
| `teamsfx new`| Erstellen Sie eine neue Teams Anwendung.|
| `teamsfx account`| Verwalten von Clouddienstkonten. Die unterstützten Clouddienste sind "Azure" und "Microsoft 365". |
| `teamsfx env` | Verwalten von Umgebungen. |
| `teamsfx capability`| Fügen Sie der aktuellen Anwendung neue Funktionen hinzu.|
| `teamsfx resource`  | Verwalten Sie die Ressourcen in der aktuellen Anwendung.|
| `teamsfx provision` | Bereitstellen von Cloudressourcen in der aktuellen Anwendung.|
| `teamsfx deploy` | Stellen Sie die aktuelle Anwendung bereit.  |
| `teamsfx package` | Erstellen Sie Ihre Teams-App in ein Paket für die Veröffentlichung.|
| `teamsfx validate` | Überprüfen Sie die aktuelle Anwendung.|
| `teamsfx publish` | Veröffentlichen Sie die App in Teams.|
| `teamsfx preview` | Zeigen Sie eine Vorschau der aktuellen Anwendung an. |
| `teamsfx config`  | Verwalten Sie die Konfigurationsdaten. |
| `teamsfx permission`| Arbeiten Sie mit anderen Entwicklern im selben Projekt zusammen.|

## `teamsfx new`

`teamsfx new` Standardmäßig wechselt er in den interaktiven Modus und führt Sie durch den Prozess der Erstellung einer neuen Teams Anwendung. Sie können auch mit dem nicht interaktiven Modus arbeiten, indem Sie die Kennzeichnung auf `false`festlegen`--interactive`.

| `teamsFx new` Befehl | Beschreibung |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Erstellen einer App aus einer vorhandenen Vorlage |
| `teamsfx new template list`     | Auflisten aller verfügbaren Vorlagen |

### <a name="parameters-for-teamsfx-new"></a>Parameter für `teamsfx new`

| Parameter | Anforderung | Beschreibung |
|:---------------- |:-------------|:-------------|
|`--app-name` | Ja| Name der Teams Anwendung.|
|`--interactive`| Nein | Wählen Sie die Optionen interaktiv aus. Die Optionen sind `true` und `false` der Standardwert ist `true`.|
|`--capabilities`| Nein| Wählen Sie Teams Anwendungsfunktionen aus. Die verschiedenen Optionen sind `tab`, `bot``messaging-extension` und `tab-spfx`. Der Standardwert ist `tab`.|
|`--programming-language`| Nein| Programmiersprache für das Projekt. Die Optionen sind `javascript` oder `typescript` und der Standardwert ist `javascript`.|
|`--folder`| Nein | Project Verzeichnis. Unter diesem Verzeichnis wird ein Unterordner mit Ihrem App-Namen erstellt. Der Standardwert ist `./`.|
|`--spfx-framework-type`| Nein| Anwendbar, wenn `Tab(SPfx)` die Funktion ausgewählt ist. Frontend Framework. Die Optionen sind `none` und `react`, und der Standardwert ist `none`.|
|`--spfx-web part-name`| Nein | Anwendbar, wenn `Tab(SPfx)` die Funktion ausgewählt ist. Der Standardwert ist "helloworld".|
|`--spfx-web part-desp`| Nein | Anwendbar, wenn `Tab(SPfx)` die Funktion ausgewählt ist. Der Standardwert ist "helloworld description". |
|`--azure-resources`| Nein| Anwendbar, wenn die Funktion enthalten `tab` ist. Fügen Sie Azure-Ressourcen zu Ihrem Projekt hinzu. Die verschiedenen Optionen sind `sql` (Azure SQL-Datenbank) und `function` (Azure Functions). |

### <a name="scenarios-for-teamsfx-new"></a>Szenarien für `teamsfx new`

Sie können den interaktiven Modus verwenden, um eine Teams-App zu erstellen. Die Szenarien zum Steuern aller Parameter lauten `teamsfx new` wie folgt:

#### <a name="tab-app-hosted-on-spfx-using-react"></a>Registerkarten-App, die auf SPFx mithilfe von React gehostet wird

```bash
teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
```

#### <a name="teams-app-in-javascript-with-tab-bot-capabilities-and-azure-functions"></a>Teams-App in JavaScript mit Registerkarten-, Bot-Funktionen und Azure Functions

```bash
teamsfx new --interactive false --app-name newtabbotapp --capabilities tab bot --programming-language javascript --azure-resources function
```

#### <a name="teams-tab-app-with-azure-functions-and-azure-sql"></a>Teams Registerkarten-App mit Azure Functions und Azure SQL

```bash
teamsfx new --interactive false app-name newapp --azure-resources sql function --programming-language typescript
```

## `teamsfx account`

Verwalten von Clouddienstkonten. Die unterstützten Clouddienste sind `Azure` und `Microsoft 365`.

| `teamsFx account` Befehl | Beschreibung |
|:----------------  |:-------------|
| `teamsfx account login <service>`  | Melden Sie sich beim ausgewählten Clouddienst an. |
| `teamsfx account logout <service>`  | melden Sie sich beim ausgewählten Clouddienst ab. |
| `teamsfx account set --subscription` | Aktualisieren Sie die Kontoeinstellungen, um eine Abonnement-ID festzulegen. |

## `teamsfx env`

Verwalten Sie die Umgebungen.

| `teamsfx env` Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Fügen Sie eine neue Umgebung hinzu, indem Sie sie aus der angegebenen Umgebung kopieren. |
| `teamsfx env list` | Alle Umgebungen auflisten. |

### <a name="scenarios-for-teamsfx-env"></a>Szenarien für `teamsfx env`

Die Szenarien sind `teamsfx env` wie folgt:

#### <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Fügen Sie eine neue Umgebung hinzu, indem Sie aus der vorhandenen Entwicklungsumgebung kopieren:

```bash
teamsfx env add staging --env dev
```

## `teamsfx capability`

Fügen Sie der aktuellen Anwendung neue Funktionen hinzu.

| `teamsFx capability` Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx capability add tab` | Registerkarte hinzufügen |
| `teamsfx capability add bot` | Bot hinzufügen |
| `teamsfx capability add messaging-extension`| Hinzufügen der MessagE-Erweiterung |

> [!NOTE]
> Wenn Ihr Projekt einen Bot enthält, kann die Nachrichtenerweiterung nicht hinzugefügt werden und gilt umgekehrt. Sie können sowohl Bot- als auch Nachrichtenerweiterungen in Ihr Projekt einbeziehen, während Sie ein neues Teams App-Projekt erstellen.

## `teamsfx resource`

Verwalten Sie die Ressourcen in der aktuellen Anwendung. Unterstützt `<resource-type>` werden: `azure-sql`und `azure-function` `azure-apim` .

| `teamsFx resource` Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx resource add <resource-type>`      | Fügen Sie der aktuellen Anwendung Eine Ressource hinzu.|
| `teamsfx resource show <resource-type>`      | Zeigt Konfigurationsdetails der Ressource an. |
| `teamsfx resource list`      | Listet alle Ressourcen in der aktuellen Anwendung auf. |

### <a name="parameters-for-teamsfx-resource-add-azure-function"></a>Parameter für `teamsfx resource add azure-function`

| Parameter  | Anforderung | Beschreibung |
|----------------  |-------------|-------------|
|`--function-name`| Ja | Geben Sie einen Funktionsnamen an. Der Standardwert ist `getuserprofile`. |

### <a name="parameters-for-teamsfx-resource-add-azure-sql"></a>Parameter für `teamsfx resource add azure-sql`

#### `--function-name`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--function-name`| Ja | Geben Sie einen Funktionsnamen an. Der Standardwert ist `getuserprofile`. |

> [!NOTE]
> Der Funktionsname wird als SQL überprüft und muss über die Serverarbeitsauslastung aufgerufen werden. Wenn Ihr Projekt nicht enthalten `Azure Functions`ist, erstellen Sie eine für Sie.

### <a name="parameters-for-teamsfx-resource-add-azure-apim"></a>Parameter für `teamsfx resource add azure-apim`

> [!TIP]
> Die Optionen werden wirksam, wenn Sie versuchen, eine vorhandene `APIM` Instanz zu verwenden. Standardmäßig müssen Sie keine Optionen angeben, und es wird während des `teamsfx provision` Schritts eine neue Instanz erstellt.

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--subscription`| Ja | Auswählen eines Azure-Abonnements|
|`--apim-resource-group`| Ja| Der Name der Ressourcengruppe. |
|`--apim-service-name`| Ja | Der Name der API-Verwaltungsdienstinstanz. |
|`--function-name`| Ja | Geben Sie einen Funktionsnamen an. Der Standardwert ist `getuserprofile`. |

> [!NOTE]
> `Azure API Management` muss mit `Azure Functions`arbeiten. Wenn Ihr Projekt nicht enthalten `Azure Functions`ist, können Sie eines erstellen.

## `teamsfx provision`

Stellen Sie die Cloudressourcen in der aktuellen Anwendung bereit.

### <a name="parameters-for-teamsfx-provision"></a>Parameter für `teamsfx provision`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine Umgebung für das Projekt aus. |
|`--subscription`| Nein | Geben Sie eine Azure-Abonnement-ID an. |
|`--resource-group`| Nein | Legen Sie den Namen einer vorhandenen Ressourcengruppe fest. |
|`--sql-admin-name`| Nein | Anwendbar, wenn SQL Ressource im Projekt vorhanden ist. Administratorname der SQL.|
|`--sql-password`| Nein| Anwendbar, wenn SQL Ressource im Projekt vorhanden ist. Administratorkennwort von SQL.|

## `teamsfx deploy`

Dieser Befehl wird verwendet, um die aktuelle Anwendung bereitzustellen. Standardmäßig wird das gesamte Projekt bereitgestellt, aber es ist auch möglich, die Bereitstellung teilweise durchzuführen. Die mehreren Optionen sind `frontend-hosting`, `function`, `apim`, `teamsbot`und `spfx`.

### <a name="parameters-for-teamsfx-deploy"></a>Parameter für `teamsfx deploy`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--open-api-document`| Nein | Anwendbar, wenn im Projekt EINE APIM-Ressource vorhanden ist. Der Pfad der geöffneten API-Dokumentdatei. |
|`--api-prefix`| Nein | Anwendbar, wenn im Projekt EINE APIM-Ressource vorhanden ist. Das API-Namenspräfix. Der eindeutige Standardname der API ist `{api-prefix}-{resource-suffix}-{api-version}`. |
|`--api-version`| Nein | Anwendbar, wenn im Projekt EINE APIM-Ressource vorhanden ist. Die API-Version. |

## `teamsfx validate`

Überprüfen sie die aktuelle Anwendung. Mit diesem Befehl wird die Manifestdatei Ihrer Anwendung überprüft.

### <a name="parameters-for-teamsfx-validate"></a>Parameter für `teamsfx validate`

`--env`: Wählen Sie eine vorhandene Umgebung für das Projekt aus.

## `teamsfx publish`

Veröffentlichen Sie die App in Teams.

### <a name="parameters-for-teamsfx-publish"></a>Parameter für `teamsfx publish`

`--env`: Wählen Sie eine vorhandene Umgebung für das Projekt aus.

## `teamsfx package`

Erstellen Sie Ihre Teams-App in einem Paket für die Veröffentlichung.

## `teamsfx preview`

Zeigen Sie eine Vorschau der aktuellen Anwendung von lokal oder remote an.

### <a name="parameters-for-teamsfx-preview"></a>Parameter für `teamsfx preview`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--local`| Nein | Zeigen Sie eine Vorschau der Anwendung aus der lokalen Umgebung an. `--local` ist exklusiv mit `--remote`. |
|`--remote`| Nein | Zeigen Sie eine Vorschau der Anwendung von remote an. `--remote` ist exklusiv mit `--local`. |
|`--env`| Nein | Wählen Sie eine vorhandene Umgebung für das Projekt aus, wenn der Parameter `--remote` angefügt wird. |
|`--folder`| Nein | Project Stammverzeichnis. Der Standardwert ist `./`. |
|`--browser`| Nein | Der Browser zum Öffnen Teams Webclients. Die Optionen sind `chrome`, `edge` `default` wie z. B. der Systemstandardbrowser, und der Wert lautet `default`. |
|`--browser-arg`| Nein | Argument, das an den Browser übergeben werden soll, erfordert --browser, kann mehrmals verwendet werden, z. B. --browser-args="--guest" |
|`--sharepoint-site`| Nein | SharePoint Website-URL, z`{your-tenant-name}.sharepoint.com`. B. für SPFx Projekt-Remotevorschau. |

### <a name="scenarios-for-teamsfx-preview"></a>Szenarien für `teamsfx preview`

#### <a name="local-preview"></a>Lokale Vorschau

Abhängigkeiten:

* Node.js
* .NET SDK
* Azure Functions Kerntools

```bash
teamsfx preview --local
teamsfx preview --local --browser chrome
```

#### <a name="remote-preview"></a>Remotevorschau

```bash
teamsfx preview --remote
teamsfx preview --remote --browser edge
```

> [!NOTE]
> Die Protokolle der Hintergrunddienste, z. B. React, werden in `~/.fx/cli-log/local-preview/`gespeichert.

## `teamsfx config`

Verwalten Sie die Konfigurationsdaten entweder im Benutzerbereich oder im Projektbereich.

| `teamsfx config` Befehl  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Anzeigen des Konfigurationswerts der Option |
| `teamsfx config set <option> <value>` | Aktualisieren des Konfigurationswerts der Option |

### <a name="parameters-for-teamsfx-config"></a>Parameter für `teamsfx config`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--folder`| Nein | Project Verzeichnis. Dies wird zum Abrufen oder Festlegen der Projektkonfiguration verwendet. Der Standardwert ist `./`. |
|`--global`| Nein | Bewältigung der Konfiguration. Wenn dies zutrifft, ist der Bereich auf den Benutzerbereich und nicht auf den Projektbereich beschränkt. Der Standardwert ist `false`. Derzeit umfassen `telemetry`die unterstützten globalen Konfigurationen , `validate-dotnet-sdk`, `validate-func-core-tools`, `validate-node`. |

### <a name="scenerios-for-teamsfx-config"></a>Scenerios für `teamsfx config`

Geheime Schlüssel in `.userdata` der Datei sind verschlüsselt und können Ihnen helfen, `teamsfx config` die Werte anzuzeigen oder zu aktualisieren.

#### <a name="stop-sending-telemetry-data"></a>Senden von Telemetriedaten beenden

```bash
teamsfx config set telemetry off
```

#### <a name="disable-environment-checker"></a>Deaktivieren der Umgebungsprüfung

Es gibt drei Konfigurationen zum Aktivieren oder Deaktivieren Node.js, .NET SDK und Azure Functions Core Tools-Überprüfung, und alle sind standardmäßig aktiviert. Sie können die Konfiguration auf "aus" festlegen, wenn Sie die Abhängigkeitsüberprüfung nicht benötigen und die Abhängigkeiten selbst installieren möchten. Überprüfen Sie die folgenden Leitfäden:

* [Node.js Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)
* [Installationshandbuch für .NET SDK](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk)
* [Azure Functions Installationshandbuch für Core Tools](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure-functions-core-tools).

Zum Deaktivieren der .NET SDK-Überprüfung können Sie den folgenden Befehl verwenden:

```bash
teamsfx config set validate-dotnet-sdk off
```

Zum Aktivieren der .NET SDK-Überprüfung können Sie den folgenden Befehl verwenden:

```bash
teamsfx config set validate-dotnet-sdk on
```

#### <a name="view-all-the-user-scope-configuration"></a>Anzeigen der gesamten Konfiguration des Benutzerbereichs

```bash
teamsfx config get -g
```

#### <a name="view-all-the-configuration-in-project"></a>Anzeigen der gesamten Konfiguration im Projekt

Der geheime Schlüssel wird automatisch entschlüsselt:

```bash
teamsfx config get --env dev
```

#### <a name="update-the-secret-configuration-in-project"></a>Aktualisieren der geheimen Konfiguration im Projekt

```bash
teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
```

## `teamsfx permission`

TeamsFx CLI stellt `teamsFx permission` Befehle für das Szenario der Zusammenarbeit bereit.

| `teamsFx permission` Befehl | Beschreibung |
|:------------------------------|-------------|
| `teamsfx permission grant --env --email` | Erteilen Sie die Berechtigung für das Microsoft 365 Konto des Mitarbeiters für das Projekt einer angegebenen Umgebung. |
| `teamsfx permission status` | Berechtigungsstatus für das Projekt anzeigen |

### <a name="parameters-for-teamsfx-permission-grant"></a>Parameter für `teamsfx permission grant`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Geben Sie env-Namen an. |
|`--email`| Ja | Geben Sie die Microsoft 365 E-Mail-Adresse des Mitarbeiters an. Stellen Sie sicher, dass sich das Konto des Mitarbeiters im selben Mandanten mit dem Ersteller befindet. |

### <a name="parameters-for-teamsfx-permission-status"></a>Parameter für `teamsfx permission status`

| Parameter | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Geben Sie env-Namen an. |
|`--list-all-collaborators` | Nein | Mit diesem Flag druckt Teams Toolkit CLI alle Mitarbeiter für dieses Projekt. |

### <a name="scenarios-for-teamsfx-permission"></a>Szenarien für `teamsfx permission`

Die Berechtigungen für `TeamsFx` Projekte lauten wie folgt:

#### <a name="grant-permission"></a>Berechtigung erteilen

Project Ersteller und Mitarbeiter können den Befehl verwenden`teamsfx permission grant`, um dem Projekt einen neuen Mitarbeiter hinzuzufügen:

```bash
teamsfx permission grant --env dev --email user-email@user-tenant.com
```

Nach erhalt der erforderlichen Berechtigung können Projektersteller und Projektmitarbeiter das Projekt mit dem neuen Mitarbeiter durch GitHub teilen, und der neue Mitarbeiter kann über alle Berechtigungen für Microsoft 365 Konto verfügen.

#### <a name="show-permission-status"></a>Berechtigungsstatus anzeigen

Project Ersteller und Mitarbeiter können den Befehl verwenden`teamsfx permission status`, um seine Microsoft 365 Kontoberechtigung für bestimmte env anzuzeigen:

```bash
teamsfx permission status --env dev
```

#### <a name="list-all-collaborators"></a>Alle Mitarbeiter auflisten

Project Ersteller und Mitarbeiter können den Befehl verwenden`teamsfx permission status`, um alle Mitarbeiter für bestimmte env anzuzeigen:

```bash
teamsfx permission status --env dev --list-all-collaborators
```

#### <a name="e2e-collaboration-work-flow-in-cli"></a>E2E-Zusammenarbeits-Arbeitsablauf in CLI

Als Projektersteller:

* So erstellen Sie ein neues TeamsFx-Registerkarten- oder Botprojekt, und wählen Sie Azure als Hosttyp aus:

  ```bash
  teamsfx new --interactive false --app-name newapp --host-type azure
  ```

* So melden Sie sich bei Microsoft 365- und Azure-Konto an:

  ```bash
  teamsfx account login azure
  teamsfx account login Microsoft 365
  ```

* So stellen Sie Ihr Projekt bereit:

  ```bash
  teamsfx provision
  ```

* So zeigen Sie Mitarbeiter an:

  ```bash
  teamsfx permission status --env dev --list-all-collaborators
  ```

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-status-all-1.png" alt-text="permission-1":::

* So fügen Sie ein weiteres Konto als Mitarbeiter hinzu. Stellen Sie sicher, dass sich das hinzugefügte Konto unter demselben Mandanten befindet:

  ```bash
  teamsfx permission grant --env dev --email user-email@user-tenant.com
  ```

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/permission-grant-1.png" alt-text="permission":::

* So schieben Sie Ihr Projekt an GitHub

Als Project Mitarbeiter:

* Klonen Sie das Projekt aus GitHub.
* Melden Sie sich bei Microsoft 365 Konto an. Stellen Sie sicher, dass dasselbe Microsoft 365 Konto hinzugefügt wird:

  ```bash
  teamsfx account login Microsoft 365
  ```

* Melden Sie sich beim Azure-Konto mit der Berechtigung "Mitwirkender" für alle Azure-Ressourcen an.

  ```bash
  teamsfx account login azure
  ```

* Überprüfen Sie den Berechtigungsstatus. Sie sollten über die Berechtigung "Besitzer" des Projekts verfügen:

  ```bash
  teamsfx permission status --env dev
  ```

  ![Berechtigungsstatus](./images/permission-status.png)

* Aktualisieren Sie den Tabulatorcode, und stellen Sie das Projekt remote bereit.
* Starten Sie remote, und das Projekt sollte einwandfrei funktionieren.

## <a name="see-also"></a>Siehe auch

* [TeamsFx SDK für TypeScript oder JavaScript](TeamsFx-SDK.md)
* [Verwalten mehrerer Umgebungen im Teams-Toolkit](TeamsFx-multi-env.md)
* [Zusammenarbeiten an Teams Projekt mit Teams Toolkit](TeamsFx-collaboration.md)
* [Übersicht über das Teams-Toolkit](teams-toolkit-fundamentals.md)
