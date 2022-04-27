---
title: Vorschau Teams App-Manifests im Teams Toolkit
author: zyxiaoyuer
description: Vorschau des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 57dc719f872d502beded14c30a09d72c27ee74c3
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073282"
---
# <a name="preview-app-manifest-in-toolkit"></a>Vorschau des App-Manifests im Toolkit

Die Manifestvorlagendatei `manifest.template.json` steht nach dem Gerüst unter `templates/appPackage` dem Ordner zur Verfügung. Die Vorlagendatei mit Platzhaltern und den tatsächlichen Werten wird vom Teams Toolkit aus Dateien unter `.fx/configs` und `.fx/states` für verschiedene Umgebungen aufgelöst.

## <a name="prerequisite"></a>Voraussetzungen

* Installieren der [neuesten Version von Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

## <a name="preview-manifest"></a>Vorschaumanifest

Um eine Vorschau des Manifests mit echtem Inhalt anzuzeigen, generiert Teams Toolkit Vorschaumanifestdateien unter `build/appPackage` dem Ordner:

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

1. Wählen Sie "**Vorschau**" in den Codelen der `manifest.template.json` Datei und **dann "Lokal**" aus.
2. Auswählen der **Vorschaumanifestdatei** auf der Menüleiste der `manifest.template.json` Datei
3. Wählen Sie **in der Strukturansicht zippen Teams Metadatenpaket** aus, und wählen Sie **"Lokal**" aus.

Die lokale Vorschau wird wie im Bild dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-23.png" alt-text="Preview":::

### <a name="preview-manifest-in-remote-environment"></a>Vorschaumanifest in Remoteumgebung

Wenn Sie eine Vorschau der Manifestdatei der Remoteteams-App anzeigen möchten, wählen Sie **in der** **Strukturansicht** Teams Toolkit-Erweiterung "Bereitstellung in der Cloud" aus, oder lösen **Sie Teams aus: Bereitstellen in der Cloud über die** Befehlspalette. Es generiert die Konfiguration für die Remote-Teams-App und erstellt das Paket- und Vorschaumanifest unter dem `build/appPackage` Ordner.

Sie können auch eine Vorschau des Manifests in der Remoteumgebung anzeigen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie " **Vorschau** " in den Codelen der Datei aus `manifest.template.json` .
2. Auswählen der **Vorschaumanifestdatei** auf der Menüleiste der `manifest.template.json` Datei
3. Auswählen **des Zip-Teams-Metadatenpakets** in der Strukturansicht
4. Wählen Sie Ihre Umgebung aus

Wenn mehrere Umgebungen vorhanden sind, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten, wie in der Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="env hinzufügen":::

## <a name="sync-local-changes-to-developer-portal"></a>Lokale Änderungen mit dem Entwicklerportal synchronisieren

Nachdem Sie die Manifestdatei in der Vorschau angezeigt haben, können Sie Ihre lokalen Änderungen mit dem Entwicklerportal synchronisieren, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie in **Teams der** oberen linken Ecke von`manifest.{env}.json`
2. Wählen Sie **Teams aus: Aktualisieren des Manifests auf Teams Plattform** auf der Menüleiste von`manifest.{env}.json`

 Sie können auch **Teams auslösen: Aktualisieren des Manifests auf Teams Plattform** über die Befehlspalette:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Strukturansicht":::

> [!NOTE]
> Wird von Editorcodelens oder **Titelaktualisierungen** der aktuellen Manifestdatei auf Teams Plattform ausgelöst. Der Trigger aus der Befehlspalette erfordert die Auswahl der Zielumgebung.

  

Wenn die Manifestdatei aufgrund von Konfigurationsdateiänderungen oder Vorlagenänderungen veraltet ist, wählen Sie eine der folgenden Aktionen aus:

* **Nur Vorschau**: Lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben
* **Vorschau und Update**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben und auch auf Teams Plattform aktualisiert.
* **Abbrechen**: Es wird keine Aktion ausgeführt.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::



> [!NOTE]
> Die Änderungen werden im Dev Portal aktualisiert. Alle manuellen Updates im Entwicklerportal werden überschrieben.

## <a name="see-also"></a>Siehe auch

[Anpassen Teams App-Manifests im Teams Toolkit](TeamsFx-manifest-customization.md)
