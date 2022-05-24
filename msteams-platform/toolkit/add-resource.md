---
title: Hinzufügen von Ressourcen zu Teams-Apps
author: MuyangAmigo
description: Beschreibt das Hinzufügen von Ressourcen des Teams-Toolkits.
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 27e46454658bdc95e5baf5e7453fd50b1b92f03f
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654799"
---
# <a name="add-cloud-resources-to-teams-app"></a>Hinzufügen von Cloudressourcen zur Teams-App

TeamsFx hilft bei der Bereitstellung der Cloudressourcen für Ihr Anwendungshosting. Sie können die Cloudressourcen optional hinzufügen, die Ihren Entwicklungsanforderungen entsprechen.

## <a name="advantages"></a>Vorteile

Die folgende Liste bietet Vorteile zum Hinzufügen weiterer Cloudressourcen in TeamsFx:

* Bietet Komfort
* Generiert automatisch alle Konfigurationsdateien und stellt mithilfe des Teams Toolkits eine Verbindung mit Teams App her

## <a name="limitation"></a>Einschränkung

Wenn Sie SPFx-basiertes Registerkartenprojekt erstellt haben, können Sie keine Azure-Cloudressourcen hinzufügen.

## <a name="add-cloud-resources"></a>Fügen Sie Cloud-Ressourcen hinzu

**Sie können Cloudressourcen mit den folgenden Methoden hinzufügen:**

* So fügen Sie Cloudressourcen mithilfe des Teams Toolkits in Visual Studio Code hinzu
* So fügen Sie Cloudressourcen mithilfe der Befehlspalette hinzu

  > [!NOTE]
  > Sie müssen für jede Umgebung bereitstellen, nachdem Sie die Ressource erfolgreich in Ihrer Teams-App hinzugefügt haben.
  
* **So fügen Sie Cloudressourcen mithilfe des Teams Toolkits in Visual Studio Code hinzu:**

   1. Öffnen Sie **Visual Studio Code**.
   1. Wählen Sie im linken Bereich **Teams Toolkit** aus.
   1. Wählen Sie unter **"ENTWICKLUNG****" die Option "Features hinzufügen"** aus.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/select-feature-updated.png" alt-text="Feature hinzufügen" border="true":::

* **So fügen Sie Cloudressourcen mithilfe der Befehlspalette hinzu:**

   1. Öffnen Sie **die Befehlspalette**.
   1. Geben Sie **Teams:Features hinzufügen ein**.
   1. Drücken Sie **EINGABE**.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/Teams-add-features.png" alt-text="Cloud" border="true":::

   1. Wählen Sie im Popup die Cloudressourcen aus, die In Ihrem Projekt hinzugefügt werden sollen.

        :::image type="content" source="~/assets/images/teams-toolkit-v2/manual/cloud/updated-final-cloud.png" alt-text="Finale" border="true":::

## <a name="add-cloud-resources-using-teamsfx-cli"></a>Hinzufügen von Cloudressourcen mithilfe von TeamsFx CLI

* Wechseln Sie in das Verzeichnis für **Ihr Projekt**.
* In der folgenden Tabelle sind die Funktionen und erforderlichen Befehle aufgeführt:

  |Cloudressource|Befehl|
  |---------------|----------|
  | Azure-Funktion|`teamsfx add azure-function`|
  | Azure SQL-Datenbank|`teamsfx add azure-sql`|
  | Azure-API-Verwaltung|`teamsfx resource add azure-apim`|
  | Azure Key Vault|`teamsfx resource add azure-keyvault`|

## <a name="types-of-cloud-resources"></a>Arten von Cloudressourcen

In den folgenden Szenarien lässt sich TeamsFx in Azure-Dienste integrieren:

- [Azure-Funktionen](/azure/azure-functions/functions-overview): Eine serverlose Lösung, die Ihre On-Demand-Anforderungen erfüllt, z. B. die Erstellung von Web-APIs für das Backend Ihrer Teams-Anwendungen.
- [Azure SQL-Datenbank](/azure/azure-sql/database/sql-database-paas-overview): Eine Plattform-as-a-Service (PaaS) Datenbank-Engine, die als Datenspeicher für Ihre Teams-Anwendungen dient.
- [Azure-API-Verwaltung](deploy.md): Ein API-Gateway kann verwendet werden, um APIs zu verwalten, die für Teams-Anwendungen erstellt wurden, und sie für andere Anwendungen wie Power-Apps zu veröffentlichen.
- [Azure Key Vault](/azure/key-vault/general/overview): Sichern Sie kryptografische Schlüssel und andere Geheimnisse, die von Cloud-Anwendungen und -Diensten verwendet werden.

## <a name="add-cloud-resources"></a>Cloud-Ressourcen hinzufügen

Die folgenden Änderungen werden nach dem Hinzufügen von Ressourcen in Ihrem Projekt angezeigt:

- Neue Parameter, die azure.parameter hinzugefügt wurden. {env}.json, um erforderliche Informationen für die Bereitstellung bereitzustellen.
- Neue Inhalte sind in der ARM-Vorlage enthalten `templates/azure`, mit der Ausnahme, dass sich die Dateien im `templates/azure/teamsfx` Ordner zum Hinzufügen der Azure-Ressourcen befinden.
- Die Dateien unter dem `templates/azure/teamsfx`Ordner werden neu generiert, um sicherzustellen, dass die für TeamsFx erforderliche Konfiguration für hinzugefügte Azure-Ressourcen auf dem neuesten Stand ist.
- `.fx/projectSettings.json` wird aktualisiert, um die verfügbaren Ressourcen in Ihrem Projekt nachzuverfolgen.

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