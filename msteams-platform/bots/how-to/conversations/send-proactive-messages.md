---
title: Senden proaktiver Nachrichten
description: beschreibt, wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-Bot senden.
ms.topic: overview
ms.author: anclear
Keywords: 'Senden einer Nachricht: Benutzer-ID-Kanal-ID-Unterhaltungs-ID erhalten'
ms.openlocfilehash: 7da470eaba6ae9ecb82c9a7ba04d69b2f196a9d7
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654293"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="52e7e-104">Versenden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="52e7e-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="52e7e-105">Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="52e7e-105">A proactive message is any message sent by a bot that is not in direct response to a request from a user.</span></span> <span data-ttu-id="52e7e-106">Dies kann Nachrichten wie:</span><span class="sxs-lookup"><span data-stu-id="52e7e-106">This can include messages like:</span></span>

* <span data-ttu-id="52e7e-107">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="52e7e-107">Welcome messages</span></span>
* <span data-ttu-id="52e7e-108">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="52e7e-108">Notifications</span></span>
* <span data-ttu-id="52e7e-109">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="52e7e-109">Scheduled messages</span></span>

<span data-ttu-id="52e7e-110">Damit Ihr Bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, den Gruppenchat oder das Team haben, an den Sie die Nachricht senden möchten.</span><span class="sxs-lookup"><span data-stu-id="52e7e-110">For your bot to send a proactive message, it must have access to the user, group chat, or team that you want to send the message to.</span></span> <span data-ttu-id="52e7e-111">Für einen Gruppenchat oder ein Team bedeutet dies, dass die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="52e7e-111">For a group chat or team, this means the app that contains your bot must be installed to that location first.</span></span> <span data-ttu-id="52e7e-112">Sie können [Ihre App proaktiv](#proactively-install-your-app-using-graph) mithilfe von Graph in [](/microsoftteams/teams-custom-app-policies-and-settings) einem Team installieren, falls erforderlich, oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu pushen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-112">You can [proactively install your app using Graph](#proactively-install-your-app-using-graph) in a team, if required or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="52e7e-113">Für Benutzer muss Ihre App entweder für den Benutzer installiert sein, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="52e7e-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="52e7e-114">Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht.</span><span class="sxs-lookup"><span data-stu-id="52e7e-114">Sending a proactive message is different than sending a regular message.</span></span> <span data-ttu-id="52e7e-115">In diesem Bereich ist keine aktive `turnContext` Für eine Antwort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-115">In that, there is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="52e7e-116">Möglicherweise müssen Sie auch die Unterhaltung erstellen, bevor Sie die Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-116">You may also need to create the conversation before sending the message.</span></span> <span data-ttu-id="52e7e-117">Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="52e7e-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="52e7e-118">Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="52e7e-119">Auf einer hohen Ebene sind die Schritte, die Sie ausführen müssen, um eine proaktive Nachricht zu senden:</span><span class="sxs-lookup"><span data-stu-id="52e7e-119">At a high level the steps you'll need to complete to send a proactive message are:</span></span>

1. <span data-ttu-id="52e7e-120">[Die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich) erhalten.</span><span class="sxs-lookup"><span data-stu-id="52e7e-120">[Get the user ID or team/channel ID](#get-the-user-id-or-teamchannel-id) (if needed).</span></span>
1. <span data-ttu-id="52e7e-121">[Erstellen Sie den Unterhaltungs- oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="52e7e-121">[Create the conversation or conversation thread](#create-the-conversation) (if needed).</span></span>
1. <span data-ttu-id="52e7e-122">[Die Unterhaltungs-ID erhalten.](#get-the-conversation-id)</span><span class="sxs-lookup"><span data-stu-id="52e7e-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="52e7e-123">[Senden Sie die Nachricht](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="52e7e-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="52e7e-124">Die Codeausschnitte im Abschnitt [Beispiele](#examples) sind zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="52e7e-124">The code snippets in the [examples](#examples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="52e7e-125">Links zum Abschließen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiele](#code-samples).</span><span class="sxs-lookup"><span data-stu-id="52e7e-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code samples](#code-samples).</span></span>

## <a name="get-the-user-id-or-teamchannel-id"></a><span data-ttu-id="52e7e-126">Benutzer-ID oder Team-/Kanal-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="52e7e-126">Get the user ID or team/channel ID</span></span>

<span data-ttu-id="52e7e-127">Zum Erstellen einer neuen Unterhaltung oder eines neuen Unterhaltungsthreads in einem Kanal benötigen Sie die richtige ID.</span><span class="sxs-lookup"><span data-stu-id="52e7e-127">To create a new conversation or conversation thread in a channel, you need the correct ID.</span></span> <span data-ttu-id="52e7e-128">Sie können diese ID auf verschiedene Weise empfangen oder abrufen:</span><span class="sxs-lookup"><span data-stu-id="52e7e-128">You can receive or retrieve this ID in multiple ways:</span></span>

1. <span data-ttu-id="52e7e-129">Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="52e7e-129">When your app is installed in any particular context, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="52e7e-130">Wenn einem Kontext, in dem Ihre App installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="52e7e-130">When a new user is added to a context where your app is installed, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="52e7e-131">Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="52e7e-131">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team your app is installed.</span></span>
1. <span data-ttu-id="52e7e-132">Sie können die Liste [der Mitglieder eines Teams abrufen,](~/bots/how-to/get-teams-context.md) in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="52e7e-132">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team your app is installed.</span></span>
1. <span data-ttu-id="52e7e-133">Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="52e7e-133">Every Activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="52e7e-134">Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder speichern, um `tenantId` eine neue Unterhaltung zu `userId` `channelId` erstellen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-134">Regardless of how you gain the information, you'll need to store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="52e7e-135">Sie können auch den `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-135">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="52e7e-136">Die ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können sie nicht zwischen `userId` Bots erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-136">The `userId` is unique to your bot Id and a particular user, you cannot re-use them between bots.</span></span> <span data-ttu-id="52e7e-137">The `channelId` is global, however, your bot must be installed in the team before you can send a proactive message to a channel.</span><span class="sxs-lookup"><span data-stu-id="52e7e-137">The `channelId` is global, however, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="52e7e-138">Erstellen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="52e7e-138">Create the conversation</span></span>

<span data-ttu-id="52e7e-139">Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen, wenn sie noch nicht vorhanden ist oder Sie die `conversationId` nicht kennen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-139">After you have the user or channel information, you need to create the conversation if it doesn't already exist or you don't know the `conversationId`.</span></span> <span data-ttu-id="52e7e-140">Sie müssen die Unterhaltung nur einmal erstellen und sicherstellen, dass Sie den Wert oder das Objekt speichern, das `conversationId` in Zukunft verwendet werden `conversationReference` soll.</span><span class="sxs-lookup"><span data-stu-id="52e7e-140">You must only create the conversation once and make sure you store the `conversationId` value or `conversationReference` object to use in the future.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="52e7e-141">Die Unterhaltungs-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="52e7e-141">Get the conversation ID</span></span>

<span data-ttu-id="52e7e-142">Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` Objekt oder und um die Nachricht zu `conversationId` `tenantId` senden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-142">After the conversation is created, use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="52e7e-143">Sie können diese ID erhalten, indem Sie die Unterhaltung erstellen oder aus allen Aktivitäten speichern, die aus diesem Kontext an Sie gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-143">You can get this ID by either creating the conversation or storing it from any Activity sent to you from that context.</span></span> <span data-ttu-id="52e7e-144">Stellen Sie sicher, dass Sie diese ID speichern.</span><span class="sxs-lookup"><span data-stu-id="52e7e-144">Make certain that you store this ID.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="52e7e-145">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="52e7e-145">Send the message</span></span>

<span data-ttu-id="52e7e-146">Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-146">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="52e7e-147">Wenn Sie das SDK verwenden, verwenden Sie dazu die -Methode und und einen direkten `continueConversation` `conversationId` `tenantId` API-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="52e7e-147">If you're using the SDK, you'll do so using the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="52e7e-148">Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="52e7e-148">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="52e7e-149">Sehen Sie [sich den Abschnitt](#examples) Beispiele an, oder verwenden Sie eines der Beispiele, die im Abschnitt [Codebeispiele aufgeführt](#code-samples) sind.</span><span class="sxs-lookup"><span data-stu-id="52e7e-149">See the [examples](#examples) section or use one of the samples listed in the [code samples](#code-samples) section.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="52e7e-150">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="52e7e-150">Best practices for proactive messaging</span></span>

<span data-ttu-id="52e7e-151">Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="52e7e-151">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="52e7e-152">Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompted angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="52e7e-152">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="52e7e-153">Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden, Ihre Benutzer nicht zu spamen und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-153">Therefore, it is very important to use this functionality sparingly, don't spam your users, and to provide enough information to let users understand why they are being messaged.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="52e7e-154">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="52e7e-154">Welcome messages</span></span>

<span data-ttu-id="52e7e-155">Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass für die meisten Empfänger der Nachricht kein Kontext dafür besteht, warum sie sie empfängt.</span><span class="sxs-lookup"><span data-stu-id="52e7e-155">When using proactive messaging to send a welcome message to a user you must keep in mind that, for most people receiving the message, there is no context for why they are receiving it.</span></span> <span data-ttu-id="52e7e-156">Dies ist auch das erste Mal, dass sie mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="52e7e-156">This is also the first time they have interacted with your app.</span></span> <span data-ttu-id="52e7e-157">Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-157">It is your opportunity to create a good first impression.</span></span> <span data-ttu-id="52e7e-158">Die besten Willkommensnachrichten müssen Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="52e7e-158">The best welcome messages must include:</span></span>

* <span data-ttu-id="52e7e-159">**Warum ein Benutzer die Nachricht empfängt.**</span><span class="sxs-lookup"><span data-stu-id="52e7e-159">**Why a user is receiving the message.**</span></span> <span data-ttu-id="52e7e-160">Es muss dem Benutzer sehr klar sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="52e7e-160">It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="52e7e-161">Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="52e7e-161">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="52e7e-162">**Was bieten Sie?**</span><span class="sxs-lookup"><span data-stu-id="52e7e-162">**What do you offer.**</span></span> <span data-ttu-id="52e7e-163">Was können sie mit Ihrer App tun?</span><span class="sxs-lookup"><span data-stu-id="52e7e-163">What can they do with your app?</span></span> <span data-ttu-id="52e7e-164">Welchen Wert können Sie ihnen bringen?</span><span class="sxs-lookup"><span data-stu-id="52e7e-164">What value can you bring to them?</span></span>
* <span data-ttu-id="52e7e-165">**Was sollten sie als Nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="52e7e-165">**What should they do next.**</span></span> <span data-ttu-id="52e7e-166">Laden Sie sie ein, einen Befehl auszuprobieren oder auf eine Weise mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="52e7e-166">Invite them to try out a command, or interact with your app in some way.</span></span>

<span data-ttu-id="52e7e-167">Denken Sie daran, dass schlechte Willkommensnachrichten dazu führen können, dass Benutzer Ihren Bot blockieren.</span><span class="sxs-lookup"><span data-stu-id="52e7e-167">Remember, poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="52e7e-168">Verbringen Sie viel Zeit damit, Ihre Willkommensnachrichten zu erstellen, und iterieren Sie sie, wenn sie nicht den gewünschten Effekt haben.</span><span class="sxs-lookup"><span data-stu-id="52e7e-168">Spend plenty of time crafting your welcome messages, and iterate on them if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="52e7e-169">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="52e7e-169">Notification messages</span></span>

<span data-ttu-id="52e7e-170">Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer einen klaren Pfad haben, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung und einem klaren Verständnis der Gründe für die Benachrichtigung zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-170">When using proactive messaging to send notifications you must ensure your users have a clear path to take common actions based on your notification and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="52e7e-171">Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="52e7e-171">Good notification messages generally include:</span></span>

* <span data-ttu-id="52e7e-172">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="52e7e-172">**What happened.**</span></span> <span data-ttu-id="52e7e-173">Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="52e7e-173">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="52e7e-174">**Was war das Ergebnis?**</span><span class="sxs-lookup"><span data-stu-id="52e7e-174">**What was the result.**</span></span> <span data-ttu-id="52e7e-175">Es muss klar sein, welche Elemente oder Elemente aktualisiert wurden, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-175">It must be clear what item or thing was updated to cause the notification.</span></span>
* <span data-ttu-id="52e7e-176">**Wer/was hat es ausgelöst.**</span><span class="sxs-lookup"><span data-stu-id="52e7e-176">**Who/what triggered it.**</span></span> <span data-ttu-id="52e7e-177">Wer oder was hat maßnahmen, die dazu führte, dass die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="52e7e-177">Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="52e7e-178">**Was können Benutzer als Antwort tun?**</span><span class="sxs-lookup"><span data-stu-id="52e7e-178">**What can users do in response.**</span></span> <span data-ttu-id="52e7e-179">Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-179">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="52e7e-180">**Wie können Benutzer abmelden?** Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.</span><span class="sxs-lookup"><span data-stu-id="52e7e-180">**How can users opt out.** You must provide a path for users to opt out of additional notifications.</span></span>

### <a name="scheduled-messages"></a><span data-ttu-id="52e7e-181">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="52e7e-181">Scheduled messages</span></span>

<span data-ttu-id="52e7e-182">Wenn Sie proaktives Messaging zum Senden geplanter Nachrichten an Benutzer verwenden, stellen Sie sicher, dass Ihre Zeitzone auf ihre Zeitzone aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="52e7e-182">When using proactive messaging to send scheduled messages to users, verify that your time zone is updated to their time zone.</span></span> <span data-ttu-id="52e7e-183">Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer zugestellt werden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-183">This ensures that the messages are delivered to the users at the relevant time.</span></span> <span data-ttu-id="52e7e-184">Zu den Geplanten Nachrichten gehören im Allgemeinen:</span><span class="sxs-lookup"><span data-stu-id="52e7e-184">Schedule messages generally include:</span></span>

* <span data-ttu-id="52e7e-185">**Warum empfängt der Benutzer die Nachricht:** Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, warum sie die Nachricht empfangen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-185">**Why is the user receiving the message**: Make it easy for your users to understand the reason for which they are receiving the message.</span></span>
* <span data-ttu-id="52e7e-186">**Wie kann der Benutzer als Nächstes** vorgehen: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ergreifen.</span><span class="sxs-lookup"><span data-stu-id="52e7e-186">**What can user do next**: Users can take the required action based on the message content.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="52e7e-187">Proaktive Installation Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="52e7e-187">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="52e7e-188">Die proaktive Installation von Apps mit Microsoft Graph befindet sich derzeit in der Betaversion.</span><span class="sxs-lookup"><span data-stu-id="52e7e-188">Proactively installing apps using the Microsoft Graph is currently in beta.</span></span>

<span data-ttu-id="52e7e-189">Gelegentlich ist es möglicherweise erforderlich, Benutzer proaktiv zu entsenden, die ihre App zuvor nicht installiert oder mit ihr interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="52e7e-189">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="52e7e-190">Beispielsweise möchten Sie den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-190">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="52e7e-191">Für dieses Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das Ihre App bei der Installation `conversationUpdate` empfängt.</span><span class="sxs-lookup"><span data-stu-id="52e7e-191">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="52e7e-192">Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams-App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="52e7e-192">You can only install apps that are in your organizational app catalog or the Teams app store.</span></span>

<span data-ttu-id="52e7e-193">Weitere [Informationen finden Sie](/graph/api/userteamwork-post-installedapps) unter Installieren von Apps für Benutzer in der Graph-Dokumentation und proaktiver Botinstallation und [-messaging in Teams mit Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span><span class="sxs-lookup"><span data-stu-id="52e7e-193">See [Install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [Proactive bot installation and messaging in Teams with Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="52e7e-194">Es gibt auch ein [Microsoft .NET-Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.</span><span class="sxs-lookup"><span data-stu-id="52e7e-194">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="examples"></a><span data-ttu-id="52e7e-195">Beispiele</span><span class="sxs-lookup"><span data-stu-id="52e7e-195">Examples</span></span>

# <a name="cnet"></a>[<span data-ttu-id="52e7e-196">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="52e7e-196">C#/.NET</span></span>](#tab/dotnet)

```csharp
[Route("api/notify")]
[ApiController]
public class NotifyController : ControllerBase
{
    private readonly IBotFrameworkHttpAdapter _adapter;
    private readonly string _appId;
    private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

    public NotifyController(IBotFrameworkHttpAdapter adapter, IConfiguration configuration, ConcurrentDictionary<string, ConversationReference> conversationReferences)
    {
        _adapter = adapter;
        _conversationReferences = conversationReferences;
        _appId = configuration["MicrosoftAppId"] ?? string.Empty;
    }

    public async Task<IActionResult> Get()
    {
        foreach (var conversationReference in _conversationReferences.Values)
        {
            await ((BotAdapter)_adapter).ContinueConversationAsync(_appId, conversationReference, BotCallback, default(CancellationToken));
        }
        
        // Let the caller know proactive messages have been sent
        return new ContentResult()
        {
            Content = "<html><body><h1>Proactive messages have been sent.</h1></body></html>",
            ContentType = "text/html",
            StatusCode = (int)HttpStatusCode.OK,
        };
    }

    private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
    {
        // If you encounter permission-related errors when sending this message, see
        // https://aka.ms/BotTrustServiceUrl
        await turnContext.SendActivityAsync("proactive hello");
    }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="52e7e-197">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="52e7e-197">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="52e7e-198">Python</span><span class="sxs-lookup"><span data-stu-id="52e7e-198">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="52e7e-199">Json</span><span class="sxs-lookup"><span data-stu-id="52e7e-199">JSON</span></span>](#tab/json)

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

<span data-ttu-id="52e7e-200">Sie müssen die Benutzer-ID und die Mandanten-ID liefern.</span><span class="sxs-lookup"><span data-stu-id="52e7e-200">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="52e7e-201">Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Antwortobjekt zurück.</span><span class="sxs-lookup"><span data-stu-id="52e7e-201">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a><span data-ttu-id="52e7e-202">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="52e7e-202">Code samples</span></span>

<span data-ttu-id="52e7e-203">Die offiziellen proaktiven Messagingbeispiele sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="52e7e-203">The official proactive messaging samples are as follows:</span></span>

| <span data-ttu-id="52e7e-204">Beispielname</span><span class="sxs-lookup"><span data-stu-id="52e7e-204">Sample Name</span></span>           | <span data-ttu-id="52e7e-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="52e7e-205">Description</span></span>                                                                      | <span data-ttu-id="52e7e-206">.NET</span><span class="sxs-lookup"><span data-stu-id="52e7e-206">.NET</span></span>    | <span data-ttu-id="52e7e-207">JavaScript</span><span class="sxs-lookup"><span data-stu-id="52e7e-207">JavaScript</span></span>   | <span data-ttu-id="52e7e-208">Python</span><span class="sxs-lookup"><span data-stu-id="52e7e-208">Python</span></span>  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="52e7e-209">Grundlagen für Teams-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="52e7e-209">Teams Conversation Basics</span></span>  | <span data-ttu-id="52e7e-210">Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich des Sendens von proaktiven 1:1-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="52e7e-210">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>|[<span data-ttu-id="52e7e-211">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="52e7e-211">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="52e7e-212">JavaScript</span><span class="sxs-lookup"><span data-stu-id="52e7e-212">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="52e7e-213">Python</span><span class="sxs-lookup"><span data-stu-id="52e7e-213">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|<span data-ttu-id="52e7e-214">Starten eines neuen Threads in einem Kanal</span><span class="sxs-lookup"><span data-stu-id="52e7e-214">Start new thread in a channel</span></span>     | <span data-ttu-id="52e7e-215">Veranschaulicht das Erstellen eines neuen Threads in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="52e7e-215">Demonstrates creating a new thread in a channel.</span></span> |[<span data-ttu-id="52e7e-216">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="52e7e-216">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="52e7e-217">JavaScript</span><span class="sxs-lookup"><span data-stu-id="52e7e-217">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="52e7e-218">Python</span><span class="sxs-lookup"><span data-stu-id="52e7e-218">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a><span data-ttu-id="52e7e-219">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="52e7e-219">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="52e7e-220">**Proaktive Messagingcodebeispiele für Teams**</span><span class="sxs-lookup"><span data-stu-id="52e7e-220">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
