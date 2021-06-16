---
title: Senden proaktiver Nachrichten
description: Beschreibt, wie proaktive Nachrichten mit Ihrem Microsoft Teams Bot gesendet werden.
ms.topic: conceptual
ms.author: anclear
localization_priority: Normal
Keywords: Nachricht senden Benutzer-ID Kanal-ID Unterhaltungs-ID abrufen
ms.openlocfilehash: d2e9900e6c7d1f5ea5edfabe6dacb2f18b429b3f
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949777"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="61120-104">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="61120-104">Send proactive messages</span></span>

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="61120-105">Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers erfolgt.</span><span class="sxs-lookup"><span data-stu-id="61120-105">A proactive message is any message sent by a bot that is not in response to a request from a user.</span></span> <span data-ttu-id="61120-106">Dies kann Nachrichten umfassen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="61120-106">This can include messages, such as:</span></span>

* <span data-ttu-id="61120-107">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="61120-107">Welcome messages</span></span>
* <span data-ttu-id="61120-108">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="61120-108">Notifications</span></span>
* <span data-ttu-id="61120-109">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="61120-109">Scheduled messages</span></span>

<span data-ttu-id="61120-110">Damit Ihr Bot eine proaktive Nachricht an einen Benutzer, einen Gruppenchat oder ein Team senden kann, muss er Zugriff haben, um die Nachricht zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-110">For your bot to send a proactive message to a user, group chat, or team, it must have access to send the message.</span></span> <span data-ttu-id="61120-111">Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden.</span><span class="sxs-lookup"><span data-stu-id="61120-111">For a group chat or team, the app that contains your bot must be first installed in that location.</span></span> <span data-ttu-id="61120-112">Sie können [Ihre App proaktiv mithilfe von Microsoft Graph](#proactively-install-your-app-using-graph) in einem Team installieren, falls erforderlich, oder eine [App-Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-112">You can [proactively install your app using Microsoft Graph](#proactively-install-your-app-using-graph) in a team, if required, or use an [app policy](/microsoftteams/teams-custom-app-policies-and-settings) to push apps out to teams and users in your tenant.</span></span> <span data-ttu-id="61120-113">Für Benutzer muss Ihre App entweder für den Benutzer installiert werden, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="61120-113">For users, your app either must be installed for the user or your user must be part of a team where your app is installed.</span></span>

<span data-ttu-id="61120-114">Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht.</span><span class="sxs-lookup"><span data-stu-id="61120-114">Sending a proactive message is different from sending a regular message.</span></span> <span data-ttu-id="61120-115">Es ist nicht aktiv `turnContext` für eine Antwort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="61120-115">There is no active `turnContext` to use for a reply.</span></span> <span data-ttu-id="61120-116">Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="61120-116">You must create the conversation before sending the message.</span></span> <span data-ttu-id="61120-117">Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="61120-117">For example, a new one-to-one chat or a new conversation thread in a channel.</span></span> <span data-ttu-id="61120-118">Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktiven Nachrichten erstellen.</span><span class="sxs-lookup"><span data-stu-id="61120-118">You cannot create a new group chat or a new channel in a team with proactive messaging.</span></span>

<span data-ttu-id="61120-119">**So senden Sie eine proaktive Nachricht**</span><span class="sxs-lookup"><span data-stu-id="61120-119">**To send a proactive message**</span></span>

1. <span data-ttu-id="61120-120">Rufen Sie bei Bedarf [die Benutzer-ID, Team-ID oder Kanal-ID](#get-the-user-id-team-id-or-channel-id)ab.</span><span class="sxs-lookup"><span data-stu-id="61120-120">[Get the user ID, team ID, or channel ID](#get-the-user-id-team-id-or-channel-id), if required.</span></span>
1. <span data-ttu-id="61120-121">[Erstellen Sie die Unterhaltung,](#create-the-conversation)falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="61120-121">[Create the conversation](#create-the-conversation), if required.</span></span>
1. <span data-ttu-id="61120-122">[Rufen Sie die Unterhaltungs-ID](#get-the-conversation-id)ab.</span><span class="sxs-lookup"><span data-stu-id="61120-122">[Get the conversation ID](#get-the-conversation-id).</span></span>
1. <span data-ttu-id="61120-123">[Senden Sie die Nachricht.](#send-the-message)</span><span class="sxs-lookup"><span data-stu-id="61120-123">[Send the message](#send-the-message).</span></span>

<span data-ttu-id="61120-124">Die Codeausschnitte im [Beispielabschnitt](#samples) dienen zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="61120-124">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="61120-125">Links zum Ausführen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie im [Codebeispiel.](#code-sample)</span><span class="sxs-lookup"><span data-stu-id="61120-125">For links to complete working samples for both one-to-one conversations and group or channels , see [code sample](#code-sample).</span></span>

<span data-ttu-id="61120-126">Informationen zur effektiven Verwendung proaktiver Nachrichten finden Sie in [den bewährten Methoden für proaktives Messaging.](#best-practices-for-proactive-messaging)</span><span class="sxs-lookup"><span data-stu-id="61120-126">For using proactive messages effectively, see [best practices for proactive messaging](#best-practices-for-proactive-messaging).</span></span> <span data-ttu-id="61120-127">Für bestimmte Szenarien müssen Sie [Ihre App proaktiv mit Graph installieren.](#proactively-install-your-app-using-graph)</span><span class="sxs-lookup"><span data-stu-id="61120-127">For certain scenarios, you must [proactively install your app using Graph](#proactively-install-your-app-using-graph).</span></span> <span data-ttu-id="61120-128">Die Codeausschnitte im [Beispielabschnitt](#samples) dienen zum Erstellen einer 1:1-Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="61120-128">The code snippets in the [samples](#samples) section are for creating a one-to-one conversation.</span></span> <span data-ttu-id="61120-129">Vollständige Arbeitsbeispiele für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie im [Codebeispiel.](#code-sample)</span><span class="sxs-lookup"><span data-stu-id="61120-129">For complete working samples for both one-to-one conversations and groups or channels, see [code sample](#code-sample).</span></span>

## <a name="get-the-user-id-team-id-or-channel-id"></a><span data-ttu-id="61120-130">Abrufen der Benutzer-ID, Team-ID oder Kanal-ID</span><span class="sxs-lookup"><span data-stu-id="61120-130">Get the user ID, team ID or channel ID</span></span>

<span data-ttu-id="61120-131">Zum Erstellen eines neuen Unterhaltungs- oder Unterhaltungsthreads in einem Kanal benötigen Sie die richtige ID.</span><span class="sxs-lookup"><span data-stu-id="61120-131">To create a new conversation or conversation thread in a channel, you must have the correct ID.</span></span> <span data-ttu-id="61120-132">Sie können diese ID mit einer der folgenden Optionen empfangen oder abrufen:</span><span class="sxs-lookup"><span data-stu-id="61120-132">You can receive or retrieve this ID using any of the following:</span></span>

* <span data-ttu-id="61120-133">Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="61120-133">When your app is installed in any particular context, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="61120-134">Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="61120-134">When a new user is added to a context where your app is installed, you receive an [`onMembersAdded` activity](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="61120-135">Sie können die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="61120-135">You can retrieve the [list of channels](~/bots/how-to/get-teams-context.md) in a team where your app is installed.</span></span>
* <span data-ttu-id="61120-136">Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="61120-136">You can retrieve the [list of members](~/bots/how-to/get-teams-context.md) of a team where your app is installed.</span></span>
* <span data-ttu-id="61120-137">Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="61120-137">Every activity your bot receives must contain the required information.</span></span>

<span data-ttu-id="61120-138">Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die `tenantId` und entweder die oder zum Erstellen einer neuen Unterhaltung `userId` `channelId` speichern.</span><span class="sxs-lookup"><span data-stu-id="61120-138">Regardless of how you get the information, you must store the `tenantId` and either the `userId` or `channelId` to create a new conversation.</span></span> <span data-ttu-id="61120-139">Sie können den auch `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="61120-139">You can also use the `teamId` to create a new conversation thread in the general or default channel of a team.</span></span>

<span data-ttu-id="61120-140">Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="61120-140">The `userId` is unique to your bot ID and a particular user.</span></span> <span data-ttu-id="61120-141">Sie können die zwischen Bots nicht `userId` wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="61120-141">You cannot reuse the `userId` between bots.</span></span> <span data-ttu-id="61120-142">Dies `channelId` ist global.</span><span class="sxs-lookup"><span data-stu-id="61120-142">The `channelId` is global.</span></span> <span data-ttu-id="61120-143">Ihr Bot muss jedoch im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.</span><span class="sxs-lookup"><span data-stu-id="61120-143">However, your bot must be installed in the team before you can send a proactive message to a channel.</span></span>

<span data-ttu-id="61120-144">Nachdem Sie die Benutzer- oder Kanalinformationen erhalten haben, müssen Sie die Unterhaltung erstellen.</span><span class="sxs-lookup"><span data-stu-id="61120-144">After you have the user or channel information, you must create the conversation.</span></span>

## <a name="create-the-conversation"></a><span data-ttu-id="61120-145">Erstellen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="61120-145">Create the conversation</span></span>

<span data-ttu-id="61120-146">Sie müssen die Unterhaltung erstellen, wenn sie nicht vorhanden ist oder Sie die `conversationId` .</span><span class="sxs-lookup"><span data-stu-id="61120-146">You must create the conversation if it does not exist or you do not know the `conversationId`.</span></span> <span data-ttu-id="61120-147">Sie müssen die Unterhaltung nur einmal erstellen und den Wert oder das `conversationId` `conversationReference` Objekt speichern.</span><span class="sxs-lookup"><span data-stu-id="61120-147">You must only create the conversation once and store the `conversationId` value or `conversationReference` object.</span></span>

<span data-ttu-id="61120-148">Nachdem die Unterhaltung erstellt wurde, müssen Sie die Unterhaltungs-ID abrufen.</span><span class="sxs-lookup"><span data-stu-id="61120-148">After the conversation is created, you must get the conversation ID.</span></span>

## <a name="get-the-conversation-id"></a><span data-ttu-id="61120-149">Abrufen der Unterhaltungs-ID</span><span class="sxs-lookup"><span data-stu-id="61120-149">Get the conversation ID</span></span>

<span data-ttu-id="61120-150">Verwenden Sie entweder das `conversationReference` Objekt oder senden Sie die `conversationId` `tenantId` Nachricht.</span><span class="sxs-lookup"><span data-stu-id="61120-150">Use either the `conversationReference` object or `conversationId` and `tenantId` to send the message.</span></span> <span data-ttu-id="61120-151">Sie können diese ID abrufen, indem Sie entweder die Unterhaltung erstellen oder sie aus jeder Aktivität speichern, die Aus diesem Kontext an Sie gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="61120-151">You can get this ID by either creating the conversation or storing it from any activity sent to you from that context.</span></span> <span data-ttu-id="61120-152">Store diese ID als Referenz.</span><span class="sxs-lookup"><span data-stu-id="61120-152">Store this ID for reference.</span></span>

<span data-ttu-id="61120-153">Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="61120-153">After you get the appropriate address information, you can send your message.</span></span>

## <a name="send-the-message"></a><span data-ttu-id="61120-154">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="61120-154">Send the message</span></span>

<span data-ttu-id="61120-155">Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="61120-155">Now that you have the right address information, you can send your message.</span></span> <span data-ttu-id="61120-156">Wenn Sie das SDK verwenden, verwenden Sie dazu die `continueConversation` Methode und den direkten `conversationId` `tenantId` API-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="61120-156">If you're using the SDK, you'll do so using the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call.</span></span> <span data-ttu-id="61120-157">Sie müssen die richtige Einstellung `conversationParameters` festlegen, um Ihre Nachricht erfolgreich zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-157">You must set the `conversationParameters` correctly to successfully send your message.</span></span> <span data-ttu-id="61120-158">Sehen Sie [sich](#samples) den Beispielabschnitt an, oder verwenden Sie eines der Im [Codebeispielabschnitt](#code-sample) aufgeführten Beispiele.</span><span class="sxs-lookup"><span data-stu-id="61120-158">See the [samples](#samples) section or use one of the samples listed in the [code sample](#code-sample) section.</span></span>

<span data-ttu-id="61120-159">Wenn Sie das SDK verwenden, müssen Sie die `continueConversation` Methode und den und einen direkten `conversationId` `tenantId` API-Aufruf verwenden, um die Nachricht zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-159">If you are using the SDK, you must use the `continueConversation` method, and the `conversationId` and `tenantId` to make a direct API call to send the message.</span></span> <span data-ttu-id="61120-160">Sie müssen die richtige Einstellung `conversationParameters` festlegen, um Ihre Nachricht erfolgreich zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-160">You must set the `conversationParameters` correctly to successfully send your message.</span></span>

<span data-ttu-id="61120-161">Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="61120-161">Now that you have sent the proactive message, you must follow these best practices while sending proactive messages for better information exchange between users and the bot.</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="61120-162">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="61120-162">Best practices for proactive messaging</span></span>

<span data-ttu-id="61120-163">Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="61120-163">Sending proactive messages to users is a very effective way to communicate with your users.</span></span> <span data-ttu-id="61120-164">Aus ihrer Sicht kann diese Nachricht jedoch völlig unaufgeladen erscheinen, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="61120-164">However, from their perspective, this message can appear completely unprompted, and in the case of welcome messages, it is the first time they have interacted with your app.</span></span> <span data-ttu-id="61120-165">Daher ist es sehr wichtig, proaktives Messaging sparsam zu verwenden, nicht Ihre Benutzer zu spammen, und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie die Nachrichten empfangen.</span><span class="sxs-lookup"><span data-stu-id="61120-165">Therefore, it is very important to use proactive messaging sparingly, not spam your users, and provide enough information to let users understand why they are receiving the messages.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="61120-166">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="61120-166">Welcome messages</span></span>

<span data-ttu-id="61120-167">Wenn proaktives Messaging verwendet wird, um eine Willkommensnachricht an einen Benutzer zu senden, gibt es keinen Kontext dafür, warum die Benutzer die Nachricht empfangen.</span><span class="sxs-lookup"><span data-stu-id="61120-167">When proactive messaging is used to send a welcome message to a user, there is no context for why the users receive the message.</span></span> <span data-ttu-id="61120-168">Dies ist auch das erste Mal, dass Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="61120-168">This is also the first time users interact with your app.</span></span> <span data-ttu-id="61120-169">Es ist eine Gelegenheit, einen guten ersten Eindruck zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="61120-169">It is an opportunity to create a good first impression.</span></span> <span data-ttu-id="61120-170">Die besten Willkommensnachrichten müssen Folgendes enthalten:</span><span class="sxs-lookup"><span data-stu-id="61120-170">The best welcome messages must include:</span></span>

* <span data-ttu-id="61120-171">Warum ein Benutzer die Nachricht empfängt: Dem Benutzer muss klar sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="61120-171">Why a user is receiving the message: It must be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="61120-172">Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihm mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.</span><span class="sxs-lookup"><span data-stu-id="61120-172">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and who installed it.</span></span>
* <span data-ttu-id="61120-173">Was bieten Sie an: Benutzer müssen in der Lage sein, zu erkennen, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bieten können.</span><span class="sxs-lookup"><span data-stu-id="61120-173">What do you offer: Users must be able to identify what they can do with your app and what value can you bring to them.</span></span>
* <span data-ttu-id="61120-174">Was sollten sie als Nächstes tun: Benutzer einladen, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="61120-174">What should they do next: Invite users to try out a command, or interact with your app.</span></span>

<span data-ttu-id="61120-175">Nachrichten mit schlechter Willkommensseite können dazu führen, dass Benutzer Ihren Bot blockieren.</span><span class="sxs-lookup"><span data-stu-id="61120-175">Poor welcome messages can lead to users blocking your bot.</span></span> <span data-ttu-id="61120-176">Schreiben Sie auf den Punkt, und löschen Sie Willkommensnachrichten.</span><span class="sxs-lookup"><span data-stu-id="61120-176">Write to the point and clear welcome messages.</span></span> <span data-ttu-id="61120-177">Iterieren Sie die Willkommensnachrichten, wenn sie nicht den gewünschten Effekt haben.</span><span class="sxs-lookup"><span data-stu-id="61120-177">Iterate on the welcome messages if they are not having the desired effect.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="61120-178">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="61120-178">Notification messages</span></span>

<span data-ttu-id="61120-179">Um Benachrichtigungen mithilfe proaktiver Nachrichten zu senden, stellen Sie sicher, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="61120-179">To send notifications using proactive messaging, ensure your users have a clear path to take common actions based on your notification.</span></span> <span data-ttu-id="61120-180">Stellen Sie sicher, dass die Benutzer genau wissen, warum sie eine Benachrichtigung erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="61120-180">Ensure users have a clear understanding of why they have received a notification.</span></span> <span data-ttu-id="61120-181">Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="61120-181">Good notification messages generally include the following:</span></span>

* <span data-ttu-id="61120-182">Was passiert ist: Ein eindeutiger Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="61120-182">What happened: A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="61120-183">Was war das Ergebnis: Es muss klar sein, welches Element aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="61120-183">What was the result: It must be clear what item was updated to cause the notification.</span></span>
* <span data-ttu-id="61120-184">Wer oder was ausgelöst wurde: Wer oder welche Aktion ausgeführt wurde, durch die die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="61120-184">Who or what triggered it: Who or what took action that caused the notification to be sent.</span></span>
* <span data-ttu-id="61120-185">Was können Benutzer als Reaktion tun: Erleichtern Sie Es Ihren Benutzern, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="61120-185">What can users do in response: Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="61120-186">Wie können Benutzer sich abmelden: Sie müssen einen Pfad angeben, über den Benutzer zusätzliche Benachrichtigungen deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="61120-186">How can users opt-out: You must provide a path for users to opt-out of additional notifications.</span></span>

<span data-ttu-id="61120-187">Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mit Graph.</span><span class="sxs-lookup"><span data-stu-id="61120-187">To send messages to a large group of users, for example to your organization, proactively install your app using Graph.</span></span>

### <a name="scheduled-messages"></a><span data-ttu-id="61120-188">Geplante Nachrichten</span><span class="sxs-lookup"><span data-stu-id="61120-188">Scheduled messages</span></span>

<span data-ttu-id="61120-189">Wenn Sie proaktive Nachrichten verwenden, um geplante Nachrichten an Benutzer zu senden, überprüfen Sie, ob Ihre Zeitzone auf ihre Zeitzone aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="61120-189">When using proactive messaging to send scheduled messages to users, verify that your time zone is updated to their time zone.</span></span> <span data-ttu-id="61120-190">Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="61120-190">This ensures that the messages are delivered to the users at the relevant time.</span></span> <span data-ttu-id="61120-191">Zum Planen von Nachrichten gehören in der Regel:</span><span class="sxs-lookup"><span data-stu-id="61120-191">Schedule messages generally include:</span></span>

* <span data-ttu-id="61120-192">Warum erhält der Benutzer die Nachricht: Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, aus dem sie die Nachricht empfangen.</span><span class="sxs-lookup"><span data-stu-id="61120-192">Why is the user receiving the message: Make it easy for your users to understand the reason for which they are receiving the message.</span></span>
* <span data-ttu-id="61120-193">Was der Benutzer als Nächstes tun kann: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ausführen.</span><span class="sxs-lookup"><span data-stu-id="61120-193">What can user do next: Users can take the required action based on the message content.</span></span>

## <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="61120-194">Proaktives Installieren Ihrer App mit Graph</span><span class="sxs-lookup"><span data-stu-id="61120-194">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="61120-195">Die proaktive Installation von Apps mit Graph befindet sich derzeit in der Betaversion.</span><span class="sxs-lookup"><span data-stu-id="61120-195">Proactively installing apps using Graph is currently in beta.</span></span>

<span data-ttu-id="61120-196">Proaktive Meldung von Benutzern, die zuvor nicht installiert oder mit Ihrer App interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="61120-196">Proactively message users that have previously not installed or interacted with your app.</span></span> <span data-ttu-id="61120-197">Sie möchten z. B. den [Unternehmenskommunikator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="61120-197">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="61120-198">In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren.</span><span class="sxs-lookup"><span data-stu-id="61120-198">In this case, you can use the Graph API to proactively install your app for your users.</span></span> <span data-ttu-id="61120-199">Speichern Sie die erforderlichen Werte aus dem Ereignis zwischen, das `conversationUpdate` Ihre App bei der Installation empfängt.</span><span class="sxs-lookup"><span data-stu-id="61120-199">Cache the necessary values from the `conversationUpdate` event your app receives upon installation.</span></span>

<span data-ttu-id="61120-200">Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="61120-200">You can only install apps that are in your organizational app catalog or the Teams App Store.</span></span>

<span data-ttu-id="61120-201">Informationen zum [Installieren von Apps für Benutzer](/graph/api/userteamwork-post-installedapps) finden Sie in der Dokumentation zu Graph und [proaktiver Bot-Installation und Messaging in Teams mit Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md)</span><span class="sxs-lookup"><span data-stu-id="61120-201">See [install apps for users](/graph/api/userteamwork-post-installedapps) in the Graph documentation and [proactive bot installation and messaging in Teams with Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md).</span></span> <span data-ttu-id="61120-202">Es gibt auch ein [Microsoft .NET Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.</span><span class="sxs-lookup"><span data-stu-id="61120-202">There is also a [Microsoft .NET framework sample](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) on the GitHub platform.</span></span>

## <a name="samples"></a><span data-ttu-id="61120-203">Beispiele</span><span class="sxs-lookup"><span data-stu-id="61120-203">Samples</span></span>

<span data-ttu-id="61120-204">Der folgende Code zeigt ein einfaches Codebeispiel, das Ihre App proaktiv mit Graph installiert:</span><span class="sxs-lookup"><span data-stu-id="61120-204">The following code shows a simple code sample that proactively installs your app using Graph:</span></span>

# <a name="c"></a>[<span data-ttu-id="61120-205">C#</span><span class="sxs-lookup"><span data-stu-id="61120-205">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="61120-206">TypeScript</span><span class="sxs-lookup"><span data-stu-id="61120-206">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="61120-207">Python</span><span class="sxs-lookup"><span data-stu-id="61120-207">Python</span></span>](#tab/python)

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

# <a name="json"></a>[<span data-ttu-id="61120-208">Json</span><span class="sxs-lookup"><span data-stu-id="61120-208">JSON</span></span>](#tab/json)

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

<span data-ttu-id="61120-209">Sie müssen die Benutzer-ID und die Mandanten-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="61120-209">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="61120-210">Wenn der Aufruf erfolgreich ist, gibt die API das folgende Antwortobjekt zurück:</span><span class="sxs-lookup"><span data-stu-id="61120-210">If the call succeeds, the API returns the following response object:</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

> [!NOTE]
> <span data-ttu-id="61120-211">Derzeit können Bots keinen Gruppenchat über Bot-APIs oder Graph erstellen.</span><span class="sxs-lookup"><span data-stu-id="61120-211">Currently bots cannot create a group chat through bot APIs or Graph.</span></span> <span data-ttu-id="61120-212">`createConversation` ist nur für 1:1-Chats verfügbar.</span><span class="sxs-lookup"><span data-stu-id="61120-212">`createConversation` is available only for 1:1 chats.</span></span>

## <a name="code-sample"></a><span data-ttu-id="61120-213">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="61120-213">Code sample</span></span>

<span data-ttu-id="61120-214">Die folgende Tabelle enthält ein einfaches Codebeispiel, das den grundlegenden Unterhaltungsfluss in eine Teams Anwendung integriert und wie Sie einen neuen Unterhaltungsthread in einem Kanal in Teams erstellen:</span><span class="sxs-lookup"><span data-stu-id="61120-214">The following table provides a simple code sample that incorporate basic conversation flow into a Teams application and how to create a new conversation thread in a channel in Teams:</span></span>

| <span data-ttu-id="61120-215">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="61120-215">**Sample Name**</span></span> | <span data-ttu-id="61120-216">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="61120-216">**Description**</span></span> | <span data-ttu-id="61120-217">**.NET**</span><span class="sxs-lookup"><span data-stu-id="61120-217">**.NET**</span></span> | <span data-ttu-id="61120-218">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="61120-218">**Node.js**</span></span> | <span data-ttu-id="61120-219">**Python**</span><span class="sxs-lookup"><span data-stu-id="61120-219">**Python**</span></span> |
|---------------|--------------|--------|-------------|--------|
| <span data-ttu-id="61120-220">Teams Grundlagen zu Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="61120-220">Teams Conversation Basics</span></span>  | <span data-ttu-id="61120-221">Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="61120-221">Demonstrates basics of conversations in Teams, including sending one-to-one proactive messages.</span></span>| [<span data-ttu-id="61120-222">View</span><span class="sxs-lookup"><span data-stu-id="61120-222">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="61120-223">View</span><span class="sxs-lookup"><span data-stu-id="61120-223">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="61120-224">View</span><span class="sxs-lookup"><span data-stu-id="61120-224">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| <span data-ttu-id="61120-225">Starten eines neuen Threads in einem Kanal</span><span class="sxs-lookup"><span data-stu-id="61120-225">Start new thread in a channel</span></span> | <span data-ttu-id="61120-226">Veranschaulicht das Erstellen eines neuen Threads in einem Kanal.</span><span class="sxs-lookup"><span data-stu-id="61120-226">Demonstrates creating a new thread in a channel.</span></span> | [<span data-ttu-id="61120-227">View</span><span class="sxs-lookup"><span data-stu-id="61120-227">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="61120-228">View</span><span class="sxs-lookup"><span data-stu-id="61120-228">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [<span data-ttu-id="61120-229">View</span><span class="sxs-lookup"><span data-stu-id="61120-229">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

### <a name="additional-code-sample"></a><span data-ttu-id="61120-230">Zusätzliches Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="61120-230">Additional code sample</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="61120-231">Codebeispiele für proaktives Messaging Teams</span><span class="sxs-lookup"><span data-stu-id="61120-231">Teams proactive messaging code samples</span></span>](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a><span data-ttu-id="61120-232">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="61120-232">Next step</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="61120-233">Codebeispiele für [**proaktives Messaging Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp) 
>  [Formatieren Von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)</span><span class="sxs-lookup"><span data-stu-id="61120-233">[**Teams proactive messaging code samples**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
[Format your bot messages](~/bots/how-to/format-your-bot-messages.md)</span></span>
