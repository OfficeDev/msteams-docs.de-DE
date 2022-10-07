---
title: TeamsFX mit mehreren Umgebungen im Teams Toolkit
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über TeamsFX Multi-Umgebung, z. B. erstellen Sie eine neue Umgebung, wählen Sie die Zielumgebung und vieles mehr
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 11/29/2021
ms.openlocfilehash: 20bdb351eeff9a11d9460cf8206cfdc7dcbea0ff
ms.sourcegitcommit: 637b8f93b103297b1ff9f1af181680fca6f4499d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2022
ms.locfileid: "68499300"
---
# <a name="manage-multiple-environments"></a>Verwalten mehrerer Umgebungen

 Das Microsoft Teams-Toolkit bietet Ihnen eine einfache Möglichkeit, mehrere Umgebungen zu erstellen und zu verwalten, Artefakte in der Zielumgebung für Ihre Microsoft Teams-App bereitzustellen und bereitzustellen.

 Sie können Folgendes in mehreren Umgebungen ausführen:

1. **Test vor der Produktion**: Sie können mehrere Umgebungen einrichten, z. B. Entwickeln, Testen und Staging, bevor Sie eine Teams-App in der Produktionsumgebung im Entwicklungslebenszyklus moderner Apps veröffentlichen.

2. **Verwalten von App-Verhalten in verschiedenen Umgebungen**: Sie können verschiedene App-Verhaltensweisen für mehrere Umgebungen einrichten, z. B. Telemetrie in Produktionsumgebungen aktivieren.

   > [!NOTE]
   > Stellen Sie sicher, dass die Telemetrie in der Entwicklungsumgebung deaktiviert ist.

   > [!TIP]
   > Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

## <a name="create-new-environment"></a>Erstellen einer neuen Umgebung

Nachdem Sie ein Projekt erstellt haben, konfiguriert das Teams-Toolkit standardmäßig Folgendes:

* Eine `local` Umgebung, die die Konfiguration der lokalen Computerumgebung darstellt.
* Eine `dev` Umgebung, die die Remote- oder Cloudumgebungskonfiguration darstellt.

> [!NOTE]
> Jedes Projekt kann nur eine `local` Umgebung, aber mehrere Remoteumgebungen haben.

**Remoteumgebung hinzufügen**:

1. Wählen Sie in :::image type="content" source="~/assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.png" alt-text="der Aktivitätsleiste in der Aktivitätsleiste"::: das **Teams-Toolkit** aus.
2. Wählen Sie **"+Teams" aus: Erstellen Sie eine neue Umgebung** im Abschnitt **"UMGEBUNG** ", wie in der folgenden Abbildung dargestellt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/create new env.png" alt-text="Erstellen einer neuen Umgebung":::

> [!Note]
> Wenn Sie über mehrere Umgebungen verfügen, müssen Sie eine vorhandene Umgebung auswählen, um dieselbe zu erstellen. Der Befehl kopiert den Dateiinhalt der `config.<newEnv>.json` vorhandenen Umgebung, die Sie ausgewählt haben, in `azure.parameters.<newEnv>.json` die erstellte neue Umgebung.

## <a name="target-environment"></a>Zielumgebung

Sie können die Zielumgebung auswählen. Das Teams-Toolkit fordert Sie auf, eine Zielumgebung auszuwählen, wenn Sie über mehrere Remoteumgebungen verfügen:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="project-folder-structure"></a>Projektordnerstruktur

Nachdem Sie das Projekt erstellt haben, können Sie die Projektordner und Dateien unter **Explorer** in Visual Studio Code anzeigen. Neben den benutzerdefinierten Codes verwendet das Teams-Toolkit einige Dateien, um die `configs``states`App und `templates` die App zu verwalten. Die folgende Liste enthält Dateien und beschreibt deren Beziehung zu mehreren Umgebungen.

* `.fx/configs`: Konfiguriert die Dateien, die der Benutzer für die Teams-App anpassen kann.
  * `config.<envName>.json`: Konfigurationsdatei pro Umgebung.
  * `azure.parameters.<envName>.json`: Parameterdatei für die Azure-Bicep-Bereitstellung pro Umgebung.
  * `projectSettings.json`: Globale Projekteinstellungen, die für alle Umgebungen gelten.
* `.fx/states`: Bereitstellungsergebnis, das vom Teams-Toolkit generiert wird.
  * `state.<envName>.json`: Bereitstellen der Ausgabedatei pro Umgebung.
  * `<env>.userdata`: Benutzerdaten für die Bereitstellungsausgabe pro Umgebung.
* `templates`
  * `appPackage`: App-Manifestvorlagendateien.
  * `azure`: Bicep-Vorlagendateien.

## <a name="customize-resource-provision"></a>Passen Sie die Ressourcenbereitstellung an

Mit dem Teams-Toolkit können Sie die Konfigurationsdateien und Vorlagendateien ändern, um die Ressourcenbereitstellung in jeder Umgebung anzupassen.

In der folgenden Tabelle sind die allgemeinen Szenarien für die benutzerdefinierte Ressourcenbereitstellung aufgeführt:

| Szenarien | Standort| Beschreibung |
| --- | --- | --- |
| Anpassen der Azure-Ressource |Bicep-Dateien unter `templates/azure` `.fx/azure.parameters.<envName>.json` | [Passen Sie ARM-Parameter und -Vorlagen an](provision.md#customize-arm-template-files) |
| Vorhandene Azure AD-App für Teams-App wiederverwenden | `auth` Abschnitt in`.fx/config.<envName>.json`|  [Verwenden Sie eine vorhandene Azure AD-App für Ihre Teams-App](provision.md#use-an-existing-azure-ad-app-for-your-teams-app) |
| Vorhandene Azure AD-App für Bot wiederverwenden |`bot` Abschnitt in`.fx/config.<envName>.json`| [Verwenden Sie eine vorhandene Azure AD-App für Ihren Bot](provision.md#use-an-existing-azure-ad-app-for-your-bot) |
| Überspringen des Hinzufügens von Benutzern während der Sql-Bereitstellung |`skipAddingSqlUser` -Eigenschaft in`.fx/config.<envName>.json`| [Überspringen Sie das Hinzufügen eines Benutzers für die SQL-Datenbank](provision.md#skip-adding-user-for-sql-database) |
| Anpassen des App-Manifests |`templates/manifest.template.json` Datei unter `manifest` Abschnitt in `.fx/config.<envName>.json`| [Vorschau des App-Manifests im Toolkit](TeamsFx-preview-and-customize-app-manifest.md)|

## <a name="scenarios"></a>Szenarien

Sie können die folgenden Szenarien sehen, um die Ressourcenbereitstellung in verschiedenen Umgebungen anzupassen.
<br>

<br><details>
<summary><b>Szenario 1: Anpassen des Teams-App-Namens für unterschiedliche Umgebungen </b></summary>

Sie können den Namen `myapp(dev)` der Teams-App für die Standardumgebung `dev` und `myapp(staging)` für die Stagingumgebung `staging`festlegen.

Schritte für die Anpassung:

1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
2. Aktualisieren Sie die Eigenschaft von **`manifest`** > **`appName`** > **short** auf **`myapp(dev)`**.

  Die Aktualisierungen `.fx/configs/config.dev.json` sind:

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

3. Sie können eine neue Umgebung erstellen und sie `staging` benennen, wenn sie nicht vorhanden ist.
4. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.staging.json`.
5. Aktualisieren Sie dieselbe Eigenschaft `myapp(staging)`.
6. Jetzt können Sie den Bereitstellungsbefehl `dev` für und `staging` die Umgebung ausführen, um den App-Namen in Remoteumgebungen zu aktualisieren. Informationen zum Ausführen des Bereitstellungsbefehls mit dem Teams-Toolkit finden Sie [unter "Bereitstellung"](provision.md#provision-using-teams-toolkit-in-visual-studio-code).

</details>

<details>
<summary><b>Szenario 2: Anpassen der Beschreibung der Teams-App für unterschiedliche Umgebungen</b></summary>

Sie können verschiedene Teams-App-Beschreibungen für die verschiedenen Umgebungen festlegen:

* Für die Standardumgebung `dev`lautet `my app description for dev`die Beschreibung .
* Für die Stagingumgebung `staging`lautet `my app description for staging`die Beschreibung .

Schritte für die Anpassung:

1. Öffnen Sie die Konfigurationsdatei `.fx/configs/config.dev.json`.
2. Fügen Sie eine neue Eigenschaft mit dem **`manifest`** > **`short`** > **`description`** Wert **`my app description for dev`** hinzu.

  Die Aktualisierungen `.fx/configs/config.dev.json` sind:

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
6. Öffnen Sie die Manifestvorlage `templates/appPackage/manifest.template.json`der Teams-App.
7. Aktualisieren Sie die Eigenschaft **`description`** > **`short`** so, dass die **variable** verwendet wird, die in der Konfiguration von Dateien mit geschweiften Klammern **`{{config.manifest.description.short}}`** definiert ist.
  
  Die Aktualisierungen `manifest.template.json` sind:

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

8. Sie können jetzt den Bereitstellungsbefehl für `dev` und `staging` die Umgebung ausführen, um den App-Namen in Remoteumgebungen zu aktualisieren.

</details>

<details>
<summary><b>Szenario 3: Anpassen der Beschreibung der Teams-App für alle Umgebungen</b></summary>

Sie können die Beschreibung der Teams-App `my app description` für alle Umgebungen festlegen.

Da die Manifestvorlage der Teams-App in allen Umgebungen freigegeben ist, können wir den darin angegebenen Beschreibungswert für unser Ziel aktualisieren:

1. Öffnen Sie die Manifestvorlage `templates/appPackage/manifest.template.json`der Teams-App.
2. Aktualisieren Sie die Eigenschaft **`description`** > **`short`** mit hartcodierter Zeichenfolge.**`my app description`**
  
  Die Aktualisierungen `manifest.template.json` sind:

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

3. Sie können jetzt den Bereitstellungsbefehl für **alle** Umgebungen ausführen, um den App-Namen in Remoteumgebungen zu aktualisieren.

</details>

<details>
<br><summary><b>Szenario 4: Anpassen von Azure-Ressourcen für unterschiedliche Umgebungen</b></summary>

Sie können Azure-Ressourcen für jede Umgebung anpassen, z. B. die Umgebung entsprechend fx/configs/azure.parameters bearbeiten. {env}.json-Datei, um den Namen der Azure-Funktion anzugeben.

Weitere Informationen zu Bicep-Vorlagen- und Parameterdateien finden Sie [unter Bereitstellen von Cloudressourcen](provision.md).
</details>
</br>

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Hinzufügen weiterer Cloudressourcen](add-resource.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
* [Testen des App-Verhaltens in unterschiedlichen Umgebungen](test-app-behavior.md)
