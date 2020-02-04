---
title: Nur Benachrichtigungs Bots
description: Beschreibt, welche Benachrichtigungen nur für Bots in Microsoft Teams gelten
keywords: Teams-Bots-Benachrichtigung
ms.date: 05/20/2019
ms.openlocfilehash: 37652bc2d6171191c81be4e5a2875f47c79574f9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674118"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Nur Benachrichtigungs Bots in Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Wenn Ihr bot nur den Zweck hat, Benachrichtigungen an Benutzer zu übertragen und keine Konversation vorzunehmen, können Sie `isNotificationOnly` das Feld in Ihrem App-Manifest aktivieren. Dadurch werden die folgenden Änderungen erstellt:

* Benutzer können Ihre Benachrichtigung nur bot senden.
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

* Sie können keine `personal` bereichsbezogene Benachrichtigung nur bot erstellen, da der Benutzer ihre Benachrichtigung nur bot in einem persönlichen Chat senden kann. Dies bedeutet, dass Sie kein `conversationUpdate` Ereignis empfangen können, das die erforderlichen Details zum Senden einer Benachrichtigung bereitstellt. Ihre Benachrichtigung nur der bot funktioniert nur dann ordnungsgemäß, `team` wenn er den Bereich unterstützt und einem Team hinzugefügt wird. In der Team Einstellung hat ihr bot Zugriff auf die erforderlichen Informationen, um entweder eine Benachrichtigung an einen Kanal oder privat an einen Benutzer zu senden.
* Benachrichtigung nur Bots verwenden proaktives Messaging zur Kommunikation mit dem Benutzer. Weitere Informationen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .
