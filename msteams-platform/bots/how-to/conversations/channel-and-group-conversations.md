---
title: Kanal- und Gruppenunterhaltungen mit einem Bot
author: clearab
description: Senden, Empfangen und Behandeln von Nachrichten für einen Bot in einem Kanal- oder Gruppenchat.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8a9a58208fff5cc2fe376fcb9932bad6ac2bf36f
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797841"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="e5cad-103">Kanal- und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="e5cad-103">Channel and group chat conversations with a Microsoft Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="e5cad-104">Durch Hinzufügen des Bereichs oder des Bereichs zu Ihrem Bot kann er in einem Team- oder `teams` `groupchat` Gruppenchat installiert werden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-104">By adding the `teams` or `groupchat` scope to your bot, it can be available to be installed in a team or group chat.</span></span> <span data-ttu-id="e5cad-105">Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren.</span><span class="sxs-lookup"><span data-stu-id="e5cad-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="e5cad-106">Sobald er installiert ist, hat er auch Zugriff auf Metadaten zu der Unterhaltung wie der Liste der Unterhaltungsmitglieder, und wenn er in einem Team installiert wurde, auf Details zu diesem Team sowie die vollständige Liste der Kanäle.</span><span class="sxs-lookup"><span data-stu-id="e5cad-106">Once installed, it will also have access to metadata about the conversation like the list of conversation members, and when installed in a team details about that team and the full list of channels.</span></span>

<span data-ttu-id="e5cad-107">Bots in einer Gruppe oder einem Kanal empfangen nachrichten nur, wenn sie erwähnt werden (@botname), sie empfangen keine anderen Nachrichten, die an die Unterhaltung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-107">Bots in a group or channel only receive messages when they are mentioned (@botname), they do not receive any other messages sent to the conversation.</span></span>

> [!NOTE]
> <span data-ttu-id="e5cad-108">Der Bot muss direkt @erwähnt werden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-108">The bot must be @mentioned directly.</span></span> <span data-ttu-id="e5cad-109">Ihr Bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem Bot antwortet, ohne @mentioning senden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-109">Your bot will not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="e5cad-110">Richtlinien für den Entwurf</span><span class="sxs-lookup"><span data-stu-id="e5cad-110">Design guidelines</span></span>

<span data-ttu-id="e5cad-111">Erfahren Sie, wie [Sie Botunterhaltungen in Kanälen und Chats entwerfen.](~/bots/design/bots.md)</span><span class="sxs-lookup"><span data-stu-id="e5cad-111">See how to [design bot conversations in channels and chats](~/bots/design/bots.md).</span></span>

## <a name="creating-new-conversation-threads"></a><span data-ttu-id="e5cad-112">Erstellen neuer Unterhaltungsthreads</span><span class="sxs-lookup"><span data-stu-id="e5cad-112">Creating new conversation threads</span></span>

<span data-ttu-id="e5cad-113">Wenn Ihr Bot in einem Team installiert ist, kann es manchmal erforderlich sein, einen neuen Unterhaltungsthread zu erstellen, anstatt auf einen vorhandenen zu antworten.</span><span class="sxs-lookup"><span data-stu-id="e5cad-113">When your bot is installed in a team, it can sometimes be necessary to create a new conversation thread rather than replying to an existing one.</span></span> <span data-ttu-id="e5cad-114">Dies ist eine Form von [proaktivem Messaging.](~/bots/how-to/conversations/send-proactive-messages.md)</span><span class="sxs-lookup"><span data-stu-id="e5cad-114">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

## <a name="working-with-mentions"></a><span data-ttu-id="e5cad-115">Arbeiten mit Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="e5cad-115">Working with mentions</span></span>

<span data-ttu-id="e5cad-116">Jede Nachricht von einer Gruppe oder einem Kanal an Ihren Bot enthält eine „@Erwähnung“ mit seinem eigenen Namen im Nachrichtentext, weshalb Sie sicherstellen müssen, dass Ihre Nachrichtenanalyse dies verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="e5cad-116">Every message to your bot from a group or channel will contain an @mention with its own name in the message text, so you'll need to ensure your message parsing handles that.</span></span> <span data-ttu-id="e5cad-117">Der Bot kann auch andere in einer Nachricht erwähnte Benutzer abrufen und jeder von ihm gesendeten Nachricht Erwähnungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e5cad-117">Your bot can also retrieve other users mentioned in a message, and add mentions to any messages it sends.</span></span>

### <a name="stripping-mentions-from-message-text"></a><span data-ttu-id="e5cad-118">Beschneiden von Erwähnungen aus dem Nachrichtentext</span><span class="sxs-lookup"><span data-stu-id="e5cad-118">Stripping mentions from message text</span></span>

<span data-ttu-id="e5cad-119">Möglicherweise halten Sie es für notwendig, die @Erwähnungen aus dem Text der Nachricht zu entfernen, die ihr Bot empfängt.</span><span class="sxs-lookup"><span data-stu-id="e5cad-119">You may find it necessary to strip out the @mentions from the text of the message your bot receives.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="e5cad-120">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="e5cad-120">Retrieving mentions</span></span>

<span data-ttu-id="e5cad-121">Erwähnungen werden in der Nutzlast des Objekts zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen `entities` des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="e5cad-121">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="e5cad-122">Der Text der Nachricht enthält außerdem die Erwähnung ähnlich wie `<at>@John Smith<at>`.</span><span class="sxs-lookup"><span data-stu-id="e5cad-122">The text of the message will also include the mention like `<at>@John Smith<at>`.</span></span> <span data-ttu-id="e5cad-123">Sie sollten sich jedoch nicht auf den Text in der Nachricht verlassen, um Informationen über den Benutzer abzurufen. Die Person, die die Nachricht sendet, kann sie ändern.</span><span class="sxs-lookup"><span data-stu-id="e5cad-123">However, you should not rely on the text in the message to retrieve any information about the user; it is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="e5cad-124">Verwenden Sie stattdessen das `entities` Objekt.</span><span class="sxs-lookup"><span data-stu-id="e5cad-124">Instead, use the `entities` object.</span></span>

<span data-ttu-id="e5cad-125">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion im Bot Builder SDK aufrufen, die `GetMentions` ein Array von Objekten `Mention` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="e5cad-125">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK which returns an array of `Mention` objects.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e5cad-126">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e5cad-126">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    Mention[] mentions = turnContext.Activity.GetMentions();
    if(mentions != null)
    {
        ChannelAccount firstMention = mentions[0].Mentioned;
        await turnContext.SendActivityAsync($"Hello {firstMention.Name}");
    }
    else
    {
        await turnContext.SendActivityAsync("Aw, no one was mentioned.");
    }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="e5cad-127">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e5cad-127">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mentions = TurnContext.getMentions(turnContext.activity);
    if (mentions){
        const firstMention = mentions[0].mentioned;
        await turnContext.sendActivity(`Hello ${firstMention.name}.`);
    } else {
        await turnContext.sendActivity(`Aw, no one was mentioned.`);
    }

    await next();
});
```

# <a name="json"></a>[<span data-ttu-id="e5cad-128">Json</span><span class="sxs-lookup"><span data-stu-id="e5cad-128">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

# <a name="python"></a>[<span data-ttu-id="e5cad-129">Python</span><span class="sxs-lookup"><span data-stu-id="e5cad-129">Python</span></span>](#tab/python)

```python
@staticmethod
def get_mentions(activity: Activity) -> List[Mention]:
    result: List[Mention] = []
    if activity.entities is not None:
        for entity in activity.entities:
            if entity.type.lower() == "mention":
                    result.append(entity)
     return result
```

* * *

### <a name="adding-mentions-to-your-messages"></a><span data-ttu-id="e5cad-130">Hinzufügen von Erwähnungen zu Ihren Nachrichten</span><span class="sxs-lookup"><span data-stu-id="e5cad-130">Adding mentions to your messages</span></span>

<span data-ttu-id="e5cad-131">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-131">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="e5cad-132">Dazu muss Ihre Nachricht folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="e5cad-132">To do this, your message must do the following:</span></span>

<span data-ttu-id="e5cad-133">Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie festlegen müssen:</span><span class="sxs-lookup"><span data-stu-id="e5cad-133">The `Mention` object has two properties that you will need to set:</span></span>

* <span data-ttu-id="e5cad-134">Schließen <at>@username</at> in den Nachrichtentext ein</span><span class="sxs-lookup"><span data-stu-id="e5cad-134">Include <at>@username</at> in the message text</span></span>
* <span data-ttu-id="e5cad-135">Schließen Sie das Erwähnungsobjekt in die Entitätensammlung ein.</span><span class="sxs-lookup"><span data-stu-id="e5cad-135">Include the mention object inside the entities collection</span></span>

<span data-ttu-id="e5cad-136">Das Bot Framework SDK bietet Hilfsmethoden und Objekte, um die Erstellung der Erwähnung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e5cad-136">The Bot Framework SDK provides helper methods and objects to make constructing the mention easier.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e5cad-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e5cad-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="e5cad-138">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e5cad-138">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="json"></a>[<span data-ttu-id="e5cad-139">Json</span><span class="sxs-lookup"><span data-stu-id="e5cad-139">JSON</span></span>](#tab/json)

<span data-ttu-id="e5cad-140">Das Feld im Objekt im Array muss genau mit einem Teil `text` `entities` des Nachrichtenfelds  `text` übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="e5cad-140">The `text` field in the object in the `entities` array must *exactly* match a portion of the message `text` field.</span></span> <span data-ttu-id="e5cad-141">Andern falls nicht, wird die Erwähnung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e5cad-141">If it does not, the mention will be ignored.</span></span>

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

# <a name="python"></a>[<span data-ttu-id="e5cad-142">Python</span><span class="sxs-lookup"><span data-stu-id="e5cad-142">Python</span></span>](#tab/python)

```python
async def _mention_activity(self, turn_context: TurnContext):
        mention = Mention(
            mentioned=turn_context.activity.from_property,
            text=f"<at>{turn_context.activity.from_property.name}</at>",
            type="mention"
        )

        reply_activity = MessageFactory.text(f"Hello {mention.text}")
        reply_activity.entities = [Mention().deserialize(mention.serialize())]
        await turn_context.send_activity(reply_activity)
```

* * *

## <a name="sending-a-message-on-installation"></a><span data-ttu-id="e5cad-143">Senden einer Nachricht bei der Installation</span><span class="sxs-lookup"><span data-stu-id="e5cad-143">Sending a message on installation</span></span>

<span data-ttu-id="e5cad-144">Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, kann es hilfreich sein, eine Nachricht zu senden, die ihn einf?nist.</span><span class="sxs-lookup"><span data-stu-id="e5cad-144">When your bot is first added to the group or team, it may be useful to send a message introducing it.</span></span> <span data-ttu-id="e5cad-145">Die Nachricht sollte eine kurze Beschreibung der Funktionen des Bots und deren Verwendung enthalten.</span><span class="sxs-lookup"><span data-stu-id="e5cad-145">The message should provide a brief description of the bot's features, and how to use them.</span></span> <span data-ttu-id="e5cad-146">Sie möchten das Ereignis mit dem `conversationUpdate` `teamMemberAdded` eventType abonnieren.</span><span class="sxs-lookup"><span data-stu-id="e5cad-146">You'll want to subscribe to the `conversationUpdate` event, with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="e5cad-147">Da das Ereignis gesendet wird, wenn ein neues Teammitglied hinzugefügt wird, müssen Sie überprüfen, ob das neue hinzugefügte Mitglied der Bot ist.</span><span class="sxs-lookup"><span data-stu-id="e5cad-147">Since the event is sent when any new team member is added, you need to check to determine if the new member added is the bot.</span></span> <span data-ttu-id="e5cad-148">Weitere [Informationen finden Sie unter "Senden einer Willkommensnachricht an](~/bots/how-to/conversations/send-proactive-messages.md) ein neues Teammitglied".</span><span class="sxs-lookup"><span data-stu-id="e5cad-148">See [Sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md) for more details.</span></span>

<span data-ttu-id="e5cad-149">Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="e5cad-149">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="e5cad-150">Dazu können Sie die Teamliste erhalten und jedem Benutzer eine direkte Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="e5cad-150">To do this, you could get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="e5cad-151">Es wird nicht empfohlen, in den folgenden Situationen eine Nachricht zu senden:</span><span class="sxs-lookup"><span data-stu-id="e5cad-151">It is not recommended to send a message in the following situations:</span></span>

* <span data-ttu-id="e5cad-152">Das Team ist groß (natürlich subjektiv, aber z. B. größer als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="e5cad-152">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="e5cad-153">Ihr Bot wird möglicherweise als "Spammy" betrachtet, und die Person, die ihn hinzugefügt hat, kann Beanstandungen erhalten, es sei denn, Sie teilen das Wertversprechen Ihres Bots jedem klar mit, der die Willkommensnachricht sieht.</span><span class="sxs-lookup"><span data-stu-id="e5cad-153">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="e5cad-154">Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten Hinzufügen zu einem Team)</span><span class="sxs-lookup"><span data-stu-id="e5cad-154">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="e5cad-155">Eine Gruppe oder ein Kanal wird umbenannt</span><span class="sxs-lookup"><span data-stu-id="e5cad-155">A group or channel is renamed</span></span>
* <span data-ttu-id="e5cad-156">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="e5cad-156">A team member is added to a group or channel</span></span>

## <a name="learn-more"></a><span data-ttu-id="e5cad-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5cad-157">Learn more</span></span>

<span data-ttu-id="e5cad-158">Ihr Bot hat Zugriff auf zusätzliche Informationen über den Gruppenchat oder das Team, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="e5cad-158">Your bot has access to additional information about the group chat or team it is installed in.</span></span> <span data-ttu-id="e5cad-159">Weitere APIs, die für Ihren Bot verfügbar sind, finden Sie unter ["Teams-Kontext](~/bots/how-to/get-teams-context.md) erhalten".</span><span class="sxs-lookup"><span data-stu-id="e5cad-159">See [get teams context](~/bots/how-to/get-teams-context.md) for additional APIs available for your bot.</span></span>

<span data-ttu-id="e5cad-160">Es gibt auch weitere Ereignisse, die Ihr Bot abonnieren und beantworten kann.</span><span class="sxs-lookup"><span data-stu-id="e5cad-160">There are also additional events that your bot can subscribe and respond to.</span></span> <span data-ttu-id="e5cad-161">Erfahren [Sie, wie Sie Unterhaltungsereignisse](~/bots/how-to/conversations/subscribe-to-conversation-events.md) abonnieren.</span><span class="sxs-lookup"><span data-stu-id="e5cad-161">See [subscribe to conversation events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) to learn how.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
