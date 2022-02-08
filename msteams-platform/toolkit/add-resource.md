---
title: Hinzufügen von Ressourcen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt das Hinzufügen von Ressourcen des Teams Toolkits
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 87420b5e2b133de32b8c27a4a8d34a90072a3c76
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435824"
---
# <a name="add-cloud-resources-to-your-teams-app"></a>Hinzufügen von Cloudressourcen zu Ihrer Teams-App

TeamsFx hilft bei der Bereitstellung von Cloudressourcen für Ihr Anwendungshosting. Sie können optional auch Cloudressourcen hinzufügen, die Ihren Entwicklungsanforderungen entsprechen.

## <a name="prerequisite"></a>Voraussetzungen

[Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Sie Teams App-Projekt in Visual Studio Code haben.

## <a name="add-cloud-resources-using-teams-toolkit"></a>Hinzufügen von Cloudressourcen mit Teams Toolkit

> [!IMPORTANT]
> Sie müssen jede Umgebung bereitstellen, nachdem Sie eine Ressource hinzugefügt haben.

1. Öffnen **Sie Microsoft Visual Studio Code**.
1. Wählen Sie im linken Bereich **Teams Toolkit** aus.
1. Wählen Sie im Bereich der Teams Toolkit-Seitenleiste die Option **"Cloudressourcen hinzufügen**" aus:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add cloudresources.png" alt-text="Hinzufügen von Ressourcen":::

   Sie können auch die Befehlspalette öffnen und **Teams: Hinzufügen von Cloudressourcen** eingeben:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addcloud.png" alt-text="Hinzufügen von Cloudressourcen":::

1. Wählen Sie im Popup die Cloudressourcen aus, die Sie Ihrem Teams App-Projekt hinzufügen möchten:

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addresources.png" alt-text="Hinzufügen":::

1. Wählen Sie **OK** aus.

Die ausgewählten Ressourcen werden ihrem Projekt erfolgreich hinzugefügt.

## <a name="add-cloud-resources-using-teamsfx-cli-in-command-window"></a>Hinzufügen von Cloudressourcen mithilfe von TeamsFx CLI im Befehlsfenster

1. Ändern Sie das Verzeichnis in Das **Projektverzeichnis**.
1. Führen Sie den folgenden Befehl aus, um ihrem Projekt unterschiedliche Ressourcen hinzuzufügen:

|Cloud-Ressource|Befehl|
|---------------|----------|
| Azure-Funktion|`teamsfx resource add azure-function --function-name your-func-name`|
| Azure SQL-Datenbank|`teamsfx resource add --function-name your-func-name`|
| Azure-API-Verwaltung|`teamsfx resource add azure-apim`|
| Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Arten von Cloudressourcen

TeamsFx lässt sich in azure-Dienste für die folgenden Szenarien integrieren:

- [Azure-Funktionen](/azure/azure-functions/functions-overview): Eine serverlose Lösung, die Ihre Anforderungen bei Bedarf erfüllt, z. B. das Erstellen von Web-APIs für Ihre Teams-Anwendungs-Back-End.
- [Azure SQL-Datenbank](/azure/azure-sql/database/sql-database-paas-overview): Ein PaaS-Datenbankmodul (Platform as a Service), das als datenspeicher für Ihre Teams Anwendungen dient.
- [Azure-API-Verwaltung](/azure/azure-sql/database/sql-database-paas-overview): Ein API-Gateway, das verwendet werden kann, um APIs zu verwalten, die für Teams Anwendungen erstellt wurden, und diese für andere Anwendungen wie Power-Apps zu veröffentlichen.
- [Azure Key Vault](/azure/key-vault/general/overview): Schützen kryptografischer Schlüssel und anderer geheimer Schlüssel, die von Cloud-Apps und -Diensten verwendet werden.

## <a name="add-cloud-resources"></a>Hinzufügen von Cloudressourcen

Nach dem Hinzufügen einer Ressource sind die Änderungen in Ihrem Projekt wie folgt:

- Azure.parameter können neue Parameter hinzugefügt werden. {env}.json zum Bereitstellen der erforderlichen Informationen für die Bereitstellung.
- Neue Inhalte werden an die ARM-Vorlage unter `templates/azure` Ordner angefügt, mit Ausnahme der Dateien unter `templates/azure/teamsfx` Ordner, um die hinzugefügten Azure-Ressourcen zu erstellen.
- Die Dateien im `templates/azure/teamsfx` Ordner werden neu generiert, um sicherzustellen, dass die erforderliche Konfiguration von TeamsFx für hinzugefügte Azure-Ressourcen auf dem neuesten Stand ist.
- `.fx/projectSettings.json` aktualisiert wird, um die in Ihrem Projekt vorhandenen Ressourcen nachzuverfolgen.

Nach dem Hinzufügen von erneuten Änderungen sind die folgenden zusätzlichen Änderungen in Ihrem Projekt:

|Ressourcen|Änderungen|Beschreibung|
|---------------|---------------|-----------------------------|
|Azure-Funktionen|Ein Vorlagencode für Azure-Funktionen wird einem Unterordner mit Pfad hinzugefügt. `yourProjectFolder/api`</br></br>`launch.json` und `task.json` unter `.visual studio code` Ordner aktualisiert.| Enthält eine HTTP-Triggervorlage "Hello World" in Ihr Projekt.</br></br> Enthält die erforderlichen Skripts, damit Visual Studio Code ausgeführt werden kann, wenn Sie Ihre Anwendung lokal debuggen möchten.|
|Azure-API-Verwaltung|Eine geöffnete API-Spezifikationsdatei, die einem Unterordner mit Pfad hinzugefügt wurde `yourProjectFolder/openapi`|Definiert Ihre API nach der Veröffentlichung, es ist die API-Spezifikationsdatei.|

## <a name="limitation"></a>Einschränkung

Sie können keine Ressourcen hinzufügen, wenn Sie SPFx basierte Registerkartenprojekt erstellt haben.

## <a name="see-also"></a>Siehe auch

[Bereitstellen von Cloudressourcen](provision.md)
