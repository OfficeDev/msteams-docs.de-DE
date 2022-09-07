---
title: Hinzufügen von Ressourcen zu Teams-Apps
author: MuyangAmigo
description: In diesem Modul erfahren Sie, wie Sie Ressourcen des Teams-Toolkits, Vorteile, Einschränkungen und Funktionen hinzufügen.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: fc58610802a51af19efc32e579566fbf5e36feca
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616534"
---
# <a name="add-cloud-resources-to-microsoft-teams-app"></a>Hinzufügen von Cloudressourcen zur Microsoft Teams-App

Das Teams-Toolkit hilft Ihnen bei der Bereitstellung der Cloudressourcen für Ihr Anwendungshosting. Sie können die Cloudressourcen optional hinzufügen, die Ihren Entwicklungsanforderungen entsprechen. Der Vorteil des Hinzufügens weiterer Cloudressourcen in TeamsFx besteht darin, dass Sie alle Konfigurationsdateien automatisch generieren und mithilfe des Teams-Toolkits eine Verbindung mit der Teams-App herstellen können.

> [!NOTE]
> Wenn Sie ein SPFx-basiertes Registerkartenprojekt erstellt haben, können Sie keine Azure-Cloudressourcen hinzufügen.

## <a name="add-cloud-resources"></a>Fügen Sie Cloud-Ressourcen hinzu

Sie können Cloudressourcen mit den folgenden Methoden hinzufügen:

### <a name="to-add-cloud-resources-by-using-teams-toolkit-in-visual-studio-code"></a>So fügen Sie Cloudressourcen mithilfe des Teams-Toolkits in Visual Studio Code hinzu

   1. Öffnen Sie **Visual Studio Code**.
   1. Wählen Sie in der Aktivitätsleiste das **Teams-Toolkit** aus.
   1. Wählen Sie unter **"ENTWICKLUNG****" die Option "Features hinzufügen"** aus.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/select-feature-updated.png" alt-text="Hinzufügen eines Features aus dem Teams-Toolkit":::

### <a name="to-add-cloud-resources-by-using-command-palette"></a>So fügen Sie Cloudressourcen mithilfe der Befehlspalette hinzu

   1. Wählen Sie **"****Ansichtsbefehlspalette** > ... oder **STRG+UMSCHALT+P**" aus.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features.png" alt-text="Hinzufügen eines Features aus der Befehlspalette":::

   1. Geben Sie **Teams ein: Fügen Sie Features hinzu**.
   1. Drücken Sie **EINGABE**.

      :::image type="content" source="../assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features1.png" alt-text="Geben Sie &quot;Feature hinzufügen&quot; ein, und geben Sie":::

   1. Wählen Sie im Popup die **Cloudressourcen** aus, die Sie in Ihrem Projekt hinzufügen möchten.

      :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/updated-final-cloud.png" alt-text="Finale":::

  > [!NOTE]
  > Sie müssen die Bereitstellung für jede Umgebung durchführen, nachdem Sie die Ressource erfolgreich in Ihrer Teams-App hinzugefügt haben.

### <a name="add-cloud-resources-using-teamsfx-cli"></a>Hinzufügen von Cloudressourcen mithilfe von TeamsFx CLI

* Wechseln Sie in das Verzeichnis für **Ihr Projekt**.
* In der folgenden Tabelle sind die Funktionen und erforderlichen Befehle aufgeführt:

  |Cloudressource|Befehl|
  |---------------|----------|
  | Azure-Funktion|`teamsfx add azure-function`|
  | Azure SQL-Datenbank|`teamsfx add azure-sql`|
  | Azure-API-Verwaltung|`teamsfx add azure-apim`|
  | Azure Key Vault|`teamsfx add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Arten von Cloudressourcen

In den folgenden Szenarien lässt sich TeamsFx in Azure-Dienste integrieren:

* [Azure-Funktionen](/azure/azure-functions/functions-overview): Eine serverlose Lösung, die Ihre On-Demand-Anforderungen erfüllt, z. B. die Erstellung von Web-APIs für das Backend Ihrer Teams-Anwendungen.
* [Azure SQL-Datenbank](/azure/azure-sql/database/sql-database-paas-overview): Eine Plattform-as-a-Service (PaaS) Datenbank-Engine, die als Datenspeicher für Ihre Teams-Anwendungen dient.
* [Azure-API-Verwaltung](deploy.md): Ein API-Gateway kann verwendet werden, um APIs zu verwalten, die für Teams-Anwendungen erstellt wurden, und sie für die Nutzung in anderen Anwendungen wie Power-Apps zu veröffentlichen.
* [Azure Key Vault](/azure/key-vault/general/overview): Sichern Sie kryptografische Schlüssel und andere Geheimnisse, die von Cloud-Anwendungen und -Diensten verwendet werden.

## <a name="changes-after-adding-cloud-resources"></a>Änderungen nach dem Hinzufügen von Cloudressourcen

Die folgenden Änderungen werden nach dem Hinzufügen von Ressourcen in Ihrem Projekt angezeigt:

* Neue Parameter, die azure.parameter hinzugefügt wurden. {env}.json, um erforderliche Informationen für die Bereitstellung bereitzustellen.
* Neue Inhalte sind in der ARM-Vorlage enthalten `templates/azure`, mit der Ausnahme, dass sich die Dateien im `templates/azure/teamsfx` Ordner zum Hinzufügen der Azure-Ressourcen befinden.
* Die Dateien unter dem `templates/azure/teamsfx`Ordner werden neu generiert, um sicherzustellen, dass die für TeamsFx erforderliche Konfiguration für hinzugefügte Azure-Ressourcen auf dem neuesten Stand ist.
* `.fx/projectSettings.json` wird aktualisiert, um die verfügbaren Ressourcen in Ihrem Projekt nachzuverfolgen.

Die folgenden zusätzlichen Änderungen werden nach dem Hinzufügen von Ressourcen in Ihrem Projekt angezeigt:

|Ressourcen|Änderungen|Beschreibung|
|---------------|---------------|-----------------------------|
|Azure-Funktionen|Ein Vorlagencode für Azure-Funktionen wird einem Unterordner mit Pfad hinzugefügt.`yourProjectFolder/api`</br></br>`launch.json` und `task.json` unter `.visual studio code` Ordner aktualisiert.| Fügt eine Hallo Welt http-Trigger-Vorlage in Ihr Projekt ein.</br></br> Enthält die notwendigen Skripte für Visual Studio Code, die ausgeführt werden, wenn Sie Ihre Anwendung lokal debuggen möchten.|
|Azure-API-Verwaltung|Eine geöffnete API-Spezifikationsdatei, die einem Unterordner mit pfad `yourProjectFolder/openapi`|Definiert Ihre API nach der Veröffentlichung, es ist die API-Spezifikationsdatei.|

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Erstellen einer neuen Teams-App](create-new-project.md)
* [Hinzufügen von Funktionen zu Teams-Apps](add-capability.md)
* [Bereitstellen in die Cloud](deploy.md)
