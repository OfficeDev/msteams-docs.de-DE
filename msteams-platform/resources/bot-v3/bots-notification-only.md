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
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="a54af-104">Nur-Benachrichtigungs-Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a54af-104">Notification-only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="a54af-105">Wenn Ihr bot nur den Zweck hat, Benachrichtigungen an Benutzer zu übertragen und keine Konversation vorzunehmen, können Sie `isNotificationOnly` das Feld in Ihrem App-Manifest aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a54af-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="a54af-106">Dadurch werden die folgenden Änderungen erstellt:</span><span class="sxs-lookup"><span data-stu-id="a54af-106">This produces the following changes:</span></span>

* <span data-ttu-id="a54af-107">Benutzer können Ihren nur-Benachrichtigung-bot nicht Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="a54af-107">Users cannot message your notification-only bot.</span></span>
* <span data-ttu-id="a54af-108">Benutzer können den bot nicht @mention.</span><span class="sxs-lookup"><span data-stu-id="a54af-108">Users cannot @mention the bot.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="a54af-109">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="a54af-109">App manifest</span></span>

<span data-ttu-id="a54af-110">Um dies zu aktivieren, `isNotificationOnly` legen `true`Sie auf fest.</span><span class="sxs-lookup"><span data-stu-id="a54af-110">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="a54af-111">Beachten Sie, dass der Wert `isNotificationOnly` Boolean und keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="a54af-111">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="a54af-112">Bewährte Methoden und Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="a54af-112">Best practices and limitations</span></span>

* <span data-ttu-id="a54af-113">Nur für Benachrichtigungs-Bots wird proaktives Messaging verwendet, um mit dem Benutzer zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="a54af-113">Notification-only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="a54af-114">Weitere Informationen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .</span><span class="sxs-lookup"><span data-stu-id="a54af-114">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more details.</span></span>
