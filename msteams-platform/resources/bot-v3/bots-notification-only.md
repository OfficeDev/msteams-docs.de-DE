---
title: Reine Benachrichtigungsbots
description: In diesem Modul erfahren Sie, was reine Benachrichtigungsbots in Microsoft Teams sind, welche App-Manifeste es gibt und welche bewährten Methoden und Einschränkungen es gibt.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: ac412f37cba03c5da43163bf2eadd47adc676f08
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833016"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Reine Benachrichtigungs-Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benachrichtigungen an Benutzer zu übermitteln und nicht konversationsfähig zu sein, können Sie das `isNotificationOnly` Feld in Ihrem App-Manifest aktivieren. Dies führt zu den folgenden Änderungen:

* Benutzer können Ihrem Bot, der nur Benachrichtigungen enthält, keine Nachrichten senden.
* Benutzer können den Bot nicht @mention.

> [!NOTE]
> Die reinen Bot-Apps werden in beiden Fällen in der persönlichen Anwendungsleiste angezeigt: `isNotificationOnly: true` oder `isNotificationOnly: false`.

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, legen Sie `isNotificationOnly` auf `true` fest.

> [!NOTE]
> Der Wert von `isNotificationOnly` boolescher Wert und keine Zeichenfolge.

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

Reine Benachrichtigungs-Bots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
