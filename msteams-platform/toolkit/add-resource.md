---
title: Hinzufügen von Ressourcen zu Ihren Teams-Apps
author: MuyangAmigo
description: Beschreibt das Hinzufügen von Ressourcen des Teams-Toolkits.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 50cd3de693f70fd0c8414408bd6f4e6d3332d544
ms.sourcegitcommit: 430bf416bb8d1b74f926c8b5d5ffd3dbb0782286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2022
ms.locfileid: "65297205"
---
# <a name="add-cloud-resources-to-your-teams-app"></a>Hinzufügen von Cloudressourcen zur Teams-App

TeamsFx hilft bei der Bereitstellung von Cloud-Ressourcen für das Hosting Ihrer Anwendungen. Sie können auch optional Cloud-Ressourcen hinzufügen, die Ihren Entwicklungsanforderungen entsprechen.

## <a name="prerequisite"></a>Voraussetzungen

[Installieren des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Sie Teams app Projekt in Visual Studio Code haben.

## <a name="add-cloud-resources-using-teams-toolkit"></a>Cloud-Ressourcen mit Teams Toolkit hinzufügen

> [!IMPORTANT]
> Sie müssen jede Umgebung bereitstellen, nachdem Sie eine Ressource hinzugefügt haben.

1. Öffnen Sie **Visual Studio Code.**
1. Wählen Sie im linken Bereich **Teams** aus.
1. Wählen Sie im Leistenbereich Teams Toolkit die Option **"Cloudressourcen hinzufügen" aus**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/add cloudresources.png" alt-text="Fügen Sie Ressourcen hinzu.":::

   Sie können auch die Befehlspalette öffnen und **Teams eingeben: Hinzufügen von Cloudressourcen**:

    :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addcloud.png" alt-text="Fügen Sie Cloud-Ressourcen hinzu":::

1. Wählen Sie im Popup die Cloudressourcen aus, die Sie Ihrem Teams App-Projekt hinzufügen möchten:

     :::image type="content" source="../assets/images/teams-toolkit-v2/manual/addresources.png" alt-text="Hinzufügen":::

1. Wählen Sie **OK** aus.

Die ausgewählten Ressourcen wurden ihrem Projekt erfolgreich hinzugefügt.

## <a name="add-cloud-resources-using-teamsfx-cli-in-command-window"></a>Cloud-Ressourcen mit TeamsFx CLI im Befehlsfenster hinzufügen

1. Wechseln Sie in das Verzeichnis für **Ihr Projekt**.
1. Führen Sie den folgenden Befehl aus, um verschiedene Ressourcen zu Ihrem Projekt hinzuzufügen:

|Cloudressource|Befehl|
|---------------|----------|
| Azure-Funktion|`teamsfx resource add azure-function --function-name your-func-name`|
| Azure SQL-Datenbank|`teamsfx resource add --function-name your-func-name`|
| Azure-API-Verwaltung|`teamsfx resource add azure-apim`|
| Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Arten von Cloudressourcen

TeamsFx kann für die folgenden Szenarien in Azure-Dienste integriert werden:

- [Azure-Funktionen](/azure/azure-functions/functions-overview): Eine serverlose Lösung, die Ihre On-Demand-Anforderungen erfüllt, z. B. die Erstellung von Web-APIs für das Backend Ihrer Teams-Anwendungen.
- [Azure SQL-Datenbank](/azure/azure-sql/database/sql-database-paas-overview): Eine Plattform-as-a-Service (PaaS) Datenbank-Engine, die als Datenspeicher für Ihre Teams-Anwendungen dient.
- [Azure-API-Verwaltung](deploy.md): Ein API-Gateway, das zur Verwaltung von APIs verwendet werden kann, die für Teams-Anwendungen erstellt wurden, und sie zur Nutzung in anderen Anwendungen, wie z. B. Power Apps, veröffentlicht.
- [Azure Key Vault](/azure/key-vault/general/overview): Sichern Sie kryptografische Schlüssel und andere Geheimnisse, die von Cloud-Anwendungen und -Diensten verwendet werden.

## <a name="add-cloud-resources"></a>Cloud-Ressourcen hinzufügen

Nachdem Sie eine Ressource hinzugefügt haben, sehen die Änderungen in Ihrem Projekt wie folgt aus:

- Neue Parameter können zu azure.parameter.{env}.json hinzugefügt werden, um die für die Bereitstellung erforderlichen Informationen bereitzustellen.
- Neue Inhalte werden an die ARM-Vorlage im `templates/azure`Ordner angehängt, mit Ausnahme der Dateien im `templates/azure/teamsfx`Ordner, um die hinzugefügten Azure-Ressourcen zu erstellen.
- Die Dateien unter dem `templates/azure/teamsfx`Ordner werden neu generiert, um sicherzustellen, dass die für TeamsFx erforderliche Konfiguration für hinzugefügte Azure-Ressourcen auf dem neuesten Stand ist.
- `.fx/projectSettings.json`wird aktualisiert, um die in Ihrem Projekt vorhandenen Ressourcen zu verfolgen.

Nach dem Hinzufügen von Ressourcen sind die zusätzlichen Änderungen in Ihrem Projekt wie folgt:

|Ressourcen|Änderungen|Beschreibung|
|---------------|---------------|-----------------------------|
|Azure-Funktionen|Ein Vorlagencode für Azure-Funktionen wird einem Unterordner mit Pfad hinzugefügt.`yourProjectFolder/api`</br></br>`launch.json` und `task.json` unter `.visual studio code` Ordner aktualisiert.| Fügt eine Hallo Welt http-Trigger-Vorlage in Ihr Projekt ein.</br></br> Enthält die notwendigen Skripte für Visual Studio Code, die ausgeführt werden, wenn Sie Ihre Anwendung lokal debuggen möchten.|
|Azure-API-Verwaltung|Eine geöffnete API-Spezifikationsdatei, die einem Unterordner mit pfad `yourProjectFolder/openapi`|Definiert Ihre API nach der Veröffentlichung, es ist die API-Spezifikationsdatei.|

## <a name="limitation"></a>Einschränkung

Sie können keine Ressourcen hinzufügen, wenn Sie ein SPFx-basiertes Registerkartenprojekt erstellt haben.

## <a name="see-also"></a>Siehe auch

[Bereitstellen von Cloudressourcen](provision.md)
