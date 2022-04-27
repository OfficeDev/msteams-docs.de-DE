---
title: Anpassen Teams App-Manifests im Teams Toolkit
author: zyxiaoyuer
description: Anpassen des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: de85674891a53c1e87b43ae1d472daf35716c348
ms.sourcegitcommit: 3bfd0d2c4d83f306023adb45c8a3f829f7150b1d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65073540"
---
# <a name="customize-app-manifest-in-toolkit"></a>Anpassen des App-Manifests im Toolkit

Teams Toolkit besteht aus den folgenden Manifestvorlagendateien unter `manifest.template.json` ordnerübergreifenden lokalen und Remoteumgebungen:

* `manifest.template.json`
* `templates/appPackage`


## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Stellen Sie sicher, dass Teams App-Projekt in Visual Studio Code geöffnet ist.

Während des lokalen Debuggens oder der lokalen Bereitstellung lädt Teams Toolkit manifest aus `manifest.template.json`, mit Konfigurationen von `state.{env}.json`, `config.{env}.json`und erstellt die Teams-App im [Dev Portal](https://dev.teams.microsoft.com/apps).


## <a name="placeholders-supported-in-manifesttemplatejson"></a>In manifest.template.json unterstützte Platzhalter

* `{{state.xx}}`ist vordefinierter Platzhalter, und sein Wert wird durch Teams Toolkit aufgelöst, definiert in `state.{env}.json`. Stellen Sie sicher, dass die Werte nicht im Zustand geändert werden. {env}.json
* `{{config.manifest.xx}}` ist benutzerdefinierter Platzhalter, und sein Wert wird von `config.{env}.json`

  1. Sie können einen benutzerdefinierten Parameter wie folgt hinzufügen:
      1. Fügen Sie einen Platzhalter in "manifest.template.json" mit dem Muster hinzu: `{{config.manifest.xx}}`
      2. Fügen Sie einen Config-Wert in config hinzu. {env}.json

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

   2. Sie können zur Konfigurationsdatei navigieren, indem Sie einen der Konfigurationsplatzhalter " **Gehe zu Konfigurationsdatei** " oder **"Statusdatei anzeigen** in" auswählen. `manifest.template.json`

## <a name="see-also"></a>Siehe auch

[Vorschau Teams App-Manifests im Teams Toolkit](TeamsFx-manifest-preview.md)
