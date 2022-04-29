---
title: TeamsFx-Befehlszeilenschnittstelle
author: MuyangAmigo
description: Beschreibt die TeamsFx-Befehlszeilenschnittstelle
ms.author: zhany
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: ab9bad973d337d783c1de70c2ad8575a67d6cb6e
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111437"
---
# <a name="teamsfx-library"></a>TeamsFx-Bibliothek

Microsoft Teams Framework (TeamsFx) ist eine Bibliothek, die allgemeine Funktionalitäts- und Integrationsmuster (z. B. den vereinfachten Zugriff auf Microsoft Identity) kapselt. Sie können Apps für Microsoft Teams ohne Konfiguration erstellen.

Im Folgenden finden Sie eine Liste der wichtigsten TeamsFx-Features:

* **TeamsFx-Zusammenarbeit**: Ermöglichen Sie es Entwicklern und Projektbesitzern, andere Mitarbeiter zum TeamsFx-Projekt einzuladen. Sie können zusammenarbeiten, um ein TeamsFx-Projekt zu debuggen und bereitzustellen.

* **TeamsFx-CLI**: Sie beschleunigt die Entwicklung von Teams-Anwendungen. Außerdem wird ein CI/CD-Szenario ermöglicht, in dem Sie die CLI zur Automatisierung in Skripts integrieren können.

* **TeamsFx-SDK**: TeamsFx-SDK (Software Development Kit) ist die Hauptcodebibliothek von TeamsFx, die eine einfache Authentifizierung für client- und serverseitigen Code kapselt, der auf Teams-Entwickler zugeschnitten ist.

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
| `teamsfx account`| Verwalten Sie Clouddienstkonten. Die unterstützten Clouddienste sind „Azure“ und „Microsoft 365“. |
| `teamsfx env` | Verwalten Sie Umgebungen. |
| `teamsfx capability`| Fügen Sie der aktuellen Anwendung neue Funktionen hinzu.|
| `teamsfx resource`  | Verwalten Sie die Ressourcen in der aktuellen Anwendung.|
| `teamsfx provision` | Stellen Sie Cloudressourcen in der aktuellen Anwendung bereit.|
| `teamsfx deploy` | Stellen Sie die aktuelle Anwendung bereit.  |
| `teamsfx package` | Erstellen Sie Ihre Teams-App in einem Paket für die Veröffentlichung.|
| `teamsfx validate` | Überprüfen Sie die aktuelle Anwendung.|
| `teamsfx publish` | Veröffentlichen Sie die App in Teams.|
| `teamsfx preview` | Zeigen Sie eine Vorschau der aktuellen Anwendung an. |
| `teamsfx config`  | Verwalten Sie die Konfigurationsdaten. |
| `teamsfx permission`| Arbeiten Sie mit anderen Entwicklern im selben Projekt zusammen.|

## `teamsfx new`

Standardmäßig wechselt `teamsfx new` in den interaktiven Modus und führt Sie durch den Prozess der Erstellung einer neuen Teams-Anwendung. Sie können auch im nicht interaktiven Modus arbeiten, indem Sie das Flag `--interactive` auf `false`festlegen.

| Befehl `teamsFx new` | Beschreibung |
|:----------------  |:-------------|
| `teamsfx new template <template-name>`     | Erstellen einer App aus einer vorhandenen Vorlage |
| `teamsfx new template list`     | Auflisten aller verfügbaren Vorlagen |

### <a name="parameters-for-teamsfx-new"></a>Parameter für `teamsfx new`

| Parameter | Anforderung | Beschreibung |
|:---------------- |:-------------|:-------------|
|`--app-name` | Ja| Name Ihrer Teams-Anwendung.|
|`--interactive`| Nein | Wählen Sie die Optionen interaktiv aus. Die Optionen sind `true` und `false`, und der Standardwert ist `true`.|
|`--capabilities`| Nein| Wählen Sie Teams-Anwendungsfunktionen aus. Die verschiedenen Optionen sind `tab`, `bot`, `messaging-extension` und `tab-spfx`. Der Standardwert ist `tab`.|
|`--programming-language`| Nein| Programmiersprache für das Projekt. Die Optionen sind `javascript` oder `typescript`, und der Standardwert ist `javascript`.|
|`--folder`| Nein | Projektverzeichnis. Unter diesem Verzeichnis wird ein Unterordner mit Ihrem App-Namen erstellt. Der Standardwert ist `./`.|
|`--spfx-framework-type`| Nein| Gilt, wenn die Funktion `Tab(SPfx)` ausgewählt ist. Front-End-Framework. Die Optionen sind `none` und `react`, und der Standardwert ist `none`.|
|`--spfx-web part-name`| Nein | Gilt, wenn die Funktion `Tab(SPfx)` ausgewählt ist. Der Standardwert ist „helloworld“.|
|`--spfx-web part-desp`| Nein | Gilt, wenn die Funktion `Tab(SPfx)` ausgewählt ist. Der Standardwert ist „helloworld description“. |
|`--azure-resources`| Nein| Gilt, wenn die Funktion `tab` enthalten ist. Fügen Sie Azure-Ressourcen zu Ihrem Projekt hinzu. Die verschiedenen Optionen sind `sql` (Azure SQL-Datenbank) und `function` (Azure Functions). |

### <a name="scenarios-for-teamsfx-new"></a>Szenarien für `teamsfx new`

Sie können den interaktiven Modus verwenden, um eine Teams-App zu erstellen. Die Szenarien zum Steuern aller Parameter mit `teamsfx new` lauten wie folgt:

#### <a name="tab-app-hosted-on-spfx-using-react"></a>Registerkarten-App, die auf SPFx mithilfe von React gehostet wird

```bash
teamsfx new --interactive false --app-name newspfxapp --capabilities tab-spfx --spfx-framework-type react
```

#### <a name="teams-app-in-javascript-with-tab-bot-capabilities-and-azure-functions"></a>Teams-App in JavaScript mit Registerkarten- und Bot-Funktionen sowie Azure Functions

```bash
teamsfx new --interactive false --app-name newtabbotapp --capabilities tab bot --programming-language javascript --azure-resources function
```

#### <a name="teams-tab-app-with-azure-functions-and-azure-sql"></a>Teams-Registerkarten-App mit Azure Functions und Azure SQL

```bash
teamsfx new --interactive false app-name newapp --azure-resources sql function --programming-language typescript
```

## `teamsfx account`

Verwalten Sie Clouddienstkonten. Die unterstützten Clouddienste sind `Azure` und `Microsoft 365`.

| Befehl `teamsFx account` | Beschreibung |
|:----------------  |:-------------|
| `teamsfx account login <service>`  | Melden Sie sich beim ausgewählten Clouddienst an. |
| `teamsfx account logout <service>`  | Melden Sie sich beim ausgewählten Clouddienst ab. |
| `teamsfx account set --subscription` | Aktualisieren Sie die Kontoeinstellungen, um eine Abonnement-ID festzulegen. |

## `teamsfx env`

Verwalten Sie die Umgebungen.

| Befehl `teamsfx env`  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx env add <new_env_name> --env <existing_env_name>` | Fügen Sie eine neue Umgebung hinzu, indem Sie sie aus der angegebenen Umgebung kopieren. |
| `teamsfx env list` | Listen Sie alle Umgebungen auf. |

### <a name="scenarios-for-teamsfx-env"></a>Szenarien für `teamsfx env`

Die Szenarien für `teamsfx env` lauten wie folgt:

#### <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Fügen Sie eine neue Umgebung hinzu, indem Sie sie aus der vorhandenen Entwicklungsumgebung kopieren:

```bash
teamsfx env add staging --env dev
```

## `teamsfx capability`

Fügen Sie der aktuellen Anwendung neue Funktionen hinzu.

| Befehl `teamsFx capability`  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx capability add tab` | Registerkarte hinzufügen |
| `teamsfx capability add bot` | Bot hinzufügen |
| `teamsfx capability add messaging-extension`| Nachrichtenerweiterung hinzufügen |

> [!NOTE]
> Wenn Ihr Projekt einen Bot enthält, kann die Nachrichtenerweiterung nicht hinzugefügt werden, und dies gilt auch umgekehrt. Sie können sowohl Bot- als auch Nachrichtenerweiterungen in Ihr Projekt einschließen, während Sie ein neues Teams-App-Projekt erstellen.

## `teamsfx resource`

Verwalten Sie die Ressourcen in der aktuellen Anwendung. Als `<resource-type>` wird Folgendes unterstützt: `azure-sql`, `azure-function` und `azure-apim`.

| Befehl `teamsFx resource`  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx resource add <resource-type>`      | Fügen Sie der aktuellen Anwendung eine Ressource hinzu.|
| `teamsfx resource show <resource-type>`      | Zeigen Sie die Konfigurationsdetails der Ressource an. |
| `teamsfx resource list`      | Listen Sie alle Ressourcen in der aktuellen Anwendung auf. |

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
> Der Funktionsname wird als SQL verifiziert und muss über die Serverworkload aufgerufen werden. Wenn Ihr Projekt keine `Azure Functions` enthält, erstellen Sie sich eine.

### <a name="parameters-for-teamsfx-resource-add-azure-apim"></a>Parameter für `teamsfx resource add azure-apim`

> [!TIP]
> Die Optionen werden wirksam, wenn Sie versuchen, eine vorhandene `APIM`-Instanz zu verwenden. Standardmäßig müssen Sie keine Optionen angeben, und während des Schritts `teamsfx provision` wird eine neue Instanz erstellt.

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--subscription`| Ja | Azure-Abonnement auswählen|
|`--apim-resource-group`| Ja| Der Name der Ressourcengruppe. |
|`--apim-service-name`| Ja | Der Name der API-Verwaltungsdienstinstanz. |
|`--function-name`| Ja | Geben Sie einen Funktionsnamen an. Der Standardwert ist `getuserprofile`. |

> [!NOTE]
> `Azure API Management` muss mit `Azure Functions`arbeiten. Wenn Ihr Projekt keine `Azure Functions` enthält, können Sie eine erstellen.

## `teamsfx provision`

Stellen Sie die Cloudressourcen in der aktuellen Anwendung bereit.

### <a name="parameters-for-teamsfx-provision"></a>Parameter für `teamsfx provision`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine Umgebung für das Projekt aus. |
|`--subscription`| Nein | Geben Sie eine Azure-Abonnement-ID an. |
|`--resource-group`| Nein | Legen Sie den Namen einer vorhandenen Ressourcengruppe fest. |
|`--sql-admin-name`| Nein | Gilt, wenn das Projekt eine SQL-Ressource enthält. Administratorname von SQL.|
|`--sql-password`| Nein| Gilt, wenn das Projekt eine SQL-Ressource enthält. Administratorkennwort von SQL.|

## `teamsfx deploy`

Dieser Befehl wird verwendet, um die aktuelle Anwendung bereitzustellen. Standardmäßig wird das gesamte Projekt bereitgestellt, aber es ist auch möglich, es nur teilweise bereitzustellen. Die verschiedenen Optionen sind `frontend-hosting`, `function`, `apim`, `teamsbot` und `spfx`.

### <a name="parameters-for-teamsfx-deploy"></a>Parameter für `teamsfx deploy`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja| Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--open-api-document`| Nein | Gilt, wenn das Projekt eine APIM-Ressource enthält. Der Pfad der geöffneten API-Dokumentdatei. |
|`--api-prefix`| Nein | Gilt, wenn das Projekt eine APIM-Ressource enthält. Das API-Namenspräfix. Der eindeutige Standardname der API ist `{api-prefix}-{resource-suffix}-{api-version}`. |
|`--api-version`| Nein | Gilt, wenn das Projekt eine APIM-Ressource enthält. Die API-Version. |

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

### <a name="scenarios-for-teamsfx-preview"></a>Szenarien für `teamsfx preview`

#### <a name="local-preview"></a>Lokale Vorschau

Abhängigkeiten:

* Node.js
* .NET SDK
* Azure Functions Core Tools

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
> Die Protokolle der Hintergrunddienste, z. B. React, werden in `~/.fx/cli-log/local-preview/` gespeichert.

## `teamsfx config`

Verwalten Sie die Konfigurationsdaten entweder im Benutzerbereich oder im Projektbereich.

| Befehl `teamsfx config`  | Beschreibung |
|:----------------  |:-------------|
| `teamsfx config get [option]` | Anzeigen des Konfigurationswerts der Option |
| `teamsfx config set <option> <value>` | Aktualisieren des Konfigurationswerts der Option |

### <a name="parameters-for-teamsfx-config"></a>Parameter für `teamsfx config`

| Parameter  | Anforderung | Beschreibung |
|:----------------  |:-------------|:-------------|
|`--env`| Ja | Wählen Sie eine vorhandene Umgebung für das Projekt aus. |
|`--folder`| Nein | Projektverzeichnis. Es wird zum Abrufen oder Festlegen der Projektkonfiguration verwendet. Der Standardwert ist `./`. |
|`--global`| Nein | Bereich der Konfiguration. Bei „true“ ist der Bereich auf den Benutzerbereich statt auf den Projektbereich beschränkt. Der Standardwert ist `false`. Derzeit sind die unterstützten globalen Konfigurationen `telemetry`, `validate-dotnet-sdk`, `validate-func-core-tools`, `validate-node`. |

### <a name="scenerios-for-teamsfx-config"></a>Szenarien für `teamsfx config`

Geheimnisse in der `.userdata`-Datei werden verschlüsselt, `teamsfx config` kann Ihnen helfen, die Werte anzuzeigen oder zu aktualisieren.

#### <a name="stop-sending-telemetry-data"></a>Senden von Telemetriedaten beenden

```bash
teamsfx config set telemetry off
```

#### <a name="disable-environment-checker"></a>Deaktivieren der Umgebungsprüfung

Es gibt drei Konfigurationen zum Aktivieren oder Deaktivieren der Überprüfung von Node.js, .NET SDK und Azure Functions Core Tools, und alle sind standardmäßig aktiviert. Sie können die Konfiguration auf „Aus“ festlegen, wenn Sie die Abhängigkeitsüberprüfung nicht benötigen und die Abhängigkeiten selbst installieren möchten. Überprüfen Sie die folgenden Handbücher:

* [Node.js-Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-nodejs)
* [.NET SDK-Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-net-sdk)
* [Azure Functions Core Tools-Installationshandbuch](https://github.com/OfficeDev/TeamsFx/blob/dev/docs/vscode-extension/envchecker-help.md#how-to-install-azure-functions-core-tools)

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

Das Geheimnis wird automatisch entschlüsselt:

```bash
teamsfx config get --env dev
```

#### <a name="update-the-secret-configuration-in-project"></a>Aktualisieren der Geheimniskonfiguration im Projekt

```bash
teamsfx config set fx-resource-aad-app-for-teams.clientSecret xxx --env dev
```

## `teamsfx permission`

Die TeamsFx-CLI bietet `teamsFx permission`-Befehle für das Szenario für die Zusammenarbeit.

| Befehl `teamsFx permission` | Beschreibung |
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

Die Berechtigungen für `TeamsFx`-Projekte lauten wie folgt:

#### <a name="grant-permission"></a>Erteilen von Berechtigungen

Projektersteller und Mitarbeiter können den Befehl `teamsfx permission grant` verwenden, um dem Projekt einen neuen Mitarbeiter hinzuzufügen:

```bash
teamsfx permission grant --env dev --email user-email@user-tenant.com
```

Nachdem sie die erforderliche Berechtigung erhalten haben, können Projektersteller und Mitarbeiter das Projekt für die neuen Mitarbeiter über GitHub freigeben, und der neue Mitarbeiter verfügt über alle Berechtigungen für das Microsoft 365-Konto.

#### <a name="show-permission-status"></a>Anzeigen des Berechtigungsstatus

Projektersteller und Mitarbeiter können den Befehl `teamsfx permission status` verwenden, um Microsoft 365-Kontoberechtigungen für eine bestimmte Umgebung anzuzeigen:

```bash
teamsfx permission status --env dev
```

#### <a name="list-all-collaborators"></a>Auflisten aller Mitarbeiter

Projektersteller und Mitarbeiter können den Befehl `teamsfx permission status` verwenden, um alle Mitarbeiter für eine bestimmte Umgebung anzuzeigen:

```bash
teamsfx permission status --env dev --list-all-collaborators
```

#### <a name="e2e-collaboration-work-flow-in-cli"></a>Workflow der E2E-Zusammenarbeit in CLI

Als Projektersteller:

* So erstellen Sie ein neues TeamsFx-Registerkarten- oder -Bot-Projekt und wählen Azure als Hosttyp aus

  ```bash
  teamsfx new --interactive false --app-name newapp --host-type azure
  ```

* So melden Sie sich beim Microsoft 365- und Azure-Konto an

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

Als Projektmitarbeiter:

* Klonen Sie das Projekt von GitHub.
* Melden Sie sich beim Microsoft 365-Konto an. Stellen Sie sicher, dass dasselbe Microsoft 365-Konto hinzugefügt wird:

  ```bash
  teamsfx account login Microsoft 365
  ```

* Melden Sie sich beim Azure-Konto mit der Berechtigung „Mitwirkender“ für alle Azure-Ressourcen an.

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
