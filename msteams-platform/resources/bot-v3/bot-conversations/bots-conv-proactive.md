---
title: Proaktive Nachrichten
description: Beschreibt, dass Bots eine Konversation in Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Teams Szenarien proaktive Messaging-Konversation Bot
ms.openlocfilehash: baf148d0f4d0a669de582dfca70ed5d5bed0274c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566789"
---
# <a name="proactive-messaging-for-bots"></a><span data-ttu-id="1a56a-104">Proaktives Messaging für Bots</span><span class="sxs-lookup"><span data-stu-id="1a56a-104">Proactive messaging for bots</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="1a56a-105">Eine proaktive Nachricht ist eine Nachricht, die von einem Bot gesendet wird, um eine Unterhaltung zu starten.</span><span class="sxs-lookup"><span data-stu-id="1a56a-105">A proactive message is a message that is sent by a bot to start a conversation.</span></span> <span data-ttu-id="1a56a-106">Vielleicht möchten Sie, dass Ihr Bot aus verschiedenen Gründen eine Unterhaltung beginnt, darunter:</span><span class="sxs-lookup"><span data-stu-id="1a56a-106">You may want your bot to start a conversation for a number of reasons, including:</span></span>

* <span data-ttu-id="1a56a-107">Willkommensbotschaften für persönliche Bot-Gespräche.</span><span class="sxs-lookup"><span data-stu-id="1a56a-107">Welcome messages for personal bot conversations.</span></span>
* <span data-ttu-id="1a56a-108">Umfrageantworten.</span><span class="sxs-lookup"><span data-stu-id="1a56a-108">Poll responses.</span></span>
* <span data-ttu-id="1a56a-109">Externe Ereignisbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-109">External event notifications.</span></span>

<span data-ttu-id="1a56a-110">Das Senden einer Nachricht zum Starten eines neuen Unterhaltungsthreads unterscheidet sich von dem Senden einer Nachricht als Antwort auf eine vorhandene Unterhaltung: Wenn Ihr Bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, an die die Nachricht gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1a56a-110">Sending a message to start a new conversation thread is different than sending a message in response to an existing conversation: when your bot starts a new a conversation, there is no pre-existing conversation to post the message to.</span></span> <span data-ttu-id="1a56a-111">Um eine proaktive Nachricht zu senden, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="1a56a-111">In order to send a proactive message you need to:</span></span>

1. [<span data-ttu-id="1a56a-112">Entscheiden Sie, was Sie sagen werden</span><span class="sxs-lookup"><span data-stu-id="1a56a-112">Decide what you're going to say</span></span>](#best-practices-for-proactive-messaging)
1. [<span data-ttu-id="1a56a-113">Abrufen der eindeutigen ID und Mandanten-ID des Benutzers</span><span class="sxs-lookup"><span data-stu-id="1a56a-113">Obtain the user's unique Id and tenant Id</span></span>](#obtain-necessary-user-information)
1. [<span data-ttu-id="1a56a-114">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="1a56a-114">Send the message</span></span>](#examples)

<span data-ttu-id="1a56a-115">Beim Erstellen proaktiver Nachrichten **müssen** Sie anrufen `MicrosoftAppCredentials.TrustServiceUrl` und die Dienst-URL übergeben, bevor Sie die `ConnectorClient` zum Senden der Nachricht verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a56a-115">When creating proactive messages you **must** call `MicrosoftAppCredentials.TrustServiceUrl`, and pass in the service URL before creating the `ConnectorClient` you will use to send the message.</span></span> <span data-ttu-id="1a56a-116">Andernfalls erhält Ihre App eine `401: Unauthorized` Antwort.</span><span class="sxs-lookup"><span data-stu-id="1a56a-116">If you do not, your app will receive a `401: Unauthorized` response.</span></span> <span data-ttu-id="1a56a-117">Weitere Informationen finden Sie [in den folgenden Beispielen](#net-example-from-this-sample).</span><span class="sxs-lookup"><span data-stu-id="1a56a-117">For more information, see [the samples below](#net-example-from-this-sample).</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="1a56a-118">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="1a56a-118">Best practices for proactive messaging</span></span>

<span data-ttu-id="1a56a-119">Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit sein, mit Ihren Benutzern zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="1a56a-119">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="1a56a-120">Aus ihrer Sicht kann diese Nachricht jedoch völlig unaufgefordert zu ihnen kommen, und im Falle von Begrüßungsnachrichten wird es das erste Mal sein, dass sie mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="1a56a-120">However, from their perspective this message can appear to come to them completely unprompted, and in the case of welcome messages will be the first time they've interacted with your app.</span></span> <span data-ttu-id="1a56a-121">Daher ist es sehr wichtig, diese Funktionalität sparsam zu nutzen (Spam für Ihre Benutzer) und ihnen genügend Informationen zur Verfügung zu stellen, damit sie verstehen können, warum sie informiert werden.</span><span class="sxs-lookup"><span data-stu-id="1a56a-121">As such, it is very important to use this functionality sparingly (don't spam your users), and to provide them with enough information to let them understand why they are being messaged.</span></span>

<span data-ttu-id="1a56a-122">Proaktive Nachrichten können generell in zwei Kategorien unterteilt werden: Willkommensnachrichten und Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-122">Proactive messages generally fall into one of two categories, welcome messages or notifications.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="1a56a-123">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="1a56a-123">Welcome messages</span></span>

<span data-ttu-id="1a56a-124">Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass sie für die meisten Personen, die die Nachricht erhalten, keinen Kontext haben, warum sie sie erhalten.</span><span class="sxs-lookup"><span data-stu-id="1a56a-124">When using proactive messaging to send a welcome message to a user you must keep in mind that for most people receiving the message they will have no context for why they are receiving it.</span></span> <span data-ttu-id="1a56a-125">Dies ist auch das erste Mal, dass sie mit Ihrer App interagiert haben. es ist Ihre Chance, einen guten ersten Eindruck zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-125">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="1a56a-126">Zu den besten Willkommensbotschaften gehören:</span><span class="sxs-lookup"><span data-stu-id="1a56a-126">The best welcome messages will include:</span></span>

* <span data-ttu-id="1a56a-127">**Warum erhalten sie diese Nachricht?**</span><span class="sxs-lookup"><span data-stu-id="1a56a-127">**Why are they receiving this message.**</span></span> <span data-ttu-id="1a56a-128">Es sollte dem Benutzer sehr klar sein, warum er die Nachricht erhält.</span><span class="sxs-lookup"><span data-stu-id="1a56a-128">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="1a56a-129">Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="1a56a-129">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="1a56a-130">**Was bieten Sie an?**</span><span class="sxs-lookup"><span data-stu-id="1a56a-130">**What do you offer.**</span></span> <span data-ttu-id="1a56a-131">Was können sie mit Ihrer App tun?</span><span class="sxs-lookup"><span data-stu-id="1a56a-131">What can they do with your app?</span></span> <span data-ttu-id="1a56a-132">Welchen Wert können Sie ihnen bringen?</span><span class="sxs-lookup"><span data-stu-id="1a56a-132">What value can you bring to them?</span></span>
* <span data-ttu-id="1a56a-133">**Was sollen sie als nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="1a56a-133">**What should they do next.**</span></span> <span data-ttu-id="1a56a-134">Bitten Sie sie, einen Befehl auszuprobieren oder in irgendeiner Weise mit Ihrer App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="1a56a-134">Invite them to try out a command, or interact with your app in some way.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="1a56a-135">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="1a56a-135">Notification messages</span></span>

<span data-ttu-id="1a56a-136">Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um basierend auf Ihrer Benachrichtigung allgemeine Aktionen zu ergreifen und ein klares Verständnis dafür zu haben, warum die Benachrichtigung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="1a56a-136">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification, and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="1a56a-137">Gute Benachrichtigungen umfassen in der Regel:</span><span class="sxs-lookup"><span data-stu-id="1a56a-137">Good notification messages will generally include:</span></span>

* <span data-ttu-id="1a56a-138">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="1a56a-138">**What happened.**</span></span> <span data-ttu-id="1a56a-139">Ein klarer Hinweis darauf, was die Meldung verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="1a56a-139">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="1a56a-140">**Was es passiert ist.**</span><span class="sxs-lookup"><span data-stu-id="1a56a-140">**What it happened to.**</span></span> <span data-ttu-id="1a56a-141">Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-141">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="1a56a-142">**Wer hat es getan.**</span><span class="sxs-lookup"><span data-stu-id="1a56a-142">**Who did it.**</span></span> <span data-ttu-id="1a56a-143">Wer die Aktion ergriffen, die dazu führte, dass die Benachrichtigung gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="1a56a-143">Who took the action that caused the notification to be sent.</span></span>
* <span data-ttu-id="1a56a-144">**Was sie dagegen tun können.**</span><span class="sxs-lookup"><span data-stu-id="1a56a-144">**What they can do about it.**</span></span> <span data-ttu-id="1a56a-145">Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-145">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="1a56a-146">**Wie sie sich abmelden können.** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="1a56a-146">**How they can opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="obtain-necessary-user-information"></a><span data-ttu-id="1a56a-147">Erforderliche Benutzerinformationen abrufen</span><span class="sxs-lookup"><span data-stu-id="1a56a-147">Obtain necessary user information</span></span>

<span data-ttu-id="1a56a-148">Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams Benutzer erstellen, indem sie die *eindeutige ID* und *Mandanten-ID* des Benutzers abrufen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-148">Bots can create new conversations with an individual Microsoft Teams user by obtaining the user's *unique ID* and *tenant ID.*</span></span> <span data-ttu-id="1a56a-149">Sie können diese Werte mit einer der folgenden Methoden abrufen:</span><span class="sxs-lookup"><span data-stu-id="1a56a-149">You can obtain these values using one of the following methods:</span></span>

* <span data-ttu-id="1a56a-150">Durch [Abrufen des Team-Rosters](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) von einem Kanal, in dem Ihre App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1a56a-150">By [fetching the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) from a channel your app is installed in.</span></span>
* <span data-ttu-id="1a56a-151">Indem sie zwischenspeichern, wenn ein Benutzer [mit Ihrem Bot in einem Kanal interagiert.](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)</span><span class="sxs-lookup"><span data-stu-id="1a56a-151">By caching them when a user [interacts with your bot in a channel](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).</span></span>
* <span data-ttu-id="1a56a-152">Wenn ein Benutzer [in einer Kanalunterhaltung @mentioned](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) wird, ist der Bot Ein Teil davon.</span><span class="sxs-lookup"><span data-stu-id="1a56a-152">When a users is [@mentioned in a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) the bot is a part of.</span></span>
* <span data-ttu-id="1a56a-153">Indem Sie sie [zwischenspeichern, `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) wenn Sie das Ereignis erhalten, wenn Ihre App in einem persönlichen Bereich installiert ist oder neue Mitglieder zu einem Kanal oder Gruppenchat hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1a56a-153">By caching them when you [receive the `conversationUpdate`](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) event when your app is installed in a personal scope, or new members are added to a channel or group chat that.</span></span>

### <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="1a56a-154">Proaktive Installation Ihrer App mithilfe Graph</span><span class="sxs-lookup"><span data-stu-id="1a56a-154">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="1a56a-155">Die proaktive Installation von Apps mit Graph befindet sich derzeit in der Betaversion.</span><span class="sxs-lookup"><span data-stu-id="1a56a-155">Proactively installing apps using graph is currently in beta.</span></span>

<span data-ttu-id="1a56a-156">Gelegentlich kann es erforderlich sein, Benutzer, die zuvor nicht installiert oder mit Ihrer App interagiert haben, proaktiv zu melden.</span><span class="sxs-lookup"><span data-stu-id="1a56a-156">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="1a56a-157">Sie möchten z. B. den [Unternehmenskommunikator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="1a56a-157">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="1a56a-158">In diesem Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das `conversationUpdate` Ihre App bei der Installation erhält.</span><span class="sxs-lookup"><span data-stu-id="1a56a-158">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="1a56a-159">Sie können nur Apps installieren, die sich in Ihrem Organisations-App-Katalog befinden, oder im Teams App Store.</span><span class="sxs-lookup"><span data-stu-id="1a56a-159">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="1a56a-160">Ausführliche Informationen finden Sie unter Installieren von [Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1a56a-160">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation for complete details.</span></span> <span data-ttu-id="1a56a-161">Es gibt auch ein [Beispiel in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span><span class="sxs-lookup"><span data-stu-id="1a56a-161">There is also a [sample in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span></span>

## <a name="examples"></a><span data-ttu-id="1a56a-162">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1a56a-162">Examples</span></span>

<span data-ttu-id="1a56a-163">Stellen Sie sicher, dass Sie sich authentifizieren und über ein Inhabertoken verfügen, bevor Sie eine neue Unterhaltung mithilfe der REST-API erstellen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-163">Be sure that you authenticate and have a bearer token before creating a new conversation using the REST API.</span></span>

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

<span data-ttu-id="1a56a-164">Sie müssen die Benutzer-ID und die Mandanten-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="1a56a-164">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="1a56a-165">Wenn der Aufruf erfolgreich ist, wird die API mit dem folgenden Antwortobjekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="1a56a-165">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

<span data-ttu-id="1a56a-166">Diese ID ist die eindeutige Konversations-ID des persönlichen Chats.</span><span class="sxs-lookup"><span data-stu-id="1a56a-166">This ID is the personal chat's unique conversation ID.</span></span> <span data-ttu-id="1a56a-167">Speichern Sie diesen Wert, und verwenden Sie ihn für zukünftige Interaktionen mit dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="1a56a-167">Please store this value and reuse it for future interactions with the user.</span></span>

### <a name="using-net"></a><span data-ttu-id="1a56a-168">Verwenden von .NET</span><span class="sxs-lookup"><span data-stu-id="1a56a-168">Using .NET</span></span>

<span data-ttu-id="1a56a-169">In diesem Beispiel wird das [NuGet-Paket Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a56a-169">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create or get existing chat conversation with user
var response = client.Conversations.CreateOrGetDirectConversation(activity.Recipient, activity.From, activity.GetTenantId());

// Construct the message to post to conversation
Activity newActivity = new Activity()
{
    Text = "Hello",
    Type = ActivityTypes.Message,
    Conversation = new ConversationAccount
    {
        Id = response.Id
    },
};

// Post the message to chat conversation with user
await client.Conversations.SendToConversationAsync(newActivity, response.Id);
```

### <a name="using-nodejs"></a><span data-ttu-id="1a56a-170">Verwenden Node.js</span><span class="sxs-lookup"><span data-stu-id="1a56a-170">Using Node.js</span></span>

```javascript
var address =
{
    channelId: 'msteams',
    user: { id: userId },
    channelData: {
        tenant: {
            id: tenantId
        }
    },
    bot:
    {
        id: appId,
        name: appName
    },
    serviceUrl: session.message.address.serviceUrl,
    useAuth: true
}

var msg = new builder.Message().address(address);
msg.text('Hello, this is a notification');
bot.send(msg);
```

## <a name="creating-a-channel-conversation"></a><span data-ttu-id="1a56a-171">Erstellen einer Kanalunterhaltung</span><span class="sxs-lookup"><span data-stu-id="1a56a-171">Creating a channel conversation</span></span>

<span data-ttu-id="1a56a-172">Der von Ihrem Team hinzugefügte Bot kann Beiträge in einen Kanal versenden, um eine neue Antwortkette zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-172">Your team-added bot can post into a channel to create a new reply chain.</span></span> <span data-ttu-id="1a56a-173">Wenn Sie das Node.js Teams SDK verwenden, verwenden Sie diese Verwendung, die `startReplyChain()` Ihnen eine voll ausgefüllte Adresse mit der richtigen Aktivitäts-ID und Konversations-ID gibt. Wenn Sie c- verwenden, lesen Sie das folgende Beispiel.</span><span class="sxs-lookup"><span data-stu-id="1a56a-173">If you're using the Node.js Teams SDK, use `startReplyChain()` which gives you a fully-populated address with the correct activity id and conversation id. If you are using C#, see the example below.</span></span>

<span data-ttu-id="1a56a-174">Alternativ können Sie die REST-API verwenden und eine POST-Anforderung an die [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) Ressource ausstellen.</span><span class="sxs-lookup"><span data-stu-id="1a56a-174">Alternatively, you can use the REST API and issue a POST request to [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) resource.</span></span>

### <a name="net-example-from-this-sample"></a><span data-ttu-id="1a56a-175">.NET-Beispiel (aus [diesem Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span><span class="sxs-lookup"><span data-stu-id="1a56a-175">.NET example (from [this sample](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span></span>

```csharp
using Microsoft.Bot.Builder.Dialogs;
using Microsoft.Bot.Connector;
using Microsoft.Bot.Connector.Teams.Models;
using Microsoft.Teams.TemplateBotCSharp.Properties;
using System;
using System.Threading.Tasks;

namespace Microsoft.Teams.TemplateBotCSharp.Dialogs
{
    [Serializable]
    public class ProactiveMsgTo1to1Dialog : IDialog<object>
    {
        public async Task StartAsync(IDialogContext context)
        {
            if (context == null)
            {
                throw new ArgumentNullException(nameof(context));
            }

            var channelData = context.Activity.GetChannelData<TeamsChannelData>();
            var message = Activity.CreateMessageActivity();
            message.Text = "Hello World";

            var conversationParameters = new ConversationParameters
            {
                  IsGroup = true,
                  ChannelData = new TeamsChannelData
                  {
                      Channel = new ChannelInfo(channelData.Channel.Id),
                  },
                  Activity = (Activity) message
            };

            MicrosoftAppCredentials.TrustServiceUrl(serviceUrl, DateTime.MaxValue);
            var connectorClient = new ConnectorClient(new Uri(activity.ServiceUrl));
            var response = await connectorClient.Conversations.CreateConversationAsync(conversationParameters);

            context.Done<object>(null);
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="1a56a-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1a56a-176">See also</span></span>

[<span data-ttu-id="1a56a-177">Bot Framework-Beispiele</span><span class="sxs-lookup"><span data-stu-id="1a56a-177">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)