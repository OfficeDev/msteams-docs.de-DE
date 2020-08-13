---
title: Was sind webhooks und Connectors?
author: clearab
description: Erfahren Sie, wie webhooks und Connectors ihre Webdienste mit dem Microsoft Teams-Client verbinden können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 740806e43af94d5a5da876affec2070a5a461b11
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651998"
---
# <a name="what-are-webhooks-and-connectors"></a><span data-ttu-id="9ead8-103">Was sind webhooks und Connectors?</span><span class="sxs-lookup"><span data-stu-id="9ead8-103">What are webhooks and connectors?</span></span>

<span data-ttu-id="9ead8-104">Webhooks und Connectors sind einfache Möglichkeiten zum Verbinden externer Systeme und Dienste mit Microsoft Teams-Kanälen und-Chats.</span><span class="sxs-lookup"><span data-stu-id="9ead8-104">Webhooks and connectors are straightforward ways to connect external systems and services with Microsoft Teams channels and chats.</span></span>

<span data-ttu-id="9ead8-105">Benutzer können beispielsweise Benachrichtigungen von einer anderen APP abonnieren (normalerweise in Form von Karten).</span><span class="sxs-lookup"><span data-stu-id="9ead8-105">Users can, for example, subscribe to notifications from another app (typically in the form of cards).</span></span>

## <a name="incoming-webhooks"></a><span data-ttu-id="9ead8-106">Eingehende webhooks</span><span class="sxs-lookup"><span data-stu-id="9ead8-106">Incoming webhooks</span></span>

<span data-ttu-id="9ead8-107">Eingehende webhooks sind die einfachste Art von Connector und eine schnelle und einfache Möglichkeit, den Kanal eines Teams mit einem externen Dienst zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="9ead8-107">Incoming webhooks are the simplest type of connector and a quick and easy way to connect a team's channel to an external service.</span></span> <span data-ttu-id="9ead8-108">Für jeden Kanal (falls für dieses Team aktiviert) können Sie einen HTTPS-Endpunkt verfügbar machen, der ordnungsgemäß formatierte JSON akzeptiert und Nachrichten in den Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="9ead8-108">For any channel (if enabled for that team), you can expose an HTTPS endpoint that accepts correctly formatted JSON and insert messages into the channel.</span></span>

<span data-ttu-id="9ead8-109">Siehe [Erstellen eines eingehenden webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).</span><span class="sxs-lookup"><span data-stu-id="9ead8-109">See [Create an incoming webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="9ead8-110">Benutzerszenarien</span><span class="sxs-lookup"><span data-stu-id="9ead8-110">User scenarios</span></span>

<span data-ttu-id="9ead8-111">Eingehende webhooks eignen sich am besten für Szenarien, die für ein bestimmtes Team eindeutig sind.</span><span class="sxs-lookup"><span data-stu-id="9ead8-111">Incoming webhooks are best for scenarios unique to a particular team.</span></span> <span data-ttu-id="9ead8-112">Sie können beispielsweise einen eingehenden webhook in Ihrem DevOps-Kanal erstellen und ihre Build-, Bereitstellungs-und Überwachungsdienste so konfigurieren, dass Warnungen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9ead8-112">For example, you could create an incoming webhook in your DevOps channel and configure your build, deployment, and monitoring services to send alerts.</span></span>

## <a name="office-365-connectors"></a><span data-ttu-id="9ead8-113">Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="9ead8-113">Office 365 Connectors</span></span>

<span data-ttu-id="9ead8-114">Mit einem Office 365-Konnektor können Sie eine benutzerdefinierte Konfigurationsseite für den eingehenden webhook erstellen und als Teil einer Teams-App verpacken.</span><span class="sxs-lookup"><span data-stu-id="9ead8-114">An Office 365 Connector allows you to create a custom configuration page for your incoming webhook and package it as part of a Teams app.</span></span> <span data-ttu-id="9ead8-115">Sie können diese APP dann breiter oder sogar in unserem App Store verteilen.</span><span class="sxs-lookup"><span data-stu-id="9ead8-115">You can then distribute that app more broadly or even to our app store.</span></span> <span data-ttu-id="9ead8-116">Sie senden Nachrichten in erster Linie mit Office 365-connectorkarten, die auch eine beschränkte Reihe von Karten Aktionen haben können.</span><span class="sxs-lookup"><span data-stu-id="9ead8-116">You send messages primarily using Office 365 Connector cards that can also have a limited set of card actions.</span></span> <span data-ttu-id="9ead8-117">Sie werden auf Kanalebene konfiguriert, aber auf Teamebene installiert.</span><span class="sxs-lookup"><span data-stu-id="9ead8-117">They are configured on the channel level but installed at the team level.</span></span>

<span data-ttu-id="9ead8-118">Weitere Informationen finden Sie unter [Erstellen eines Office 365-Konnektors](~/webhooks-and-connectors/how-to/connectors-creating.md).</span><span class="sxs-lookup"><span data-stu-id="9ead8-118">See [Create an Office 365 Connector](~/webhooks-and-connectors/how-to/connectors-creating.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="9ead8-119">Benutzerszenarien</span><span class="sxs-lookup"><span data-stu-id="9ead8-119">User scenarios</span></span>

<span data-ttu-id="9ead8-120">Ein Wetter-Konnektor, mit dem Sie einen Standort und eine Tageszeit für den Empfang von Updates für die Prognose von morgen auswählen können.</span><span class="sxs-lookup"><span data-stu-id="9ead8-120">A weather connector that lets you choose a location and time of day to receive updates about tomorrow's forecast.</span></span>

## <a name="outgoing-webhooks"></a><span data-ttu-id="9ead8-121">Ausgehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="9ead8-121">Outgoing webhooks</span></span>

<span data-ttu-id="9ead8-122">Ausgehende Webhooks ermöglichen Benutzern das Senden von Textnachrichten aus einem Kanal an Ihre Webdienste.</span><span class="sxs-lookup"><span data-stu-id="9ead8-122">Outgoing webhooks allow your users to send text messages from a channel to your web services.</span></span> <span data-ttu-id="9ead8-123">Nach der Konfiguration können Benutzer Ihre APP @mention und eine Nachricht an Ihren externen Dienst senden.</span><span class="sxs-lookup"><span data-stu-id="9ead8-123">Once configured, users can @mention your app and send a message to your external service.</span></span> <span data-ttu-id="9ead8-124">Ihr Dienst hat fünf Sekunden Zeit, um eine Antwort auf die Nachricht zu senden, die möglicherweise Text oder eine Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="9ead8-124">Your service has five seconds to send a response to the message, potentially containing text or a card.</span></span>

<span data-ttu-id="9ead8-125">Ausgehende webhooks werden pro Team konfiguriert und können nicht als Teil einer normalen Teams-App eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="9ead8-125">Outgoing webhooks are configured on a per-team basis and can't be included as part of a normal Teams app.</span></span>

<span data-ttu-id="9ead8-126">Weitere Informationen finden Sie unter [Create an Outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).</span><span class="sxs-lookup"><span data-stu-id="9ead8-126">See [Create an outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="9ead8-127">Benutzerszenarien</span><span class="sxs-lookup"><span data-stu-id="9ead8-127">User scenarios</span></span>

<span data-ttu-id="9ead8-128">Ausgehende webhooks eignen sich am besten für die Durchführung Team spezifischer Workflows, die nicht das Sammeln oder austauschen großer Informationsmengen erfordern.</span><span class="sxs-lookup"><span data-stu-id="9ead8-128">Outgoing webhooks are best suited for completing team-specific workflows that don't require collecting or exchanging large amounts of information.</span></span>

## <a name="learn-more"></a><span data-ttu-id="9ead8-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9ead8-129">Learn more</span></span>

* [<span data-ttu-id="9ead8-130">Planen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="9ead8-130">Planning your app</span></span>](../../concepts/extensibility-points.md)
* [<span data-ttu-id="9ead8-131">Erstellen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="9ead8-131">Building your app</span></span>](../../concepts/building-an-app.md)
* [<span data-ttu-id="9ead8-132">Veröffentlichen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="9ead8-132">Publishing your app</span></span>](../../concepts/deploy-and-publish/overview.md)
