---
title: Nur-Benachrichtigungs-Bots
description: Beschreibt, welche nur-Benachrichtigungs-Bots in Microsoft Teams sind
keywords: Teams-Bots-Benachrichtigung
ms.date: 01/29/2020
ms.openlocfilehash: d312f9cd4558d35fc2492b5cf0b4f77b65660833
ms.sourcegitcommit: 44ac886c0ca34a16222d3991a61606f8483b8481
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "41783906"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Nur-Benachrichtigungs-Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn Ihr bot nur den Zweck hat, Benachrichtigungen an Benutzer zu übertragen und keine Konversation vorzunehmen, können Sie `isNotificationOnly` das Feld in Ihrem App-Manifest aktivieren. Dadurch werden die folgenden Änderungen erstellt:

* Benutzer können Ihren nur-Benachrichtigung-bot nicht Nachrichten.
* Benutzer können den bot nicht @mention.

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, `isNotificationOnly` legen `true`Sie auf fest.

> [!NOTE]
> Beachten Sie, dass der Wert `isNotificationOnly` Boolean und keine Zeichenfolge ist.

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

* Nur für Benachrichtigungs-Bots wird proaktives Messaging verwendet, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .
