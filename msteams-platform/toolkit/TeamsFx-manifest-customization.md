---
title: Anpassen Teams App-Manifests in Teams Toolkit
author: zyxiaoyuer
description: Anpassen Teams App-Manifests
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 34b454f63eb900fce2f38748838ce46558835ac5
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61228106"
---
# <a name="customize-teams-app-manifest-in-teams-toolkit"></a>Anpassen Teams App-Manifests in Teams Toolkit

Teams Toolkit besteht aus zwei Manifestvorlagendateien im `templates/appPackage` Ordner:

- `manifest.local.template.json` – lokale Debug-Teams-App
- `manifest.remote.template.json` – in allen Umgebungen freigegeben

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Sie sollten bereits ein Teams App-Projekt in VS-Code geöffnet haben.

Während der Bereitstellung lädt Teams Toolkit das Manifest aus `manifest.remote.template.json` , kombiniert mit Konfigurationen von und `state.{env}.json` `config.{env}.json` . Anschließend wird eine Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps) mit diesem Manifest erstellt.

Während des lokalen Debuggens lädt Teams Toolkit das Manifest aus `manifest.local.template.json` , kombiniert mit Konfigurationen von `localSettings.json` . Anschließend wird eine Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps) mit diesem Manifest erstellt.

## <a name="supported-placeholder-in-manifestremotetemplatejson"></a>Unterstützter Platzhalter in "manifest.remote.template.json"

- `{{state.xx}}`ist ein vordefinierter Platzhalter, dessen Wert durch Teams Toolkit aufgelöst wird, definiert in `state.{env}.json` . Sie sollten die Werte nicht im Zustand ändern. {env}.json.
- `{{config.manifest.xx}}` ist ein angepasster Platzhalter, dessen Wert aufgelöst `config.{env}.json` wird.
  - Sie können einen angepassten Parameter wie folgt hinzufügen:
    - Fügen Sie einen Platzhalter in "manifest.remote.template.json" mit Muster hinzu: `{{config.manifest.xx}}`
    - Fügen Sie einen Konfigurationswert in der Konfiguration hinzu. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

    Neben jedem Konfigurationsplatzhalter in `manifest.remote.template.json` gibt es eine `Go to config file` Schaltfläche. Sie können zur Konfigurationsdatei navigieren, indem Sie sie wie in der Abbildung dargestellt auswählen:

    ![zur Konfigurationsdatei wechseln](./images/gotoconfigfile.png)

## <a name="supported-placeholder-in-manifestlocaltemplatejson"></a>Unterstützter Platzhalter in "manifest.local.template.json"

`{{localSettings.xx}}`ist ein vordefinierter Platzhalter, dessen Wert durch Teams Toolkit aufgelöst wird, definiert in `localSettings.json` . Sie sollten die Werte in "localSettings.json" nicht ändern.

 > [!NOTE]
 > Die Anpassung des lokalen Manifests wird nicht vorgeschlagen.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Vorschau Teams App-Manifests im Teams Toolkit](TeamsFx-manifest-preview.md)
