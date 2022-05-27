---
title: TeamsFX mehrere Umgebungen in Teams Toolkit
author: MuyangAmigo
description: Informationen zu TeamsFX Multi-Umgebungen
ms.author: nintan
ms.localizationpriority: medium
ms.topic: overview of multiple environment
ms.date: 11/29/2021
ms.openlocfilehash: 72d980849d48498dddedb87db35ae15ca69e4cda
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756933"
---
# <a name="manage-multiple-environments"></a>Verwalten mehrerer Umgebungen

 Teams Toolkit bietet ihnen eine einfache Möglichkeit, mehrere Umgebungen zu erstellen und zu verwalten, Artefakte in der Zielumgebung für Teams App bereitzustellen und bereitzustellen.

 Mit den verschiedenen Umgebungen können Sie Folgendes ausführen:

1. **Test vor der Produktion**: Sie können mehrere Umgebungen einrichten, z. B. Entwickeln, Testen und Staging, bevor Sie eine Teams App in der Produktionsumgebung im Lebenszyklus der modernen App-Entwicklung veröffentlichen.

2. **Verwalten von App-Verhalten in verschiedenen Umgebungen**: Sie können unterschiedliche Verhaltensweisen für mehrere Umgebungen einrichten, z. B. Telemetrie in der Produktionsumgebung aktivieren, jedoch in entwicklungsumgebung deaktivieren

## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Stellen Sie sicher, dass sie Teams App-Projekt in Microsoft Visual Studio Code geöffnet haben.

## <a name="create-a-new-environment"></a>Erstellen einer neuen Umgebung

Nach dem Erstellen eines neuen Projekts erstellt Teams Toolkit standardmäßig Folgendes:

* Eine `local` Umgebung zur Darstellung der Konfigurationen der lokalen Computerumgebung
* Eine `dev` Umgebung zur Darstellung der Remote- oder Cloudumgebungskonfigurationen

> [!NOTE]
> Jedes Projekt kann nur eine `local` Umgebung, aber mehrere Remoteumgebungen haben.

**So fügen Sie eine weitere Remoteumgebung hinzu**:

1. Wählen Sie das **Symbol Teams** in der Randleiste aus.
2. Wählen Sie **+Teams: Erstellen Sie eine neue Umgebung** unter dem Abschnitt "Umgebung", wie in der folgenden Abbildung dargestellt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="create":::

   Wenn Sie über mehrere Umgebungen verfügen, müssen Sie eine vorhandene Umgebung auswählen, um dieselbe zu erstellen. Der Befehl kopiert den Dateiinhalt der `config.<newEnv>.json` vorhandenen Umgebung, die Sie ausgewählt haben, in `azure.parameters.<newEnv>.json` die neu erstellte Umgebung.

## <a name="select-target-environment"></a>Zielumgebung auswählen

Sie können die Zielumgebung für alle umgebungsbezogenen Vorgänge auswählen. Das Toolkit fordert eine Zielumgebung auf und fordert sie auf, wenn Sie über mehrere Remoteumgebungen verfügen, wie in der folgenden Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="project-folder-structure"></a>Project Ordnerstruktur

Nachdem Sie das Projekt erstellt haben, können Sie die Projektordner und Dateien im Explorer-Bereich von Visual Studio Code anzeigen. Neben den benutzerdefinierten Codes werden einige Dateien vom Teams Toolkit verwendet, um die Konfiguration, den Zustand und die Vorlage der App zu verwalten. Die folgende Liste enthält Dateien und beschreibt deren Beziehung zu mehreren Umgebungen.

* `.fx/configs`: Konfigurieren von Dateien, die der Benutzer für die Teams-App anpassen kann
  * `config.<envName>.json`: Konfigurationsdatei pro Umgebung 
  * `azure.parameters.<envName>.json`: pro Umgebungsparameterdatei für die Azure-Bicep-Bereitstellung
  * `projectSettings.json`: Globale Projekteinstellungen, die für alle Umgebungen gelten
* `.fx/states`: Bereitstellungsergebnis, das vom Toolkit generiert wird
  * `state.<envName>.json`: Bereitstellungsausgabedatei pro Umgebung
  * `<env>.userdata`: Pro Umgebung vertrauliche Benutzerdaten für die Bereitstellungsausgabe
* `templates`
  * `appPackage`: App-Manifestvorlagendateien
  * `azure`: Bicep-Vorlagendateien

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Teams Toolkit können Sie die Konfigurationsdateien und Vorlagendateien ändern, um die Ressourcenbereitstellung in jeder Umgebung anzupassen.

In der folgenden Tabelle sind die allgemeinen Szenarien für die benutzerdefinierte Ressourcenbereitstellung aufgeführt:

| Szenarien | Standort| Beschreibung |
| --- | --- | --- |
| Anpassen der Azure-Ressource | <ul> <li>Bicep-Dateien unter `templates/azure`</li> <li>`.fx/azure.parameters.<envName>.json`</li></ul> | [Passen Sie ARM-Parameter und -Vorlagen an](provision.md#customize-arm-parameters-and-templates) |
| Vorhandene Azure AD-App für Teams-App wiederverwenden | <ul> <li>`auth` Abschnitt in`.fx/config.<envName>.json`</li> </ul> |  [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Vorhandene Azure AD-App für Bot wiederverwenden | <ul> <li>`bot` Abschnitt in`.fx/config.<envName>.json`</li> </ul> | [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Überspringen des Hinzufügens von Benutzern während der Bereitstellung SQL | <ul> <li>`skipAddingSqlUser` -Eigenschaft in`.fx/config.<envName>.json`</li> </ul> | [Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank](provision.md#skip-adding-user-for-sql-database) |
| Anpassen des App-Manifests | <ul> <li>`templates/manifest.template.json`</li> <li>`manifest` Abschnitt in `.fx/config.<envName>.json`</li>  </ul> | [Vorschau des App-Manifests im Toolkit](TeamsFx-preview-and-customize-app-manifest.md)|

## <a name="scenarios"></a>Szenarien

Es gibt vier Szenarien, um die Ressourcenbereitstellung in verschiedenen Umgebungen anzupassen.
<br>

<br><details>
<summary><b>Szenario 1: Anpassen Teams App-Namens für unterschiedliche Umgebungen</b></summary>

Sie können den Teams App-Namen `myapp(dev)` für die Standardumgebung `dev` und `myapp(staging)` für die Stagingumgebung `staging`festlegen.

Führen Sie die folgenden Schritte zur Anpassung aus:

1. Konfigurationsdatei öffnen `.fx/configs/config.dev.json`
2. Aktualisieren Sie die Eigenschaft des *manifest > appName-> kurz* auf `myapp(dev)`

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

3. Erstellen Sie eine neue Umgebung, und benennen Sie sie `staging` , wenn sie nicht vorhanden ist.
4. Konfigurationsdatei öffnen `.fx/configs/config.staging.json`
5. Aktualisieren derselben Eigenschaft `myapp(staging)`
6. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter [Provision](provision.md#provision-using-teams-toolkit)
</details>
<br>


<details>
<summary><b>Szenario 2: Anpassen Teams App-Beschreibung für unterschiedliche Umgebungen</b></summary>

In diesem Szenario erfahren Sie, wie Sie unterschiedliche Teams App-Beschreibung für die verschiedenen Umgebungen festlegen:

* Für die Standardumgebung `dev`lautet die Beschreibung `my app description for dev`
* Für die Stagingumgebung `staging`lautet die Beschreibung `my app description for staging`

Führen Sie die folgenden Schritte zur Anpassung aus:

1. Konfigurationsdatei öffnen `.fx/configs/config.dev.json`
2. Hinzufügen einer neuen Eigenschaft des *Manifests > Beschreibung > kurz* mit Wert `my app description for dev`

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

3. Erstellen Sie eine neue Umgebung, und benennen Sie sie `staging` , wenn sie nicht vorhanden ist.
4. Konfigurationsdatei öffnen `.fx/configs/config.staging.json`
5. Hinzufügen derselben Eigenschaft zu `my app description for staging`
6. Öffnen Teams App-Manifestvorlage`templates/appPackage/manifest.template.json`
7. Aktualisieren der Eigenschaft `description > short` so, dass die **variable** verwendet wird, die in der Konfiguration von Dateien mit Schnurrbartsyntax definiert ist `{{config.manifest.description.short}}`
  
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

8. Führen Sie den Bereitstellungsbefehl für `dev` und `staging` die Umgebung aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter [Provision](provision.md#provision-using-teams-toolkit)

</details>
<br>

<details>
<summary><b>Szenario 3: Anpassen Teams App-Beschreibung für alle Umgebungen</b></summary>

In diesem Szenario erfahren Sie, wie Sie die Beschreibung Teams App `my app description` für alle Umgebungen festlegen.

Da die Teams App-Manifestvorlage in allen Umgebungen gemeinsam genutzt wird, können wir den Darin enthaltenen Beschreibungswert für unser Ziel aktualisieren:

1. Öffnen Teams App-Manifestvorlage`templates/appPackage/manifest.template.json`
2. Aktualisieren der Eigenschaft `description > short` mit **hartcodierter Zeichenfolge** `my app description`
  
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

3. Führen Sie den Bereitstellungsbefehl für **alle** Umgebungen aus, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit Teams Toolkit finden Sie unter ["Bereitstellung"](provision.md#provision-using-teams-toolkit).

<br></details>
<br>

<details>
<br><summary><b>Szenario 4: Anpassen von Azure-Ressourcen für unterschiedliche Umgebungen</b></summary>
Sie können Azure-Ressourcen für jede Umgebung anpassen, z. B. den Namen der Azure-Funktion angeben, indem Sie die Umgebung entsprechend fx/configs/azure.parameters bearbeiten. {env}.json. Datei.

Weitere Informationen zu Bicep-Vorlagen- und Parameterdateien finden Sie [unter Bereitstellen von Cloudressourcen](provision.md)
</details>
</br>

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen weiterer Cloudressourcen](add-resource.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
