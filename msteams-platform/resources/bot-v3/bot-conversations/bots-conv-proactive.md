---
title: Proaktive Nachrichten
description: Beschreibt, wie Bots eine Unterhaltung in Microsoft Teams starten können
keywords: Teams-Szenarien proaktiver Messaging-Unterhaltungs bot
ms.openlocfilehash: c5c779b7ec5733b19366ae73053ef7d45ca6c1d6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674133"
---
# <a name="proactive-messaging-for-bots"></a><span data-ttu-id="a5a43-104">Proaktives Messaging für Bots</span><span class="sxs-lookup"><span data-stu-id="a5a43-104">Proactive messaging for bots</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="a5a43-105">Eine proaktive Nachricht ist eine Nachricht, die von einem bot gesendet wird, um eine Unterhaltung zu starten.</span><span class="sxs-lookup"><span data-stu-id="a5a43-105">A proactive message is a message that is sent by a bot to start a conversation.</span></span> <span data-ttu-id="a5a43-106">Möglicherweise möchten Sie, dass Ihr bot eine Unterhaltung aus einer Reihe von Gründen startet, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="a5a43-106">You may want your bot to start a conversation for a number of reasons, including:</span></span>

* <span data-ttu-id="a5a43-107">Begrüßungsnachrichten für persönliche bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="a5a43-107">Welcome messages for personal bot conversations</span></span>
* <span data-ttu-id="a5a43-108">Umfrage Antworten</span><span class="sxs-lookup"><span data-stu-id="a5a43-108">Poll responses</span></span>
* <span data-ttu-id="a5a43-109">Externe Ereignisbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="a5a43-109">External event notifications</span></span>

<span data-ttu-id="a5a43-110">Das Senden einer Nachricht zum Starten eines neuen Unterhaltungs Threads unterscheidet sich vom Senden einer Nachricht als Reaktion auf eine vorhandene Unterhaltung: Wenn Ihr bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, an die die Nachricht gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a5a43-110">Sending a message to start a new conversation thread is different than sending a message in response to an existing conversation: when your bot starts a new a conversation, there is no pre-existing conversation to post the message to.</span></span> <span data-ttu-id="a5a43-111">Um eine proaktive Nachricht zu senden, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="a5a43-111">In order to send a proactive message you need to:</span></span>

1. [<span data-ttu-id="a5a43-112">Entscheiden, was Sie sagen werden</span><span class="sxs-lookup"><span data-stu-id="a5a43-112">Decide what you're going to say</span></span>](#best-practices-for-proactive-messaging)
1. [<span data-ttu-id="a5a43-113">Abrufen der eindeutigen ID des Benutzers und der Mandanten-ID</span><span class="sxs-lookup"><span data-stu-id="a5a43-113">Obtain the user's unique Id and tenant Id</span></span>](#obtain-necessary-user-information)
1. [<span data-ttu-id="a5a43-114">Senden der Nachricht</span><span class="sxs-lookup"><span data-stu-id="a5a43-114">Send the message</span></span>](#examples)

<span data-ttu-id="a5a43-115">Wenn Sie proaktive nach \*\*\*\* richten erstellen `MicrosoftAppCredentials.TrustServiceUrl`, müssen Sie die Dienst-URL aufrufen und weiter `ConnectorClient` geben, bevor Sie die Nachricht senden, die Sie verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="a5a43-115">When creating proactive messages you **must** call `MicrosoftAppCredentials.TrustServiceUrl`, and pass in the service URL before creating the `ConnectorClient` you will use to send the message.</span></span> <span data-ttu-id="a5a43-116">Wenn dies nicht der Fall ist, erhält Ihre APP `401: Unauthorized` eine Antwort.</span><span class="sxs-lookup"><span data-stu-id="a5a43-116">If you do not, your app will receive a `401: Unauthorized` response.</span></span> <span data-ttu-id="a5a43-117">Siehe [Beispiele unten](#net-example-from-this-sample).</span><span class="sxs-lookup"><span data-stu-id="a5a43-117">See [the samples below](#net-example-from-this-sample).</span></span>

## <a name="best-practices-for-proactive-messaging"></a><span data-ttu-id="a5a43-118">Bewährte Methoden für proaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="a5a43-118">Best practices for proactive messaging</span></span>

<span data-ttu-id="a5a43-119">Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit zur Kommunikation mit ihren Benutzern sein.</span><span class="sxs-lookup"><span data-stu-id="a5a43-119">Sending proactive messages to users can be a very effective way to communicate with your users.</span></span> <span data-ttu-id="a5a43-120">Aus ihrer Perspektive kann diese Nachricht jedoch scheinbar völlig unaufgefordert angezeigt werden, und im Fall von Begrüßungsnachrichten ist das erste Mal, dass Sie mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="a5a43-120">However, from their perspective this message can appear to come to them completely unprompted, and in the case of welcome messages will be the first time they've interacted with your app.</span></span> <span data-ttu-id="a5a43-121">Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden (keine Spam-e-Mail-Benutzer) und Ihnen genügend Informationen zur Verfügung zu stellen, damit Sie verstehen, warum Sie Nachrichten erhalten.</span><span class="sxs-lookup"><span data-stu-id="a5a43-121">As such, it is very important to use this functionality sparingly (don't spam your users), and to provide them with enough information to let them understand why they are being messaged.</span></span>

<span data-ttu-id="a5a43-122">Proaktive Nachrichten fallen im Allgemeinen in eine von zwei Kategorien, Begrüßungsnachrichten oder Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-122">Proactive messages generally fall into one of two categories, welcome messages or notifications.</span></span>

### <a name="welcome-messages"></a><span data-ttu-id="a5a43-123">Begrüßungsnachrichten</span><span class="sxs-lookup"><span data-stu-id="a5a43-123">Welcome messages</span></span>

<span data-ttu-id="a5a43-124">Bei der Verwendung von proaktivem Messaging zum Senden einer Willkommensnachricht an einen Benutzer müssen Sie Bedenken, dass für die meisten Personen, die die Nachricht erhalten, kein Kontext dafür vorhanden ist, warum Sie Sie empfangen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-124">When using proactive messaging to send a welcome message to a user you must keep in mind that for most people receiving the message they will have no context for why they are receiving it.</span></span> <span data-ttu-id="a5a43-125">Dies ist auch das erste Mal, dass Sie mit Ihrer APP interagieren; Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-125">This is also the first time they will have interacted with your app; it is your opportunity to create a good first impression.</span></span> <span data-ttu-id="a5a43-126">Die besten Begrüßungsnachrichten umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a5a43-126">The best welcome messages will include:</span></span>

* <span data-ttu-id="a5a43-127">**Warum erhalten Sie diese Nachricht.**</span><span class="sxs-lookup"><span data-stu-id="a5a43-127">**Why are they receiving this message.**</span></span> <span data-ttu-id="a5a43-128">Dem Benutzer sollte sehr deutlich sein, warum er die Nachricht empfängt.</span><span class="sxs-lookup"><span data-stu-id="a5a43-128">It should be very clear to the user why they are receiving the message.</span></span> <span data-ttu-id="a5a43-129">Wenn Ihr bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, sollten Sie wissen, in welchem Kanal Sie installiert wurde und wer Sie möglicherweise installiert hat.</span><span class="sxs-lookup"><span data-stu-id="a5a43-129">If your bot was installed in a channel and you sent a welcome message to all users, let them know what channel it was installed in and potentially who installed it.</span></span>
* <span data-ttu-id="a5a43-130">**Was bieten Sie an?**</span><span class="sxs-lookup"><span data-stu-id="a5a43-130">**What do you offer.**</span></span> <span data-ttu-id="a5a43-131">Was können Sie mit Ihrer APP tun?</span><span class="sxs-lookup"><span data-stu-id="a5a43-131">What can they do with your app?</span></span> <span data-ttu-id="a5a43-132">Welchen Wert können Sie Ihnen bringen?</span><span class="sxs-lookup"><span data-stu-id="a5a43-132">What value can you bring to them?</span></span>
* <span data-ttu-id="a5a43-133">**Was sollten Sie als nächstes tun?**</span><span class="sxs-lookup"><span data-stu-id="a5a43-133">**What should they do next.**</span></span> <span data-ttu-id="a5a43-134">Laden Sie Sie ein, einen Befehl auszuprobieren oder mit ihrer app in irgendeiner Weise zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="a5a43-134">Invite them to try out a command, or interact with your app in some way.</span></span>

### <a name="notification-messages"></a><span data-ttu-id="a5a43-135">Benachrichtigungsmeldungen</span><span class="sxs-lookup"><span data-stu-id="a5a43-135">Notification messages</span></span>

<span data-ttu-id="a5a43-136">Bei der Verwendung von proaktivem Messaging zum Senden von Benachrichtigungen müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um häufige Aktionen basierend auf Ihrer Benachrichtigung durchzuführen, und ein klares Verständnis dafür, warum die Benachrichtigung erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="a5a43-136">When using proactive messaging to send notifications you need to make sure your users have a clear path to take common actions based on your notification, and a clear understanding of why the notification occurred.</span></span> <span data-ttu-id="a5a43-137">Gute Benachrichtigungsnachrichten umfassen im Allgemeinen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a5a43-137">Good notification messages will generally include:</span></span>

* <span data-ttu-id="a5a43-138">**Was ist passiert.**</span><span class="sxs-lookup"><span data-stu-id="a5a43-138">**What happened.**</span></span> <span data-ttu-id="a5a43-139">Ein klarer Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-139">A clear indication of what happened to cause the notification.</span></span>
* <span data-ttu-id="a5a43-140">**Was passiert ist.**</span><span class="sxs-lookup"><span data-stu-id="a5a43-140">**What it happened to.**</span></span> <span data-ttu-id="a5a43-141">Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-141">It should be clear what item/thing was updated to cause the notification.</span></span>
* <span data-ttu-id="a5a43-142">**Wer hat es getan?**</span><span class="sxs-lookup"><span data-stu-id="a5a43-142">**Who did it.**</span></span> <span data-ttu-id="a5a43-143">Wer hat die Aktion durchgeführt, die die Benachrichtigung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="a5a43-143">Who took the action that caused the notification to be sent.</span></span>
* <span data-ttu-id="a5a43-144">**Was Sie dagegen tun können.**</span><span class="sxs-lookup"><span data-stu-id="a5a43-144">**What they can do about it.**</span></span> <span data-ttu-id="a5a43-145">Erleichtern Sie Ihren Benutzern das Ausführen von Aktionen basierend auf Ihren Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-145">Make it easy for your users to take actions based on your notifications.</span></span>
* <span data-ttu-id="a5a43-146">**Wie Sie sich abmelden können.** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="a5a43-146">**How they can opt out.** You need to provide a path for users to opt out of additional notifications.</span></span>

## <a name="obtain-necessary-user-information"></a><span data-ttu-id="a5a43-147">Abrufen der erforderlichen Benutzerinformationen</span><span class="sxs-lookup"><span data-stu-id="a5a43-147">Obtain necessary user information</span></span>

<span data-ttu-id="a5a43-148">Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams-Benutzer erstellen, indem Sie die *eindeutige ID* und die *Mandanten-ID* des Benutzers abrufen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-148">Bots can create new conversations with an individual Microsoft Teams user by obtaining the user’s *unique ID* and *tenant ID.*</span></span> <span data-ttu-id="a5a43-149">Sie können diese Werte mit einer der folgenden Methoden abrufen:</span><span class="sxs-lookup"><span data-stu-id="a5a43-149">You can obtain these values using one of the following methods:</span></span>

* <span data-ttu-id="a5a43-150">Indem Sie [die Team Liste](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) von einem Kanal abrufen, in dem Ihre APP installiert ist.</span><span class="sxs-lookup"><span data-stu-id="a5a43-150">By [fetching the team roster](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) from a channel your app is installed in.</span></span>
* <span data-ttu-id="a5a43-151">Durch Zwischenspeicherung, wenn ein Benutzer [mit Ihrem bot in einem Kanal interagiert](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).</span><span class="sxs-lookup"><span data-stu-id="a5a43-151">By caching them when a user [interacts with your bot in a channel](~/resources/bot-v3/bot-conversations/bots-conv-channel.md).</span></span>
* <span data-ttu-id="a5a43-152">Wenn ein Benutzer [in einer Kanal Unterhaltung @mentioned](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) wird, ist der bot ein Teil von.</span><span class="sxs-lookup"><span data-stu-id="a5a43-152">When a users is [@mentioned in a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) the bot is a part of.</span></span>
* <span data-ttu-id="a5a43-153">Durch Zwischenspeicherung, wenn Sie [das `conversationUpdate` Ereignis empfangen](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) , wenn Ihre APP im persönlichen Bereich installiert ist, oder neue Mitglieder zu einem Kanal oder Gruppenchat hinzugefügt werden, der</span><span class="sxs-lookup"><span data-stu-id="a5a43-153">By caching them when you [receive the `conversationUpdate`](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) event when your app is installed in a personal scope, or new members are added to a channel or group chat that</span></span>

### <a name="proactively-install-your-app-using-graph"></a><span data-ttu-id="a5a43-154">Proaktive Installation Ihrer App mithilfe von Graph</span><span class="sxs-lookup"><span data-stu-id="a5a43-154">Proactively install your app using Graph</span></span>

> [!Note]
> <span data-ttu-id="a5a43-155">Die proaktive Installation von apps mithilfe von Graph befindet sich derzeit in der Betaphase.</span><span class="sxs-lookup"><span data-stu-id="a5a43-155">Proactively installing apps using graph is currently in beta.</span></span>

<span data-ttu-id="a5a43-156">Gelegentlich kann es erforderlich sein, Benutzer proaktiv Nachrichten zu verständigen, die zuvor noch nicht mit Ihrer APP installiert oder mit ihr interagiert haben.</span><span class="sxs-lookup"><span data-stu-id="a5a43-156">Occasionally it may be necessary to proactively message users that have not installed or interacted with your app previously.</span></span> <span data-ttu-id="a5a43-157">Beispielsweise möchten Sie das [Unternehmens Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an die gesamte Organisation zu senden.</span><span class="sxs-lookup"><span data-stu-id="a5a43-157">For example, you want to use the [company communicator](~/samples/app-templates.md#company-communicator) to send messages to your entire organization.</span></span> <span data-ttu-id="a5a43-158">In diesem Szenario können Sie die Graph-API verwenden, um Ihre APP proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus `conversationUpdate` dem Ereignis Zwischenspeichern, das Ihre APP bei der Installation empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="a5a43-158">For this scenario you can use the Graph API to proactively install your app for your users, then cache the necessary values from the `conversationUpdate` event your app will receive upon install.</span></span>

<span data-ttu-id="a5a43-159">Sie können nur apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Microsoft Teams-App-Store befinden.</span><span class="sxs-lookup"><span data-stu-id="a5a43-159">You can only install apps that are in your organizational app catalogue, or the Teams app store.</span></span>

<span data-ttu-id="a5a43-160">Ausführliche Informationen finden Sie unter [Installieren von Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="a5a43-160">See [Install apps for users](/graph/teams-proactive-messaging) in the Graph documentation for complete details.</span></span> <span data-ttu-id="a5a43-161">Es gibt auch ein [Beispiel in .net](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span><span class="sxs-lookup"><span data-stu-id="a5a43-161">There is also a [sample in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).</span></span>

## <a name="examples"></a><span data-ttu-id="a5a43-162">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a5a43-162">Examples</span></span>

<span data-ttu-id="a5a43-163">Stellen Sie sicher, dass Sie sich authentifizieren und über ein Bearer-Token verfügen, bevor Sie eine neue Unterhaltung mit der Rest-API erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-163">Be sure that you authenticate and have a bearer token before creating a new conversation using the REST API.</span></span>

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

<span data-ttu-id="a5a43-164">Sie müssen die Benutzer-ID und die Mandanten-ID angeben.</span><span class="sxs-lookup"><span data-stu-id="a5a43-164">You must supply the user ID and the tenant ID.</span></span> <span data-ttu-id="a5a43-165">Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Response-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="a5a43-165">If the call succeeds, the API returns with the following response object.</span></span>

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

<span data-ttu-id="a5a43-166">Diese ID ist die eindeutige Unterhaltungs-ID des persönlichen Chats.</span><span class="sxs-lookup"><span data-stu-id="a5a43-166">This ID is the personal chat's unique conversation ID.</span></span> <span data-ttu-id="a5a43-167">Speichern Sie diesen Wert, und verwenden Sie ihn für zukünftige Interaktionen mit dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a5a43-167">Please store this value and reuse it for future interactions with the user.</span></span>

### <a name="using-net"></a><span data-ttu-id="a5a43-168">Verwenden von .net</span><span class="sxs-lookup"><span data-stu-id="a5a43-168">Using .NET</span></span>

<span data-ttu-id="a5a43-169">In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.</span><span class="sxs-lookup"><span data-stu-id="a5a43-169">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

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

### <a name="using-nodejs"></a><span data-ttu-id="a5a43-170">Verwenden von "Node. js"</span><span class="sxs-lookup"><span data-stu-id="a5a43-170">Using Node.js</span></span>

<span data-ttu-id="a5a43-171">In diesem Beispiel wird das NPM [-Paket botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) verwendet.</span><span class="sxs-lookup"><span data-stu-id="a5a43-171">This example uses the [botbuilder-teams](https://www.npmjs.com/package/botbuilder-teams) npm package.</span></span>

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

## <a name="creating-a-channel-conversation"></a><span data-ttu-id="a5a43-172">Erstellen einer Kanal Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="a5a43-172">Creating a channel conversation</span></span>

<span data-ttu-id="a5a43-173">Ihr von einem Team hinzugefügter bot kann in einem Kanal Posten, um eine neue Antwort Kette zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5a43-173">Your team-added bot can post into a channel to create a new reply chain.</span></span> <span data-ttu-id="a5a43-174">Wenn Sie das Node. js Teams-SDK verwenden, verwenden `startReplyChain()` Sie das, das Ihnen eine vollständig aufgefüllte Adresse mit der korrekten Aktivitäts-ID und der entsprechenden Unterhaltungs-ID zur Verfügung stellt. Wenn Sie C# verwenden, lesen Sie das Beispiel unten.</span><span class="sxs-lookup"><span data-stu-id="a5a43-174">If you're using the Node.js Teams SDK, use `startReplyChain()` which gives you a fully-populated address with the correct activity id and conversation id. If you are using C#, see the example below.</span></span>

<span data-ttu-id="a5a43-175">Alternativ können Sie die Rest-API verwenden und eine Post-Anforderung an [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) die Ressource ausgeben.</span><span class="sxs-lookup"><span data-stu-id="a5a43-175">Alternatively, you can use the REST API and issue a POST request to [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) resource.</span></span>

### <a name="net-example-from-this-samplehttpsgithubcomofficedevmicrosoft-teams-sample-complete-csharpblob32c39268d60078ef54f21fb3c6f42d122b97da22template-bot-master-csharpsrcdialogsexamplesteamsproactivemsgto1to1dialogcs"></a><span data-ttu-id="a5a43-176">.NET-Beispiel (in [diesem Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span><span class="sxs-lookup"><span data-stu-id="a5a43-176">.NET example (from [this sample](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))</span></span>

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
