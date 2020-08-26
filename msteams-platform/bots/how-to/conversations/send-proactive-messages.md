---
title: Versenden proaktiver Nachrichten
author: clearab
description: Wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-bot senden.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2dfb8e18243079ca38d505f4b80deb7abf2de32f
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874849"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="02fd4-103">Versenden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="02fd4-103">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="02fd4-104">Eine proaktive Nachricht ist eine Nachricht, die von einem bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="02fd4-104">A proactive message is any message sent by a bot that is not in direct response to a request from a user.</span></span> <span data-ttu-id="02fd4-105">Dies kann beispielsweise folgende Nachrichten enthalten:</span><span class="sxs-lookup"><span data-stu-id="02fd4-105">This can include messages like:</span></span>

* <span data-ttu-id="02fd4-106">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="02fd4-106">Welcome messages</span></span>
* <span data-ttu-id="02fd4-107">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="02fd4-107">Notifications</span></span>
* <span data-ttu-id="02fd4-108">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="02fd4-108">Scheduled messages</span></span>

<span data-ttu-id="02fd4-109">Damit Ihr bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, den Gruppenchat oder das Team haben, an das Sie die Nachricht senden möchten.</span><span class="sxs-lookup"><span data-stu-id="02fd4-109">In order for your bot to send a proactive message, it must have access to the user, group chat, or team that you wish to send the message to.</span></span> <span data-ttu-id="02fd4-110">Für einen Gruppenchat oder ein Team bedeutet dies, dass die APP, die ihren bot enthält, zuerst an diesem Speicherort installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="02fd4-110">For a group chat or team, this means the app that contains your bot must first be installed to that location.</span></span> <span data-ttu-id="02fd4-111">Sie können [Ihre APP bei Bedarf proaktiv mithilfe von Graph](#proactively-install-your-app-using-graph) in einem Team installieren oder mithilfe einer APP- [Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) apps an Microsoft Teams und Benutzer in Ihrem Mandanten verschieben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-111">You can [proactively install your app using Graph](#proactively-install-your-app-using-graph) in a team if necessary, or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="02fd4-112">Für Benutzer muss Ihre APP entweder für diesen Benutzer installiert sein, oder der Benutzer muss Teil eines Teams sein, in dem die APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="02fd4-112">For users, your app either needs to be installed for that user, or your user needs to be part of a team where your app is installed.</span></span>

<span data-ttu-id="02fd4-113">Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht dadurch, dass Sie keine aktive Person `turnContext` für eine Antwort verwenden müssen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-113">Sending a proactive message is different than sending a regular message in that you won't have an active `turnContext` to use for a reply.</span></span> <span data-ttu-id="02fd4-114">Möglicherweise müssen Sie auch die Unterhaltung erstellen (beispielsweise einen neuen eins-zu-eins-Chat oder einen neuen Unterhaltungsthread in einem Kanal), bevor Sie die Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-114">You may also need to create the conversation (for example a new one-to-one chat, or a new conversation thread in a channel) before sending the message.</span></span> <span data-ttu-id="02fd4-115">Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-115">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="02fd4-116">Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine proaktive Nachricht zu senden:</span><span class="sxs-lookup"><span data-stu-id="02fd4-116">At a high level the steps you'll need to complete to send a proactive message are:</span></span>

1. <span data-ttu-id="02fd4-117">[Rufen Sie die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich) ab.</span><span class="sxs-lookup"><span data-stu-id="02fd4-117">[Get the user ID or team/channel ID](#get-the-user-id-or-teamchannel-id) (if needed).</span></span>
1. <span data-ttu-id="02fd4-118">[Erstellen Sie den Unterhaltung-oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="02fd4-118">[Create the conversation or conversation thread](#create-the-conversation) (if needed).</span></span>
1. <span data-ttu-id="02fd4-119">[Rufen Sie die Unterhaltungs-ID](#get-the-conversation-id)ab.</span><span class="sxs-lookup"><span data-stu-id="02fd4-119">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="02fd4-120">[Senden Sie die Nachricht](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="02fd4-120">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="02fd4-121">Die Codeausschnitte im folgenden Abschnitt " [Beispiele](#examples) " dienen zum Erstellen einer 1:1-Unterhaltung, im Abschnitt " [Verweise](#references) " finden Sie Links zu vollständigen Arbeitsbeispielen für einmalige Unterhaltungen und Gruppen/Kanäle.</span><span class="sxs-lookup"><span data-stu-id="02fd4-121">The code snippets in the [examples](#examples) section below are for creating a one-to-one conversation, see the [references](#references) section for links to complete working samples for both one-to-once conversations and group/channels.</span></span>

## <a name="get-the-user-id-or-teamchannel-id"></a><span data-ttu-id="02fd4-122">Abrufen der Benutzer-ID oder der Team/Kanal-ID</span><span class="sxs-lookup"><span data-stu-id="02fd4-122">Get the user ID or team/channel ID</span></span>

<span data-ttu-id="02fd4-123">Wenn Sie einen neuen Unterhaltungs-oder Unterhaltungsthread in einem Kanal erstellen müssen, benötigen Sie zunächst die richtige ID, um die Unterhaltung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-123">If you need to create a new conversation or conversation thread in a channel you'll first need the right ID to create the conversation.</span></span> <span data-ttu-id="02fd4-124">Sie können diese ID auf verschiedene Arten empfangen/abrufen:</span><span class="sxs-lookup"><span data-stu-id="02fd4-124">You can receive/retrieve this ID in multiple ways:</span></span>

1. <span data-ttu-id="02fd4-125">Wenn Ihre APP in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="02fd4-125">When your app is installed in any particular context, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="02fd4-126">Wenn einem Kontext, in dem Ihre APP installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="02fd4-126">When a new user is added to a context where your app is installed, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="02fd4-127">Sie können die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, auf dem Ihre APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="02fd4-127">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team your app is installed.</span></span>
1. <span data-ttu-id="02fd4-128">Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, auf dem Ihre APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="02fd4-128">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team your app is installed.</span></span>
1. <span data-ttu-id="02fd4-129">Jede Aktivität, die ihr bot erhält, enthält die notwendigen Informationen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-129">Every Activity your bot receives will contain the necessary information.</span></span>

<span data-ttu-id="02fd4-130">Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die `tenantId` -und entweder die oder-speichern, um `userId` `channelId` eine neue Unterhaltung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-130">Regardless of how you gain the information, you'll need to store the `tenantId` and either the `userId` or `channelId` in order to create a new conversation.</span></span> <span data-ttu-id="02fd4-131">Sie können auch die verwenden `teamId` , um einen neuen Unterhaltungsthread im allgemeinen/Standardkanal eines Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-131">You can also use the `teamId` to create a new conversation thread in the general/default channel of a team.</span></span>

<span data-ttu-id="02fd4-132">Die `userId` ist für Ihre bot-ID und einen bestimmten Benutzer eindeutig, Sie können Sie nicht zwischen Bots wieder verwenden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-132">The `userId` is unique to your bot Id and a particular user, you cannot re-use them between bots.</span></span> <span data-ttu-id="02fd4-133">Das `channelId` ist Global, aber Ihr bot _muss_ im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.</span><span class="sxs-lookup"><span data-stu-id="02fd4-133">The `channelId` is global, however your bot _must_ be installed in the team before you can send a proactive message to a channel.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="02fd4-134">Erstellen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="02fd4-134">Create the conversation</span></span>

<span data-ttu-id="02fd4-135">Sobald Sie über die Benutzer/Kanal-Informationen verfügen, müssen Sie die Unterhaltung erstellen, wenn Sie noch nicht vorhanden ist (oder Sie wissen nicht, welche `conversationId` ).</span><span class="sxs-lookup"><span data-stu-id="02fd4-135">Once you have the user/channel information, you'll need to create the conversation if it doesn't already exist (or you don't know the `conversationId`).</span></span> <span data-ttu-id="02fd4-136">Sie sollten die Unterhaltung nur einmal erstellen; Stellen Sie sicher, dass Sie den `conversationId` Wert oder das `conversationReference` Objekt speichern, das in Zukunft verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="02fd4-136">You should only create the conversation once; make sure you store the `conversationId` value or `conversationReference` object to use in the future.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="02fd4-137">Abrufen der Unterhaltungs-ID</span><span class="sxs-lookup"><span data-stu-id="02fd4-137">Get the conversation ID</span></span>

<span data-ttu-id="02fd4-138">Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` -Objekt oder das `conversationId` und- `tenantId` , um die Nachricht zu senden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-138">Once the conversation has been created, you will use either the `conversationReference` object or the `conversationId` and the `tenantId` to send the message.</span></span> <span data-ttu-id="02fd4-139">Sie können diese ID abrufen, indem Sie die Unterhaltung entweder erstellen oder aus einer Aktivität speichern, die Sie aus diesem Kontext erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-139">You can get this Id by either creating the conversation, or storing it from any Activity sent to you from that context.</span></span> <span data-ttu-id="02fd4-140">Stellen Sie sicher, dass Sie diese ID speichern.</span><span class="sxs-lookup"><span data-stu-id="02fd4-140">Make certain that you store this Id.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="02fd4-141">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="02fd4-141">Send the message</span></span>

<span data-ttu-id="02fd4-142">Da Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-142">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="02fd4-143">Wenn Sie das SDK verwenden, verwenden Sie die `continueConversation` -Methode und den `conversationId` und `tenantId` , um einen direkten API-Aufruf zu tätigen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-143">If you're using the SDK, you'll do so using the `continueConversation` method,and the `conversationId` and `tenantId` to make a direct API call.</span></span>  <span data-ttu-id="02fd4-144">Sie müssen das `conversationParameters` ordnungsgemäße festlegen, um Ihre Nachricht erfolgreich zu senden-siehe die [Beispiele](#examples) unten oder verwenden Sie eines der Beispiele im Abschnitt [Verweise](#references) aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="02fd4-144">You'll need to set the `conversationParameters` correctly to successfully send your message - see the [examples](#examples) below or use one of the samples listed in the [references](#references) section.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="02fd4-145">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="02fd4-145">Best practices for proactive messaging</span></span>

<span data-ttu-id="02fd4-146">Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit zur Kommunikation mit ihren Benutzern sein.</span><span class="sxs-lookup"><span data-stu-id="02fd4-146">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="02fd4-147">Aus ihrer Perspektive kann diese Nachricht jedoch vollständig unaufgefordert angezeigt werden, und im Fall von Begrüßungsnachrichten ist dies das erste Mal, dass Sie mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="02fd4-147">However, from their perspective this message can appear completely unprompted and, in the case of welcome messages, it will be the first time they've interacted with your app.</span></span> <span data-ttu-id="02fd4-148">Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden (keine Spam-e-Mail-Benutzer) und genügend Informationen bereitzustellen, damit Benutzer verstehen, warum Sie Nachrichten erhalten.</span><span class="sxs-lookup"><span data-stu-id="02fd4-148">As such, it is very important to use this functionality sparingly (don't spam your users) and to provide enough information to let users understand why they are being messaged.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="02fd4-149">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="02fd4-149">Welcome messages</span></span>

<span data-ttu-id="02fd4-150">Bei Verwendung von proaktivem Messaging zum Senden einer Willkommensnachricht an einen Benutzer müssen Sie Bedenken, dass für die meisten Personen, die die Nachricht erhalten, kein Kontext dafür vorhanden ist, warum Sie Sie empfangen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-150">When using proactive messaging to send a welcome message to a user you must keep in mind that, for most people receiving the message, there will be no context for why they are receiving it.</span></span> <span data-ttu-id="02fd4-151">Dies ist auch das erste Mal, dass Sie mit Ihrer APP interagieren; Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-151">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="02fd4-152">Die besten Begrüßungsnachrichten umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="02fd4-152">The best welcome messages will include:</span></span>

* <span data-ttu-id="02fd4-153">**Warum ein Benutzer die Nachricht empfängt.**</span><span class="sxs-lookup"><span data-stu-id="02fd4-153">**Why a user is receiving the message.**</span></span> <span data-ttu-id="02fd4-154">Dem Benutzer sollte sehr deutlich sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="02fd4-154">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="02fd4-155">Wenn Ihr bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, sollten Sie wissen, in welchem Kanal Sie installiert wurde und wer Sie möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="02fd4-155">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="02fd4-156">**Was bieten Sie an?**</span><span class="sxs-lookup"><span data-stu-id="02fd4-156">**What do you offer.**</span></span> <span data-ttu-id="02fd4-157">Was können Sie mit Ihrer APP tun?</span><span class="sxs-lookup"><span data-stu-id="02fd4-157">What can they do with your app?</span></span> <span data-ttu-id="02fd4-158">Welchen Wert können Sie Ihnen bringen?</span><span class="sxs-lookup"><span data-stu-id="02fd4-158">What value can you bring to them?</span></span>
* <span data-ttu-id="02fd4-159">**Was sollten Sie als nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="02fd4-159">**What should they do next.**</span></span> <span data-ttu-id="02fd4-160">Laden Sie Sie ein, einen Befehl auszuprobieren oder mit ihrer app in irgendeiner Weise zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="02fd4-160">Invite them to try out a command, or interact with your app in some way.</span></span>

<span data-ttu-id="02fd4-161">Denken Sie daran, dass schlechte Begrüßungsnachrichten dazu führen können, dass Benutzer ihren bot blockieren.</span><span class="sxs-lookup"><span data-stu-id="02fd4-161">Remember, poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="02fd4-162">Sie sollten viel Zeit damit verbringen, ihre Begrüßungsnachrichten zu entwerfen und Sie zu durchlaufen, wenn Sie nicht den gewünschten Effekt haben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-162">You should spend plenty of time crafting your welcome messages, and iterate on them if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="02fd4-163">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="02fd4-163">Notification messages</span></span>

<span data-ttu-id="02fd4-164">Bei der Verwendung von proaktivem Messaging zum Senden von Benachrichtigungen müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um häufige Aktionen basierend auf Ihrer Benachrichtigung durchzuführen, und ein klares Verständnis dafür, warum die Benachrichtigung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="02fd4-164">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="02fd4-165">Gute Benachrichtigungsnachrichten umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="02fd4-165">Good notification messages will generally include:</span></span>

* <span data-ttu-id="02fd4-166">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="02fd4-166">**What happened.**</span></span> <span data-ttu-id="02fd4-167">Ein klarer Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-167">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="02fd4-168">**Was war das Ergebnis?**</span><span class="sxs-lookup"><span data-stu-id="02fd4-168">**What was the result.**</span></span> <span data-ttu-id="02fd4-169">Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-169">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="02fd4-170">**Wer/was hat ihn ausgelöst.**</span><span class="sxs-lookup"><span data-stu-id="02fd4-170">**Who/what triggered it.**</span></span> <span data-ttu-id="02fd4-171">Die Person oder die Aktion, die die Benachrichtigung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="02fd4-171">Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="02fd4-172">**Was können Benutzer als Antwort tun?**</span><span class="sxs-lookup"><span data-stu-id="02fd4-172">**What can users do in response.**</span></span> <span data-ttu-id="02fd4-173">Erleichtern Sie Ihren Benutzern das Ausführen von Aktionen basierend auf Ihren Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="02fd4-173">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="02fd4-174">**Wie können sich Benutzer abmelden?** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="02fd4-174">**How can users opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="02fd4-175">Proaktive Installation Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="02fd4-175">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="02fd4-176">Die proaktive Installation von apps mithilfe von Microsoft Graph befindet sich derzeit in der Betaphase.</span><span class="sxs-lookup"><span data-stu-id="02fd4-176">Proactively installing apps using the Microsoft Graph is currently in beta.</span></span>

<span data-ttu-id="02fd4-177">Gelegentlich kann es erforderlich sein, Benutzer proaktiv Nachrichten zu verständigen, die zuvor noch nicht mit Ihrer APP installiert oder mit ihr interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-177">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="02fd4-178">Beispielsweise möchten Sie das [Unternehmens Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an die gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-178">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="02fd4-179">In diesem Szenario können Sie die Graph-API verwenden, um Ihre APP proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis Zwischenspeichern, das `conversationUpdate` Ihre APP bei der Installation empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="02fd4-179">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="02fd4-180">Sie können nur apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Microsoft Teams-App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="02fd4-180">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="02fd4-181">Siehe [Installieren von Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation und [proaktive bot-Installation und-Messaging in Microsoft Teams mit Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span><span class="sxs-lookup"><span data-stu-id="02fd4-181">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation and [Proactive bot installation and messaging in Teams with Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="02fd4-182">Es gibt auch ein [Microsoft .NET Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  auf der GitHub-Plattform.</span><span class="sxs-lookup"><span data-stu-id="02fd4-182">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  on the GitHub platform.</span></span>

## <a name="examples"></a><span data-ttu-id="02fd4-183">Beispiele</span><span class="sxs-lookup"><span data-stu-id="02fd4-183">Examples</span></span>

# <a name="cnet"></a>[<span data-ttu-id="02fd4-184">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="02fd4-184">C#/.NET</span></span>](#tab/dotnet)

```csharp
private async Task MessageAllMembersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var teamsChannelId = turnContext.Activity.TeamsGetChannelId();
    var serviceUrl = turnContext.Activity.ServiceUrl;
    var credentials = new MicrosoftAppCredentials(_appId, _appPassword);
    ConversationReference conversationReference = null;

    //Get the set of member IDs to send the message to
    var members = await GetPagedMembers(turnContext, cancellationToken);

    foreach (var teamMember in members)
    {
        var proactiveMessage = MessageFactory.Text($"Hello {teamMember.GivenName} {teamMember.Surname}. I'm a Teams conversation bot.");

        var conversationParameters = new ConversationParameters
        {
            IsGroup = false,
            Bot = turnContext.Activity.Recipient,
            Members = new ChannelAccount[] { teamMember },
            TenantId = turnContext.Activity.Conversation.TenantId,
        };
        //create the new one-to-one conversations
        await ((BotFrameworkAdapter)turnContext.Adapter).CreateConversationAsync(
            teamsChannelId,
            serviceUrl,
            credentials,
            conversationParameters,
            async (t1, c1) =>
            {
                //Get the conversationReference
                conversationReference = t1.Activity.GetConversationReference();
                //Send the proactive message
                await ((BotFrameworkAdapter)turnContext.Adapter).ContinueConversationAsync(
                    _appId,
                    conversationReference,
                    async (t2, c2) =>
                    {
                        await t2.SendActivityAsync(proactiveMessage, c2);
                    },
                    cancellationToken);
            },
            cancellationToken);
    }

    await turnContext.SendActivityAsync(MessageFactory.Text("All messages have been sent."), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="02fd4-185">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="02fd4-185">TypeScript/Node.js</span></span>](#tab/typescript)

```javascript

async messageAllMembersAsync(context) {
    const members = await this.getPagedMembers(context);

    members.forEach(async (teamMember) => {
        const message = MessageFactory.text('Hello ${ teamMember.givenName } ${ teamMember.surname }. I\'m a Teams conversation bot.');

        var ref = TurnContext.getConversationReference(context.activity);
        ref.user = teamMember;

        await context.adapter.createConversation(ref,
            async (t1) => {
                const ref2 = TurnContext.getConversationReference(t1.activity);
                await t1.adapter.continueConversation(ref2, async (t2) => {
                    await t2.sendActivity(message);
                });
            });
    });

    await context.sendActivity(MessageFactory.text('All messages have been sent.'));
}
```

# <a name="python"></a>[<span data-ttu-id="02fd4-186">Python</span><span class="sxs-lookup"><span data-stu-id="02fd4-186">Python</span></span>](#tab/python)

```python
async def _message_all_members(self, turn_context: TurnContext):
    team_members = await self._get_paged_members(turn_context)

    for member in team_members:
        conversation_reference = TurnContext.get_conversation_reference(
            turn_context.activity
        )

        conversation_parameters = ConversationParameters(
            is_group=False,
            bot=turn_context.activity.recipient,
            members=[member],
            tenant_id=turn_context.activity.conversation.tenant_id,
        )

        async def get_ref(tc1):
            conversation_reference_inner = TurnContext.get_conversation_reference(
                tc1.activity
            )
            return await tc1.adapter.continue_conversation(
                conversation_reference_inner, send_message, self._app_id
            )

        async def send_message(tc2: TurnContext):
            return await tc2.send_activity(
                f"Hello {member.name}. I'm a Teams conversation bot."
            )

        await turn_context.adapter.create_conversation(
            conversation_reference, get_ref, conversation_parameters
        )

    await turn_context.send_activity(
        MessageFactory.text("All messages have been sent")
    )

```

# <a name="json"></a>[<span data-ttu-id="02fd4-187">Json</span><span class="sxs-lookup"><span data-stu-id="02fd4-187">JSON</span></span>](#tab/json)

```json
POST /v3/conversations
{
  "bot": {
    "id": "28:10j12ou0d812-2o1098-c1mjojzldxcj-1098028n ",
    "name": "The Bot"
  },
  "members": [
    {
      "id": "29:012d20j1cjo20211"
    }
  ],
  "channelData": {
    "tenant": {
      "id": "197231joe-1209j01821-012kdjoj"
    }
  }
}
```

<span data-ttu-id="02fd4-188">Sie müssen die Benutzer-ID und die Mandanten-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-188">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="02fd4-189">Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Response-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="02fd4-189">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="references"></a><span data-ttu-id="02fd4-190">Informationsquellen</span><span class="sxs-lookup"><span data-stu-id="02fd4-190">References</span></span>

<span data-ttu-id="02fd4-191">Die offiziellen Proactive Messaging-Beispiele sind unten aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="02fd4-191">The official proactive messaging samples are listed below.</span></span>

|  <span data-ttu-id="02fd4-192">Nein.</span><span class="sxs-lookup"><span data-stu-id="02fd4-192">No.</span></span>  | <span data-ttu-id="02fd4-193">Beispiel Name</span><span class="sxs-lookup"><span data-stu-id="02fd4-193">Sample Name</span></span>           | <span data-ttu-id="02fd4-194">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="02fd4-194">Description</span></span>                                                                      | <span data-ttu-id="02fd4-195">.NET</span><span class="sxs-lookup"><span data-stu-id="02fd4-195">.NET</span></span>    | <span data-ttu-id="02fd4-196">JavaScript</span><span class="sxs-lookup"><span data-stu-id="02fd4-196">JavaScript</span></span>   | <span data-ttu-id="02fd4-197">Python</span><span class="sxs-lookup"><span data-stu-id="02fd4-197">Python</span></span>  |
|:--:|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="02fd4-198">57</span><span class="sxs-lookup"><span data-stu-id="02fd4-198">57</span></span>|<span data-ttu-id="02fd4-199">Grundlagen der Microsoft Teams-Konversation</span><span class="sxs-lookup"><span data-stu-id="02fd4-199">Teams Conversation Basics</span></span>  | <span data-ttu-id="02fd4-200">Veranschaulicht Grundlagen der Unterhaltungen in Microsoft Teams, einschließlich des Sendens von 1:1-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="02fd4-200">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>|[<span data-ttu-id="02fd4-201">.Net- &nbsp; Kern</span><span class="sxs-lookup"><span data-stu-id="02fd4-201">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="02fd4-202">JavaScript</span><span class="sxs-lookup"><span data-stu-id="02fd4-202">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="02fd4-203">Python</span><span class="sxs-lookup"><span data-stu-id="02fd4-203">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|<span data-ttu-id="02fd4-204">58</span><span class="sxs-lookup"><span data-stu-id="02fd4-204">58</span></span>|<span data-ttu-id="02fd4-205">Neuen Thread in einem Kanal starten</span><span class="sxs-lookup"><span data-stu-id="02fd4-205">Start new thread in a channel</span></span>     | <span data-ttu-id="02fd4-206">Veranschaulicht das Erstellen eines neuen Threads in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="02fd4-206">Demonstrates creating a new thread in a channel.</span></span> |[<span data-ttu-id="02fd4-207">.Net- &nbsp; Kern</span><span class="sxs-lookup"><span data-stu-id="02fd4-207">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="02fd4-208">JavaScript</span><span class="sxs-lookup"><span data-stu-id="02fd4-208">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="02fd4-209">Python</span><span class="sxs-lookup"><span data-stu-id="02fd4-209">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

<span data-ttu-id="02fd4-210">Das Beispiel unten veranschaulicht die minimale Menge an Informationen, die zum Senden einer proaktiven Nachricht benötigt werden (ohne Verwendung eines `conversationReference` Objekts).</span><span class="sxs-lookup"><span data-stu-id="02fd4-210">The sample below demonstrates the minimal amount of information needed to send a proactive message (without using a `conversationReference` object).</span></span> <span data-ttu-id="02fd4-211">Dieses Beispiel kann hilfreich sein, wenn Sie Rest-API-Aufrufe direkt verwenden oder keine vollständigen `conversationReference` Objekte gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="02fd4-211">This sample can be useful if you're using REST API calls directly, or haven't been storing full `conversationReference` objects.</span></span>

* [<span data-ttu-id="02fd4-212">Proaktive Messaging Teams</span><span class="sxs-lookup"><span data-stu-id="02fd4-212">Teams Proactive Messaging</span></span>](https://github.com/clearab/teamsProactiveMessaging)

## <a name="view-additional-code"></a><span data-ttu-id="02fd4-213">Anzeigen von zusätzlichem Code</span><span class="sxs-lookup"><span data-stu-id="02fd4-213">View additional code</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="02fd4-214">**Proaktive Messaging-Codebeispiele für Teams**</span><span class="sxs-lookup"><span data-stu-id="02fd4-214">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>