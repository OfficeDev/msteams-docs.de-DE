---
title: Vorschau Teams App-Manifests in Teams Toolkit
author: zyxiaoyuer
description: Vorschau des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 453dc7e3c2698504ea755cd4564f588cdd95ba36
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435370"
---
# <a name="preview-teams-app-manifest-in-teams-toolkit"></a>Vorschau Teams App-Manifests in Teams Toolkit

Nach dem Erstellen des Gerüsts sind die Manifestvorlagendateien im Ordner verfügbar `templates/appPackage` :

- `manifest.local.template.json` – lokale Debug-Teams-App.
- `manifest.remote.template.json` – freigegeben zwischen allen Remoteumgebungen.

Die Vorlagendateien, die aus Platzhaltern bestehen, und die tatsächlichen Werte aus Teams Toolkit werden in Dateien unter `.fx/configs` und `.fx/states`aufgelöst.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

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

### <a name="preview-local-manifest-file"></a>Lokale Manifestdatei in der Vorschau anzeigen

Um eine Vorschau der Manifestdatei der lokalen Teams-App anzuzeigen, müssen Sie **F5** drücken, um das lokale Debuggen auszuführen. Es generiert lokale Standardeinstellungen für Sie, dann die App-Paket- und Vorschaumanifestbuilds unter **dem Ordner "build/appPackage** ".

Sie können auch eine Vorschau des lokalen Manifests anzeigen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie in der Codelens der Datei **"manifest.local.template.json" die** Option **"Vorschau**" aus.
2. Wählen Sie in der Menüleiste der Datei **manifest.local.template.json** die Option "**Vorschaumanifestdatei**" aus.
3. Wählen Sie **zip Teams Metadatenpaket** in der Strukturansicht aus, und wählen Sie **Lokal** aus.
Das Lokale der Vorschau wird wie in der Abbildung dargestellt angezeigt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/preview-1.png" alt-text="Preview":::

### <a name="preview-manifest-in-remote-environment"></a>Vorschaumanifest in Remoteumgebung

Wenn Sie eine Vorschau der Manifestdatei der Remote-Teams-App anzeigen möchten, wählen Sie **"Bereitstellung in der Cloud**" im **BEREICH "ENTWICKLUNG**" der Strukturansicht der Teams Toolkit-Erweiterung aus, oder lösen **Sie Teams aus: Bereitstellung in der Cloud über die** Befehlspalette. Sie generiert die Konfiguration für die Remote-Teams-App und erstellt das Paket- und Vorschaumanifest unter dem Ordner **"build/appPackage** ".

Sie können auch eine Vorschau des Manifests in einer Remoteumgebung anzeigen, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie in der Codelens der Datei **"manifest.remote.template.json" die** Option **"Vorschau**" aus.
2. Wählen Sie in der Menüleiste der Datei **"manifest.remote.template.json" die** Option "**Vorschaumanifestdatei**" aus.
3. Wählen Sie **zip Teams Metadatenpaket** in der Strukturansicht aus.
4. Wählen Sie Ihre Umgebung aus.

Wenn mehrere Umgebungen vorhanden sind, müssen Sie die Umgebung auswählen, die Sie in der Vorschau anzeigen möchten, wie in der Abbildung dargestellt:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="Hinzufügen von &quot;env&quot;":::

## <a name="sync-local-changes-to-dev-portal"></a>Synchronisieren lokaler Änderungen mit dem Dev-Portal

Nach der Vorschau der Manifestdatei können Sie Ihre lokalen Änderungen mit dem Dev-Portal synchronisieren, indem Sie die folgenden Schritte ausführen:

1.  Wählen Sie in der oberen linken Ecke von **Aktualisieren auf Teams Plattform** aus.`manifest.{env}.json`
2. Select **Teams: Update manifest to Teams platform** at the menu bar of`manifest.{env}.json`

 Sie können auch **Teams auslösen: Aktualisieren des Manifests auf Teams Plattform** über die Befehlspalette

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pre.png" alt-text="Strukturansicht":::

> [!NOTE]
> Trigger from editor codelens or **title** will update current manifest file to Teams platform. Für das Auslösen aus der Befehlspalette muss die Zielumgebung ausgewählt werden.

Wenn die Manifestdatei aufgrund von Konfigurationsdateiänderungen oder Vorlagenänderungen veraltet ist, stellen Sie sicher, dass Die folgende Aktion bestätigt wird:

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview -3.png" alt-text="pre":::

- **Nur Vorschau**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben.
- **Vorschau und Aktualisierung**: Die lokale Manifestdatei wird gemäß der aktuellen Konfiguration überschrieben und auch auf Teams Plattform aktualisiert.
- **Abbrechen**: Nichts tun

> [!NOTE]
> Die Änderungen werden auf das Entwicklungsportal aktualisiert. Wenn Sie über einige manuelle Updates im Dev Portal verfügen, wird es überschrieben.

## <a name="see-also"></a>Siehe auch

[Anpassen Teams App-Manifests im Teams Toolkit](TeamsFx-manifest-customization.md)
