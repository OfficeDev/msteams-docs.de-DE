---
title: TeamsFX mehrere Umgebungen im Teams Toolkit
author: MuyangAmigo
description: Informationen zu TeamsFX-Multiumgebungen
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 0e53d90dd6ead30200dd1f07ba9a100a3d1f4ca1
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61228069"
---
# <a name="manage-multiple-environments-in-teams-toolkit"></a>Verwalten mehrerer Umgebungen in Teams Toolkit

 Teams Toolkit bietet Entwicklern eine einfache Möglichkeit zum Erstellen und Verwalten mehrerer Umgebungen, zum Bereitstellen und Bereitstellen von Artefakten in der Zielumgebung für Teams App.

 Mit mehreren Umgebungen können Entwickler:

1. **Testen vor der Produktion:** Es ist üblich, mehrere Umgebungen (Entwicklung, Test, Staging) einzurichten, bevor eine Teams App in der Produktionsumgebung im modernen App-Entwicklungslebenszyklus veröffentlicht wird.

2. **Verwalten des App-Verhaltens in verschiedenen Umgebungen:** Entwickler können unterschiedliche Verhaltensweisen für unterschiedliche Umgebungen festlegen, z. B. entwickler möchten Telemetrie in der Produktionsumgebung aktivieren, aber in der Entwicklungsumgebung deaktivieren.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

>[!TIP]
> Sie sollten bereits ein Teams App-Projekt in VS-Code geöffnet haben.

## <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Nach dem Erstellen eines neuen Projekts erstellt Teams Toolkit standardmäßig Folgendes:

- Eine `local` Umgebung, die die Konfigurationen der lokalen Computerumgebung darstellt.
- Eine `dev` Umgebung, die die Konfigurationen der Remote-/Cloudumgebung darstellt.

> [!NOTE]
> Jedes Projekt kann nur eine `local` Umgebung, aber mehrere Remoteumgebungen haben.

Um eine weitere Remoteumgebung hinzuzufügen, wählen Sie das symbol Teams in der Randleiste aus, klicken Sie auf die Plus-Schaltfläche im Abschnitt "Umgebung", und folgen Sie den Fragen, die Sie erstellen möchten, wie in der folgenden Abbildung dargestellt:

![add-env](./images/create-env.png)

> [!NOTE]
> Wenn Sie über mehrere vorhandene Umgebungen verfügen, müssen Sie eine vorhandene Umgebung auswählen, um die Umgebung zu erstellen. Der Befehl kopiert den Dateiinhalt der `config.<newEnv>.json` ausgewählten und aus der vorhandenen Umgebung in die neue `azure.parameters.<newEnv>.json` Umgebung, die erstellt wird.

## <a name="select-target-environment"></a>Auswählen der Zielumgebung 

Mit dem in Teams Toolkit eingeführten Umgebungskonzept können Sie für alle umgebungsbezogenen Vorgänge die Zielumgebung auswählen, für die die Vorgänge ausgeführt werden sollen. Das Toolkit fordert eine Zielumgebung an und fordert sie an, wenn Sie über mehrere Remoteumgebungen verfügen, wie in der folgenden Abbildung dargestellt:

![env auswählen](./images/select-env.png)

## <a name="project-folder-structure"></a>Project Ordnerstruktur 

Nach dem Erstellen des Projekts können Sie die Projektordner und -dateien im Explorer-Bereich von Visual Studio Code anzeigen. Neben den benutzerdefinierten Codes werden einige Dateien von Teams Toolkit verwendet, um die Konfiguration, den Status und die Vorlage der App zu verwalten. Im Folgenden werden diese Dateien aufgeführt und ihre Beziehung zu mehreren Umgebungen beschrieben.

- `.fx/configs`: Konfigurationsdateien, die der Benutzer für die Teams-App anpassen kann.
  - `config.<envName>.json`: Konfigurationsdatei pro Umgebung.
  - `azure.parameters.<envName>.json`: Parameterdatei pro Umgebung für die Azure BICEP-Bereitstellung.
  - `projectSettings.json`: Globale Projekteinstellungen, die für alle Umgebungen gelten.
  - `localSettings.json`: Lokale Debugkonfigurationsdatei.
- `.fx/states`: Bereitstellungsergebnis, das vom Toolkit generiert wird.
  - `state.<envName>.json`: Bereitstellungsdatei pro Umgebung.
  - `<env>.userdata`: Pro Umgebung vertrauliche Benutzerdaten für die Bereitstellungsausgabe.
- `templates`
  - `appPackage`: App-Manifestvorlagendateien.
  - `azure`: BICEP-Vorlagendateien.

## <a name="customize-the-provision"></a>Anpassen der Bereitstellung 

Teams Toolkit ermöglicht es Ihnen, die Konfigurationsdateien und Vorlagendateien so zu ändern, dass die Ressourcenbereitstellung in jeder Umgebung angepasst wird.

In der folgenden Tabelle sind die allgemeinen Szenarien aufgeführt, die für die angepasste Bereitstellung unterstützt werden, und wo sie angepasst werden müssen:

| Szenarien | Anpassen | Anpassen |
| --- | --- | --- |
| Anpassen der Azure-Ressource | <ul> <li>BICEP-Dateien unter `templates/azure` .</li> <li>`.fx/azure.parameters.<envName>.json`.</li></ul> | Weitere Informationen finden Sie unter [Anpassen von ARM-Parametern und Vorlagen.](provision.md#customize-arm-parameters-and-templates) |
| Wiederverwenden vorhandener AAD-App für Teams-App | <ul> <li>`auth` abschnitt in `.fx/config.<envName>.json` .</li> </ul> | Weitere Informationen finden Sie unter [Verwenden einer vorhandenen AAD-App für Ihre Teams-App.](provision.md#use-an-existing-aad-app-for-your-teams-app) |
| Wiederverwenden vorhandener AAD-App für Bot | <ul> <li>`bot` abschnitt in `.fx/config.<envName>.json` .</li> </ul> | Weitere Informationen finden Sie unter [Verwenden einer vorhandenen AAD-App für Ihren Bot.](provision.md#use-an-existing-aad-app-for-your-bot) |
| Überspringen des Hinzufügens von Benutzern beim Bereitstellen von SQL | <ul> <li>`skipAddingSqlUser` -Eigenschaft in `.fx/config.<envName>.json` .</li> </ul> | Weitere Informationen finden Sie unter ["Überspringen des Hinzufügens von Benutzern für SQL Datenbank".](provision.md#skip-adding-user-for-sql-database) |
| Anpassen des App-Manifests | <ul> <li>`templates/manifest.remote.template.json`.</li> <li>`manifest` abschnitt in `.fx/config.<envName>.json` .</li>  </ul> | Weitere Informationen finden Sie unter [Anpassen Teams App-Manifests in Teams Toolkit.](TeamsFx-manifest-customization.md) |

## <a name="scenarios"></a>Szenarien

### <a name="scenario-1-customize-teams-app-name-for-different-environment"></a>Szenario 1: Anpassen Teams App-Namens für verschiedene Umgebungen

In diesem Beispiel erfahren Sie, wie Sie den Teams App-Namen `myapp(dev)` für die Standardumgebung `dev` und für `myapp(staging)` die Stagingumgebung `staging` festlegen.

Führen Sie die Schritte zur Anpassung aus:

- Schritt 1: Öffnen Sie die `.fx/configs/config.dev.json` Konfigurationsdatei.
- Schritt 2: Aktualisieren Sie die Eigenschaft des *Manifests > appName > kurz* auf `myapp(dev)`

  Updates `.fx/configs/config.dev.json` für:

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

- Schritt 3: Erstellen Sie eine neue Umgebung, die benannt `staging` wird, wenn sie nicht vorhanden ist.
- Schritt 4: Öffnen Sie die `.fx/configs/config.staging.json` Konfigurationsdatei.
- Schritt 5: Aktualisieren Sie die gleiche Eigenschaft von Schritt 2 auf `myapp(staging)` .
- Schritt 6: Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit. Weitere Informationen finden Sie in [diesem Dokument.](provision.md#provision-using-teams-toolkit)

### <a name="scenario-2-customize-teams-app-description-for-different-environment"></a>Szenario 2: Anpassen Teams App-Beschreibung für verschiedene Umgebungen

In diesem Szenario erfahren Sie, wie Sie verschiedene Teams App-Beschreibung für verschiedene Umgebungen festlegen:

- Für die Standardumgebung `dev` lautet die Beschreibung `my app description for dev` ;
- Für die Stagingumgebung `staging` lautet die Beschreibung `my app description for staging` ;

Schritte zur Anpassung:

- Schritt 1: Öffnen Sie die `.fx/configs/config.dev.json` Konfigurationsdatei.
- Schritt 2: Hinzufügen einer neuen Eigenschaft des *Manifests > Beschreibung > kurz* mit `my app description for dev` Wert.

  Updates für `.fx/configs/config.dev.json`

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

- Schritt 3: Erstellen Sie eine neue Umgebung mit dem `staging` Namen, wenn sie nicht vorhanden ist.
- Schritt 4: Öffnen Sie die `.fx/configs/config.staging.json` Konfigurationsdatei.
- Schritt 5: Fügen Sie die gleiche Eigenschaft von Schritt 2 zu `my app description for staging` hinzu.
- Schritt 6: Öffnen Sie Teams App-Manifestvorlage für `templates/appPackage/manifest.remote.template.json` Remote.
- Schritt 7: Aktualisieren Sie die Eigenschaft `description > short` so, dass sie die in Konfigurationsdateien definierte **Variable** mit must syntax `{{config.manifest.description.short}}` verwendet.
  
  Updates `manifest.remote.template.json` für:

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
- Schritt 8: Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Weitere Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie in [diesem Dokument.](provision.md#provision-using-teams-toolkit)

### <a name="scenario-3-customize-teams-app-description-for-all-environments"></a>Szenario 3: Anpassen Teams App-Beschreibung für alle Umgebungen

In diesem Szenario erfahren Sie, wie Sie die Beschreibung der Teams App `my app description` für alle Umgebungen festlegen.

Da die Teams App-Manifestvorlage in allen Umgebungen gemeinsam verwendet wird, können wir den darin enthaltenen Beschreibungswert für unser Ziel aktualisieren:

- Schritt 1: Öffnen Sie Teams App-Manifestvorlage für `templates/appPackage/manifest.remote.template.json` Remote.
- Schritt 2: Aktualisieren Sie die Eigenschaft `description > short` mit **einer hartcodierten Zeichenfolge.** `my app description`
  
  Updates `manifest.remote.template.json` für:

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

- Step 3: run provision command against **all** environment to update the app name in remote environments. For how to run provision command with Teams Toolkit, you can refer to [this document](provision.md#provision-using-teams-toolkit) for more details.

### Scenario 4: customize Azure resources for different environment

You can customize Azure resources for each environment, for example specifying Azure Function name, by editing the environment corresponding `.fx/configs/azure.parameters.{env}.json` file.

For more information on BICEP template and parameter files, see [provision cloud resources](provision.md)

## See also

> [!div class="nextstepaction"]
> [Provision cloud resources](provision.md)

> [!div class="nextstepaction"]
> [Add more cloud resources](add-resource.md)

> [!div class="nextstepaction"]
> [Collaborate with other developers on Teams project](TeamsFx-collaboration.md)
