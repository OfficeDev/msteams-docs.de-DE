---
title: Kanal- und Gruppenunterhaltungen
author: clearab
description: Vorgehensweise zum Senden, empfangen und Verarbeiten von Nachrichten für einen bot in einem Kanal-oder Gruppenchat.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: ccc27d7638820cfa3c2b7cfe12b91b3a3a9fef1d
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2020
ms.locfileid: "44801340"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="88a8b-103">Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="88a8b-103">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="88a8b-104">Indem Sie den `teams` oder `groupchat` -Bereich zu Ihrem bot hinzufügen, kann er für die Installation in einem Team-oder Gruppenchat zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="88a8b-104">By adding the `teams` or `groupchat` scope to your bot, it can be available to be installed in a team or group chat.</span></span> <span data-ttu-id="88a8b-105">Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren.</span><span class="sxs-lookup"><span data-stu-id="88a8b-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="88a8b-106">Sobald er installiert ist, hat er auch Zugriff auf Metadaten zu der Unterhaltung wie der Liste der Unterhaltungsmitglieder, und wenn er in einem Team installiert wurde, auf Details zu diesem Team sowie die vollständige Liste der Kanäle.</span><span class="sxs-lookup"><span data-stu-id="88a8b-106">Once installed, it will also have access to metadata about the conversation like the list of conversation members, and when installed in a team details about that team and the full list of channels.</span></span>

<span data-ttu-id="88a8b-107">Bots in einer Gruppe oder einem Kanal empfangen nur Nachrichten, wenn Sie erwähnt werden ("@botname"), Sie erhalten keine weiteren Nachrichten, die an die Unterhaltung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="88a8b-107">Bots in a group or channel only receive messages when they are mentioned ("@botname"), they do not receive any other messages sent to the conversation.</span></span>

> [!NOTE]
> <span data-ttu-id="88a8b-108">Der Bot muss direkt @erwähnt werden.</span><span class="sxs-lookup"><span data-stu-id="88a8b-108">The bot must be @mentioned directly.</span></span> <span data-ttu-id="88a8b-109">Ihr bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem bot antwortet, ohne Sie zu @mentioning.</span><span class="sxs-lookup"><span data-stu-id="88a8b-109">Your bot will not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

## <a name="design-considerations"></a><span data-ttu-id="88a8b-110">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="88a8b-110">Design considerations</span></span>

<span data-ttu-id="88a8b-111">Ein bot sollte Informationen bereitstellen, die für alle Mitglieder in einer Gruppe oder einem Kanal geeignet und relevant sind.</span><span class="sxs-lookup"><span data-stu-id="88a8b-111">A bot should provide information that is both appropriate and relevant to all members in a group or channel.</span></span> <span data-ttu-id="88a8b-112">Unterhaltungen mit dieser sind für alle sichtbar, die Teil der Gruppe oder des Kanals sind.</span><span class="sxs-lookup"><span data-stu-id="88a8b-112">Conversations with it are visible to everyone that is a part of the group or channel.</span></span> <span data-ttu-id="88a8b-113">Ein gut konzipierter bot kann allen Benutzern einen Mehrwert geben, ohne versehentlich Informationen freizugeben, die in einer 1:1-Unterhaltung besser geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="88a8b-113">A well designed bot can add value to all users while not inadvertently sharing information that is more appropriate in a one-to-one conversation.</span></span> <span data-ttu-id="88a8b-114">Multi-Turn-Unterhaltungen wie Dialoge sollten vermieden werden – verwenden Sie Karten und/oder Aufgaben Module, um stattdessen Informationen zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="88a8b-114">Multi-turn conversations like dialogs should be avoided - use cards and/or task modules to collect information instead.</span></span>

## <a name="creating-new-conversation-threads"></a><span data-ttu-id="88a8b-115">Erstellen neuer Unterhaltungs Threads</span><span class="sxs-lookup"><span data-stu-id="88a8b-115">Creating new conversation threads</span></span>

<span data-ttu-id="88a8b-116">Wenn Ihr bot in einem Team installiert ist, kann es manchmal erforderlich sein, einen neuen Unterhaltungsthread zu erstellen, statt einem vorhandenen zu antworten.</span><span class="sxs-lookup"><span data-stu-id="88a8b-116">When your bot is installed in a team, it can sometimes be necessary to create a new conversation thread rather than replying to an existing one.</span></span> <span data-ttu-id="88a8b-117">Dies ist eine Form von [proaktivem Messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="88a8b-117">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

## <a name="working-with-mentions"></a><span data-ttu-id="88a8b-118">Arbeiten mit Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="88a8b-118">Working with mentions</span></span>

<span data-ttu-id="88a8b-119">Jede Nachricht von einer Gruppe oder einem Kanal an Ihren Bot enthält eine „@Erwähnung“ mit seinem eigenen Namen im Nachrichtentext, weshalb Sie sicherstellen müssen, dass Ihre Nachrichtenanalyse dies verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="88a8b-119">Every message to your bot from a group or channel will contain an @mention with its own name in the message text, so you'll need to ensure your message parsing handles that.</span></span> <span data-ttu-id="88a8b-120">Der Bot kann auch andere in einer Nachricht erwähnte Benutzer abrufen und jeder von ihm gesendeten Nachricht Erwähnungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="88a8b-120">Your bot can also retrieve other users mentioned in a message, and add mentions to any messages it sends.</span></span>

### <a name="stripping-mentions-from-message-text"></a><span data-ttu-id="88a8b-121">Entfernen von Erwähnungen aus dem Nachrichtentext</span><span class="sxs-lookup"><span data-stu-id="88a8b-121">Stripping mentions from message text</span></span>

<span data-ttu-id="88a8b-122">Möglicherweise halten Sie es für notwendig, die @Erwähnungen aus dem Text der Nachricht zu entfernen, die ihr Bot empfängt.</span><span class="sxs-lookup"><span data-stu-id="88a8b-122">You may find it necessary to strip out the @mentions from the text of the message your bot receives.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="88a8b-123">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="88a8b-123">Retrieving mentions</span></span>

<span data-ttu-id="88a8b-124">Erwähnungen werden im `entities` Objekt in Payload zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="88a8b-124">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="88a8b-125">Der Text der Nachricht enthält außerdem die Erwähnung ähnlich wie `<at>@John Smith<at>`.</span><span class="sxs-lookup"><span data-stu-id="88a8b-125">The text of the message will also include the mention like `<at>@John Smith<at>`.</span></span> <span data-ttu-id="88a8b-126">Sie sollten sich jedoch nicht darauf verlassen, dass der Text in der Nachricht alle Informationen zum Benutzer abruft. Es ist möglich, dass die Person, die die Nachricht sendet, Sie ändert.</span><span class="sxs-lookup"><span data-stu-id="88a8b-126">However, you should not rely on the text in the message to retrieve any information about the user; it is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="88a8b-127">Verwenden Sie stattdessen das- `entities` Objekt.</span><span class="sxs-lookup"><span data-stu-id="88a8b-127">Instead, use the `entities` object.</span></span>

<span data-ttu-id="88a8b-128">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im bot Builder SDK aufrufen, das ein Array von Objekten zurückgibt `Mention` .</span><span class="sxs-lookup"><span data-stu-id="88a8b-128">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK which returns an array of `Mention` objects.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="88a8b-129">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="88a8b-129">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="88a8b-130">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="88a8b-130">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="88a8b-131">Json</span><span class="sxs-lookup"><span data-stu-id="88a8b-131">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="88a8b-132">Python</span><span class="sxs-lookup"><span data-stu-id="88a8b-132">Python</span></span>](#tab/python)

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

### <a name="adding-mentions-to-your-messages"></a><span data-ttu-id="88a8b-133">Hinzufügen von Erwähnungen zu ihren Nachrichten</span><span class="sxs-lookup"><span data-stu-id="88a8b-133">Adding mentions to your messages</span></span>

<span data-ttu-id="88a8b-134">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden.</span><span class="sxs-lookup"><span data-stu-id="88a8b-134">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="88a8b-135">Hierzu muss Ihre Nachricht folgendermaßen vorgehen:</span><span class="sxs-lookup"><span data-stu-id="88a8b-135">To do this, your message must do the following:</span></span>

<span data-ttu-id="88a8b-136">Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie festlegen müssen:</span><span class="sxs-lookup"><span data-stu-id="88a8b-136">The `Mention` object has two properties that you will need to set:</span></span>

* <span data-ttu-id="88a8b-137">Einschließen von <at>@username</at> im Nachrichtentext</span><span class="sxs-lookup"><span data-stu-id="88a8b-137">Include <at>@username</at> in the message text</span></span>
* <span data-ttu-id="88a8b-138">Einschließen des mention-Objekts in die Entities-Auflistung</span><span class="sxs-lookup"><span data-stu-id="88a8b-138">Include the mention object inside the entities collection</span></span>

<span data-ttu-id="88a8b-139">Das bot-Framework-SDK stellt Hilfsmethoden und-Objekte bereit, damit die Erwähnung einfacher gestaltet wird.</span><span class="sxs-lookup"><span data-stu-id="88a8b-139">The Bot Framework SDK provides helper methods and objects to make constructing the mention easier.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="88a8b-140">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="88a8b-140">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="88a8b-141">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="88a8b-141">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="88a8b-142">Json</span><span class="sxs-lookup"><span data-stu-id="88a8b-142">JSON</span></span>](#tab/json)

<span data-ttu-id="88a8b-143">Das `text` Feld im Objekt im `entities` Array muss *exakt* mit einem Teil des Nachrichtenfelds übereinstimmen `text` .</span><span class="sxs-lookup"><span data-stu-id="88a8b-143">The `text` field in the object in the `entities` array must *exactly* match a portion of the message `text` field.</span></span> <span data-ttu-id="88a8b-144">Wenn dies nicht der Fall ist, wird die Erwähnung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="88a8b-144">If it does not, the mention will be ignored.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="88a8b-145">Python</span><span class="sxs-lookup"><span data-stu-id="88a8b-145">Python</span></span>](#tab/python)

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

## <a name="sending-a-message-on-installation"></a><span data-ttu-id="88a8b-146">Senden einer Nachricht bei der Installation</span><span class="sxs-lookup"><span data-stu-id="88a8b-146">Sending a message on installation</span></span>

<span data-ttu-id="88a8b-147">Wenn Ihr bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, kann es hilfreich sein, eine Nachricht mit der Einführung zu senden.</span><span class="sxs-lookup"><span data-stu-id="88a8b-147">When your bot is first added to the group or team, it may be useful to send a message introducing it.</span></span> <span data-ttu-id="88a8b-148">Die Nachricht sollte eine kurze Beschreibung der Funktionen des bot enthalten und deren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="88a8b-148">The message should provide a brief description of the bot's features, and how to use them.</span></span> <span data-ttu-id="88a8b-149">Sie möchten das `conversationUpdate` Ereignis mit dem `teamMemberAdded` eventType abonnieren.</span><span class="sxs-lookup"><span data-stu-id="88a8b-149">You'll want to subscribe to the `conversationUpdate` event, with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="88a8b-150">Da das Ereignis gesendet wird, wenn ein neues Teammitglied hinzugefügt wird, müssen Sie überprüfen, ob das hinzugefügte neue Mitglied der Bot ist.</span><span class="sxs-lookup"><span data-stu-id="88a8b-150">Since the event is sent when any new team member is added, you need to check to determine if the new member added is the bot.</span></span> <span data-ttu-id="88a8b-151">Weitere Informationen finden Sie unter [Senden einer Willkommensnachricht an ein neues Teammitglied](~/bots/how-to/conversations/send-proactive-messages.md) .</span><span class="sxs-lookup"><span data-stu-id="88a8b-151">See [Sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md) for more details.</span></span>

<span data-ttu-id="88a8b-152">Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="88a8b-152">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="88a8b-153">Dazu können Sie das Team-Dienstplan erhalten und jedem Benutzer eine direkte Nachricht senden.</span><span class="sxs-lookup"><span data-stu-id="88a8b-153">To do this, you could get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="88a8b-154">Es wird nicht empfohlen, eine Nachricht in den folgenden Situationen zu senden:</span><span class="sxs-lookup"><span data-stu-id="88a8b-154">It is not recommended to send a message in the following situations:</span></span>

* <span data-ttu-id="88a8b-155">Das Team ist groß (offensichtlich subjektiv, aber zum Beispiel größer als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="88a8b-155">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="88a8b-156">Ihr bot wird möglicherweise als "spammy" angesehen, und die Person, die Sie hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen dem Benutzer, der die Willkommensnachricht sieht, eindeutig den Wert Vorschlag Ihres bot mit.</span><span class="sxs-lookup"><span data-stu-id="88a8b-156">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="88a8b-157">Ihr bot wird erstmals in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten hinzufügen zu einem Team).</span><span class="sxs-lookup"><span data-stu-id="88a8b-157">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="88a8b-158">Eine Gruppe oder ein Kanal wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="88a8b-158">A group or channel is renamed</span></span>
* <span data-ttu-id="88a8b-159">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="88a8b-159">A team member is added to a group or channel</span></span>

## <a name="learn-more"></a><span data-ttu-id="88a8b-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88a8b-160">Learn more</span></span>

<span data-ttu-id="88a8b-161">Ihr bot hat Zugriff auf zusätzliche Informationen über den Gruppenchat oder das Team, in dem er installiert ist.</span><span class="sxs-lookup"><span data-stu-id="88a8b-161">Your bot has access to additional information about the group chat or team it is installed in.</span></span> <span data-ttu-id="88a8b-162">Weitere APIs für Ihren bot finden Sie unter [Get Teams Context](~/bots/how-to/get-teams-context.md) .</span><span class="sxs-lookup"><span data-stu-id="88a8b-162">See [get teams context](~/bots/how-to/get-teams-context.md) for additional APIs available for your bot.</span></span>

<span data-ttu-id="88a8b-163">Es gibt auch zusätzliche Ereignisse, die ihr bot abonnieren und auf die Sie Antworten können.</span><span class="sxs-lookup"><span data-stu-id="88a8b-163">There are also additional events that your bot can subscribe and respond to.</span></span> <span data-ttu-id="88a8b-164">Weitere Informationen finden Sie unter [Subscribe to Conversation Events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) .</span><span class="sxs-lookup"><span data-stu-id="88a8b-164">See [subscribe to conversation events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) to learn how.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
