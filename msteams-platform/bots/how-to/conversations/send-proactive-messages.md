---
title: Senden proaktiver Nachrichten
description: Beschreibt das Senden proaktiver Nachrichten mit Ihrem Microsoft Teams-Bot.
ms.topic: conceptual
ms.author: anclear
localization_priority: Normal
Keywords: 'Senden einer Nachricht: Benutzer-ID-Kanal-ID-Unterhaltungs-ID erhalten'
ms.openlocfilehash: ae651ac94b1b092374f6fae284b67070036b561f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020919"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="82c40-104">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="82c40-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="82c40-105">Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht auf eine Anforderung eines Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="82c40-105">A proactive message is any message sent by a bot that is not in response to a request from a user.</span></span> <span data-ttu-id="82c40-106">Dies kann Nachrichten umfassen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="82c40-106">This can include messages, such as:</span></span>

* <span data-ttu-id="82c40-107">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="82c40-107">Welcome messages</span></span>
* <span data-ttu-id="82c40-108">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="82c40-108">Notifications</span></span>
* <span data-ttu-id="82c40-109">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="82c40-109">Scheduled messages</span></span>

<span data-ttu-id="82c40-110">Damit Ihr Bot eine proaktive Nachricht an einen Benutzer, Gruppenchat oder ein Team senden kann, muss er Zugriff auf das Senden der Nachricht haben.</span><span class="sxs-lookup"><span data-stu-id="82c40-110">For your bot to send a proactive message to a user, group chat, or team, it must have access to send the message.</span></span> <span data-ttu-id="82c40-111">Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden.</span><span class="sxs-lookup"><span data-stu-id="82c40-111">For a group chat or team, the app that contains your bot must be first installed in that location.</span></span> <span data-ttu-id="82c40-112">Sie können Ihre App bei Bedarf proaktiv mithilfe von Microsoft [](/microsoftteams/teams-custom-app-policies-and-settings) [Graph](#proactively-install-your-app-using-graph) in einem Team installieren oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-112">You can [proactively install your app using Microsoft Graph](#proactively-install-your-app-using-graph) in a team, if required, or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="82c40-113">Für Benutzer muss Ihre App entweder für den Benutzer installiert sein, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="82c40-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="82c40-114">Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht.</span><span class="sxs-lookup"><span data-stu-id="82c40-114">Sending a proactive message is different from sending a regular message.</span></span> <span data-ttu-id="82c40-115">Es ist nicht `turnContext` aktiv, eine Antwort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="82c40-115">There is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="82c40-116">Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-116">You must create the conversation before sending the message.</span></span> <span data-ttu-id="82c40-117">Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="82c40-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="82c40-118">Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.</span><span class="sxs-lookup"><span data-stu-id="82c40-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="82c40-119">**So senden Sie eine proaktive Nachricht**</span><span class="sxs-lookup"><span data-stu-id="82c40-119">**To send a proactive message**</span></span>

1. <span data-ttu-id="82c40-120">Wenn erforderlich, erhalten Sie die [Benutzer-, Team- oder Kanal-ID.](#get-the-user-id-team-id-or-channel-id)</span><span class="sxs-lookup"><span data-stu-id="82c40-120">[Get the user ID, team ID, or channel ID](#get-the-user-id-team-id-or-channel-id), if required.</span></span>
1. <span data-ttu-id="82c40-121">[Erstellen Sie die Unterhaltung](#create-the-conversation), falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="82c40-121">[Create the conversation](#create-the-conversation), if required.</span></span>
1. <span data-ttu-id="82c40-122">[Die Unterhaltungs-ID erhalten.](#get-the-conversation-id)</span><span class="sxs-lookup"><span data-stu-id="82c40-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="82c40-123">[Senden Sie die Nachricht](#send-the-message).</span><span class="sxs-lookup"><span data-stu-id="82c40-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="82c40-124">Die Codeausschnitte im [Abschnitt Beispiele](#samples) sind zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="82c40-124">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="82c40-125">Links zum Abschließen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).</span><span class="sxs-lookup"><span data-stu-id="82c40-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code sample](#code-sample).</span></span>

<span data-ttu-id="82c40-126">Informationen zur effektiven Verwendung proaktiver Nachrichten finden Sie [unter Best Practices for proactive messaging](#best-practices-for-proactive-messaging).</span><span class="sxs-lookup"><span data-stu-id="82c40-126">For using proactive messages effectively, see [best practices for proactive messaging](#best-practices-for-proactive-messaging).</span></span> <span data-ttu-id="82c40-127">In bestimmten Szenarien müssen Sie Ihre App [proaktiv mithilfe von Graph installieren.](#proactively-install-your-app-using-graph)</span><span class="sxs-lookup"><span data-stu-id="82c40-127">For certain scenarios, you must [proactively install your app using Graph](#proactively-install-your-app-using-graph).</span></span> <span data-ttu-id="82c40-128">Die Codeausschnitte im [Abschnitt Beispiele](#samples) sind zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="82c40-128">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="82c40-129">Vollständige Arbeitsbeispiele für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).</span><span class="sxs-lookup"><span data-stu-id="82c40-129">For complete working samples for both one-to-one conversations and groups or channels, see [code sample](#code-sample).</span></span>

## <a name="get-the-user-id-team-id-or-channel-id"></a><span data-ttu-id="82c40-130">Benutzer-ID, Team-ID oder Kanal-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="82c40-130">Get the user ID, team ID or channel ID</span></span>

<span data-ttu-id="82c40-131">Zum Erstellen einer neuen Unterhaltung oder eines neuen Unterhaltungsthreads in einem Kanal müssen Sie über die richtige ID verfügen.</span><span class="sxs-lookup"><span data-stu-id="82c40-131">To create a new conversation or conversation thread in a channel, you must have the correct ID.</span></span> <span data-ttu-id="82c40-132">Sie können diese ID mithilfe einer der folgenden Optionen empfangen oder abrufen:</span><span class="sxs-lookup"><span data-stu-id="82c40-132">You can receive or retrieve this ID using any of the following:</span></span>

* <span data-ttu-id="82c40-133">Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="82c40-133">When your app is installed in any particular context, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="82c40-134">Wenn einem Kontext, in dem Ihre App installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span><span class="sxs-lookup"><span data-stu-id="82c40-134">When a new user is added to a context where your app is installed, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="82c40-135">Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="82c40-135">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team where your app is installed.</span></span>
* <span data-ttu-id="82c40-136">Sie können die Liste [der Mitglieder eines Teams](~/bots/how-to/get-teams-context.md) abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="82c40-136">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team where your app is installed.</span></span>
* <span data-ttu-id="82c40-137">Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="82c40-137">Every activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="82c40-138">Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder speichern, um `tenantId` eine neue Unterhaltung zu `userId` `channelId` erstellen.</span><span class="sxs-lookup"><span data-stu-id="82c40-138">Regardless of how you get the information, you must store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="82c40-139">Sie können auch den `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82c40-139">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="82c40-140">Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="82c40-140">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="82c40-141">Sie können die zwischen `userId` Bots nicht wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="82c40-141">You cannot reuse the `userId` between bots.</span></span> <span data-ttu-id="82c40-142">Der `channelId` ist global.</span><span class="sxs-lookup"><span data-stu-id="82c40-142">The `channelId` is global.</span></span> <span data-ttu-id="82c40-143">Ihr Bot muss jedoch im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.</span><span class="sxs-lookup"><span data-stu-id="82c40-143">However, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

<span data-ttu-id="82c40-144">Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen.</span><span class="sxs-lookup"><span data-stu-id="82c40-144">After you have the user or channel information, you must create the conversation.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="82c40-145">Erstellen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="82c40-145">Create the conversation</span></span>

<span data-ttu-id="82c40-146">Sie müssen die Unterhaltung erstellen, wenn sie nicht vorhanden ist oder Sie die `conversationId` nicht kennen.</span><span class="sxs-lookup"><span data-stu-id="82c40-146">You must create the conversation if it does not exist or you do not know the `conversationId`.</span></span> <span data-ttu-id="82c40-147">Sie müssen die Unterhaltung nur einmal erstellen und den `conversationId` Wert oder das Objekt `conversationReference` speichern.</span><span class="sxs-lookup"><span data-stu-id="82c40-147">You must only create the conversation once and store the `conversationId` value or `conversationReference` object.</span></span>

<span data-ttu-id="82c40-148">Nachdem die Unterhaltung erstellt wurde, müssen Sie die Unterhaltungs-ID erhalten.</span><span class="sxs-lookup"><span data-stu-id="82c40-148">After the conversation is created, you must get the conversation ID.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="82c40-149">Die Unterhaltungs-ID erhalten</span><span class="sxs-lookup"><span data-stu-id="82c40-149">Get the conversation ID</span></span>

<span data-ttu-id="82c40-150">Verwenden Sie entweder `conversationReference` das Objekt oder und um die Nachricht zu `conversationId` `tenantId` senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-150">Use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="82c40-151">Sie können diese ID erhalten, indem Sie die Unterhaltung entweder erstellen oder aus allen Aktivitäten speichern, die aus diesem Kontext an Sie gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="82c40-151">You can get this ID by either creating the conversation or storing it from any activity sent to you from that context.</span></span> <span data-ttu-id="82c40-152">Speichern Sie diese ID als Referenz.</span><span class="sxs-lookup"><span data-stu-id="82c40-152">Store this ID for reference.</span></span>

<span data-ttu-id="82c40-153">Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-153">After you get the appropriate address information, you can send your message.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="82c40-154">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="82c40-154">Send the message</span></span>

<span data-ttu-id="82c40-155">Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-155">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="82c40-156">Wenn Sie das SDK verwenden, verwenden Sie dazu die -Methode und und einen direkten `continueConversation` `conversationId` `tenantId` API-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="82c40-156">If you're using the SDK, you'll do so using the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="82c40-157">Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="82c40-157">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="82c40-158">Lesen Sie [den Abschnitt](#samples) Beispiele, oder verwenden Sie eines der Im [Codebeispielabschnitt aufgeführten](#code-sample) Beispiele.</span><span class="sxs-lookup"><span data-stu-id="82c40-158">See the [samples](#samples) section or use one of the samples listed in the [code sample](#code-sample) section.</span></span>

<span data-ttu-id="82c40-159">Wenn Sie das SDK verwenden, müssen Sie die -Methode und das und verwenden, um einen direkten API-Aufruf zum Senden `continueConversation` `conversationId` der Nachricht zu `tenantId` erstellen.</span><span class="sxs-lookup"><span data-stu-id="82c40-159">If you are using the SDK, you must use the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call to send the message.</span></span> <span data-ttu-id="82c40-160">Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="82c40-160">You must set the `conversationParameters` correctly to successfully send your message.</span></span>

<span data-ttu-id="82c40-161">Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und gleichzeitig proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="82c40-161">Now that you have sent the proactive message, you must follow these best practices while sending proactive messages for better information exchange between users and the bot.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="82c40-162">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="82c40-162">Best practices for proactive messaging</span></span>

<span data-ttu-id="82c40-163">Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="82c40-163">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="82c40-164">Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompted angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="82c40-164">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="82c40-165">Daher ist es sehr wichtig, proaktives Messaging sparsam zu verwenden, keine Spamnachrichten für Ihre Benutzer zu verwenden und genügend Informationen zur Verfügung zu stellen, damit Benutzer verstehen können, warum sie die Nachrichten empfangen.</span><span class="sxs-lookup"><span data-stu-id="82c40-165">Therefore, it is very important to use proactive messaging sparingly, not spam your users, and provide enough information to let users understand why they are receiving the messages.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="82c40-166">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="82c40-166">Welcome messages</span></span>

<span data-ttu-id="82c40-167">Wenn proaktives Messaging zum Senden einer Willkommensnachricht an einen Benutzer verwendet wird, gibt es keinen Kontext dafür, warum die Benutzer die Nachricht empfangen.</span><span class="sxs-lookup"><span data-stu-id="82c40-167">When proactive messaging is used to send a welcome message to a user, there is no context for why the users receive the message.</span></span> <span data-ttu-id="82c40-168">Dies ist auch das erste Mal, dass Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="82c40-168">This is also the first time users interact with your app.</span></span> <span data-ttu-id="82c40-169">Es ist eine Gelegenheit, einen guten ersten Eindruck zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="82c40-169">It is an opportunity to create a good first impression.</span></span> <span data-ttu-id="82c40-170">Die besten Willkommensnachrichten müssen Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="82c40-170">The best welcome messages must include:</span></span>

* <span data-ttu-id="82c40-171">Warum ein Benutzer die Nachricht empfängt: Es muss dem Benutzer sehr klar sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="82c40-171">Why a user is receiving the message: It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="82c40-172">Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.</span><span class="sxs-lookup"><span data-stu-id="82c40-172">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and who installed it.</span></span>
* <span data-ttu-id="82c40-173">Was bieten Sie: Benutzer müssen in der Lage sein, zu ermitteln, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bieten können.</span><span class="sxs-lookup"><span data-stu-id="82c40-173">What do you offer: Users must be able to identify what they can do with your app and what value can you bring to them.</span></span>
* <span data-ttu-id="82c40-174">Was sollten sie als Nächstes tun: Laden Sie Benutzer ein, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="82c40-174">What should they do next: Invite users to try out a command, or interact with your app.</span></span>

<span data-ttu-id="82c40-175">Schlechte Willkommensnachrichten können dazu führen, dass Benutzer Ihren Bot blockieren.</span><span class="sxs-lookup"><span data-stu-id="82c40-175">Poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="82c40-176">Schreiben Sie auf den Punkt, und löschen Sie Begrüßungsnachrichten.</span><span class="sxs-lookup"><span data-stu-id="82c40-176">Write to the point and clear welcome messages.</span></span> <span data-ttu-id="82c40-177">Iterate on the welcome messages if they are not having the desired effect.</span><span class="sxs-lookup"><span data-stu-id="82c40-177">Iterate on the welcome messages if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="82c40-178">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="82c40-178">Notification messages</span></span>

<span data-ttu-id="82c40-179">Um Benachrichtigungen mit proaktivem Messaging zu senden, stellen Sie sicher, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="82c40-179">To send notifications using proactive messaging, ensure your users have a clear path to take common actions based on your notification.</span></span> <span data-ttu-id="82c40-180">Stellen Sie sicher, dass Benutzer ein klares Verständnis dafür haben, warum sie eine Benachrichtigung erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="82c40-180">Ensure users have a clear understanding of why they have received a notification.</span></span> <span data-ttu-id="82c40-181">Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="82c40-181">Good notification messages generally include the following:</span></span>

* <span data-ttu-id="82c40-182">Was passiert ist: Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="82c40-182">What happened: A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="82c40-183">Das Ergebnis: Es muss klar sein, welches Element aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="82c40-183">What was the result: It must be clear what item was updated to cause the notification.</span></span>
* <span data-ttu-id="82c40-184">Wer oder was hat sie ausgelöst: Wer oder welche Aktion hat die Benachrichtigung gesendet.</span><span class="sxs-lookup"><span data-stu-id="82c40-184">Who or what triggered it: Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="82c40-185">Was können Benutzer als Reaktion tun: Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="82c40-185">What can users do in response: Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="82c40-186">Wie können Benutzer sich abmelden: Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.</span><span class="sxs-lookup"><span data-stu-id="82c40-186">How can users opt-out: You must provide a path for users to opt-out of additional notifications.</span></span>

<span data-ttu-id="82c40-187">Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mithilfe von Graph.</span><span class="sxs-lookup"><span data-stu-id="82c40-187">To send messages to a large group of users, for example to your organization, proactively install your app using Graph.</span></span>

### <a name="scheduled-messages"></a><span data-ttu-id="82c40-188">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="82c40-188">Scheduled messages</span></span>

<span data-ttu-id="82c40-189">Wenn Sie proaktives Messaging zum Senden geplanter Nachrichten an Benutzer verwenden, stellen Sie sicher, dass Ihre Zeitzone auf ihre Zeitzone aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="82c40-189">When using proactive messaging to send scheduled messages to users, verify that your time zone is updated to their time zone.</span></span> <span data-ttu-id="82c40-190">Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer zugestellt werden.</span><span class="sxs-lookup"><span data-stu-id="82c40-190">This ensures that the messages are delivered to the users at the relevant time.</span></span> <span data-ttu-id="82c40-191">Zu den Geplanten Nachrichten gehören im Allgemeinen:</span><span class="sxs-lookup"><span data-stu-id="82c40-191">Schedule messages generally include:</span></span>

* <span data-ttu-id="82c40-192">Warum empfängt der Benutzer die Nachricht: Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, warum sie die Nachricht empfangen.</span><span class="sxs-lookup"><span data-stu-id="82c40-192">Why is the user receiving the message: Make it easy for your users to understand the reason for which they are receiving the message.</span></span>
* <span data-ttu-id="82c40-193">Was der Benutzer als Nächstes tun kann: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ergreifen.</span><span class="sxs-lookup"><span data-stu-id="82c40-193">What can user do next: Users can take the required action based on the message content.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="82c40-194">Proaktive Installation Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="82c40-194">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="82c40-195">Die proaktive Installation von Apps mithilfe von Graph befindet sich derzeit in der Betaversion.</span><span class="sxs-lookup"><span data-stu-id="82c40-195">Proactively installing apps using Graph is currently in beta.</span></span>

<span data-ttu-id="82c40-196">Proaktiv nachrichtenbenutzer, die zuvor nicht installiert oder mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="82c40-196">Proactively message users that have previously not installed or interacted with your app.</span></span> <span data-ttu-id="82c40-197">Beispielsweise möchten Sie den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="82c40-197">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="82c40-198">In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="82c40-198">In this case, you can use the Graph API to proactively install your app for your users.</span></span> <span data-ttu-id="82c40-199">Speichern Sie die erforderlichen Werte aus dem `conversationUpdate` Ereignis, das Ihre App bei der Installation empfängt.</span><span class="sxs-lookup"><span data-stu-id="82c40-199">Cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="82c40-200">Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams App Store befinden.</span><span class="sxs-lookup"><span data-stu-id="82c40-200">You can only install apps that are in your organizational app catalog or the Teams App Store.</span></span>

<span data-ttu-id="82c40-201">Weitere [Informationen finden Sie](/graph/api/userteamwork-post-installedapps) unter Installieren von Apps für Benutzer in der Graph-Dokumentation und proaktiver Botinstallation und [-messaging in Teams mit Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span><span class="sxs-lookup"><span data-stu-id="82c40-201">See [install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [proactive bot installation and messaging in Teams with Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="82c40-202">Es gibt auch ein [Microsoft .NET-Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.</span><span class="sxs-lookup"><span data-stu-id="82c40-202">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="samples"></a><span data-ttu-id="82c40-203">Beispiele</span><span class="sxs-lookup"><span data-stu-id="82c40-203">Samples</span></span>

<span data-ttu-id="82c40-204">Der folgende Code zeigt ein einfaches Codebeispiel, das Ihre App proaktiv mithilfe von Graph installiert:</span><span class="sxs-lookup"><span data-stu-id="82c40-204">The following code shows a simple code sample that proactively installs your app using Graph:</span></span>

# <a name="c"></a>[<span data-ttu-id="82c40-205">C#</span><span class="sxs-lookup"><span data-stu-id="82c40-205">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="82c40-206">TypeScript</span><span class="sxs-lookup"><span data-stu-id="82c40-206">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="82c40-207">Python</span><span class="sxs-lookup"><span data-stu-id="82c40-207">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="82c40-208">Json</span><span class="sxs-lookup"><span data-stu-id="82c40-208">JSON</span></span>](#tab/json)

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

<span data-ttu-id="82c40-209">Sie müssen die Benutzer-ID und die Mandanten-ID liefern.</span><span class="sxs-lookup"><span data-stu-id="82c40-209">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="82c40-210">Wenn der Aufruf erfolgreich ist, gibt die API das folgende Antwortobjekt zurück:</span><span class="sxs-lookup"><span data-stu-id="82c40-210">If the call succeeds, the API returns the following response object:</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-sample"></a><span data-ttu-id="82c40-211">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="82c40-211">Code sample</span></span>

<span data-ttu-id="82c40-212">Die folgende Tabelle enthält ein einfaches Codebeispiel, das grundlegenden Unterhaltungsfluss in eine Teams-Anwendung integriert und wie Sie einen neuen Unterhaltungsthread in einem Kanal in Teams erstellen:</span><span class="sxs-lookup"><span data-stu-id="82c40-212">The following table provides a simple code sample that incorporate basic conversation flow into a Teams application and how to create a new conversation thread in a channel in Teams:</span></span>

| <span data-ttu-id="82c40-213">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="82c40-213">**Sample Name**</span></span> | <span data-ttu-id="82c40-214">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="82c40-214">**Description**</span></span> | <span data-ttu-id="82c40-215">**.NET**</span><span class="sxs-lookup"><span data-stu-id="82c40-215">**.NET**</span></span> | <span data-ttu-id="82c40-216">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="82c40-216">**Node.js**</span></span> | <span data-ttu-id="82c40-217">**Python**</span><span class="sxs-lookup"><span data-stu-id="82c40-217">**Python**</span></span> |
|---------------|--------------|--------|-------------|--------|
| <span data-ttu-id="82c40-218">Grundlagen für Teams-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="82c40-218">Teams Conversation Basics</span></span>  | <span data-ttu-id="82c40-219">Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich des Sendens von proaktiven 1:1-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="82c40-219">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>| [<span data-ttu-id="82c40-220">View</span><span class="sxs-lookup"><span data-stu-id="82c40-220">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="82c40-221">View</span><span class="sxs-lookup"><span data-stu-id="82c40-221">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="82c40-222">View</span><span class="sxs-lookup"><span data-stu-id="82c40-222">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| <span data-ttu-id="82c40-223">Starten eines neuen Threads in einem Kanal</span><span class="sxs-lookup"><span data-stu-id="82c40-223">Start new thread in a channel</span></span> | <span data-ttu-id="82c40-224">Veranschaulicht das Erstellen eines neuen Threads in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="82c40-224">Demonstrates creating a new thread in a channel.</span></span> | [<span data-ttu-id="82c40-225">View</span><span class="sxs-lookup"><span data-stu-id="82c40-225">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="82c40-226">View</span><span class="sxs-lookup"><span data-stu-id="82c40-226">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="82c40-227">View</span><span class="sxs-lookup"><span data-stu-id="82c40-227">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

### <a name="additional-code-sample"></a><span data-ttu-id="82c40-228">Zusätzliches Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="82c40-228">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82c40-229">Proaktive Messagingcodebeispiele für Teams</span><span class="sxs-lookup"><span data-stu-id="82c40-229">Teams proactive messaging code samples</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a><span data-ttu-id="82c40-230">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="82c40-230">Next step</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="82c40-231">[**Proaktive Messagingcodebeispiele für Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp) 
>  [Formatieren von Botnachrichten](~/bots/how-to/format-your-bot-messages.md)</span><span class="sxs-lookup"><span data-stu-id="82c40-231">[**Teams proactive messaging code samples**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
[Format your bot messages](~/bots/how-to/format-your-bot-messages.md)</span></span>
