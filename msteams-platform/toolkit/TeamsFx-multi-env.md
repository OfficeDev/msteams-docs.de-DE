---
title: TeamsFX mehrere Umgebungen in Teams Toolkit
author: MuyangAmigo
description: Informationen zu TeamsFX-Multiumgebungen
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 27172617db35126fb086d8691486e86c2946f0bd
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453586"
---
# <a name="manage-multiple-environments-in-teams-toolkit"></a>Verwalten mehrerer Umgebungen in Teams Toolkit

 Teams Toolkit bietet Ihnen eine einfache Möglichkeit zum Erstellen und Verwalten mehrerer Umgebungen, zum Bereitstellen und Bereitstellen von Artefakten in der Zielumgebung für Teams App.

 Mit mehreren Umgebungen können Sie Folgendes ausführen:

1. **Testen vor der Produktion**: Es ist üblich, mehrere Umgebungen wie Entwicklungs-, Test- und Stagingumgebungen einzurichten, bevor sie eine Teams App in der Produktionsumgebung im modernen App-Entwicklungslebenszyklus veröffentlichen.

2. **Verwalten des App-Verhaltens in verschiedenen Umgebungen**: Sie können unterschiedliche Verhaltensweisen für mehrere Umgebungen festlegen, z. B. Telemetrie in der Produktionsumgebung aktivieren, aber in der Entwicklungsumgebung deaktivieren.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Microsoft Visual Studio Code geöffnet ist.

## <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Nach dem Erstellen eines neuen Projekts erstellt Teams Toolkit standardmäßig Folgendes:

* Eine `local` Umgebung, die die Konfigurationen der lokalen Computerumgebung darstellt.
* Eine `dev` Umgebung, die die Konfigurationen der Remote- oder Cloudumgebung darstellt.

> [!NOTE]
> Jedes Projekt kann nur eine `local` Umgebung, aber mehrere Remoteumgebungen haben.

Um eine weitere Remoteumgebung hinzuzufügen, wählen Sie das symbol Teams in der Randleiste aus, und wählen Sie im Abschnitt "Umgebung" die Option "Neue Umgebung erstellen" aus, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="create":::

> [!NOTE]
> Wenn Sie über mehrere vorhandene Umgebungen verfügen, müssen Sie eine vorhandene Umgebung auswählen, um dieselbe zu erstellen. Der Befehl kopiert den Dateiinhalt der `config.<newEnv>.json` ausgewählten und `azure.parameters.<newEnv>.json` aus der vorhandenen Umgebung in die neue Umgebung, die erstellt wird.

## <a name="select-target-environment"></a>Auswählen der Zielumgebung

Sie können die Zielumgebung für alle umgebungsbezogenen Vorgänge auswählen. Das Toolkit fordert eine Zielumgebung an und fordert sie auf, wenn Sie über mehrere Remoteumgebungen verfügen, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="project-folder-structure"></a>Project Ordnerstruktur

Nach dem Erstellen des Projekts können Sie die Projektordner und -dateien im Explorer-Bereich von Visual Studio Code anzeigen. Neben den benutzerdefinierten Codes werden einige Dateien von Teams Toolkit verwendet, um die Konfiguration, den Status und die Vorlage der App zu verwalten. Die folgende Liste enthält Dateien und beschreibt deren Beziehung mit mehreren Umgebungen.

* `.fx/configs`: Konfigurieren von Dateien, die der Benutzer für die Teams-App anpassen kann.
  * `config.<envName>.json`: Konfigurationsdatei pro Umgebung.
  * `azure.parameters.<envName>.json`: Parameterdatei pro Umgebung für die Azure-Biicep-Bereitstellung.
  * `projectSettings.json`: Globale Projekteinstellungen, die für alle Umgebungen gelten.
  * `localSettings.json`: Lokale Debugkonfigurationsdatei.
* `.fx/states`: Bereitstellungsergebnis, das vom Toolkit generiert wird.
  * `state.<envName>.json`: Bereitstellungsdatei pro Umgebung.
  * `<env>.userdata`: Pro Umgebung vertrauliche Benutzerdaten für die Bereitstellungsausgabe.
* `templates`
  * `appPackage`: App-Manifestvorlagendateien.
  * `azure`: Bicep-Vorlagendateien.

## <a name="customize-the-provision"></a>Anpassen der Bereitstellung

Teams Toolkit ermöglicht es Ihnen, die Konfigurationsdateien und Vorlagendateien so zu ändern, dass die Ressourcenbereitstellung in jeder Umgebung angepasst wird.

In der folgenden Tabelle sind die allgemeinen Szenarien aufgeführt, die für die angepasste Bereitstellung unterstützt werden, und die Möglichkeiten zum Anpassen:

| Szenarien | Standort| Beschreibung |
| --- | --- | --- |
| Anpassen der Azure-Ressource | <ul> <li>Bicep-Dateien unter `templates/azure`.</li> <li>`.fx/azure.parameters.<envName>.json`.</li></ul> | [Passen Sie ARM-Parameter und -Vorlagen an](provision.md#customize-arm-parameters-and-templates). |
| Wiederverwenden vorhandener Azure AD-App für Teams-App | <ul> <li>`auth` abschnitt in`.fx/config.<envName>.json`.</li> </ul> |  [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](provision.md#use-an-existing-azure-ad-app-for-your-teams-app). |
| Wiederverwenden vorhandener Azure AD-App für Bot | <ul> <li>`bot` abschnitt in`.fx/config.<envName>.json`.</li> </ul> | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](provision.md#use-an-existing-azure-ad-app-for-your-bot). |
| Überspringen des Hinzufügens von Benutzern während der Bereitstellung SQL | <ul> <li>`skipAddingSqlUser` -Eigenschaft in`.fx/config.<envName>.json`.</li> </ul> | [Überspringen Sie das Hinzufügen von Benutzern für SQL Datenbank](provision.md#skip-adding-user-for-sql-database). |
| Anpassen des App-Manifests | <ul> <li>`templates/manifest.remote.template.json`.</li> <li>`manifest` abschnitt in`.fx/config.<envName>.json`.</li>  </ul> | [Passen Sie Teams App-Manifest im Teams Toolkit an](TeamsFx-manifest-customization.md). |

## <a name="scenarios"></a>Szenarien

### <a name="scenario-1-customize-teams-app-name-for-different-environment"></a>Szenario 1: Anpassen Teams App-Namens für eine andere Umgebung

Sie können den Teams App-Namen `myapp(dev)` für die Standardumgebung `dev` und `myapp(staging)` für die Stagingumgebung `staging`festlegen.

Führen Sie die folgenden Schritte zur Anpassung aus:

* 1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
* 2. Aktualisieren Sie die Eigenschaft des *Manifests > appName > kurz* auf `myapp(dev)`

  Die updates to `.fx/configs/config.dev.json` are as follows:

  ```json
  {
      "$schema": "https://aka.ms/teamsfx-env-config-schema",
      "description": "You can customize the TeamsFx config for different environments.   Visit https://aka.ms/teamsfx-env-config to learn more about this.",
      "manifest": {
          "appName": {
              "short": "myapp(dev)"
              ...
          }
      }
      ...
  }
  ```

* 3. Erstellen Sie eine neue Umgebung, und nennen Sie sie `staging` , wenn sie nicht vorhanden ist.
* 4. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.staging.json`.
* 5. Aktualisieren Sie dieselbe Eigenschaft `myapp(staging)`.
* 6. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter ["Bereitstellung](provision.md#provision-using-teams-toolkit)".

### <a name="scenario-2-customize-teams-app-description-for-different-environment"></a>Szenario 2: Anpassen Teams App-Beschreibung für verschiedene Umgebungen

In diesem Szenario erfahren Sie, wie Sie verschiedene Teams App-Beschreibung für verschiedene Umgebungen festlegen:

* Für die Standardumgebung `dev`lautet `my app description for dev`die Beschreibung ;
* Für die Stagingumgebung `staging`lautet `my app description for staging`die Beschreibung ;

Führen Sie die folgenden Schritte zur Anpassung aus:

* 1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
* 2. Fügen Sie neue Eigenschaft des *Manifests > Beschreibung > kurz* mit Wert `my app description for dev`hinzu.

  Die updates to `.fx/configs/config.dev.json` are as follows:

  ```json
  {
      "$schema": "https://aka.ms/teamsfx-env-config-schema",
      "description": "You can customize the TeamsFx config for different environments.   Visit https://aka.ms/teamsfx-env-config to learn more about this.",
      "manifest": {
          ...
          "description": {
              "short": "`my app description for dev"
              ...
          }
      }
      ...
  }
  ```

* 3. Erstellen Sie eine neue Umgebung, und nennen Sie sie `staging` , wenn sie nicht vorhanden ist.
* 4. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.staging.json`.
* 5. Fügen Sie die gleiche Eigenschaft zu `my app description for staging`.
* 6. Öffnen Sie Teams App-Manifestvorlage für Remote.`templates/appPackage/manifest.remote.template.json`
* 7. Aktualisieren Sie die Eigenschaft `description > short` so, dass sie die **Variable** verwendet, die in der Konfiguration von Dateien mit Musttax-Syntax `{{config.manifest.description.short}}`definiert ist.
  
  Die updates to `manifest.remote.template.json` are as follows:

  ```json
  {
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    ...
    "description": {
      "short": "{{config.manifest.description.short}}", 
      ...
    },
    ...
  }
  ```

* 8. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter ["Bereitstellung](provision.md#provision-using-teams-toolkit)".

### <a name="scenario-3-customize-teams-app-description-for-all-environments"></a>Szenario 3: Anpassen Teams App-Beschreibung für alle Umgebungen

In diesem Szenario erfahren Sie, wie Sie die Beschreibung der Teams App `my app description` für alle Umgebungen festlegen.

Da die Teams App-Manifestvorlage in allen Umgebungen gemeinsam verwendet wird, können wir den darin enthaltenen Beschreibungswert für unser Ziel aktualisieren:

* 1. Öffnen Sie Teams App-Manifestvorlage für Remote.`templates/appPackage/manifest.remote.template.json`
* 2. Aktualisieren Sie die Eigenschaft `description > short` mit **einer hartcodierten Zeichenfolge**`my app description`.
  
  Die updates to `manifest.remote.template.json` are as follows:

  ```json
  {
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    ...
    "description": {
      "short": "my app description",
      ...
    },
    ...
  }

* 3. Run provision command against **all** environment to update the app name in remote environments. To run provision command with Teams Toolkit, see [provision](provision.md#provision-using-teams-toolkit).

### Scenario 4: customize Azure resources for different environment

You can customize Azure resources for each environment, for example specify Azure Function name, by editing the environment corresponding to `.fx/configs/azure.parameters.{env}.json` file.

For more information on Bicep template and parameter files, see [provision cloud resources](provision.md)

## See also

* [Provision cloud resources](provision.md)
* [Add more cloud resources](add-resource.md)
* [Collaborate with other developers on Teams project](TeamsFx-collaboration.md)
