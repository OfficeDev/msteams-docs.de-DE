---
title: Reine Benachrichtigungsbots
description: Beschreibt, welche Bots nur Benachrichtigungen in Microsoft Teams
keywords: Teams-Bots-Benachrichtigung
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: d3ee5343ea159950859237f2a488557d9063eb6e
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355727"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots nur für Benachrichtigungen in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn der einzige Zweck Ihres Bots darin besteht, Benachrichtigungen an Benutzer zu senden und nicht unterhaltungsativ ist, können Sie das `isNotificationOnly` Feld in Ihrem App-Manifest aktivieren. Dadurch werden die folgenden Änderungen erzeugt:

* Benutzer können Ihren Bot nur für Benachrichtigungen nicht benachrichtigen.
* Benutzer können den Bot nicht @mention.

> [!NOTE]
> Die reinen Bot-Apps werden in beiden Fällen in der persönlichen App-Leiste angezeigt: `isNotificationOnly: true` oder `isNotificationOnly: false`.

## <a name="app-manifest"></a>App-Manifest

Um dies zu aktivieren, legen Sie den Wert `isNotificationOnly` auf `true`.

> [!NOTE]
> Der Wert von `isNotificationOnly` Boolean ist keine Zeichenfolge.

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

* Bots, die nur Benachrichtigungen verwenden, verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren. Weitere Informationen finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
