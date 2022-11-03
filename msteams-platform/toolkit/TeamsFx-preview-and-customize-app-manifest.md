---
title: Anpassen des Teams-App-Manifests im Teams-Toolkit
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie das Teams-App-Manifest in der unterschiedlichen Umgebung bearbeiten, in der Vorschau anzeigen und anpassen.
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 05/13/2022
zone_pivot_groups: teams-app-platform
ms.openlocfilehash: e92e30cf30dd06dbbe3c513a79fe4b7ed7c4bc1a
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833100"
---
# <a name="customize-teams-app-manifest"></a>Anpassen des Teams-App-Manifests

Das Teams-App-Manifest beschreibt, wie Ihre App in das Microsoft Teams-Produkt integriert wird.

::: zone pivot="visual-studio-code"

## <a name="customize-teams-app-manifest-for-visual-studio-code"></a>Anpassen des Teams-App-Manifests für Visual Studio Code

Das Teams-App-Manifest beschreibt, wie Ihre App in das Microsoft Teams-Produkt integriert wird. Weitere Informationen zum Manifest finden Sie unter [App-Manifestschema für Teams](../resources/schema/manifest-schema.md). In diesem Abschnitt werden folgende Themen behandelt:

* [Vorschau der Manifestdatei in der lokalen Umgebung](#preview-manifest-file-in-local-environment)
* [Vorschau der Manifestdatei in einer Remoteumgebung](#preview-manifest-file-in-remote-environment)
* [Lokale Änderungen mit dem Entwicklerportal synchronisieren](#sync-local-changes-to-developer-portal)
* [Anpassen Ihres Teams-App-Manifests](#customize-your-teams-app-manifest)
* [Überprüfen des Manifests](#validate-manifest)

Die Manifestvorlagendatei `manifest.template.json` ist nach dem Gerüstbau unter `templates/appPackage` Ordner verfügbar. Die Vorlagendatei mit Platzhaltern und die tatsächlichen Werte werden vom Teams Toolkit mithilfe von Dateien unter `.fx/configs` und `.fx/states` für verschiedene Umgebungen aufgelöst.

Um eine Vorschau des Manifests mit tatsächlichen Inhalten anzuzeigen, generiert Teams Toolkit Vorschaumanifestdateien unter dem `build/appPackage` Ordner:

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
* [Vorschau der Manifestdatei in einer Remoteumgebung](#preview-manifest-file-in-remote-environment)

## <a name="preview-manifest-file-in-local-environment"></a>Vorschau der Manifestdatei in der lokalen Umgebung

Um eine Vorschau der Manifestdatei in der lokalen Umgebung anzuzeigen, können Sie **F5** drücken, um das lokale Debuggen auszuführen. Es generiert lokale Standardeinstellungen für Sie, dann werden das App-Paket und das Vorschaumanifest unter dem `build/appPackage` Ordner erstellt.

Sie können auch eine Vorschau der lokalen Manifestdatei mit zwei Methoden anzeigen.

* Mithilfe der Vorschauoption in codeLens
* Mithilfe der Option **"Teams-Metadatenpaket zippen** "

Die folgenden Schritte helfen ihnen, eine Vorschau der lokalen Manifestdatei mithilfe der Vorschauoption in codelens anzuzeigen:

1. Wählen Sie in der Codelens der Datei **Vorschau** aus `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Screenshot: Vorschau in der Codelens der Manifestdatei":::

1. Wählen Sie **lokal** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Screenshot: Beispiel für die Auswahl von &quot;Lokal&quot; in der Umgebung":::

Die folgenden Schritte helfen bei der Vorschau der lokalen Manifestdatei mithilfe der Option **Zip Teams-Metadatenpaket** :

1. Wählen Sie Datei aus `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Screenshot: Beispiel für die Auswahl von manifest.template.json":::

1. Wählen Sie auf der Visual Studio Code-Symbolleiste das Symbol Teams Toolkit :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: aus.

1. Wählen Sie unter **BEREITSTELLUNG** die Option **Teams-Metadatenpaket zippen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Screenshot: Beispiel für die Auswahl des Zip-Teams-Metadatenpakets":::

1. Wählen Sie **lokal** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-env1.png" alt-text="Screenshot: Beispiel für die Auswahl von &quot;Lokal&quot; in der Umgebung":::

Der Beispielkatalog wird wie in der folgenden Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Screenshot: Beispiel für die Vorschauversion von &quot;local&quot;":::

## <a name="preview-manifest-file-in-remote-environment"></a>Vorschau der Manifestdatei in einer Remoteumgebung

So zeigen Sie eine Vorschau der Manifestdatei mit Visual Studio Code an:

* Wählen Sie in der **Erweiterung "ENTWICKLUNG** in Teams Toolkit" die Option **Bereitstellung in der Cloud** aus.
  
  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/provision.png" alt-text="Screenshot: Beispiel für die Auswahl der Bereitstellung in der Cloudressource.":::

So zeigen Sie eine Vorschau der Manifestdatei mithilfe der Befehlspalette an:

* Teams auslösen **: Bereitstellen in der Cloud über die** Befehlspalette.

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/command palatte.png" alt-text="Screenshot: Bereitstellen einer Cloudressource mithilfe der Befehlspalette":::

Es generiert die Konfiguration für die Teams-Remote-App und erstellt das Paket- und Vorschaumanifest unter dem `build/appPackage` Ordner.

Sie können eine Vorschau der Manifestdatei auch mit zwei Methoden in einer Remoteumgebung anzeigen.

* Mithilfe der Vorschauoption in codeLens
* Mithilfe der Option **"Teams-Metadatenpaket zippen** "

Die folgenden Schritte helfen bei der Vorschau der Manifestdatei mithilfe der Vorschauoption in codelens:

1. Wählen Sie in der Codelens der Datei **Vorschau** aus `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Screenshot ist ein Beispiel für die Vorschau in der Codelens der Manifestdatei.":::

1. Wählen Sie Ihre Umgebung aus.

   > [!NOTE]
   > Wenn es mehr als eine Umgebung gibt, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten (siehe Abbildung):

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Screenshot: Beispiel für das Hinzufügen einer Umgebung":::

Die folgenden Schritte helfen bei der Vorschau der Manifestdatei mithilfe der Option **Zip Teams-Metadatenpaket** in einer Remoteumgebung:

1. Wählen Sie Datei aus `manifest.template.json` .

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manifest-json.png" alt-text="Screenshot: Beispiel für die Auswahl von manifest.template.json":::

1. Wählen Sie auf der Visual Studio Code-Symbolleiste das Symbol Teams Toolkit :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: aus.

1. Wählen Sie unter **BEREITSTELLUNG** die Option **Teams-Metadatenpaket zippen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/teams-metadata-package.png" alt-text="Screenshot: Beispiel für die Auswahl des Zip-Teams-Metadatenpakets":::

1. Wählen Sie Ihre Umgebung aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Screenshot: Beispiel für das Hinzufügen einer Umgebung":::

   > [!NOTE]
   > Wenn es mehr als eine Umgebung gibt, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten (siehe Abbildung):

## <a name="sync-local-changes-to-developer-portal"></a>Lokale Änderungen mit dem Entwicklerportal synchronisieren

Nach dem Anzeigen einer Vorschau der Manifestdatei können Sie Ihre lokalen Änderungen wie folgt mit dem Entwicklerportal synchronisieren:

> [!NOTE]
> Weitere Informationen zum Entwicklerportal finden Sie unter [Entwicklerportal für Teams](../concepts/build-and-test/teams-developer-portal.md).

1. Bereitstellen des Teams-App-Manifests.

   Sie können das Teams-App-Manifest auf eine der folgenden Arten bereitstellen:

   * Wechseln Sie zur `manifest.template.json` Datei, und klicken Sie mit der rechten Maustaste, um aus dem Kontextmenü auszuwählen `Deploy Teams app manifest` .

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-manifest.png" alt-text="Der Screenshot zeigt ein Beispiel für die Auswahl des Teams-App-Manifests bereitstellen.":::

   * Trigger `Teams: Deploy Teams app manifest` aus der Befehlspalette.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/deploy-command.png" alt-text="Screenshot: Beispiel für die Bereitstellung über die Befehlspalette":::

2. Aktualisieren sie auf die Teams-Plattform.

   Sie können auf eine der folgenden Arten auf die Teams-Plattform aktualisieren:

   * Wählen Sie in der linken oberen Ecke von **Auf Teams-Plattform aktualisieren** aus `manifest.{env}.json`.

   * Auslösen von **Teams: Aktualisieren Sie das Manifest auf der Teams-Plattform** auf der Menüleiste von `manifest.{env}.json`.

      :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/update-to-teams.png" alt-text="Screenshot: Beispiel für die Aktualisierung der Teams-Plattform auf der Menüleiste des Manifests.":::

Sie können **teams: Manifest auf der Teams-Plattform** aktualisieren auch über die Befehlspalette auslösen:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Screenshot: Beispiel für die Auswahl von &quot;Teams: Manifest auf Teams-Plattform aktualisieren&quot; aus der Befehlspalette":::

> [!NOTE]
> Der Trigger aus editor codelens oder der Menüleiste aktualisiert die aktuelle Manifestdatei auf der Teams-Plattform. Der Trigger aus der Befehlspalette erfordert die Auswahl der Zielumgebung.

 CLI-Befehl:

``` bash
        teamsfx deploy manifest --include-app-manifest yes
```

---

> [!NOTE]
> Die Änderung wird im Dev Portal aktualisiert. Alle manuellen Updates im Dev Portal werden überschrieben.

Wenn die Manifestdatei aufgrund von Konfigurationsdateiänderungen oder Vorlagenänderungen veraltet ist, wählen Sie eine der folgenden Aktionen aus:

* **Nur Vorschau**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben.
* **Vorschau und Aktualisierung**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben und auch auf die Teams-Plattform aktualisiert.
* **Abbrechen**: Es wird keine Aktion ausgeführt.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="Screenshot ist ein Beispiel für die Navigation, nur Vorschau, Vorschau und Aktualisierung und Abbrechen von Optionen, wenn die Manifestdatei aufgrund von Konfiguration oder Vorlagenänderung veraltet ist.":::

## <a name="customize-your-teams-app-manifest"></a>Anpassen Ihres Teams-App-Manifests

Teams Toolkit besteht aus den folgenden Manifest-Vorlagendateien im `manifest.template.json` Ordner in lokalen und Remote-Umgebungen:

* `manifest.template.json`
* `templates/appPackage`

Während des lokalen Debuggens oder Bereitstellens lädt das Teams-Toolkit das Manifest aus `manifest.template.json`, mit den Konfigurationen aus `state.{env}.json`, `config.{env}.json`und erstellt die Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps).

### <a name="supported-placeholders-in-manifesttemplatejson"></a>Unterstützte Platzhalter in manifest.template.json

Die folgende Liste enthält unterstützte Platzhalter in `manifest.template.json`:

* `{{state.xx}}`ist ein vordefinierter Platzhalter und sein Wert wird vom Teams Toolkit aufgelöst, definiert in `state.{env}.json`. Stellen Sie sicher, dass Sie die Werte in nicht ändern. `state.{env}.json`
* `{{config.manifest.xx}}` ist ein benutzerdefinierter Platzhalter, dessen Wert von aufgelöst wird `config.{env}.json`

**So fügen Sie einen benutzerdefinierten Parameter hinzu**

1. Fügen Sie einen benutzerdefinierten Parameter wie folgt hinzu:</br>
   a. Fügen Sie einen Platzhalter in `manifest.template.json` mit dem Muster `{{config.manifest.xx}}`hinzu.</br>
   b. Fügen Sie einen Konfigurationswert in hinzu `config.{env}.json`.

     ```json
     {
         "manifest": {
          "KEY": "VALUE"
          }
     }
     ```

2. Sie können zur Konfigurationsdatei wechseln, indem Sie einen der Konfigurationsplatzhalter **Go to config file (Zur Konfigurationsdatei wechseln** ) oder **View the state file in (Anzeigen der Zustandsdatei** in `manifest.template.json`) auswählen.

### <a name="validate-manifest"></a>Überprüfen des Manifests

Während Vorgängen wie **Zip Teams-Metadatenpaket** überprüft Teams Toolkit das Manifest anhand seines Schemas. Die folgende Liste enthält verschiedene Möglichkeiten zum Überprüfen des Manifests:

* Lösen Sie `Teams: Validate manifest file` in VSC über die Befehlspalette aus:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/validate.png" alt-text="Screenshot: Beispiel für die Teams-Überprüfungsmanifestdatei aus der Befehlspalette":::

* Verwenden Sie in der CLI den Folgenden Befehl:

     ``` bash
        teamsfx validate --env local
        teamsfx validate --env dev
        ```

---

## To preview values for local and dev environment

In `manifest.template.json`, you can go to codelens to preview the values for `local` and `dev` environment.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/codelens.png" alt-text="Screenshot is an example of showing preview values for local and dev environment.":::

> [!NOTE]
> Provision the environment or execute local debug to generate values for placeholders.

You can go to state file or configuration file by selecting the codelens, which provides a drop-down list with all the environment names. After selecting one environment, the corresponding state file or configuration file opens.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-environment.png" alt-text="Screenshot is an example of showing the selection of an environment.":::

To preview values for all the environments, you can hover over the placeholder. It shows a list with environment names and corresponding values. If you haven't provisioned the environment or executed the local debug, select `Trigger Teams: Provision in the cloud command to see placeholder value` or `Trigger local debug to see placeholder value`.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/hover.png" alt-text="Screenshot is an example of showing the preview values for all environments.":::

::: zone-end

::: zone pivot="visual-studio"

## Edit Teams app manifest using Visual Studio

Teams Toolkit in Visual Studio loads manifest from `manifest.template.json` with configurations from `state.{env}.json` and `config.{env}.json` while provisioning and preparing app dependencies. You can also create Microsoft Teams app in [Developer Portal](https://dev.teams.microsoft.com/apps) with the manifest.

After scaffolding, in the manifest template file under `templates/appPackage` folder,
`manifest.template.json` is shared between local and remote environment.

In the manifest template, select **Project** > **Teams Toolkit** > **Open Manifest File**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png" alt-text="Screenshot is an example of showing the navigation to open manifest file." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-open-manifest.png":::

### Customize app manifest in Teams Toolkit

There are two types of placeholders in `manifest.template.json`:

* `{{state.xx}}` is pre-defined placeholder, whose value is resolved by Teams Toolkit, defined in `state.{env}.json`. It's recommended to not modify the values in `state.{env}.json`.
* `{{config.manifest.xx}}` is customized placeholder, whose value is resolved from `config.{env}.json`.

You can add a customized parameter by:

* Adding a placeholder in `manifest.template.json` with pattern: `{{config.manifest.xx}}`.
* Adding a config value in `config.{env}.json`.

    ```
        {
            "manifest": {
            "KEY": "VALUE"
            }
    }
    ```

### Preview app manifest in Teams Toolkit

You can preview values in app manifest in two ways:

* When you hover over the placeholder in `manifest.template.json`, then you can see the values for **dev** and **local** environment.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png" alt-text="Screenshot is an example showing when you hover over placeholder, can view the values for dev and local environment." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-placeholder1.png":::

* You can also hover over the key besides each placeholder in `manifest.template.json`, and you can see the same values for **dev** and **local** environment.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png" alt-text="Screenshot is an example showing when you hover over key beside placeholder can view the same values for dev and local environment." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-hover-key-placeholder.png":::

   > [!NOTE]
   > If the environment has not been provisioned, or the Teams app dependencies have not been prepared, it indicates that the values for placeholder have not been generated. Please follow the guidance inside hover to generate corresponding values.

### Preview manifest file

To preview the manifest file, you can sideload for local or deploy for Azure. You can preview the manifest file by performing the following step:

* Select **Project** > **Teams Toolkit** and trigger **Prepare Teams App Dependencies** or **Provision in the Cloud** that generates configuration for local or remote Teams app.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png" alt-text="Screenshot is an example of showing preview manifest file." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview-manifest1.png":::

There are two other ways to upload zip app package before you can preview manifest file:

1. From the list of menu select **Project** > **Teams Toolkit** > **Zip App Package**, and select **For Local** or **For Azure**.

    :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png" alt-text="Screenshot is an example of showing the navigation to zip app package for local and azure." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-zip1.png":::

1. You can also upload zip app package from Solution Explorer, if you right-click on **MyTeamsApp1** and then select **Teams Toolkit** > **Zip App Package** > **For Local** or **For Azure**.

  > [!NOTE]
  > In this scenario the project name is **MyTeamsApp1**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png" alt-text="Screenshot is an example of showing the list of Teams toolkit menus from solution explorer." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-solution-explorer1.png":::

Teams Toolkit generates the zip app package, and to preview manifest file content you can follow the step below:

* Right-click on **manifest.template.json** under **appPackage** folder, select **Preview Manifest File** > **For Local** or **For Azure**.

   :::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png" alt-text="Screenshot is an example of showing the preview manifest menu for local and azure." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-preview1.png":::

This displays the preview of the manifest file in Visual Studio.

### Sync local changes to Developer Portal

After you've previewed the manifest file in Visual Studio, you can now sync the local changes to the Developer Portal. Select **Project** > **Teams Toolkit** > **Update Manifest in Teams Developer Portal**, or context menu from Solution Explorer. You can now preview the manifest file in Developer Portal as a result of syncing the local changes.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png" alt-text="Screenshot is an example of showing the navigation to update manifest in Teams developer portal." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-update-manifest1.png":::

The changes are updated to Teams Developer Portal.

> [!NOTE]
>
> * Select **Overwrite and update** or **Cancel** from the **Warning** dialog box to make any manual updates that can be overwritten in the Developer Portal.
> * When you create a Teams command bot using Visual Studio, two app IDs are registered in Azure Active Directory. You can identify the app IDs in the Developer Portal as **Application client ID** under Basic information and existing **Bot ID** under **App features**.

:::image type="content" source="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png" alt-text="Screenshot is an example of showing the update warning." lightbox="../assets/images/Tools-and-SDK-revamp/edit-manifest-for-visual-studio/vs-overwrite.png":::

::: zone-end

## See also

* [Manage multiple environments](TeamsFx-multi-env.md)
* [Reference: Manifest schema for Microsoft Teams](../resources/schema/manifest-schema.md)
* [Public developer preview for Microsoft Teams](../resources/dev-preview/developer-preview-intro.md)
* [Provision cloud resources using Visual Studio](provision-cloud-resources.md)
* [Deploy Teams app to the cloud using Visual Studio](deploy.md#deploy-teams-app-to-the-cloud-using-visual-studio)
