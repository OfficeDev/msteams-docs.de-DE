---
title: proaktive Nachrichten senden
description: beschreibt, wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-Bot senden.
ms.topic: overview
ms.author: anclear
Keywords: Senden einer Nachricht erhalten Benutzer-ID Kanal-ID Unterhaltungs-ID
ms.openlocfilehash: 2d7ff10469a181bb06fda5029c8f6b2725b0402d
ms.sourcegitcommit: 7db6eabe3ef128ac7f14b32d07e9e86c995d187f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2021
ms.locfileid: "50103605"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="3b35f-104">Versenden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3b35f-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="3b35f-105">Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="3b35f-105">A proactive message is any message sent by a bot that is not in direct response to a request from a user.</span></span> <span data-ttu-id="3b35f-106">Dies kann Nachrichten wie die folgenden umfassen:</span><span class="sxs-lookup"><span data-stu-id="3b35f-106">This can include messages like:</span></span>

* <span data-ttu-id="3b35f-107">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="3b35f-107">Welcome messages</span></span>
* <span data-ttu-id="3b35f-108">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3b35f-108">Notifications</span></span>
* <span data-ttu-id="3b35f-109">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3b35f-109">Scheduled messages</span></span>

<span data-ttu-id="3b35f-110">Damit Ihr Bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, Gruppenchat oder das Team haben, an den Sie die Nachricht senden möchten.</span><span class="sxs-lookup"><span data-stu-id="3b35f-110">For your bot to send a proactive message, it must have access to the user, group chat, or team that you want to send the message to.</span></span> <span data-ttu-id="3b35f-111">Für einen Gruppenchat oder ein Gruppenteam bedeutet dies, dass die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden muss.</span><span class="sxs-lookup"><span data-stu-id="3b35f-111">For a group chat or team, this means the app that contains your bot must be installed to that location first.</span></span> <span data-ttu-id="3b35f-112">Sie können [Ihre App](#proactively-install-your-app-using-graph) proaktiv mithilfe von Graph in [](/microsoftteams/teams-custom-app-policies-and-settings) einem Team installieren, falls erforderlich, oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu pushen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-112">You can [proactively install your app using Graph](#proactively-install-your-app-using-graph) in a team, if required or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="3b35f-113">Für Benutzer muss Ihre App entweder für den Benutzer installiert werden, oder Ihr Benutzer muss Teil eines Teams sein, in dem Die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3b35f-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="3b35f-114">Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht.</span><span class="sxs-lookup"><span data-stu-id="3b35f-114">Sending a proactive message is different than sending a regular message.</span></span> <span data-ttu-id="3b35f-115">In that, there is no active `turnContext` to use for a reply.</span><span class="sxs-lookup"><span data-stu-id="3b35f-115">In that, there is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="3b35f-116">Möglicherweise müssen Sie auch die Unterhaltung erstellen, bevor Sie die Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-116">You may also need to create the conversation before sending the message.</span></span> <span data-ttu-id="3b35f-117">Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="3b35f-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="3b35f-118">Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="3b35f-119">Auf hoher Ebene müssen Sie die folgenden Schritte ausführen, um eine proaktive Nachricht zu senden:</span><span class="sxs-lookup"><span data-stu-id="3b35f-119">At a high level the steps you'll need to complete to send a proactive message are:</span></span>

1. <span data-ttu-id="3b35f-120">[Erhalten Sie die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="3b35f-120">[Get the user ID or team/channel ID](#get-the-user-id-or-teamchannel-id) (if needed).</span></span>
1. <span data-ttu-id="3b35f-121">[Erstellen Sie den Unterhaltungs- oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="3b35f-121">[Create the conversation or conversation thread](#create-the-conversation) (if needed).</span></span>
1. <span data-ttu-id="3b35f-122">[Erhalten Sie die Unterhaltungs-ID.](#get-the-conversation-id)</span><span class="sxs-lookup"><span data-stu-id="3b35f-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="3b35f-123">[Senden Sie die Nachricht](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="3b35f-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="3b35f-124">Die Codeausschnitte im [Beispielabschnitt](#examples) sind zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="3b35f-124">The code snippets in the [examples](#examples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="3b35f-125">Links zum Vervollständigen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie in [den Codebeispielen.](#code-samples)</span><span class="sxs-lookup"><span data-stu-id="3b35f-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code samples](#code-samples).</span></span>

## <a name="get-the-user-id-or-teamchannel-id"></a><span data-ttu-id="3b35f-126">Benutzer-ID oder Team-/Kanal-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="3b35f-126">Get the user ID or team/channel ID</span></span>

<span data-ttu-id="3b35f-127">Um eine neue Unterhaltung oder einen neuen Unterhaltungsthread in einem Kanal zu erstellen, benötigen Sie die richtige ID.</span><span class="sxs-lookup"><span data-stu-id="3b35f-127">To create a new conversation or conversation thread in a channel, you need the correct ID.</span></span> <span data-ttu-id="3b35f-128">Sie können diese ID auf verschiedene Arten empfangen oder abrufen:</span><span class="sxs-lookup"><span data-stu-id="3b35f-128">You can receive or retrieve this ID in multiple ways:</span></span>

1. <span data-ttu-id="3b35f-129">Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="3b35f-129">When your app is installed in any particular context, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="3b35f-130">Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="3b35f-130">When a new user is added to a context where your app is installed, you'll receive a [`onMembersAdded` Activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
1. <span data-ttu-id="3b35f-131">Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3b35f-131">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team your app is installed.</span></span>
1. <span data-ttu-id="3b35f-132">Sie können die Liste [der Mitglieder eines Teams](~/bots/how-to/get-teams-context.md) abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3b35f-132">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team your app is installed.</span></span>
1. <span data-ttu-id="3b35f-133">Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="3b35f-133">Every Activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="3b35f-134">Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder eine `tenantId` `userId` neue Unterhaltung `channelId` speichern.</span><span class="sxs-lookup"><span data-stu-id="3b35f-134">Regardless of how you gain the information, you'll need to store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="3b35f-135">Sie können den auch `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-135">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="3b35f-136">Die ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können sie nicht zwischen `userId` Bots erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-136">The `userId` is unique to your bot Id and a particular user, you cannot re-use them between bots.</span></span> <span data-ttu-id="3b35f-137">Der Bot muss jedoch global im Team installiert sein, bevor Sie eine proaktive Nachricht an `channelId` einen Kanal senden können.</span><span class="sxs-lookup"><span data-stu-id="3b35f-137">The `channelId` is global, however, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="3b35f-138">Erstellen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="3b35f-138">Create the conversation</span></span>

<span data-ttu-id="3b35f-139">Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen, wenn sie noch nicht vorhanden ist oder Sie die nicht `conversationId` kennen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-139">After you have the user or channel information, you need to create the conversation if it doesn't already exist or you don't know the `conversationId`.</span></span> <span data-ttu-id="3b35f-140">Sie müssen die Unterhaltung nur einmal erstellen und sicherstellen, dass Sie den Wert oder das Objekt speichern, `conversationId` der zukünftig verwendet werden `conversationReference` soll.</span><span class="sxs-lookup"><span data-stu-id="3b35f-140">You must only create the conversation once and make sure you store the `conversationId` value or `conversationReference` object to use in the future.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="3b35f-141">Unterhaltungs-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="3b35f-141">Get the conversation ID</span></span>

<span data-ttu-id="3b35f-142">Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` Objekt oder und senden Sie die `conversationId` `tenantId` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="3b35f-142">After the conversation is created, use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="3b35f-143">Sie können diese ID erhalten, indem Sie entweder die Unterhaltung erstellen oder sie aus jeder Aktivität speichern, die aus diesem Kontext an Sie gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="3b35f-143">You can get this ID by either creating the conversation or storing it from any Activity sent to you from that context.</span></span> <span data-ttu-id="3b35f-144">Stellen Sie sicher, dass Sie diese ID speichern.</span><span class="sxs-lookup"><span data-stu-id="3b35f-144">Make certain that you store this ID.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="3b35f-145">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="3b35f-145">Send the message</span></span>

<span data-ttu-id="3b35f-146">Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-146">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="3b35f-147">Wenn Sie das SDK verwenden, verwenden Sie dazu die Methode und den direkten `continueConversation` `conversationId` `tenantId` API-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="3b35f-147">If you're using the SDK, you'll do so using the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="3b35f-148">Sie müssen dies `conversationParameters` ordnungsgemäß festlegen, damit die Nachricht erfolgreich gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3b35f-148">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="3b35f-149">Weitere Informationen [finden Sie im](#examples) Abschnitt "Beispiele", oder verwenden Sie eines der Beispiele, die im Abschnitt mit den [Codebeispielen aufgeführt](#code-samples) sind.</span><span class="sxs-lookup"><span data-stu-id="3b35f-149">See the [examples](#examples) section or use one of the samples listed in the [code samples](#code-samples) section.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="3b35f-150">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="3b35f-150">Best practices for proactive messaging</span></span>

<span data-ttu-id="3b35f-151">Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="3b35f-151">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="3b35f-152">Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompt angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="3b35f-152">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="3b35f-153">Daher ist es sehr wichtig, diese Funktion sparsam zu verwenden, Keine Spamnachrichten für Ihre Benutzer zu senden und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie nachrichteniert werden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-153">Therefore, it is very important to use this functionality sparingly, don't spam your users, and to provide enough information to let users understand why they are being messaged.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="3b35f-154">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="3b35f-154">Welcome messages</span></span>

<span data-ttu-id="3b35f-155">Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass für die meisten Empfänger der Nachricht kein Kontext dafür besteht, warum sie empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-155">When using proactive messaging to send a welcome message to a user you must keep in mind that, for most people receiving the message, there is no context for why they are receiving it.</span></span> <span data-ttu-id="3b35f-156">Dies ist auch das erste Mal, dass sie mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="3b35f-156">This is also the first time they have interacted with your app.</span></span> <span data-ttu-id="3b35f-157">Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-157">It is your opportunity to create a good first impression.</span></span> <span data-ttu-id="3b35f-158">Die besten Willkommensnachrichten müssen Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="3b35f-158">The best welcome messages must include:</span></span>

* <span data-ttu-id="3b35f-159">**Warum ein Benutzer die Nachricht empfängt.**</span><span class="sxs-lookup"><span data-stu-id="3b35f-159">**Why a user is receiving the message.**</span></span> <span data-ttu-id="3b35f-160">Es muss dem Benutzer klar sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="3b35f-160">It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="3b35f-161">Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="3b35f-161">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="3b35f-162">**Was bieten Sie an?**</span><span class="sxs-lookup"><span data-stu-id="3b35f-162">**What do you offer.**</span></span> <span data-ttu-id="3b35f-163">Was können sie mit Ihrer App tun?</span><span class="sxs-lookup"><span data-stu-id="3b35f-163">What can they do with your app?</span></span> <span data-ttu-id="3b35f-164">Welchen Wert können Sie ihnen mitbringen?</span><span class="sxs-lookup"><span data-stu-id="3b35f-164">What value can you bring to them?</span></span>
* <span data-ttu-id="3b35f-165">**Was sollten sie als Nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="3b35f-165">**What should they do next.**</span></span> <span data-ttu-id="3b35f-166">Laden Sie sie ein, einen Befehl auszuprobieren oder auf eine bestimmte Weise mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="3b35f-166">Invite them to try out a command, or interact with your app in some way.</span></span>

<span data-ttu-id="3b35f-167">Denken Sie daran, dass schlechte Willkommensnachrichten dazu führen können, dass Benutzer Ihren Bot blockieren.</span><span class="sxs-lookup"><span data-stu-id="3b35f-167">Remember, poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="3b35f-168">Verbringen Sie viel Zeit mit dem Erstellen Ihrer Willkommensnachrichten, und iterieren Sie sie, wenn sie nicht den gewünschten Effekt haben.</span><span class="sxs-lookup"><span data-stu-id="3b35f-168">Spend plenty of time crafting your welcome messages, and iterate on them if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="3b35f-169">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="3b35f-169">Notification messages</span></span>

<span data-ttu-id="3b35f-170">Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung zu ergreifen und klar zu verstehen, warum die Benachrichtigung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="3b35f-170">When using proactive messaging to send notifications you must ensure your users have a clear path to take common actions based on your notification and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="3b35f-171">Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="3b35f-171">Good notification messages generally include:</span></span>

* <span data-ttu-id="3b35f-172">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="3b35f-172">**What happened.**</span></span> <span data-ttu-id="3b35f-173">Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="3b35f-173">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="3b35f-174">**Was war das Ergebnis?**</span><span class="sxs-lookup"><span data-stu-id="3b35f-174">**What was the result.**</span></span> <span data-ttu-id="3b35f-175">Es muss klar sein, welches Element oder welche Elemente aktualisiert wurden, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-175">It must be clear what item or thing was updated to cause the notification.</span></span>
* <span data-ttu-id="3b35f-176">**Wer/was hat es ausgelöst?**</span><span class="sxs-lookup"><span data-stu-id="3b35f-176">**Who/what triggered it.**</span></span> <span data-ttu-id="3b35f-177">Wer oder was eine Aktion ausgelöst hat, die dazu führte, dass die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3b35f-177">Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="3b35f-178">**Was können Benutzer als Reaktion tun?**</span><span class="sxs-lookup"><span data-stu-id="3b35f-178">**What can users do in response.**</span></span> <span data-ttu-id="3b35f-179">Machen Sie es Ihren Benutzern einfach, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="3b35f-179">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="3b35f-180">**Wie können Benutzer abmelden?** Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.</span><span class="sxs-lookup"><span data-stu-id="3b35f-180">**How can users opt out.** You must provide a path for users to opt out of additional notifications.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="3b35f-181">Proaktives Installieren Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="3b35f-181">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="3b35f-182">Die proaktive Installation von Apps mit Microsoft Graph befindet sich derzeit in der Betaversion.</span><span class="sxs-lookup"><span data-stu-id="3b35f-182">Proactively installing apps using the Microsoft Graph is currently in beta.</span></span>

<span data-ttu-id="3b35f-183">Gelegentlich kann es erforderlich sein, Benutzer, die ihre App zuvor nicht installiert oder interagiert haben, proaktiv zu senden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-183">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="3b35f-184">Sie möchten z. B. den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Die gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-184">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="3b35f-185">Für dieses Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das Ihre App bei der Installation `conversationUpdate` empfängt.</span><span class="sxs-lookup"><span data-stu-id="3b35f-185">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="3b35f-186">Sie können nur Apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Teams-App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="3b35f-186">You can only install apps that are in your organizational app catalog or the Teams app store.</span></span>

<span data-ttu-id="3b35f-187">Weitere Informationen finden Sie unter ["Installieren von Apps für Benutzer"](/graph/api/userteamwork-post-installedapps) in der Graph-Dokumentation sowie in der proaktiven Botinstallation und [-messaging in Teams mit Microsoft Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)</span><span class="sxs-lookup"><span data-stu-id="3b35f-187">See [Install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [Proactive bot installation and messaging in Teams with Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="3b35f-188">Es gibt auch ein [Microsoft .NET -Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.</span><span class="sxs-lookup"><span data-stu-id="3b35f-188">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="examples"></a><span data-ttu-id="3b35f-189">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3b35f-189">Examples</span></span>

# <a name="cnet"></a>[<span data-ttu-id="3b35f-190">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="3b35f-190">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="3b35f-191">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="3b35f-191">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="3b35f-192">Python</span><span class="sxs-lookup"><span data-stu-id="3b35f-192">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="3b35f-193">Json</span><span class="sxs-lookup"><span data-stu-id="3b35f-193">JSON</span></span>](#tab/json)

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

<span data-ttu-id="3b35f-194">Sie müssen die Benutzer-ID und die Mandanten-ID liefern.</span><span class="sxs-lookup"><span data-stu-id="3b35f-194">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="3b35f-195">Wenn der Aufruf erfolgreich ist, wird die API mit dem folgenden Antwortobjekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="3b35f-195">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a><span data-ttu-id="3b35f-196">Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="3b35f-196">Code samples</span></span>

<span data-ttu-id="3b35f-197">Die offiziellen Beispiele für proaktive Nachrichten sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="3b35f-197">The official proactive messaging samples are as follows:</span></span>

| <span data-ttu-id="3b35f-198">Beispielname</span><span class="sxs-lookup"><span data-stu-id="3b35f-198">Sample Name</span></span>           | <span data-ttu-id="3b35f-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3b35f-199">Description</span></span>                                                                      | <span data-ttu-id="3b35f-200">.NET</span><span class="sxs-lookup"><span data-stu-id="3b35f-200">.NET</span></span>    | <span data-ttu-id="3b35f-201">JavaScript</span><span class="sxs-lookup"><span data-stu-id="3b35f-201">JavaScript</span></span>   | <span data-ttu-id="3b35f-202">Python</span><span class="sxs-lookup"><span data-stu-id="3b35f-202">Python</span></span>  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="3b35f-203">Grundlegendes zu Unterhaltungen in Teams</span><span class="sxs-lookup"><span data-stu-id="3b35f-203">Teams Conversation Basics</span></span>  | <span data-ttu-id="3b35f-204">Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="3b35f-204">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>|[<span data-ttu-id="3b35f-205">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="3b35f-205">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="3b35f-206">JavaScript</span><span class="sxs-lookup"><span data-stu-id="3b35f-206">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="3b35f-207">Python</span><span class="sxs-lookup"><span data-stu-id="3b35f-207">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|<span data-ttu-id="3b35f-208">Starten eines neuen Threads in einem Kanal</span><span class="sxs-lookup"><span data-stu-id="3b35f-208">Start new thread in a channel</span></span>     | <span data-ttu-id="3b35f-209">Veranschaulicht das Erstellen eines neuen Threads in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="3b35f-209">Demonstrates creating a new thread in a channel.</span></span> |[<span data-ttu-id="3b35f-210">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="3b35f-210">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="3b35f-211">JavaScript</span><span class="sxs-lookup"><span data-stu-id="3b35f-211">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[<span data-ttu-id="3b35f-212">Python</span><span class="sxs-lookup"><span data-stu-id="3b35f-212">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a><span data-ttu-id="3b35f-213">Anzeigen zusätzlicher Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="3b35f-213">View additional code samples</span></span>
>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3b35f-214">**Proaktive Messagingcodebeispiele für Teams**</span><span class="sxs-lookup"><span data-stu-id="3b35f-214">**Teams proactive messaging code samples**</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
