---
title: Anpassen des Teams-App-Manifests im Teams-Toolkit
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie das Microsoft Teams-App-Manifest in der verschiedenen Umgebung bearbeiten, in der Vorschau anzeigen und anpassen.
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
ms.openlocfilehash: 3828c357307c5f7bfd94935a75dc9d6f5cedbc39
ms.sourcegitcommit: c806c5ffe277c740d0d7b8f62e72ade562029194
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617789"
---
# <a name="customize-teams-app-manifest"></a>Anpassen des Teams-App-Manifests

Das Teams-App-Manifest beschreibt, wie Ihre App in das Microsoft Teams-Produkt integriert wird. Weitere Informationen zum Manifest finden Sie unter [App-Manifestschema für Teams](../resources/schema/manifest-schema.md). In diesem Abschnitt werden folgende Themen behandelt:

* [Vorschau der Manifestdatei in der lokalen Umgebung](#preview-manifest-file-in-local-environment)
* [Vorschau der Manifestdatei in der Remoteumgebung](#preview-manifest-file-in-remote-environment)
* [Lokale Änderungen mit Dev Portal synchronisieren](#sync-local-changes-to-dev-portal)
* [Anpassen ihres Teams-App-Manifests](#customize-your-teams-app-manifest)
* [Überprüfen des Manifests](#validate-manifest)

Die Manifestvorlagendatei `manifest.template.json` ist nach dem Gerüstbau unter `templates/appPackage` Ordner verfügbar. Die Vorlagendatei mit Platzhaltern und die tatsächlichen Werte werden vom Teams-Toolkit mithilfe von Dateien unter `.fx/configs` und `.fx/states` für verschiedene Umgebungen aufgelöst.

Um eine Vorschau des Manifests mit tatsächlichen Inhalten anzuzeigen, generiert das Teams-Toolkit Vorschaumanifestdateien unter `build/appPackage` dem Ordner:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote Teams app
        ├───appPackage.local.zip - Zipped app package of local Teams app
        ├───manifest.{env}.json  - Previewed manifest of remote Teams app
        └───manifest.local.json  - Previewed manifest of local Teams app
```

Sie können eine Vorschau der Manifestdatei in lokalen und Remoteumgebungen anzeigen.

* [Vorschau der Manifestdatei in der lokalen Umgebung](#preview-manifest-file-in-local-environment)
* [Vorschau der Manifestdatei in der Remoteumgebung](#preview-manifest-file-in-remote-environment)

## <a name="preview-manifest-file-in-local-environment"></a>Vorschau der Manifestdatei in der lokalen Umgebung

Um eine Vorschau der Manifestdatei in der lokalen Umgebung anzuzeigen, können Sie **F5** drücken, um das lokale Debuggen auszuführen. Es generiert lokale Standardeinstellungen für Sie, dann werden das App-Paket und das Vorschaumanifest unter dem `build/appPackage` Ordner erstellt.

Sie können eine Vorschau der lokalen Manifestdatei auch mit zwei Methoden anzeigen

* Verwenden der Vorschauoption in Codelens
* Mithilfe der Zip **Teams-Metadatenpaketoption**

Die folgenden Schritte helfen bei der Vorschau der lokalen Manifestdatei mithilfe der Vorschauoption in Codelens:

1. Wählen Sie " **Vorschau** " in den Codelen der `manifest.template.json` Datei aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Vorschau":::

1. Wählen Sie **"Lokal**" aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Umgebung auswählen1":::

Mit den folgenden Schritten können Sie eine Vorschau der lokalen Manifestdatei mithilfe der Zip **Teams-Metadatenpaketoption** anzeigen:

1. Datei auswählen `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Manifest auswählen":::

1. Wählen Sie das Microsoft Teams-Toolkit-Symbol :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: auf der Visual Studio Code-Symbolleiste aus.

1. Wählen Sie unter **"BEREITSTELLUNG**" **das Zip-Teams-Metadatenpaket** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Teams-Metadatenpaket auswählen":::

1. Wählen Sie **"Lokal**" aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Umgebung auswählen":::

Der Beispielkatalog wird wie in der folgenden Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Preview":::

## <a name="preview-manifest-file-in-remote-environment"></a>Vorschau der Manifestdatei in der Remoteumgebung

So zeigen Sie eine Vorschau der Manifestdatei mit Visual Studio Code an:

* Wählen Sie **"Bereitstellung in der Cloud** " unter **"ENTWICKLUNG** in Teams-Toolkit"-Erweiterung aus.
  
  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/provision.png" alt-text="Bereitstellen einer Cloudressource":::

So zeigen Sie eine Vorschau der Manifestdatei mithilfe der Befehlspapatte an:

* Trigger **Teams: Bereitstellung in der Cloud über die** Befehlspalette.

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/command palatte.png" alt-text="Bereitstellen von Cloudressourcen mithilfe der Befehlspapatte":::

Es generiert die Konfiguration für die Remote-Teams-App und erstellt paket- und Vorschaumanifest unter `build/appPackage` dem Ordner.

Sie können eine Vorschau der Manifestdatei auch mit zwei Methoden in der Remoteumgebung anzeigen.

* Verwenden der Vorschauoption in Codelens
* Mithilfe der Zip **Teams-Metadatenpaketoption**

Die folgenden Schritte helfen bei der Vorschau der Manifestdatei mithilfe der Vorschauoption in Codelens:

1. Wählen Sie " **Vorschau** " in den Codelen der `manifest.template.json` Datei aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Vorschau":::

1. Wählen Sie Ihre Umgebung aus.

   > [!NOTE]
   > Wenn es mehr als eine Umgebung gibt, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten (siehe Abbildung):

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

Die folgenden Schritte helfen bei der Vorschau der Manifestdatei mithilfe der **Zip Teams-Metadatenpaketoption** in der Remoteumgebung:

1. Datei auswählen `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Manifest auswählen":::

1. Wählen Sie das Microsoft Teams-Toolkit-Symbol :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: auf der Visual Studio Code-Symbolleiste aus.

1. Wählen Sie unter **"BEREITSTELLUNG**" **das Zip-Teams-Metadatenpaket** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Teams-Metadatenpaket auswählen":::

1. Wählen Sie Ihre Umgebung aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

   > [!NOTE]
   > Wenn es mehr als eine Umgebung gibt, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten (siehe Abbildung):

## <a name="sync-local-changes-to-dev-portal"></a>Lokale Änderungen mit Dev Portal synchronisieren

Nachdem Sie die Manifestdatei in der Vorschau angezeigt haben, können Sie Ihre lokalen Änderungen auf folgende Weise mit dev Portal synchronisieren:

> [!NOTE]
> Weitere Informationen zum Entwicklerportal finden Sie im [Entwicklerportal für Teams](../concepts/build-and-test/teams-developer-portal.md).

1. Bereitstellen des Teams-App-Manifests.

   Sie können das Teams-App-Manifest auf eine der folgenden Arten bereitstellen:

   * Wechseln Sie zur `manifest.template.json` Datei, und klicken Sie mit der rechten Maustaste, um aus dem Kontextmenü auszuwählen `Deploy Teams app manifest` .

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-manifest.png" alt-text="Bereitstellen des Manifests":::

   * Trigger `Teams: Deploy Teams app manifest` aus Befehlspalette.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-command.png" alt-text="Bereitstellen über die Befehlspalette":::

2. Auf Teams-Plattform aktualisieren.

   Sie können auf eine der folgenden Arten auf die Teams-Plattform aktualisieren:

   * Wählen Sie " **Auf Teams-Plattform aktualisieren** " in der oberen linken Ecke von `manifest.{env}.json`aus.

   * Trigger **Teams: Update manifest to Teams platform** on the menu bar of `manifest.{env}.json`.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/update-to-teams.png" alt-text="Auf Teams aktualisieren":::

Sie können auch **"Teams: Update manifest to Teams platform** " aus der Befehlspalette auslösen:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Strukturansicht":::

> [!NOTE]
> Trigger from editor codelens or menu bar updates current manifest file to Teams platform. Der Trigger aus der Befehlspalette erfordert die Auswahl der Zielumgebung.

 CLI-Befehl:

``` bash
        teamsfx deploy manifest --include-app-manifest yes
```

---

> [!NOTE]
> Die Änderung wird in Dev Portal aktualisiert. Alle manuellen Updates im Dev Portal werden überschrieben.

Wenn die Manifestdatei aufgrund von Konfigurationsdateiänderungen oder Vorlagenänderungen veraltet ist, wählen Sie eine der folgenden Aktionen aus:

* **Nur Vorschau**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben.
* **Vorschau und Update**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben und auch auf die Teams-Plattform aktualisiert.
* **Abbrechen**: Es wird keine Aktion ausgeführt.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::

## <a name="customize-your-teams-app-manifest"></a>Anpassen ihres Teams-App-Manifests

Teams Toolkit besteht aus den folgenden Manifest-Vorlagendateien im `manifest.template.json` Ordner in lokalen und Remote-Umgebungen:

* `manifest.template.json`
* `templates/appPackage`

Während des lokalen Debuggens oder der lokalen Bereitstellung lädt das Teams-Toolkit manifest aus `manifest.template.json`, mit den Konfigurationen von `state.{env}.json`, `config.{env}.json`und erstellt die Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps).

### <a name="supported-placeholders-in-manifesttemplatejson"></a>Unterstützte Platzhalter in manifest.template.json

Die folgende Liste enthält unterstützte Platzhalter in `manifest.template.json`:

* `{{state.xx}}`ist ein vordefinierter Platzhalter und sein Wert wird vom Teams Toolkit aufgelöst, definiert in `state.{env}.json`. Stellen Sie sicher, dass Sie die Werte in `state.{env}.json`
* `{{config.manifest.xx}}` ist ein benutzerdefinierter Platzhalter, und sein Wert wird von `config.{env}.json`

**So fügen Sie einen benutzerdefinierten Parameter hinzu**

1. Fügen Sie benutzerdefinierte Parameter wie folgt hinzu:</br>
   a. Fügen Sie einen Platzhalter `manifest.template.json` mit Muster `{{config.manifest.xx}}`hinzu.</br>
   b. Fügen Sie einen Config-Wert in `config.{env}.json`hinzu.

     ```json
     {
         "manifest": {
          "KEY": "VALUE"
          }
     }
     ```

2. Sie können zur Konfigurationsdatei navigieren, indem Sie einen der Konfigurationsplatzhalter " **Zur Konfigurationsdatei** wechseln" oder **"Statusdatei anzeigen"** in `manifest.template.json`auswählen.

### <a name="validate-manifest"></a>Überprüfen des Manifests

Bei Vorgängen wie zip **Teams-Metadatenpaketen** überprüft das Teams-Toolkit das Manifest anhand seines Schemas. Die folgende Liste bietet verschiedene Möglichkeiten zum Überprüfen des Manifests:

* Lösen Sie `Teams: Validate manifest file` in VSC aus der Befehlspalette Folgendes aus:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/validate.png" alt-text="Datei überprüfen":::

* Verwenden Sie in CLI den folgenden Befehl:

     ``` bash
        teamsfx validate --env local
        teamsfx validate --env dev
        ```

---

## To preview values for local and dev environment

In `manifest.template.json`, you can navigate to codelens to preview the values for `local` and `dev` environment.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/codelens.png" alt-text="Preview values":::

> [!NOTE]
> Provision the environment or execute local debug to generate values for placeholders.

You can navigate to state file or configuration file by selecting the codelens, which provides a drop-down list with all the environment names. After selecting one environment, the corresponding state file or configuration file opens.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-environment.png" alt-text="Select your environment":::

To preview values for all the environments, you can hover over the placeholder. It shows a list with environment names and corresponding values. If you haven't provisioned the environment or executed the local debug, select `Trigger Teams: Provision in the cloud command to see placeholder value` or `Trigger local debug to see placeholder value`.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/hover.png" alt-text="Preview all values":::

## See also

* [Manage multiple environments](TeamsFx-multi-env.md)
* [Reference: Manifest schema for Microsoft Teams](../resources/schema/manifest-schema.md)
* [Public developer preview for Microsoft Teams](../resources/dev-preview/developer-preview-intro.md)
