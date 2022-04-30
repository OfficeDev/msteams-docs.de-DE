---
title: Reine Benachrichtigungsbots
description: In diesem Artikel wird beschrieben, was reine Benachrichtigungsbots in Microsoft Teams sind
keywords: Teams-Bots Benachrichtigung
ms.topic: conceptual
ms.localizationpriority: high
ms.date: 01/29/2020
ms.openlocfilehash: 1ee009fb76a52bcebdd3fe24c7a672f1ed455b42
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111479"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Reine Benachrichtigungs-Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benachrichtigungen an Benutzer zu übermitteln und er kein Unterhaltungs-Bot ist, können Sie das `isNotificationOnly`-Feld in Ihrem App-Manifest aktivieren. Dies führt zu den folgenden Änderungen:

* Benutzer können Ihrem reinen Benachrichtigungs-Bot keine Nachricht senden.
* Benutzer können den Bot nicht @erwähnen.

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

* Reine Benachrichtigungs-Bots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
