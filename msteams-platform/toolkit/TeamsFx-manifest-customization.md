---
title: Anpassen des Teams-App-Manifests im Teams-Toolkit
author: zyxiaoyuer
description: Anpassen des Teams-App-Manifests
ms.author: nliu
ms.localizationpriority: high
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 28a06da170ee52e4340aa3d401d39ad08f58e2ba
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65110260"
---
# <a name="customize-app-manifest-in-toolkit"></a>Passen Sie das App-Manifest in Toolkit an

Teams Toolkit besteht aus den folgenden Manifest-Vorlagendateien im `manifest.template.json` Ordner in lokalen und Remote-Umgebungen:

* `manifest.template.json`
* `templates/appPackage`


## <a name="prerequisite"></a>Voraussetzungen

* Installieren Sie die [neueste Version des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

> [!TIP]
> Stellen Sie sicher, dass Sie das Team-App-Projekt in Visual Studio Code geöffnet haben.

Während des lokalen Debuggens oder Bereitstellens lädt das Teams-Toolkit das Manifest aus `manifest.template.json`, mit Konfigurationen aus `state.{env}.json`, `config.{env}.json`und erstellt die Teams-App im [Dev-Portal](https://dev.teams.microsoft.com/apps).


## <a name="placeholders-supported-in-manifesttemplatejson"></a>In manifest.template.json unterstützte Platzhalter

* `{{state.xx}}`ist ein vordefinierter Platzhalter und sein Wert wird vom Teams Toolkit aufgelöst, definiert in `state.{env}.json`. Stellen Sie sicher, dass Sie die Werte in state.{env}.json nicht ändern
* `{{config.manifest.xx}}` ist ein benutzerdefinierter Platzhalter, dessen Wert aufgelöst wird `config.{env}.json`

  1. Sie können einen benutzerdefinierten Parameter wie folgt hinzufügen:
      1. Fügen Sie einen Platzhalter in manifest.template.json mit Muster hinzu: `{{config.manifest.xx}}`
      2. Fügen Sie einen Konfigurationswert in config.{env}.json hinzu

        ```json
        {
            "manifest": {
                "KEY": "VALUE"
            }
        }
        ```

   2. Sie können zur Konfigurationsdatei navigieren, indem Sie einen der Konfigurationsplatzhalter **Go to config file** oder **View the state file** in auswählen `manifest.template.json`

## <a name="see-also"></a>Siehe auch

[Zeigen Sie eine Vorschau des Teams-App-Manifests im Teams-Toolkit an](TeamsFx-manifest-preview.md)
