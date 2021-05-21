---
title: Reine Benachrichtigungsbots
description: Beschreibt, welche Nur-Benachrichtigungs-Bots in Microsoft Teams
keywords: Teams-Bots-Benachrichtigung
ms.topic: conceptual
localization_priority: Normal
ms.date: 01/29/2020
ms.openlocfilehash: 3de462f73733f5f7cf223444ffe6deeb53faaaaa
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566761"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Nur-Benachrichtigungs-Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots die Zustellung von Benachrichtigungen an Benutzer ist und keine Unterhaltung ist, können Sie das Feld in Ihrem `isNotificationOnly` App-Manifest aktivieren. Dadurch werden die folgenden Änderungen vorgenommen:

* Benutzer können Ihren Benachrichtigungsbot nicht senden.
* Benutzer können @mention bot nicht erstellen.

> [!NOTE]
> Die Nur-Bot-Apps werden in beiden Fällen im Tablett der persönlichen App `isNotificationOnly: true` angezeigt: oder `isNotificationOnly: false` .

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, legen Sie auf `isNotificationOnly` `true` .

> [!NOTE]
> Beachten Sie, dass der Wert von `isNotificationOnly` boolesch und keine Zeichenfolge ist.

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "isNotificationOnly": true,
      "scopes": [
        "personal",
        "team"
      ],
    }
  ],
  ...
}
```

## <a name="best-practices-and-limitations"></a>Bewährte Methoden und Einschränkungen

* Benachrichtigungsbots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
