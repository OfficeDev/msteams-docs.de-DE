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
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="535b2-104">Nur Benachrichtigungs Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="535b2-104">Notification only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="535b2-105">Wenn Ihr bot nur den Zweck hat, Benachrichtigungen an Benutzer zu übertragen und keine Konversation vorzunehmen, können Sie `isNotificationOnly` das Feld in Ihrem App-Manifest aktivieren.</span><span class="sxs-lookup"><span data-stu-id="535b2-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="535b2-106">Dadurch werden die folgenden Änderungen erstellt:</span><span class="sxs-lookup"><span data-stu-id="535b2-106">This produces the following changes:</span></span>

* <span data-ttu-id="535b2-107">Benutzer können Ihre Benachrichtigung nur bot senden.</span><span class="sxs-lookup"><span data-stu-id="535b2-107">Users cannot message your notification only bot.</span></span>
* <span data-ttu-id="535b2-108">Benutzer können den bot nicht @mention.</span><span class="sxs-lookup"><span data-stu-id="535b2-108">Users cannot @mention the bot.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="535b2-109">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="535b2-109">App manifest</span></span>

<span data-ttu-id="535b2-110">Um dies zu aktivieren, `isNotificationOnly` legen `true`Sie auf fest.</span><span class="sxs-lookup"><span data-stu-id="535b2-110">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="535b2-111">Beachten Sie, dass der Wert `isNotificationOnly` Boolean und keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="535b2-111">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="535b2-112">Bewährte Methoden und Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="535b2-112">Best practices and limitations</span></span>

* <span data-ttu-id="535b2-113">Sie können keine `personal` bereichsbezogene Benachrichtigung nur bot erstellen, da der Benutzer ihre Benachrichtigung nur bot in einem persönlichen Chat senden kann.</span><span class="sxs-lookup"><span data-stu-id="535b2-113">You cannot create a `personal` scoped notification only bot, as the user cannot message your notification only bot in a personal chat.</span></span> <span data-ttu-id="535b2-114">Dies bedeutet, dass Sie kein `conversationUpdate` Ereignis empfangen können, das die erforderlichen Details zum Senden einer Benachrichtigung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="535b2-114">This means that you can't receive a `conversationUpdate` event that would provide you with the necessary details to send a notification.</span></span> <span data-ttu-id="535b2-115">Ihre Benachrichtigung nur der bot funktioniert nur dann ordnungsgemäß, `team` wenn er den Bereich unterstützt und einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="535b2-115">Your notification only bot will only function correctly if it supports the `team` scope and is added to a team.</span></span> <span data-ttu-id="535b2-116">In der Team Einstellung hat ihr bot Zugriff auf die erforderlichen Informationen, um entweder eine Benachrichtigung an einen Kanal oder privat an einen Benutzer zu senden.</span><span class="sxs-lookup"><span data-stu-id="535b2-116">In the team setting, your bot will have access to the necessary information to either send a notification to a channel or privately to a user.</span></span>
* <span data-ttu-id="535b2-117">Benachrichtigung nur Bots verwenden proaktives Messaging zur Kommunikation mit dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="535b2-117">Notification only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="535b2-118">Weitere Informationen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .</span><span class="sxs-lookup"><span data-stu-id="535b2-118">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more details.</span></span>
