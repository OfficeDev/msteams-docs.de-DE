---
title: Senden proaktiver Nachrichten
author: clearab
description: Wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-bot senden.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2821e4d7ddeb74b3921be792cc55a136ab4ac5e4
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228080"
---
# <a name="send-proactive-messages"></a><span data-ttu-id="e387f-103">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="e387f-103">Send proactive messages</span></span>

> [!Note]
> <span data-ttu-id="e387f-104">In den Codebeispielen in diesem Artikel werden das V3 bot Framework SDK und V3 Teams bot Builder SDK-Erweiterungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="e387f-104">The code samples in this article make use of the v3 Bot Framework SDK, and v3 Teams Bot Builder SDK extensions.</span></span> <span data-ttu-id="e387f-105">Konzeptionell gelten die Informationen bei der Verwendung der V4-Versionen des SDK, aber der Code unterscheidet sich geringfügig.</span><span class="sxs-lookup"><span data-stu-id="e387f-105">Conceptually, the information applies when using the v4 versions of the SDK, but the code is slightly different.</span></span>

<span data-ttu-id="e387f-106">Eine proaktive Nachricht ist eine Nachricht, die von einem bot gesendet wird, um eine Unterhaltung zu starten.</span><span class="sxs-lookup"><span data-stu-id="e387f-106">A proactive message is a message that is sent by a bot to start a conversation.</span></span> <span data-ttu-id="e387f-107">Möglicherweise möchten Sie, dass Ihr bot eine Unterhaltung aus einer Reihe von Gründen startet, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="e387f-107">You may want your bot to start a conversation for a number of reasons, including:</span></span>

* <span data-ttu-id="e387f-108">Begrüßungsnachrichten für persönliche bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="e387f-108">Welcome messages for personal bot conversations</span></span>
* <span data-ttu-id="e387f-109">Umfrage Antworten</span><span class="sxs-lookup"><span data-stu-id="e387f-109">Poll responses</span></span>
* <span data-ttu-id="e387f-110">Externe Ereignisbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="e387f-110">External event notifications</span></span>

<span data-ttu-id="e387f-111">Das Senden einer Nachricht zum Starten eines neuen Unterhaltungs Threads unterscheidet sich vom Senden einer Nachricht als Reaktion auf eine vorhandene Unterhaltung: Wenn Ihr bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, an die die Nachricht gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e387f-111">Sending a message to start a new conversation thread is different than sending a message in response to an existing conversation: when your bot starts a new a conversation, there is no pre-existing conversation to post the message to.</span></span> <span data-ttu-id="e387f-112">Um eine proaktive Nachricht zu senden, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="e387f-112">In order to send a proactive message you need to:</span></span>

1. [<span data-ttu-id="e387f-113">Entscheiden, was Sie sagen werden</span><span class="sxs-lookup"><span data-stu-id="e387f-113">Decide what you're going to say</span></span>](#best-practices-for-proactive-messaging)
1. [<span data-ttu-id="e387f-114">Abrufen der eindeutigen ID des Benutzers und der Mandanten-ID</span><span class="sxs-lookup"><span data-stu-id="e387f-114">Obtain the user's unique Id and tenant Id</span></span>](#obtain-necessary-user-information)
1. [<span data-ttu-id="e387f-115">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="e387f-115">Send the message</span></span>](#examples)

<span data-ttu-id="e387f-116">Wenn Sie proaktive nach \*\*\*\* richten erstellen `MicrosoftAppCredentials.TrustServiceUrl`, müssen Sie die Dienst-URL aufrufen und weiter `ConnectorClient` geben, bevor Sie die Nachricht senden, die Sie verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="e387f-116">When creating proactive messages you **must** call `MicrosoftAppCredentials.TrustServiceUrl`, and pass in the service URL before creating the `ConnectorClient` you will use to send the message.</span></span> <span data-ttu-id="e387f-117">Wenn dies nicht der Fall ist, erhält Ihre APP `401: Unauthorized` eine Antwort.</span><span class="sxs-lookup"><span data-stu-id="e387f-117">If you do not, your app will receive a `401: Unauthorized` response.</span></span> 

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="e387f-118">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="e387f-118">Best practices for proactive messaging</span></span>

<span data-ttu-id="e387f-119">Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit zur Kommunikation mit ihren Benutzern sein.</span><span class="sxs-lookup"><span data-stu-id="e387f-119">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="e387f-120">Aus ihrer Perspektive kann diese Nachricht jedoch scheinbar völlig unaufgefordert angezeigt werden, und im Fall von Begrüßungsnachrichten ist das erste Mal, dass Sie mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="e387f-120">However, from their perspective this message can appear to come to them completely unprompted, and in the case of welcome messages will be the first time they've interacted with your app.</span></span> <span data-ttu-id="e387f-121">Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden (keine Spam-e-Mail-Benutzer) und Ihnen genügend Informationen zur Verfügung zu stellen, damit Sie verstehen, warum Sie Nachrichten erhalten.</span><span class="sxs-lookup"><span data-stu-id="e387f-121">As such, it is very important to use this functionality sparingly (don't spam your users), and to provide them with enough information to let them understand why they are being messaged.</span></span>

<span data-ttu-id="e387f-122">Proaktive Nachrichten fallen im Allgemeinen in eine von zwei Kategorien, Begrüßungsnachrichten oder Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e387f-122">Proactive messages generally fall into one of two categories, welcome messages or notifications.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="e387f-123">Begrüßungsnachrichten</span><span class="sxs-lookup"><span data-stu-id="e387f-123">Welcome messages</span></span>

<span data-ttu-id="e387f-124">Bei der Verwendung von proaktivem Messaging zum Senden einer Willkommensnachricht an einen Benutzer müssen Sie Bedenken, dass für die meisten Personen, die die Nachricht erhalten, kein Kontext dafür vorhanden ist, warum Sie Sie empfangen.</span><span class="sxs-lookup"><span data-stu-id="e387f-124">When using proactive messaging to send a welcome message to a user you must keep in mind that for most people receiving the message they will have no context for why they are receiving it.</span></span> <span data-ttu-id="e387f-125">Dies ist auch das erste Mal, dass Sie mit Ihrer APP interagieren; Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e387f-125">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="e387f-126">Die besten Begrüßungsnachrichten umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e387f-126">The best welcome messages will include:</span></span>

* <span data-ttu-id="e387f-127">**Warum erhalten Sie diese Nachricht.**</span><span class="sxs-lookup"><span data-stu-id="e387f-127">**Why are they receiving this message.**</span></span> <span data-ttu-id="e387f-128">Dem Benutzer sollte sehr deutlich sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="e387f-128">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="e387f-129">Wenn Ihr bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, sollten Sie wissen, in welchem Kanal Sie installiert wurde und wer Sie möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="e387f-129">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="e387f-130">**Was bieten Sie an?**</span><span class="sxs-lookup"><span data-stu-id="e387f-130">**What do you offer.**</span></span> <span data-ttu-id="e387f-131">Was können Sie mit Ihrer APP tun?</span><span class="sxs-lookup"><span data-stu-id="e387f-131">What can they do with your app?</span></span> <span data-ttu-id="e387f-132">Welchen Wert können Sie Ihnen bringen?</span><span class="sxs-lookup"><span data-stu-id="e387f-132">What value can you bring to them?</span></span>
* <span data-ttu-id="e387f-133">**Was sollten Sie als nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="e387f-133">**What should they do next.**</span></span> <span data-ttu-id="e387f-134">Laden Sie Sie ein, einen Befehl auszuprobieren oder mit ihrer app in irgendeiner Weise zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="e387f-134">Invite them to try out a command, or interact with your app in some way.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="e387f-135">Benachrichtigungsmeldungen</span><span class="sxs-lookup"><span data-stu-id="e387f-135">Notification messages</span></span>

<span data-ttu-id="e387f-136">Bei der Verwendung von proaktivem Messaging zum Senden von Benachrichtigungen müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um häufige Aktionen basierend auf Ihrer Benachrichtigung durchzuführen, und ein klares Verständnis dafür, warum die Benachrichtigung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="e387f-136">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification, and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="e387f-137">Gute Benachrichtigungsnachrichten umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="e387f-137">Good notification messages will generally include:</span></span>

* <span data-ttu-id="e387f-138">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="e387f-138">**What happened.**</span></span> <span data-ttu-id="e387f-139">Ein klarer Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="e387f-139">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="e387f-140">**Was passiert ist.**</span><span class="sxs-lookup"><span data-stu-id="e387f-140">**What it happened to.**</span></span> <span data-ttu-id="e387f-141">Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="e387f-141">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="e387f-142">**Wer hat es getan?**</span><span class="sxs-lookup"><span data-stu-id="e387f-142">**Who did it.**</span></span> <span data-ttu-id="e387f-143">Wer hat die Aktion durchgeführt, die die Benachrichtigung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="e387f-143">Who took the action that caused the notification to be sent.</span></span>
* <span data-ttu-id="e387f-144">**Was Sie dagegen tun können.**</span><span class="sxs-lookup"><span data-stu-id="e387f-144">**What they can do about it.**</span></span> <span data-ttu-id="e387f-145">Erleichtern Sie Ihren Benutzern das Ausführen von Aktionen basierend auf Ihren Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="e387f-145">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="e387f-146">**Wie Sie sich abmelden können.** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="e387f-146">**How they can opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="obtain-necessary-user-information"></a><span data-ttu-id="e387f-147">Abrufen der erforderlichen Benutzerinformationen</span><span class="sxs-lookup"><span data-stu-id="e387f-147">Obtain necessary user information</span></span>

<span data-ttu-id="e387f-148">Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams-Benutzer erstellen, indem Sie die *eindeutige ID* und die *Mandanten-ID* des Benutzers abrufen.</span><span class="sxs-lookup"><span data-stu-id="e387f-148">Bots can create new conversations with an individual Microsoft Teams user by obtaining the user’s *unique ID* and *tenant ID.*</span></span> <span data-ttu-id="e387f-149">Sie können diese Werte mit einer der folgenden Methoden abrufen:</span><span class="sxs-lookup"><span data-stu-id="e387f-149">You can obtain these values using one of the following methods:</span></span>

* <span data-ttu-id="e387f-150">Indem Sie [die Team Liste](../get-teams-context.md#fetching-the-roster-or-user-profile) von einem Kanal abrufen, in dem Ihre APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="e387f-150">By [fetching the team roster](../get-teams-context.md#fetching-the-roster-or-user-profile) from a channel your app is installed in.</span></span>
* <span data-ttu-id="e387f-151">Durch Zwischenspeicherung, wenn ein Benutzer [mit Ihrem bot in einem Kanal interagiert](./channel-and-group-conversations.md).</span><span class="sxs-lookup"><span data-stu-id="e387f-151">By caching them when a user [interacts with your bot in a channel](./channel-and-group-conversations.md).</span></span>
* <span data-ttu-id="e387f-152">Wenn ein Benutzer [in einer Kanal Unterhaltung @mentioned](./channel-and-group-conversations.md#retrieving-mentions) wird, ist der bot ein Teil von.</span><span class="sxs-lookup"><span data-stu-id="e387f-152">When a users is [@mentioned in a channel conversation](./channel-and-group-conversations.md#retrieving-mentions) the bot is a part of.</span></span>
* <span data-ttu-id="e387f-153">Durch Zwischenspeicherung, wenn Sie [das `conversationUpdate` Ereignis empfangen](./subscribe-to-conversation-events.md#team-members-added) , wenn Ihre APP im persönlichen Bereich installiert ist, oder neue Mitglieder zu einem Kanal oder Gruppenchat hinzugefügt werden, der</span><span class="sxs-lookup"><span data-stu-id="e387f-153">By caching them when you [receive the `conversationUpdate`](./subscribe-to-conversation-events.md#team-members-added) event when your app is installed in a personal scope, or new members are added to a channel or group chat that</span></span>

### <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="e387f-154">Proaktive Installation Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="e387f-154">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="e387f-155">Die proaktive Installation von apps mithilfe von Graph befindet sich derzeit in der Betaphase.</span><span class="sxs-lookup"><span data-stu-id="e387f-155">Proactively installing apps using graph is currently in beta.</span></span>

<span data-ttu-id="e387f-156">Gelegentlich kann es erforderlich sein, Benutzer proaktiv Nachrichten zu verständigen, die zuvor noch nicht mit Ihrer APP installiert oder mit ihr interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="e387f-156">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="e387f-157">Beispielsweise möchten Sie das [Unternehmens Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an die gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="e387f-157">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="e387f-158">In diesem Szenario können Sie die Graph-API verwenden, um Ihre APP proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus `conversationUpdate` dem Ereignis Zwischenspeichern, das Ihre APP bei der Installation empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="e387f-158">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="e387f-159">Sie können nur apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Microsoft Teams-App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="e387f-159">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="e387f-160">Ausführliche Informationen finden Sie unter [Installieren von Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e387f-160">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation for complete details.</span></span> <span data-ttu-id="e387f-161">Es gibt auch ein [Beispiel in .net](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span><span class="sxs-lookup"><span data-stu-id="e387f-161">There is also a [sample in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span></span>

## <a name="examples"></a><span data-ttu-id="e387f-162">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e387f-162">Examples</span></span>

<span data-ttu-id="e387f-163">Stellen Sie sicher, dass Sie sich authentifizieren und über ein Bearer-Token verfügen, bevor Sie eine neue Unterhaltung mit der Rest-API erstellen.</span><span class="sxs-lookup"><span data-stu-id="e387f-163">Be sure that you authenticate and have a bearer token before creating a new conversation using the REST API.</span></span> <span data-ttu-id="e387f-164">Das `members.id` Feld im folgenden Objekt ist für die Kombination aus Ihrem bot und einem Benutzer eindeutig.</span><span class="sxs-lookup"><span data-stu-id="e387f-164">The `members.id` field in the object below is unique to the combination of your bot and a user.</span></span> <span data-ttu-id="e387f-165">Sie können es nicht über eine andere Methode als die oben beschriebenen erhalten.</span><span class="sxs-lookup"><span data-stu-id="e387f-165">You cannot obtain it via any other method than those outlined above.</span></span>

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

<span data-ttu-id="e387f-166">Sie müssen die Benutzer-ID und die Mandanten-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="e387f-166">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="e387f-167">Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Response-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="e387f-167">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

<span data-ttu-id="e387f-168">Diese ID ist die eindeutige Unterhaltungs-ID des persönlichen Chats.</span><span class="sxs-lookup"><span data-stu-id="e387f-168">This ID is the personal chat's unique conversation ID.</span></span> <span data-ttu-id="e387f-169">Speichern Sie diesen Wert, und verwenden Sie ihn für zukünftige Interaktionen mit dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="e387f-169">Please store this value and reuse it for future interactions with the user.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e387f-170">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="e387f-170">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="e387f-171">In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.</span><span class="sxs-lookup"><span data-stu-id="e387f-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="e387f-172">JavaScript</span><span class="sxs-lookup"><span data-stu-id="e387f-172">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="e387f-173">*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="e387f-173">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>

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

# <a name="python"></a>[<span data-ttu-id="e387f-174">Python</span><span class="sxs-lookup"><span data-stu-id="e387f-174">Python</span></span>](#tab/python)

```python
async def _send_proactive_message():
  for conversation_reference in CONVERSATION_REFERENCES.values():
    return await ADAPTER.continue_conversation(APP_ID, conversation_reference,
      lambda turn_context: turn_context.send_activity("proactive hello")
    )

```

---

## <a name="creating-a-channel-conversation"></a><span data-ttu-id="e387f-175">Erstellen einer Kanal Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="e387f-175">Creating a channel conversation</span></span>

<span data-ttu-id="e387f-176">Ihr von einem Team hinzugefügter bot kann in einem Kanal Posten, um eine neue Antwort Kette zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e387f-176">Your team-added bot can post into a channel to create a new reply chain.</span></span> <span data-ttu-id="e387f-177">Wenn Sie das Node. js Teams-SDK verwenden, verwenden `startReplyChain()` Sie das, das Ihnen eine vollständig aufgefüllte Adresse mit der korrekten Aktivitäts-ID und der entsprechenden Unterhaltungs-ID zur Verfügung stellt. Wenn Sie C# verwenden, lesen Sie das Beispiel unten.</span><span class="sxs-lookup"><span data-stu-id="e387f-177">If you're using the Node.js Teams SDK, use `startReplyChain()` which gives you a fully-populated address with the correct activity id and conversation id. If you are using C#, see the example below.</span></span>

<span data-ttu-id="e387f-178">Alternativ können Sie die Rest-API verwenden und eine Post-Anforderung an [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) die Ressource ausgeben.</span><span class="sxs-lookup"><span data-stu-id="e387f-178">Alternatively, you can use the REST API and issue a POST request to [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) resource.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e387f-179">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="e387f-179">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="e387f-180">Der folgende Codeausschnitt stammt aus [diesem Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs).</span><span class="sxs-lookup"><span data-stu-id="e387f-180">The following code snippet is from [this sample](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs).</span></span>

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

# <a name="javascript"></a>[<span data-ttu-id="e387f-181">JavaScript</span><span class="sxs-lookup"><span data-stu-id="e387f-181">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="e387f-182">Der folgende Codeausschnitt stammt aus [teamsConversationBot. js](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/57.teams-conversation-bot/bots/teamsConversationBot.js).</span><span class="sxs-lookup"><span data-stu-id="e387f-182">The following code snippet is from [teamsConversationBot.js](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/57.teams-conversation-bot/bots/teamsConversationBot.js).</span></span>

[!code-javascript[messageAllMembersAsync](~/../botbuilder-samples/samples/javascript_nodejs/57.teams-conversation-bot/bots/teamsConversationBot.js?range=115-134&highlight=13-15)]

# <a name="python"></a>[<span data-ttu-id="e387f-183">Python</span><span class="sxs-lookup"><span data-stu-id="e387f-183">Python</span></span>](#tab/python)

[!code-python[message-all-members](~/../botbuilder-samples/samples/python/57.teams-conversation-bot/bots/teams_conversation_bot.py?range=101-135)]

---
