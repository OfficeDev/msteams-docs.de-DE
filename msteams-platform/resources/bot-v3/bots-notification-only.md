---
title: Reine Benachrichtigungsbots
description: Beschreibt, welche Nur-Benachrichtigungs-Bots in Microsoft Teams
keywords: Teams Bots Benachrichtigung
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
# <a name="notification-only-bots-in-microsoft-teams"></a>Nur Benachrichtigungsbots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benutzern Benachrichtigungen zu übermitteln, und nicht konversationsfähig ist, können Sie das `isNotificationOnly` Feld in Ihrem App-Manifest aktivieren. Dies führt zu den folgenden Änderungen:

* Benutzer können ihren Benachrichtigungsbot nicht mit einer Benachrichtigung snoten.
* Benutzer können den Bot nicht @mention.

> [!NOTE]
> Die reinen Bot-Apps werden in beiden Fällen im persönlichen App-Tray angezeigt: `isNotificationOnly: true` oder `isNotificationOnly: false` .

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, setzen Sie `isNotificationOnly` auf `true` .

> [!NOTE]
> Beachten Sie, dass der Wert von `isNotificationOnly` boolean und keine Zeichenfolge ist.

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

* Nur Benachrichtigungsbots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
