---
title: Kanal- und Gruppenunterhaltungen mit einem Bot
author: clearab
description: Senden, Empfangen und Behandeln von Nachrichten für einen Bot in einem Kanal- oder Gruppenchat.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: ef5cf8464fa0e93d5ea3840003a2b0c04a4a5ef5
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630999"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a><span data-ttu-id="ce612-103">Kanal- und Gruppenchatunterhaltungen mit einem Bot</span><span class="sxs-lookup"><span data-stu-id="ce612-103">Channel and group chat conversations with a bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="ce612-104">Um den Microsoft Teams in einem Team- oder Gruppenchat zu installieren, fügen Sie dem Bot den Bereich oder `teams` `groupchat` den Bereich hinzu.</span><span class="sxs-lookup"><span data-stu-id="ce612-104">To install the Microsoft Teams bot in a team or group chat, add the `teams` or `groupchat` scope to your bot.</span></span> <span data-ttu-id="ce612-105">Dadurch können alle Mitglieder der Unterhaltung mit Ihrem Bot interagieren.</span><span class="sxs-lookup"><span data-stu-id="ce612-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="ce612-106">Nachdem der Bot installiert wurde, hat er Zugriff auf Metadaten zur Unterhaltung, z. B. auf die Liste der Unterhaltungsmitglieder.</span><span class="sxs-lookup"><span data-stu-id="ce612-106">After the bot is installed, it has access to metadata about the conversation, such as the list of conversation members.</span></span> <span data-ttu-id="ce612-107">Wenn er in einem Team installiert ist, hat der Bot außerdem Zugriff auf Details zu diesem Team und die vollständige Liste der Kanäle.</span><span class="sxs-lookup"><span data-stu-id="ce612-107">Also, when it is installed in a team, the bot has access to details about that team and the full list of channels.</span></span>

<span data-ttu-id="ce612-108">Bots in einer Gruppe oder einem Kanal empfangen nachrichten nur, wenn sie @botname.</span><span class="sxs-lookup"><span data-stu-id="ce612-108">Bots in a group or channel only receive messages when they are mentioned @botname.</span></span> <span data-ttu-id="ce612-109">Sie erhalten keine weiteren Nachrichten, die an die Unterhaltung gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ce612-109">They do not receive any other messages sent to the conversation.</span></span> <span data-ttu-id="ce612-110">Der Bot muss direkt @erwähnt werden.</span><span class="sxs-lookup"><span data-stu-id="ce612-110">The bot must be @mentioned directly.</span></span> <span data-ttu-id="ce612-111">Ihr Bot erhält keine Nachricht, wenn das Team oder der Kanal erwähnt wird oder wenn jemand auf eine Nachricht von Ihrem Bot antwortet, ohne @mentioning senden.</span><span class="sxs-lookup"><span data-stu-id="ce612-111">Your bot does not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

> [!NOTE]
> <span data-ttu-id="ce612-112">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ce612-112">This feature is currently available in [public developer preview](../../../resources/dev-preview/developer-preview-intro.md) only.</span></span>
>
> <span data-ttu-id="ce612-113">Mithilfe der ressourcenspezifischen Zustimmung (RSC) können Bots alle Kanalnachrichten in Teams empfangen, in dem sie installiert sind, ohne dass @mentioned.</span><span class="sxs-lookup"><span data-stu-id="ce612-113">Using resource-specific consent (RSC), bots can receive all channel messages in teams that it is installed in without being @mentioned.</span></span> <span data-ttu-id="ce612-114">Weitere Informationen finden Sie unter [Empfangen aller Kanalnachrichten mit RSC](channel-messages-with-rsc.md).</span><span class="sxs-lookup"><span data-stu-id="ce612-114">For more information, see [receive all channel messages with RSC](channel-messages-with-rsc.md).</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="ce612-115">Richtlinien für den Entwurf</span><span class="sxs-lookup"><span data-stu-id="ce612-115">Design guidelines</span></span>

<span data-ttu-id="ce612-116">Im Gegensatz zu persönlichen Chats muss Ihr Bot in Gruppenchats und Kanälen eine schnelle Einführung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ce612-116">Unlike personal chats, in group chats and channels, your bot must provide a quick introduction.</span></span> <span data-ttu-id="ce612-117">Sie müssen diese und weitere Richtlinien für das Botdesign befolgen.</span><span class="sxs-lookup"><span data-stu-id="ce612-117">You must follow these and more bot design guidelines.</span></span> <span data-ttu-id="ce612-118">Weitere Informationen zum Entwerfen von Bots in Teams finden Sie unter Entwerfen von Botunterhaltungen [in Kanälen und Chats.](~/bots/design/bots.md)</span><span class="sxs-lookup"><span data-stu-id="ce612-118">For more information on how to design bots in Teams, see [how to design bot conversations in channels and chats](~/bots/design/bots.md).</span></span>

<span data-ttu-id="ce612-119">Jetzt können Sie neue Unterhaltungsthreads erstellen und problemlos verschiedene Unterhaltungen in Kanälen verwalten.</span><span class="sxs-lookup"><span data-stu-id="ce612-119">Now, you can create new conversation threads and easily manage different conversations in channels.</span></span>

## <a name="create-new-conversation-threads"></a><span data-ttu-id="ce612-120">Erstellen neuer Unterhaltungsthreads</span><span class="sxs-lookup"><span data-stu-id="ce612-120">Create new conversation threads</span></span>

<span data-ttu-id="ce612-121">Wenn Ihr Bot in einem Team installiert ist, müssen Sie einen neuen Unterhaltungsthread erstellen, anstatt auf einen vorhandenen zu antworten.</span><span class="sxs-lookup"><span data-stu-id="ce612-121">When your bot is installed in a team, you must create a new conversation thread rather than reply to an existing one.</span></span> <span data-ttu-id="ce612-122">Manchmal ist es schwierig, zwischen zwei Unterhaltungen zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="ce612-122">At times it is difficult to differentiate between two conversations.</span></span> <span data-ttu-id="ce612-123">Wenn die Unterhaltung threaded ist, ist es einfacher, verschiedene Unterhaltungen in Kanälen zu organisieren und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ce612-123">If the conversation is threaded, it is easier to organize and manage different conversations in channels.</span></span> <span data-ttu-id="ce612-124">Dies ist eine Form von [proaktivem Messaging.](~/bots/how-to/conversations/send-proactive-messages.md)</span><span class="sxs-lookup"><span data-stu-id="ce612-124">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

<span data-ttu-id="ce612-125">Als Nächstes können Sie Erwähnungen mithilfe des Objekts abrufen und Ihren Nachrichten Erwähnungen `entities` hinzufügen, indem Sie das Objekt `Mention` verwenden.</span><span class="sxs-lookup"><span data-stu-id="ce612-125">Next, you can retrieve mentions using the `entities` object and add mentions to your messages using the `Mention` object.</span></span>

## <a name="work-with-mentions"></a><span data-ttu-id="ce612-126">Arbeiten mit Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="ce612-126">Work with mentions</span></span>

<span data-ttu-id="ce612-127">Jede Nachricht an Ihren Bot aus einer Gruppe oder einem Kanal enthält eine @mention deren Name im Nachrichtentext enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="ce612-127">Every message to your bot from a group or channel contains an @mention with its name in the message text.</span></span> <span data-ttu-id="ce612-128">Ihr Bot kann auch andere Benutzer abrufen, die in einer Nachricht erwähnt werden, und Allen nachrichten, die er sendet, Erwähnungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ce612-128">Your bot can also retrieve other users mentioned in a message and add mentions to any messages it sends.</span></span>

<span data-ttu-id="ce612-129">Sie müssen auch die @mentions aus dem Inhalt der Nachricht, die Ihr Bot empfängt, herausstreifen.</span><span class="sxs-lookup"><span data-stu-id="ce612-129">You must also strip out the @mentions from the content of the message your bot receives.</span></span>

### <a name="retrieve-mentions"></a><span data-ttu-id="ce612-130">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="ce612-130">Retrieve mentions</span></span>

<span data-ttu-id="ce612-131">Erwähnungen werden im Objekt in nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch den Namen `entities` des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="ce612-131">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and the name of the user mentioned.</span></span> <span data-ttu-id="ce612-132">Der Text der Nachricht enthält auch die Erwähnung, z. B. `<at>@John Smith<at>` .</span><span class="sxs-lookup"><span data-stu-id="ce612-132">The text of the message also includes the mention, such as `<at>@John Smith<at>`.</span></span> <span data-ttu-id="ce612-133">Verlassen Sie sich jedoch nicht auf den Text in der Nachricht, um Informationen über den Benutzer abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ce612-133">However, do not rely on the text in the message to retrieve any information about the user.</span></span> <span data-ttu-id="ce612-134">Die Person, die die Nachricht sendet, kann sie ändern.</span><span class="sxs-lookup"><span data-stu-id="ce612-134">It is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="ce612-135">Verwenden Sie daher das `entities` Objekt.</span><span class="sxs-lookup"><span data-stu-id="ce612-135">Therefore, use the `entities` object.</span></span>

<span data-ttu-id="ce612-136">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion im Bot Builder SDK aufrufen, das `GetMentions` ein Array von Objekten `Mention` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="ce612-136">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK, which returns an array of `Mention` objects.</span></span>

<span data-ttu-id="ce612-137">Der folgende Code zeigt ein Beispiel für das Abrufen von Erwähnungen:</span><span class="sxs-lookup"><span data-stu-id="ce612-137">The following code shows an example of retrieving mentions:</span></span>

# <a name="c"></a>[<span data-ttu-id="ce612-138">C#</span><span class="sxs-lookup"><span data-stu-id="ce612-138">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="ce612-139">TypeScript</span><span class="sxs-lookup"><span data-stu-id="ce612-139">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ce612-140">Json</span><span class="sxs-lookup"><span data-stu-id="ce612-140">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ce612-141">Python</span><span class="sxs-lookup"><span data-stu-id="ce612-141">Python</span></span>](#tab/python)

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

### <a name="add-mentions-to-your-messages"></a><span data-ttu-id="ce612-142">Hinzufügen von Erwähnungen zu Ihren Nachrichten</span><span class="sxs-lookup"><span data-stu-id="ce612-142">Add mentions to your messages</span></span>

<span data-ttu-id="ce612-143">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden.</span><span class="sxs-lookup"><span data-stu-id="ce612-143">Your bot can mention other users in messages posted into channels.</span></span>

<span data-ttu-id="ce612-144">Das `Mention` Objekt verfügt über zwei Eigenschaften, die Sie mithilfe der folgenden Eigenschaften festlegen müssen:</span><span class="sxs-lookup"><span data-stu-id="ce612-144">The `Mention` object has two properties that you must set using the following:</span></span>

* <span data-ttu-id="ce612-145">Fügen <at>@username</at> in den Nachrichtentext ein.</span><span class="sxs-lookup"><span data-stu-id="ce612-145">Include <at>@username</at> in the message text.</span></span>
* <span data-ttu-id="ce612-146">Schließen Sie das Mention-Objekt in die Entitätssammlung ein.</span><span class="sxs-lookup"><span data-stu-id="ce612-146">Include the mention object inside the entities collection.</span></span>

<span data-ttu-id="ce612-147">Das Bot Framework SDK stellt Hilfsmethoden und Objekte zum Erstellen von Erwähnungen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ce612-147">The Bot Framework SDK provides helper methods and objects to create mentions.</span></span>

<span data-ttu-id="ce612-148">Der folgende Code zeigt ein Beispiel für das Hinzufügen von Erwähnungen zu Ihren Nachrichten:</span><span class="sxs-lookup"><span data-stu-id="ce612-148">The following code shows an example of adding mentions to your messages:</span></span>

# <a name="c"></a>[<span data-ttu-id="ce612-149">C#</span><span class="sxs-lookup"><span data-stu-id="ce612-149">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="ce612-150">TypeScript</span><span class="sxs-lookup"><span data-stu-id="ce612-150">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ce612-151">Json</span><span class="sxs-lookup"><span data-stu-id="ce612-151">JSON</span></span>](#tab/json)

<span data-ttu-id="ce612-152">Das `text` Feld im Objekt im Array muss einem Teil des `entities` Nachrichtenfelds `text` entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ce612-152">The `text` field in the object in the `entities` array must match a portion of the message `text` field.</span></span> <span data-ttu-id="ce612-153">Andern falls nicht, wird die Erwähnung ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ce612-153">If it does not, the mention is ignored.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="ce612-154">Python</span><span class="sxs-lookup"><span data-stu-id="ce612-154">Python</span></span>](#tab/python)

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

<span data-ttu-id="ce612-155">Jetzt können Sie eine Einführungsnachricht senden, wenn Ihr Bot zum ersten Mal installiert oder einer Gruppe oder einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ce612-155">Now you can send an introduction message when your bot is first installed or added to a group or team.</span></span>

## <a name="send-a-message-on-installation"></a><span data-ttu-id="ce612-156">Senden einer Nachricht bei der Installation</span><span class="sxs-lookup"><span data-stu-id="ce612-156">Send a message on installation</span></span>

<span data-ttu-id="ce612-157">Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, muss eine Einführungsnachricht gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ce612-157">When your bot is first added to the group or team, an introduction message must be sent.</span></span> <span data-ttu-id="ce612-158">Die Nachricht muss eine kurze Beschreibung der Funktionen des Bots und deren Verwendung enthalten.</span><span class="sxs-lookup"><span data-stu-id="ce612-158">The message must provide a brief description of the bot's features and how to use them.</span></span> <span data-ttu-id="ce612-159">Sie müssen das Ereignis `conversationUpdate` mit dem `teamMemberAdded` eventType abonnieren.</span><span class="sxs-lookup"><span data-stu-id="ce612-159">You must subscribe to the `conversationUpdate` event with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="ce612-160">Das Ereignis wird gesendet, wenn ein neues Teammitglied hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ce612-160">The event is sent when any new team member is added.</span></span> <span data-ttu-id="ce612-161">Überprüfen Sie, ob das hinzugefügte neue Mitglied der Bot ist.</span><span class="sxs-lookup"><span data-stu-id="ce612-161">Check if the new member added is the bot.</span></span> <span data-ttu-id="ce612-162">Weitere Informationen finden Sie unter [Senden einer Willkommensnachricht an ein neues Teammitglied](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="ce612-162">For more information, see [sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

<span data-ttu-id="ce612-163">Senden Sie eine persönliche Nachricht an jedes Teammitglied, wenn der Bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ce612-163">Send a personal message to each team member when the bot is added.</span></span> <span data-ttu-id="ce612-164">Dazu erhalten Sie die Teamliste, und senden Sie jedem Benutzer eine direkte Nachricht.</span><span class="sxs-lookup"><span data-stu-id="ce612-164">To do this, get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="ce612-165">Senden Sie in den folgenden Fällen keine Nachricht:</span><span class="sxs-lookup"><span data-stu-id="ce612-165">Do not send a message in the following cases:</span></span>

* <span data-ttu-id="ce612-166">Das Team ist groß, z. B. größer als 100 Mitglieder.</span><span class="sxs-lookup"><span data-stu-id="ce612-166">The team is large, for example, larger than 100 members.</span></span> <span data-ttu-id="ce612-167">Ihr Bot kann als Spam gesehen werden, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten.</span><span class="sxs-lookup"><span data-stu-id="ce612-167">Your bot can be seen as spam and the person who added it can get complaints.</span></span> <span data-ttu-id="ce612-168">Sie müssen die Wertversprechung Ihres Bots jedem klar vermitteln, der die Willkommensnachricht sieht.</span><span class="sxs-lookup"><span data-stu-id="ce612-168">You must clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="ce612-169">Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, anstatt zuerst einem Team hinzugefügt zu werden.</span><span class="sxs-lookup"><span data-stu-id="ce612-169">Your bot is first mentioned in a group or channel instead of being first added to a team.</span></span>
* <span data-ttu-id="ce612-170">Eine Gruppe oder ein Kanal wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="ce612-170">A group or channel is renamed.</span></span>
* <span data-ttu-id="ce612-171">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ce612-171">A team member is added to a group or channel.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="see-also"></a><span data-ttu-id="ce612-172">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="ce612-172">See also</span></span>

[<span data-ttu-id="ce612-173">Get Teams context</span><span class="sxs-lookup"><span data-stu-id="ce612-173">Get Teams context</span></span>](~/bots/how-to/get-teams-context.md)

## <a name="next-step"></a><span data-ttu-id="ce612-174">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ce612-174">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce612-175">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="ce612-175">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
