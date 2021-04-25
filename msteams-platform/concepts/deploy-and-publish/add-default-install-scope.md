---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a4b70df70c7b9442e29953dae8a8c4e892cb72c1
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946490"
---
# <a name="add-a-default-install-scope-and-group-capability"></a>Hinzufügen eines Standardinstallationsbereichs und einer Gruppenfunktion

Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen. Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**

![Eine App hinzufügen](../../assets/images/compose-extensions/addanapp.png)

Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert. 

## <a name="configure-your-apps-default-install-scope"></a>Konfigurieren des Standardinstallationsbereichs Ihrer App

Konfigurieren Sie den Standardinstallationsbereich für Ihre App. Sie können immer nur einen Bereich festlegen.

**So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest**

1. Öffnen Sie Ihr App-Manifest, und fügen Sie die Eigenschaft `defaultInstallScope` hinzu.
2. Legen Sie einen Wert von `personal` , , , oder `team` `groupchat` `meetings` (siehe ein Beispiel unten)

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Konfigurieren der Standardfunktion für freigegebene Bereiche

Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Chat installiert ist.

**So konfigurieren Sie Details im App-Manifest**

1. Öffnen Sie Ihr App-Manifest, und fügen Sie `defaultGroupCapability` die -Eigenschaft hinzu.
2. Speichern Sie die Updates.

    Es folgt ein JSON-Beispiel:

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```
> [!NOTE]
> Informationen zum vollständigen Schema finden Sie unter [Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Auswählen, wie Ihre App verbreitet werden soll](overview.md)
