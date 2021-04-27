---
title: Reine Benachrichtigungsbots
description: Beschreibt, was nur Benachrichtigungsbots in Microsoft Teams sind
keywords: Teams-Bots-Benachrichtigung
ms.topic: conceptual
localization_priority: Normal
ms.date: 01/29/2020
ms.openlocfilehash: 42a0b9acecbc1821ea492cb6c850c7a9b11bbbfe
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019762"
---
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="2824d-104">Nur-Benachrichtigungs-Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2824d-104">Notification-only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="2824d-105">Wenn der einzige Zweck Ihres Bots die Zustellung von Benachrichtigungen an Benutzer ist und keine Unterhaltung ist, können Sie das Feld in Ihrem `isNotificationOnly` App-Manifest aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2824d-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="2824d-106">Dadurch werden die folgenden Änderungen vorgenommen:</span><span class="sxs-lookup"><span data-stu-id="2824d-106">This produces the following changes:</span></span>

* <span data-ttu-id="2824d-107">Benutzer können Ihren Benachrichtigungsbot nicht senden.</span><span class="sxs-lookup"><span data-stu-id="2824d-107">Users cannot message your notification-only bot.</span></span>
* <span data-ttu-id="2824d-108">Benutzer können @mention bot nicht erstellen.</span><span class="sxs-lookup"><span data-stu-id="2824d-108">Users cannot @mention the bot.</span></span>

> [!NOTE]
> <span data-ttu-id="2824d-109">Die Nur-Bot-Apps werden in beiden Fällen im Tablett der persönlichen App `isNotificationOnly: true` angezeigt: oder `isNotificationOnly: false` .</span><span class="sxs-lookup"><span data-stu-id="2824d-109">The bot-only apps will surface in the personal app tray in both cases: `isNotificationOnly: true` or `isNotificationOnly: false`.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="2824d-110">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="2824d-110">App manifest</span></span>

<span data-ttu-id="2824d-111">Um dies zu aktivieren, legen Sie auf `isNotificationOnly` `true` .</span><span class="sxs-lookup"><span data-stu-id="2824d-111">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="2824d-112">Beachten Sie, dass der Wert von `isNotificationOnly` boolesch und keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="2824d-112">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="2824d-113">Bewährte Methoden und Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="2824d-113">Best practices and limitations</span></span>

* <span data-ttu-id="2824d-114">Benachrichtigungsbots verwenden proaktives Messaging, um mit dem Benutzer zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="2824d-114">Notification-only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="2824d-115">Weitere Informationen finden Sie unter Proaktives Messaging für [Bots.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)</span><span class="sxs-lookup"><span data-stu-id="2824d-115">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more details.</span></span>
