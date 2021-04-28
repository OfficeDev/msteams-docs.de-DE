---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 0afcce50a4779421016c23c4ec4e3d25cc3401d1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058614"
---
# <a name="add-a-default-install-scope-and-group-capability"></a>Hinzufügen eines Standardinstallationsbereichs und einer Gruppenfunktion

Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen. Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**

![Eine App hinzufügen](../../assets/images/compose-extensions/addanapp.png)

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
> [Auswählen, wie Ihre App verbreitet werden soll](overview.md)
