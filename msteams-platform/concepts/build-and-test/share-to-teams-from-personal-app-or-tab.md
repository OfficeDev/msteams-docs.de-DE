---
title: Für Teams über persönliche App oder Registerkarte freigeben
description: Erfahren Sie, wie Sie die Freigabe in Teams hinzufügen, die in Ihrer persönlichen App oder Registerkarte eingebettet sind
ms.topic: reference
ms.localizationpriority: medium
keywords: Freigeben Teams Freigeben für Teams
ms.openlocfilehash: c40263504b77a8a848251431de1eb49b85253b77
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757262"
---
# <a name="share-to-teams-from-personal-app-or-tab"></a>Für Teams über persönliche App oder Registerkarte freigeben

> [!NOTE]
> "Für Teams freigeben" ist derzeit nur in der [öffentlichen Entwicklervorschau](../../resources/dev-preview/developer-preview-intro.md) verfügbar.

Mit "Freigeben für Teams" können Benutzer den Inhalt aus der persönlichen App oder Registerkarte für andere Benutzer oder Gruppen oder Kanäle innerhalb Teams freigeben. Benutzer können "Freigeben" auswählen, um Teams, um die Benutzeroberfläche für Teams in einem Popupfenster zu starten. Im Popupfenster können Benutzer andere Benutzer oder Gruppen oder Kanäle hinzufügen, um den Inhalt freizugeben.

Die folgende Abbildung zeigt das Popupfenster "Für Teams freigeben":

:::image type="content" source="../../assets/images/share-to-teams/share-to-teams.PNG" alt-text="Share-to-Teams-Popup":::

## <a name="enable-share-to-teams-button"></a>Schaltfläche "Freigeben für Teams aktivieren"

> [!NOTE]
> Stellen Sie sicher, dass Sie [über Microsoft Teams JavaScript Client SDK](../../tabs/how-to/using-teams-client-sdk.md) oder [Microsoft Teams JavaScript Client SDK v2 Preview](../../tabs/how-to/using-teams-client-sdk.md) (`@microsoft/teams-js@1.11.0-beta.7`oder höher) verfügen, um "Freigeben" für Ihre persönliche App oder Registerkarte Teams zu ermöglichen.

So aktivieren Sie "Freigeben" für Teams:

1. Erstellen Sie eine persönliche App oder Registerkarte mit **Teams Javascript Client SDK**.

2. Erstellen Sie eine Schaltfläche "**Freigeben für Teams**".

3. Rufen `microsoftTeams.sharing.shareWebContent` Sie auf der Schaltfläche "Freigeben für Teams" eine Inhaltsnutzlast auf.

Im folgenden Beispiel wird erläutert, wie Sie eine Inhaltsnutzlast erstellen:

```json
microsoftTeams.sharing.shareWebContent({
        content: [
          {
            type: 'URL',
            url: '<URL to be shared>',
            message: 'Default message to be loaded in the compose box',
            preview: true
          }
        ]
      });
```

Die Nutzlast enthält die folgenden Parameter:

| Eigenschaftenname | Zweck |
|---|---|
| `type` | Der Typ muss `URL` |
| `url` | `URL` freigegeben werden |
|`message`| Standardnachricht, die im Feld zum Verfassen geladen werden soll |
| `preview` | So eingestellt, dass `true` die URL-Vorschau aktiviert wird |

Die folgende Abbildung zeigt die Option "Für Teams freigeben":

:::image type="content" source="../../assets/images/share-to-teams/share-button.PNG" alt-text="Share-to-Teams-Schaltfläche":::

## <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **100** | DIE API wird auf der aktuellen Plattform nicht unterstützt. |
| **404** | Die angegebene Datei wurde am angegebenen Speicherort nicht gefunden. |
| **500** | Interner Fehler beim Ausführen des erforderlichen Vorgangs. |
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt. |
| **1000** | Vom Benutzer verweigerte Berechtigungen. |
| **2000** | Netzwerkproblem. |
| **3000** | Die zugrunde liegende Hardware unterstützt die Funktion nicht. |
| **4000** | Mindestens ein Argument ist ungültig. |
| **5000** | Der Benutzer ist für diesen Vorgang nicht autorisiert. |
| **6000** | Der Vorgang konnte aufgrund unzureichender Ressourcen nicht abgeschlossen werden. |
| **7000** | Die Plattform hat die Anforderung gedrosselt, da die API zu häufig aufgerufen wurde. |
| **8000** | Der Benutzer hat den Vorgang abgebrochen. |
| **9000** | Der Plattformcode ist alt und implementiert diese API nicht. |
| **10000** | Der Rückgabewert ist zu groß und hat unsere Größengrenzen überschritten. |

## <a name="limitations"></a>Einschränkungen

Die Einschränkungen zum Hinzufügen von "Freigeben" zu Teams Schaltfläche:

* Die Schaltfläche "Für Teams freigeben" kann in einer App gehostet oder eingebettet werden, die innerhalb Teams ausgeführt wird.
* Sie können der App, die mit **Teams Javascript Client SDK** erstellt wurde, die Schaltfläche "Freigeben" zu Teams hinzufügen.

## <a name="end-user-share-to-teams-experience"></a>Endbenutzerfreigabe für Teams

Nachdem Sie die Schaltfläche "Für Teams freigeben" auf der persönlichen App oder Registerkarte aktiviert haben, können Sie den Inhalt freigeben. Führen Sie die folgenden Schritte aus, um auf den Zugriff zuzugreifen:

1. Öffnen Sie eine persönliche App oder Registerkarte, und wählen Sie **"Freigeben" aus, um Teams**.

    :::image type="content" source="../../assets/images/share-to-teams/share-button.PNG" alt-text="Share-to-Teams-Schaltfläche":::

2. Fügen Sie andere Benutzer oder Gruppen oder Kanäle hinzu, um den Inhalt freizugeben.

    :::image type="content" source="../../assets/images/share-to-teams/add-recepient.PNG" alt-text="Add-Empfänger":::

    > [!NOTE]
    > Sie können dazu eine Notiz **hinzufügen.**

3. Wählen Sie **Freigeben** aus.

   :::image type="content" source="../../assets/images/share-to-teams/add-notes.PNG" alt-text="Add-Note":::

4. Wählen Sie **"Ansicht"** aus, um die Unterhaltung zu erreichen, in der der Link freigegeben wurde.

   :::image type="content" source="../../assets/images/share-to-teams/link-shared.PNG" alt-text="Share-to-teams-link-shared":::

## <a name="see-also"></a>Siehe auch

* [Von Web-Apps für Teams freigeben](share-to-teams-from-web-apps.md)
* [Erstellen einer persönlichen Registerkarte](../../tabs/how-to/create-personal-tab.md)
