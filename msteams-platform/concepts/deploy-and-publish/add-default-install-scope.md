---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 561a4f2910e703db5ffce6176f6177dfd661d2ce
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230932"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a>Konfigurieren von Standardinstallationsoptionen für Ihre Microsoft Teams App

Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen. Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**

:::row:::
   :::column span="2":::

![Hinzufügen eines App-Dropdownbeispiels](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="configure-your-apps-default-install-scope"></a>Konfigurieren des Standardinstallationsbereichs Ihrer App

Konfigurieren Sie den Standardinstallationsbereich für Ihre App. Sie können immer nur einen Bereich festlegen.

**So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest**

1. Öffnen Sie Ihr App-Manifest, und fügen Sie die Eigenschaft `defaultInstallScope` hinzu.
2. Legen Sie den Standardinstallationsbereichswert als `personal` , `team` , oder `groupchat` . `meetings`

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Konfigurieren der Standardfunktion für freigegebene Bereiche

Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Gruppenchat installiert ist.

> [!NOTE]
> `defaultGroupCapability` bietet die Standardfunktion, die dem Team, dem Groupchat oder der Besprechung hinzugefügt wird. Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus, Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.

**So konfigurieren Sie Details im App-Manifest**

1. Öffnen Sie Ihr App-Manifest, und fügen Sie `defaultGroupCapability` die -Eigenschaft hinzu.
2. Legen Sie den Wert `team` , `groupchat` oder . `meetings`
3. Für die ausgewählte Gruppenfunktion sind die verfügbaren Gruppenfunktionen , `bot` `tab` oder `connector` . 

    > [!NOTE]
    > Sie können nur eine Standardfunktion, `bot` , , oder für die ausgewählte `tab` `connector` Gruppenfunktion auswählen.

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
