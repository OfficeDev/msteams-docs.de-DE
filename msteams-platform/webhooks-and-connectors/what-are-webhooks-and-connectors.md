---
title: Webhooks und Connectors
author: clearab
description: Erfahren Sie, wie Webhooks und Connectors Ihre Webdienste mit dem Teams-Client verbinden können.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2cb763a6637abd3faa500de871119f0b829871bf
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140054"
---
# <a name="webhooks-and-connectors"></a><span data-ttu-id="bd75d-103">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="bd75d-103">Webhooks and connectors</span></span>

<span data-ttu-id="bd75d-104">Webhooks und Connectors helfen beim Verbinden der Webdienste mit Kanälen und Teams in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="bd75d-104">Webhooks and connectors help to connect the web services to channels and teams in Microsoft Teams.</span></span> <span data-ttu-id="bd75d-105">Webhooks sind benutzerdefinierte HTTP-Rückrufe, mit denen Benutzer über alle Aktionen benachrichtigt werden, die im Microsoft Teams Kanal ausgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-105">Webhooks are user defined HTTP callback that notifies users about any action that has taken place in the Microsoft Teams channel.</span></span> <span data-ttu-id="bd75d-106">Es ist eine Möglichkeit für eine App, Echtzeitdaten abzurufen.</span><span class="sxs-lookup"><span data-stu-id="bd75d-106">It is a way for an app to get real time data.</span></span> <span data-ttu-id="bd75d-107">Connectors ermöglichen Benutzern, Benachrichtigungen und Nachrichten von Ihren Webdiensten zu abonnieren.</span><span class="sxs-lookup"><span data-stu-id="bd75d-107">Connectors allow users to subscribe to receive notifications and messages from your web services.</span></span> <span data-ttu-id="bd75d-108">Sie stellen einen HTTPS-Endpunkt für Ihren Dienst bereit, um Nachrichten in Form von Karten zu posten.</span><span class="sxs-lookup"><span data-stu-id="bd75d-108">They expose an HTTPS endpoint for your service to post messages in the form of cards.</span></span>

## <a name="outgoing-webhooks"></a><span data-ttu-id="bd75d-109">Ausgehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="bd75d-109">Outgoing Webhooks</span></span>

<span data-ttu-id="bd75d-110">Webhooks helfen Teams bei der Integration in externe Apps.</span><span class="sxs-lookup"><span data-stu-id="bd75d-110">Webhooks help Teams to integrate with external apps.</span></span> <span data-ttu-id="bd75d-111">Mit ausgehenden Webhooks können Sie Textnachrichten von einem Kanal an die Webdienste senden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-111">With Outgoing Webhooks, you can send text messages from a channel to the web services.</span></span> <span data-ttu-id="bd75d-112">Nach dem Konfigurieren der ausgehenden Webhooks können Benutzer ausgehenden Webhook @mention und eine Nachricht an Webdienste senden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-112">After configuring the Outgoing Webhooks, users can @mention Outgoing Webhook and send a message to web services.</span></span> <span data-ttu-id="bd75d-113">Der Dienst antwortet innerhalb von zehn Sekunden mit einem Text oder einer Karte auf die Nachricht.</span><span class="sxs-lookup"><span data-stu-id="bd75d-113">The service responds within ten seconds to the message with a text or a card.</span></span>

> [!NOTE]
> <span data-ttu-id="bd75d-114">Ausgehende Webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-114">Outgoing Webhooks are configured on a per team basis and cannot be included as part of a normal Teams app.</span></span>

## <a name="connectors"></a><span data-ttu-id="bd75d-115">Connectors</span><span class="sxs-lookup"><span data-stu-id="bd75d-115">Connectors</span></span>

<span data-ttu-id="bd75d-116">Connectors ermöglichen Benutzern das Abonnieren von Benachrichtigungen und Nachrichten von webdiensten.</span><span class="sxs-lookup"><span data-stu-id="bd75d-116">Connectors allow users to subscribe to receive notifications and messages from the web services.</span></span> <span data-ttu-id="bd75d-117">Sie machen den HTTPS-Endpunkt für den Dienst verfügbar, um Nachrichten in Teams Kanälen zu posten, in der Regel in Form von Karten.</span><span class="sxs-lookup"><span data-stu-id="bd75d-117">They expose the HTTPS endpoint for the service to post messages to Teams channels, typically in the form of cards.</span></span>

### <a name="incoming-webhooks"></a><span data-ttu-id="bd75d-118">Eingehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="bd75d-118">Incoming Webhooks</span></span>

<span data-ttu-id="bd75d-119">Eingehende Webhooks helfen beim Veröffentlichen von Nachrichten von Apps an Teams.</span><span class="sxs-lookup"><span data-stu-id="bd75d-119">Incoming Webhooks help in posting messages from apps to Teams.</span></span> <span data-ttu-id="bd75d-120">Wenn eingehende Webhooks für ein Team in einem beliebigen Kanal aktiviert sind, wird der HTTPS-Endpunkt verfügbar gemacht, der korrekt formatierte JSON akzeptiert und die Nachrichten in diesen Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="bd75d-120">If Incoming Webhooks are enabled for a team in any channel, it exposes the HTTPS endpoint, which accepts correctly formatted JSON and inserts the messages into that channel.</span></span> <span data-ttu-id="bd75d-121">Sie können beispielsweise einen eingehenden Webhook in Ihrem DevOps Kanal erstellen, Ihren Build konfigurieren und gleichzeitig Dienste bereitstellen und überwachen, um Warnungen zu senden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-121">For example, you can create an Incoming Webhook in your DevOps channel, configure your build, and simultaneously deploy and monitor services to send alerts.</span></span>

### <a name="office-365-connectors"></a><span data-ttu-id="bd75d-122">Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="bd75d-122">Office 365 Connectors</span></span>

<span data-ttu-id="bd75d-123">Office 365 Mit Connectors können Sie eine benutzerdefinierte Konfigurationsseite für Ihren eingehenden Webhook erstellen und diese als Teil einer Teams-App verpacken.</span><span class="sxs-lookup"><span data-stu-id="bd75d-123">Office 365 Connectors allow you to create a custom configuration page for your Incoming Webhook and package them as part of a Teams app.</span></span> <span data-ttu-id="bd75d-124">Sie senden Nachrichten in erster Linie mit Office 365 Connectorkarten und haben die Möglichkeit, ihnen eine begrenzte Anzahl von Kartenaktionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd75d-124">You send messages primarily using Office 365 Connector cards and have the ability to add a limited set of card actions to them.</span></span> <span data-ttu-id="bd75d-125">Beispielsweise ein Wetterconnector, mit dem Benutzer einen Ort und eine Uhrzeit auswählen können, um Updates über das Wetter von morgen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bd75d-125">For example, a weather connector that allows users to select a location and time of day, to receive updates about tomorrow's weather.</span></span> <span data-ttu-id="bd75d-126">Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.</span><span class="sxs-lookup"><span data-stu-id="bd75d-126">They are configured on a channel level but are installed at a team level.</span></span>

> [!NOTE]
> <span data-ttu-id="bd75d-127">Sie können den Office 365 Connector Teams App an unseren AppStore verteilen.</span><span class="sxs-lookup"><span data-stu-id="bd75d-127">You can distribute the Office 365 Connector Teams app to our AppStore.</span></span>

## <a name="create-and-send-messages"></a><span data-ttu-id="bd75d-128">Erstellen und Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="bd75d-128">Create and send messages</span></span>

<span data-ttu-id="bd75d-129">Nachrichten mit Aktionen ermöglichen Es Benutzern, Maßnahmen zu ergreifen, ohne ihren E-Mail-Client zu verlassen, was die Benutzerbindung erhöht.</span><span class="sxs-lookup"><span data-stu-id="bd75d-129">Actionable messages allow users to take action without leaving their email client, increasing user engagement.</span></span> <span data-ttu-id="bd75d-130">Mit Office 365 und eingehenden Webhooks können Sie Nachrichten senden, indem Sie eine JSON-Nutzlast an die Webhook-URL senden.</span><span class="sxs-lookup"><span data-stu-id="bd75d-130">With Office 365 and Incoming Webhooks, you can send messages by posting a JSON payload to the webhook URL.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd75d-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bd75d-131">See also</span></span>

* [<span data-ttu-id="bd75d-132">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="bd75d-132">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="bd75d-133">Erstellen eines Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="bd75d-133">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="bd75d-134">Erstellen und Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="bd75d-134">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)

## <a name="next-step"></a><span data-ttu-id="bd75d-135">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="bd75d-135">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd75d-136">Erstellen eines ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="bd75d-136">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
