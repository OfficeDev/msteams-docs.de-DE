---
title: Vorschau Teams App-Manifests im Teams Toolkit
author: zyxiaoyuer
description: Vorschau des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 91bc070d30136ce1f004676172594f26ca37dea5
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111871"
---
# <a name="preview-app-manifest-in-toolkit"></a>Vorschau des App-Manifests im Toolkit

Die Manifestvorlagendatei `manifest.template.json` ist nach dem Gerüstbau unter `templates/appPackage` Ordner verfügbar. Die Vorlagendatei mit Platzhaltern und die tatsächlichen Werte werden vom Teams-Toolkit aus Dateien unter `.fx/configs` und `.fx/states` für verschiedene Umgebungen aufgelöst.

## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

## <a name="preview-manifest"></a>Vorschaumanifest

Um eine Vorschau des Manifests mit echtem Inhalt zu erhalten, generiert Teams Toolkit eine Vorschau der Manifestdateien im `build/appPackage` Ordner:

```text
└───build
    └───appPackage
        ├───appPackage.{env}.zip - Zipped app package of remote teams app
        ├───appPackage.local.zip - Zipped app package of local team app
        ├───manifest.{env}.json  - Previewed manifest of remote teams app
        └───manifest.local.json  - Previewed manifest of local teams app
```

### <a name="preview-local-manifest-file"></a>Vorschau der lokalen Manifestdatei

Um eine Vorschau der Manifestdatei der lokalen Teams-App anzuzeigen, können Sie **F5** drücken, um das lokale Debuggen auszuführen. Es generiert lokale Standardeinstellungen für Sie, dann werden das App-Paket und das Vorschaumanifest unter dem `build/appPackage` Ordner erstellt.

Sie können auch eine Vorschau des lokalen Manifests anzeigen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie **Vorschau** in den Codelen der `manifest.template.json` Datei und **dann Lokal** aus
2. Auswählen der **Vorschaumanifestdatei** auf der Menüleiste der `manifest.template.json` Datei
3. Wählen Sie **Zip Teams-Metadatenpaket** in Treeview aus, und wählen Sie **lokal** aus

Der Beispielkatalog wird wie in der folgenden Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Preview":::

### <a name="preview-manifest-in-remote-environment"></a>Vorschaumanifest in Remoteumgebung

Um eine Vorschau der Manifestdatei der Remote-Teams-App anzuzeigen, wählen Sie **Bereitstellung in der Cloud** im Bereich **DEVELOPMENT** der Treeview der Teams Toolkit-Erweiterung aus, oder lösen Sie **Teams: Bereitstellung in der Cloud** über die Befehlspalette aus. Es generiert die Konfiguration für die Remote-Teams-App und erstellt das Paket- und Vorschaumanifest unter dem `build/appPackage` Ordner.

Sie können auch eine Vorschau des Manifests in der Remoteumgebung anzeigen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie **Vorschau** in den Codelen der `manifest.template.json` Datei aus 
2. Auswählen der **Vorschaumanifestdatei** auf der Menüleiste der `manifest.template.json` Datei
3. Auswählen **des Zip-Teams-Metadatenpakets** in der Treeview
4. Ihre Umgebung auswählen

Wenn es mehr als eine Umgebung gibt, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten (siehe Abbildung):

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="sync-local-changes-to-developer-portal"></a>Lokale Änderungen mit dem Entwicklerportal synchronisieren

Nachdem Sie die Manifestdatei in der Vorschau angezeigt haben, können Sie Ihre lokalen Änderungen mit dem Developer Portal synchronisieren, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie in **Update auf Teams Platform** in der oberen linken Ecke von `manifest.{env}.json`
2. Wählen Sie **Teams: Aktualisieren des Manifests auf Teams Plattform** auf der Menüleiste von `manifest.{env}.json`

 Sie können auch **Teams: Aktualisieren des Manifests auf Teams Plattform** über die Befehlspalette ausführen:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Strukturansicht":::

> [!NOTE]
> Trigger aus Editor-Codelens oder **Titel**  aktualisiert die aktuelle Manifestdatei auf der Teams-Plattform. Für den Trigger aus der Befehlspalette muss die Zielumgebung ausgewählt werden

  

Wenn die Manifestdatei aufgrund einer Änderung der Konfigurationsdatei oder einer Vorlagenänderung veraltet ist, wählen Sie eine der folgenden Aktionen aus:

* **Nur Vorschau**: Lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben
* **Vorschau und Update**: Lokale Manifestdatei wird entsprechend der aktuellen Konfiguration überschrieben und auch auf Teams-Plattform aktualisiert
* **Abbrechen**: Es wird keine Aktion ausgeführt

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::



> [!NOTE]
> Die Änderungen werden im Dev Portal aktualisiert. Alle manuellen Updates im Entwicklerportal werden überschrieben.

## <a name="see-also"></a>Siehe auch

[Anpassen des Teams App-Manifests im Teams Toolkit](TeamsFx-manifest-customization.md)
