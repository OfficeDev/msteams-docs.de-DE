---
title: Reine Benachrichtigungsbots
description: In diesem Modul erfahren Sie, welche Benachrichtigungs-Bots in Microsoft Teams, App-Manifest und den bewährten Methoden und Einschränkungen enthalten sind.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: 547ef73cfd036efe566afe15e4f50701a275c2cd
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144299"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Reine Benachrichtigungs-Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benachrichtigungen an Benutzer zu übermitteln und nicht in Unterhaltungen besteht, können Sie das `isNotificationOnly` Feld in Ihrem App-Manifest aktivieren. Dies führt zu den folgenden Änderungen:

* Benutzer können Ihrem Nur-Benachrichtigungs-Bot keine Nachricht senden.
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

* Reine Benachrichtigungs-Bots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
