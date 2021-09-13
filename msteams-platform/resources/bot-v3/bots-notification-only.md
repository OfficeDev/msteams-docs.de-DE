---
title: Reine Benachrichtigungsbots
description: Beschreibt, welche Bots nur Benachrichtigungen in Microsoft Teams
keywords: Teams-Bots-Benachrichtigung
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: 71dbc07445a57194e90ba3985c3aff1e2d4f2cdf
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156117"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots nur für Benachrichtigungen in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benachrichtigungen an Benutzer zu senden und nicht unterhaltungsativ ist, können Sie das `isNotificationOnly` Feld in Ihrem App-Manifest aktivieren. Dadurch werden die folgenden Änderungen erzeugt:

* Benutzer können Ihren Bot nur für Benachrichtigungen nicht benachrichtigen.
* Benutzer können den Bot nicht @mention.

> [!NOTE]
> Die reinen Bot-Apps werden in beiden Fällen in der persönlichen App-Leiste angezeigt: `isNotificationOnly: true` oder `isNotificationOnly: false` .

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, legen Sie den Wert `isNotificationOnly` auf `true` .

> [!NOTE]
> Beachten Sie, dass der Wert von `isNotificationOnly` Boolean und nicht String ist.

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

* Bots, die nur Benachrichtigungen verwenden, verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)
