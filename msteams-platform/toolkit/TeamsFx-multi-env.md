---
title: TeamsFX mehrere Umgebungen in Teams Toolkit
author: MuyangAmigo
description: In diesem Modul erfahren Sie mehr über TeamsFX Multi-Umgebung, z. B. erstellen Sie eine neue Umgebung, wählen Sie die Zielumgebung und vieles mehr
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 6256c620d62233da2420b3dfa7cd53101bf92978
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143571"
---
# <a name="manage-multiple-environments"></a>Verwalten mehrerer Umgebungen

 Teams Toolkit bietet ihnen eine einfache Möglichkeit, mehrere Umgebungen zu erstellen und zu verwalten, Artefakte in der Zielumgebung für Teams App bereitzustellen und bereitzustellen.

 Mit den verschiedenen Umgebungen können Sie Folgendes ausführen:

1. **Test vor der Produktion**: Sie können mehrere Umgebungen einrichten, z. B. Dev, Test und Staging, bevor Sie eine Teams App in der Produktionsumgebung im Lebenszyklus der modernen App-Entwicklung veröffentlichen.

2. **Verwalten von App-Verhalten in verschiedenen Umgebungen**: Sie können unterschiedliche Verhaltensweisen für mehrere Umgebungen einrichten, z. B. Telemetrie in der Produktionsumgebung aktivieren, sie jedoch in der Entwicklungsumgebung deaktivieren.

## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

## <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Nach dem Erstellen eines neuen Projekts erstellt Teams Toolkit standardmäßig Folgendes:

* Eine `local` Umgebung zur Darstellung der Konfigurationen der lokalen Computerumgebung
* Eine `dev` Umgebung zur Darstellung der Remote- oder Cloudumgebungskonfigurationen

> [!NOTE]
> Jedes Projekt kann nur eine `local` Umgebung, aber mehrere Remoteumgebungen haben.

**So fügen Sie eine weitere Remoteumgebung hinzu**:

1. Wählen Sie die **Teams** :::image type="content" source="../assets/images/teams-toolkit-v2/add-sso/teams-toolkit-sidebar-icon.png" alt-text="sso randleiste hinzufügen"::: von der linken Navigationsleiste aus.
2. Wählen Sie **+Teams: Erstellen Sie eine neue Umgebung** unter dem Abschnitt **"Umgebung**", wie in der folgenden Abbildung gezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="create":::

   Wenn Sie über mehrere Umgebungen verfügen, müssen Sie eine vorhandene Umgebung auswählen, um dieselbe zu erstellen. Der Befehl kopiert den Dateiinhalt der `config.<newEnv>.json` vorhandenen Umgebung, die Sie ausgewählt haben, in `azure.parameters.<newEnv>.json` die neu erstellte Umgebung.

## <a name="select-target-environment"></a>Zielumgebung auswählen

Sie können die Zielumgebung für alle umgebungsbezogenen Vorgänge auswählen. Das Toolkit fordert eine Zielumgebung auf und fordert sie auf, wenn Sie über mehrere Remoteumgebungen verfügen, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="project-folder-structure"></a>Project Ordnerstruktur

Nachdem Sie das Projekt erstellt haben, können Sie die Projektordner und Dateien unter **Explorer** in VS Code anzeigen. Neben den benutzerdefinierten Codes verwendet Teams Toolkit einige Dateien, um die Konfiguration, den Zustand und die Vorlage der App zu verwalten. Die folgende Liste enthält Dateien und beschreibt deren Beziehung zu mehreren Umgebungen.

* `.fx/configs`: Konfigurieren von Dateien, die Benutzer für die Teams-App anpassen können
  * `config.<envName>.json`: Konfigurationsdatei pro Umgebung
  * `azure.parameters.<envName>.json`: Parameterdatei für azure-bicep-Bereitstellung pro Umgebung
  * `projectSettings.json`: Globale Projekteinstellungen, die für alle Umgebungen gelten
* `.fx/states`: Bereitstellungsergebnis, das vom Toolkit generiert wird
  * `state.<envName>.json`: Bereitstellen der Ausgabedatei pro Umgebung
  * `<env>.userdata`: Benutzerdaten für die Bereitstellungsausgabe pro Umgebung
* `templates`
  * `appPackage`: App-Manifestvorlagendateien
  * `azure`: Bicep-Vorlagendateien

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Teams Toolkit können Sie die Konfigurationsdateien und Vorlagendateien ändern, um die Ressourcenbereitstellung in jeder Umgebung anzupassen.

In der folgenden Tabelle sind die allgemeinen Szenarien für die benutzerdefinierte Ressourcenbereitstellung aufgeführt:

| Szenarien | Speicherort| Beschreibung |
| --- | --- | --- |
| Anpassen der Azure-Ressource | <ul> <li>Bicep-Dateien unter `templates/azure`</li> <li>`.fx/azure.parameters.<envName>.json`</li></ul> | [Passen Sie ARM-Parameter und -Vorlagen an](provision.md#customize-arm-parameters-and-templates) |
| Vorhandene Azure AD-App für Teams-App wiederverwenden | <ul> <li>`auth` Abschnitt in`.fx/config.<envName>.json`</li> </ul> |  [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Vorhandene Azure AD-App für Bot wiederverwenden | <ul> <li>`bot` Abschnitt in`.fx/config.<envName>.json`</li> </ul> | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Überspringen des Hinzufügens von Benutzern während der Bereitstellung SQL | <ul> <li>`skipAddingSqlUser` -Eigenschaft in`.fx/config.<envName>.json`</li> </ul> | [Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank](provision.md#skip-adding-user-for-sql-database) |
| Anpassen des App-Manifests | <ul> <li>`templates/manifest.template.json`</li> <li>`manifest` Abschnitt in `.fx/config.<envName>.json`</li>  </ul> | [Vorschau des App-Manifests im Toolkit](TeamsFx-preview-and-customize-app-manifest.md)|

## <a name="scenarios"></a>Szenarien

Sie können die folgenden Szenarien sehen, um die Ressourcenbereitstellung in verschiedenen Umgebungen anzupassen.
<br>

<br><details>
<summary><b>Szenario 1: Anpassen Teams App-Namens für unterschiedliche Umgebungen</b></summary>

Sie können den Teams App-Namen `myapp(dev)` für die Standardumgebung `dev` und `myapp(staging)` für die Stagingumgebung `staging`festlegen.

Führen Sie die Schritte zur Anpassung aus:

1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
2. Aktualisieren Sie die Eigenschaft des *Manifests > appName-> kurz* auf `myapp(dev)`.

  Die folgenden Aktualisierungen `.fx/configs/config.dev.json` sind erforderlich:

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

3. Erstellen Sie eine neue Umgebung, und nennen Sie sie `staging` , wenn sie nicht vorhanden ist.
4. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.staging.json`.
5. Aktualisieren Sie dieselbe Eigenschaft `myapp(staging)`.
6. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter ["Bereitstellung"](provision.md#provision-using-teams-toolkit).

</details>

<details>
<summary><b>Szenario 2: Anpassen Teams App-Beschreibung für unterschiedliche Umgebungen</b></summary>

Sie können unterschiedliche Teams App-Beschreibung für die verschiedenen Umgebungen festlegen:

* Für die Standardumgebung `dev`lautet die Beschreibung `my app description for dev`
* Für die Stagingumgebung `staging`lautet die Beschreibung `my app description for staging`

Führen Sie die Schritte zur Anpassung aus:

1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
2. Fügen Sie eine neue Eigenschaft des *Manifests > Beschreibung hinzu, > kurz* mit dem Wert `my app description for dev`.

  Die folgenden Aktualisierungen `.fx/configs/config.dev.json` sind erforderlich:

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

3. Erstellen Sie eine neue Umgebung, und nennen Sie sie `staging` , wenn sie nicht vorhanden ist.
4. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.staging.json`.
5. Fügen Sie dieselbe Eigenschaft zu `my app description for staging`hinzu.
6. Öffnen Sie Teams App-Manifestvorlage`templates/appPackage/manifest.template.json`.
7. Aktualisieren Sie die Eigenschaft `description > short` so, dass die **variable** verwendet wird, die in der Konfiguration von Dateien mit Schnurrbartsyntax `{{config.manifest.description.short}}`definiert ist.
  
  Die folgenden Aktualisierungen `manifest.template.json` sind erforderlich:

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

8. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren.

</details>

<details>
<summary><b>Szenario 3: Anpassen Teams App-Beschreibung für alle Umgebungen</b></summary>

Sie können die Beschreibung Teams App `my app description` für alle Umgebungen festlegen.

Da die Teams App-Manifestvorlage in allen Umgebungen gemeinsam genutzt wird, können wir den Darin enthaltenen Beschreibungswert für unser Ziel aktualisieren:

1. Öffnen Sie Teams App-Manifestvorlage`templates/appPackage/manifest.template.json`.
2. Aktualisieren Sie die Eigenschaft `description > short` mit **hartcodierter Zeichenfolge**`my app description`.
  
  Die folgenden Aktualisierungen `manifest.template.json` sind erforderlich:

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

  ```

3. Führen Sie den Bereitstellungsbefehl für **alle** Umgebungen aus, um den App-Namen in Remoteumgebungen zu aktualisieren.

</details>

<details>
<br><summary><b>Szenario 4: Anpassen von Azure-Ressourcen für unterschiedliche Umgebungen</b></summary>
Sie können Azure-Ressourcen für jede Umgebung anpassen, z. B. die Umgebung entsprechend fx/configs/azure.parameters bearbeiten. {env}.json-Datei, um den Namen der Azure-Funktion anzugeben.

Weitere Informationen zu Bicep-Vorlagen- und Parameterdateien finden Sie [unter Bereitstellen von Cloudressourcen](provision.md)
</details>
</br>

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen weiterer Cloudressourcen](add-resource.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
