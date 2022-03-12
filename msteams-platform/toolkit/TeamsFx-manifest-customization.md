---
title: Anpassen Teams App-Manifests im Teams Toolkit
author: zyxiaoyuer
description: Anpassen des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 047cd9bcd86c103c3c9cab22793fb7d187f7493d
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453600"
---
# <a name="customize-app-manifest-in-teams-toolkit"></a>Anpassen des App-Manifests im Teams Toolkit

Teams Toolkit besteht aus den folgenden Manifestvorlagendateien im `templates/appPackage` Ordner:

* `manifest.local.template.json` – lokale Debug-Teams-App
* `manifest.remote.template.json` – in allen Umgebungen freigegeben

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

Während der Bereitstellung lädt Teams Toolkit das Manifest aus `manifest.remote.template.json`, kombiniert mit Konfigurationen von `state.{env}.json` und `config.{env}.json`erstellt teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps).

Während des lokalen Debuggens lädt Teams Toolkit das Manifest aus `manifest.local.template.json`, kombiniert mit Konfigurationen von `localSettings.json`, und erstellt die Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps).

## <a name="supported-placeholder-in-manifestremotetemplatejson"></a>Unterstützter Platzhalter in "manifest.remote.template.json"

* `{{state.xx}}`ist ein vordefinierter Platzhalter, dessen Wert durch Teams Toolkit aufgelöst wird, definiert in `state.{env}.json`. Ändern Sie die Werte nicht im Zustand. {env}.json.
* `{{config.manifest.xx}}`ist ein angepasster Platzhalter, dessen Wert aufgelöst wird.`config.{env}.json`
  * Sie können einen angepassten Parameter wie folgt hinzufügen:
    * Fügen Sie einen Platzhalter in "manifest.remote.template.json" mit Muster hinzu: `{{config.manifest.xx}}`
    * Fügen Sie einen Konfigurationswert in der Konfiguration hinzu. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

    Neben jedem Konfigurationsplatzhalter in `manifest.remote.template.json`gibt es eine `Go to config file`. Sie können zur Konfigurationsdatei navigieren, indem Sie sie auswählen.

## <a name="supported-placeholder-in-manifestlocaltemplatejson"></a>Unterstützter Platzhalter in "manifest.local.template.json"

`{{localSettings.xx}}`ist ein vordefinierter Platzhalter, dessen Wert durch Teams Toolkit aufgelöst wird, definiert in `localSettings.json`. Ändern Sie die Werte in "localSettings.json" nicht.

 > [!NOTE]
 > Stellen Sie sicher, dass Sie das lokale Manifest nicht anpassen.

## <a name="see-also"></a>Siehe auch

[Vorschau Teams App-Manifests in Teams Toolkit](TeamsFx-manifest-preview.md)
