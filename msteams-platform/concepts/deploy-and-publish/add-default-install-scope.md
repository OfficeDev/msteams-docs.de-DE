---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Erfahren Sie, wie Sie die Standardinstallationsoptionen und Die Standardfunktion Ihrer Teams-App für gemeinsame Bereiche angeben.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: 9055b765c30f83c4031ad0e2ba5f18f4e747ac3f
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66122901"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a>Konfigurieren von Standardinstallationsoptionen für Ihre Microsoft Teams-App

Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Möglicherweise haben Sie sie mit einem bestimmten Bereich und einer bestimmten Funktion entworfen. Wenn Ihre App beispielsweise in erster Linie für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, **"Zu einem Team hinzufügen"** lautet.

:::row:::
   :::column span="2":::

![Beispiel zum Hinzufügen eines App-Dropdowns](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="configure-your-apps-default-install-scope"></a>Konfigurieren des Standardinstallationsbereichs Ihrer App

Konfigurieren Sie den Standardinstallationsbereich für Ihre App. Sie können jeweils nur einen Bereich festlegen.

So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest:

1. Öffnen Sie Ihr App-Manifest, und fügen Sie die `defaultInstallScope` Eigenschaft hinzu.
2. Legen Sie den Standardinstallationsbereichswert entweder `personal`als , `team`, `groupchat`oder `meetings`fest.

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Konfigurieren der Standardfunktion für freigegebene Bereiche

Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder ein Gruppenchat installiert wird.

> [!NOTE]
> `defaultGroupCapability` stellt die Standardfunktion bereit, die dem Team, dem Gruppenchat oder der Besprechung hinzugefügt wird. Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus. Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.

So konfigurieren Sie Details im App-Manifest:

1. Öffnen Sie Das App-Manifest, und fügen Sie die `defaultGroupCapability` Eigenschaft hinzu.
2. Legen Sie einen Wert von `team`, `groupchat`oder `meetings`fest.
3. Für die ausgewählte Gruppenfunktion sind die verfügbaren Gruppenfunktionen: , `bot`, `tab`oder `connector`.

    > [!NOTE]
    > Sie können nur eine Standardfunktion oder `bot``tab``connector` für die ausgewählte Gruppenfunktion auswählen.

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Ihres App-Pakets](~/concepts/build-and-test/apps-package.md)
