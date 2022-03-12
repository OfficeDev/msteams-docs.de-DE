---
title: Konfigurieren der Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Die Standardinstallationsoptionen und die Standardfunktion Ihrer App für freigegebene Bereiche angegeben werden.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: surbhigupta
ms.openlocfilehash: a6857e549c688bd7078aeaceae4b9f5a885ae2c3
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453208"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a>Konfigurieren der Standardinstallationsoptionen für Ihre Microsoft Teams-App

Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Bereich und einer bestimmten Funktion entworfen. Wenn Ihre App beispielsweise in erster Linie für die Verwendung im Team oder Kanal vorgesehen ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, **"Zu einem Team hinzufügen**" ist.

:::row:::
   :::column span="2":::

![Hinzufügen eines App-Dropdownbeispiels](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch als Standardfunktion festlegen, wenn ein Benutzer Ihre App in einem Team installiert.

## <a name="configure-your-apps-default-install-scope"></a>Konfigurieren des Standardmäßigen Installationsumfangs Ihrer App

Konfigurieren Sie den Standardinstallationsbereich für Ihre App. Sie können jeweils nur einen Bereich festlegen.

So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest:

1. Öffnen Sie Das App-Manifest, und fügen Sie die `defaultInstallScope` Eigenschaft hinzu.
2. Legen Sie den Standardmäßigen Installationsbereichswert als , `personal`, `team``groupchat`oder `meetings`fest.

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).

## <a name="configure-the-default-capability-for-shared-scopes"></a>Konfigurieren der Standardfunktion für freigegebene Bereiche

Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Gruppenchat installiert wird.

> [!NOTE]
> `defaultGroupCapability` stellt die Standardfunktion bereit, die dem Team, dem Gruppenchat oder der Besprechung hinzugefügt wird. Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus. Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.

So konfigurieren Sie Details im App-Manifest:

1. Öffnen Sie Ihr App-Manifest, und fügen Sie die `defaultGroupCapability` Eigenschaft hinzu.
2. Legen Sie den Wert `team`, `groupchat`or fest `meetings`.
3. Für die ausgewählte Gruppenfunktion sind die verfügbaren Gruppenfunktionen , `bot``tab`oder `connector`.

    > [!NOTE]
    > Sie können nur eine Standardfunktion `bot``tab`oder `connector` für die ausgewählte Gruppenfunktion auswählen.

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
