---
title: Grundlagen zu Unterhaltungen
description: Beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 3cf11b5b96a1504ddb3fb8c9fc5814c5131d072f
ms.sourcegitcommit: e78c9f51c4538212c53bb6c6a45a09d994896f09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2021
ms.locfileid: "51585855"
---
# <a name="conversation-basics"></a><span data-ttu-id="ed288-103">Grundlagen zu Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="ed288-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="ed288-104">Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams-Bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed288-104">A conversation is a series of messages sent between your Microsoft Teams bot and one or more users.</span></span> <span data-ttu-id="ed288-105">Es gibt drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:</span><span class="sxs-lookup"><span data-stu-id="ed288-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="ed288-106">Unterhaltungstyp</span><span class="sxs-lookup"><span data-stu-id="ed288-106">Conversation type</span></span> | <span data-ttu-id="ed288-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed288-107">Description</span></span> |
| ------- | ----------- |
| `channel` | <span data-ttu-id="ed288-108">Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar.</span><span class="sxs-lookup"><span data-stu-id="ed288-108">This conversation type is visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="ed288-109">Dieser Unterhaltungstyp enthält Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ed288-109">This conversation type includes conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="ed288-110">Dieser Unterhaltungstyp umfasst Chats zwischen einem Bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="ed288-110">This conversation type includes chat between a bot and two or more users.</span></span> <span data-ttu-id="ed288-111">Es aktiviert ihren Bot auch in Besprechungschats.</span><span class="sxs-lookup"><span data-stu-id="ed288-111">It also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="ed288-112">Ein Bot verhält sich abhängig von der Unterhaltung, an der er beteiligt ist, unterschiedlich:</span><span class="sxs-lookup"><span data-stu-id="ed288-112">A bot behaves differently depending on the conversation it is involved in:</span></span>

* <span data-ttu-id="ed288-113">Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.</span><span class="sxs-lookup"><span data-stu-id="ed288-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="ed288-114">Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung.</span><span class="sxs-lookup"><span data-stu-id="ed288-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="ed288-115">Alle nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="ed288-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="ed288-116">Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich unterstützung im [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="ed288-116">For the bot to work in a particular conversation or scope, add support to that scope in the [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="messages-in-bot-conversations"></a><span data-ttu-id="ed288-117">Nachrichten in Botunterhaltungen</span><span class="sxs-lookup"><span data-stu-id="ed288-117">Messages in bot conversations</span></span>

<span data-ttu-id="ed288-118">Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="ed288-118">Each message in a conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="ed288-119">Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="ed288-119">When a user sends a message, Teams posts the message to your bot.</span></span> <span data-ttu-id="ed288-120">Teams sendet ein JSON-Objekt an den Messagingendpunkt Ihres Bots.</span><span class="sxs-lookup"><span data-stu-id="ed288-120">Teams sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="ed288-121">Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen, und antwortet entsprechend.</span><span class="sxs-lookup"><span data-stu-id="ed288-121">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="ed288-122">Grundlegende Unterhaltungen werden über den Bot Framework-Connector, eine einzelne REST-API, behandelt.</span><span class="sxs-lookup"><span data-stu-id="ed288-122">Basic conversations are handled through the Bot Framework connector, a single REST API.</span></span> <span data-ttu-id="ed288-123">Mit dieser API kann Ihr Bot mit Teams und anderen Kanälen kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="ed288-123">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="ed288-124">Das Bot Builder SDK bietet Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ed288-124">The Bot Builder SDK provides the following:</span></span>

* <span data-ttu-id="ed288-125">Einfacher Zugriff auf den Bot Framework-Connector.</span><span class="sxs-lookup"><span data-stu-id="ed288-125">Easy access to the Bot Framework connector.</span></span>
* <span data-ttu-id="ed288-126">Zusätzliche Funktionalität zum Verwalten des Unterhaltungsflusses und -zustands.</span><span class="sxs-lookup"><span data-stu-id="ed288-126">Additional functionality to manage conversation flow and state.</span></span>
* <span data-ttu-id="ed288-127">Einfache Möglichkeiten zum Integrieren von kognitiven Diensten wie der Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP).</span><span class="sxs-lookup"><span data-stu-id="ed288-127">Simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

<span data-ttu-id="ed288-128">Ihr Bot empfängt Nachrichten von Teams mithilfe der Eigenschaft und sendet einzelne oder `Text` mehrere Nachrichtenantworten an die Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ed288-128">Your bot receives messages from Teams using the `Text` property and it sends single or multiple message responses to the users.</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="ed288-129">Empfangen einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="ed288-129">Receive a message</span></span>

<span data-ttu-id="ed288-130">Um eine Textnachricht zu empfangen, verwenden Sie die `Text`-Eigenschaft des `Activity`-Objekts.</span><span class="sxs-lookup"><span data-stu-id="ed288-130">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="ed288-131">Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="ed288-131">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="ed288-132">Der folgende Code zeigt ein Beispiel für den Empfang einer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="ed288-132">The following code shows an example of receiving a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="ed288-133">C#</span><span class="sxs-lookup"><span data-stu-id="ed288-133">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="ed288-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="ed288-134">TypeScript</span></span>](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity(`Echo: '${context.activity.text}'`);
            await next();
        });
    }
}

```

# <a name="python"></a>[<span data-ttu-id="ed288-135">Python</span><span class="sxs-lookup"><span data-stu-id="ed288-135">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="ed288-136">Json</span><span class="sxs-lookup"><span data-stu-id="ed288-136">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot",
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

## <a name="send-a-message"></a><span data-ttu-id="ed288-137">Senden einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="ed288-137">Send a message</span></span>

<span data-ttu-id="ed288-138">Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten.</span><span class="sxs-lookup"><span data-stu-id="ed288-138">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="ed288-139">Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden.</span><span class="sxs-lookup"><span data-stu-id="ed288-139">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="ed288-140">Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten gleichzeitig zu senden.</span><span class="sxs-lookup"><span data-stu-id="ed288-140">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="ed288-141">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn ein Benutzer einer Unterhaltung hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="ed288-141">The following code shows an example of sending a message when a user is added to a conversation:</span></span>

<span data-ttu-id="ed288-142">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="ed288-142">The following code shows an example of sending a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="ed288-143">C#</span><span class="sxs-lookup"><span data-stu-id="ed288-143">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="ed288-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="ed288-144">TypeScript</span></span>](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello and welcome!');
            await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ed288-145">Python</span><span class="sxs-lookup"><span data-stu-id="ed288-145">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="ed288-146">Json</span><span class="sxs-lookup"><span data-stu-id="ed288-146">JSON</span></span>](#tab/json)

```json
{
    "text": "hi",
    "textFormat": "plain",
    "type": "message",
    "timestamp": "2019-10-31T20:57:27.2347285Z",
    "localTimestamp": "2019-10-31T13:57:27.2347285-07:00",
    "id": "1572555447214",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "29:1Xv-kvy4dKirR0rZfSF_kAVUzotoT1SXuEzkC9XGkuZng8YBw8qyu5uh4128fQRjlGgvEiRLx-0XP4KYMwcgdZw",
        "name": "Jane Doe",
        "aadObjectId": "df486eae-88fd-42a5-b45e-c581588186db"
    },
    "conversation": {
        "conversationType": "personal",
        "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
        "id": "a:1oAmWTVBBe9E0JrpGxauqNyx4CCE_iQf2ZuWon9D42722Fon3wYIpbhgbRChE3wgVS1Gwl9zS1pZy4FSu6-x1vGEq5KBQK-EbBgyPyeP_C-lbLBY3vxnGk9m9D_282jbg"
    },
    "recipient": {
        "id": "28:5baea8d1-d4ea-43a1-b101-882f4c8d9cb4",
        "name": "Imported Bot"
    },
    "entities": [
        {
            "locale": "en-US",
            "country": "US",
            "platform": "Windows",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

> [!NOTE]
> <span data-ttu-id="ed288-147">Die Nachrichtenaufteilung erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed288-147">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="ed288-148">Diese Aktivität wird von Microsoft Teams in separate Aktivitäten aufgeteilt, eine mit einer Textnachricht und die andere mit einer Anlage.</span><span class="sxs-lookup"><span data-stu-id="ed288-148">This activity is split into separate activities by Microsoft Teams, one with just a text message and the other with an attachment.</span></span> <span data-ttu-id="ed288-149">Wenn die Aktivität geteilt wird, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu aktualisieren oder zu löschen. [](~/bots/how-to/update-and-delete-bot-messages.md)</span><span class="sxs-lookup"><span data-stu-id="ed288-149">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="ed288-150">Es wird empfohlen, separate Aktivitäten zu senden, anstatt je nach Nachrichtenteilung.</span><span class="sxs-lookup"><span data-stu-id="ed288-150">It is recommended to send separate activities instead of depending on message splitting.</span></span>

<span data-ttu-id="ed288-151">Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten innerhalb der Nachricht.</span><span class="sxs-lookup"><span data-stu-id="ed288-151">Messages sent between users and bots include internal channel data within the message.</span></span> <span data-ttu-id="ed288-152">Diese Daten ermöglichen es dem Bot, ordnungsgemäß auf diesem Kanal zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="ed288-152">This data allows the bot to communicate properly on that channel.</span></span> <span data-ttu-id="ed288-153">Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.</span><span class="sxs-lookup"><span data-stu-id="ed288-153">The Bot Builder SDK allows you to modify the message structure.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="ed288-154">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="ed288-154">Teams channel data</span></span>

<span data-ttu-id="ed288-155">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="ed288-155">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="ed288-156">Optional können Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="ed288-156">Optionally, you can cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="ed288-157">Im SDK werden in der Regel wichtige Informationen aus dem Objekt `TeamsActivityHandler` `channelData` herausgeziehen, um leicht darauf zu barrierefrei zu werden.</span><span class="sxs-lookup"><span data-stu-id="ed288-157">The `TeamsActivityHandler` in the SDK typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="ed288-158">Sie können jedoch immer über das Objekt auf die ursprünglichen Daten `turnContext` zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ed288-158">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="ed288-159">Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="ed288-159">The `channelData` object is not included in messages in personal conversations, as these take place outside of a channel.</span></span>

<span data-ttu-id="ed288-160">Ein `channelData` typisches Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="ed288-160">A typical `channelData` object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="ed288-161">`eventType`: Teams-Ereignistyp, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="ed288-161">`eventType`: Teams event type passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed288-162">`tenant.id`: Azure Active Directory-Mandanten-ID, die in allen Kontexten übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="ed288-162">`tenant.id`: Azure Active Directory tenant ID passed in all contexts.</span></span>
* <span data-ttu-id="ed288-163">`team`: Wird nur in Kanalkontexten übergeben, nicht in persönlichen Chats.</span><span class="sxs-lookup"><span data-stu-id="ed288-163">`team`: Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="ed288-164">`id`: GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="ed288-164">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="ed288-165">`name`: Name des Teams, das nur in Fällen von [Teambenennungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="ed288-165">`name`: Name of the team passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed288-166">`channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="ed288-166">`channel`: Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="ed288-167">`id`: GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="ed288-167">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="ed288-168">`name`: Kanalname, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="ed288-168">`name`: Channel name passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="ed288-169">`channelData.teamsTeamId`: Veraltet.</span><span class="sxs-lookup"><span data-stu-id="ed288-169">`channelData.teamsTeamId`: Deprecated.</span></span> <span data-ttu-id="ed288-170">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="ed288-170">This property is only included for backward compatibility.</span></span>
* <span data-ttu-id="ed288-171">`channelData.teamsChannelId`: Veraltet.</span><span class="sxs-lookup"><span data-stu-id="ed288-171">`channelData.teamsChannelId`: Deprecated.</span></span> <span data-ttu-id="ed288-172">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="ed288-172">This property is only included for backward compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="ed288-173">Beispiel-channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="ed288-173">Example channelData object (channelCreated event)</span></span>

<span data-ttu-id="ed288-174">Der folgende Code zeigt ein Beispiel für ein channelData-Objekt:</span><span class="sxs-lookup"><span data-stu-id="ed288-174">The following code shows an example of channelData object:</span></span>

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

<span data-ttu-id="ed288-175">Nachrichten, die von Ihrem Bot empfangen oder an diesen gesendet werden, können verschiedene Arten von Nachrichteninhalten enthalten.</span><span class="sxs-lookup"><span data-stu-id="ed288-175">Messages received from or sent to your bot can include different types of message content.</span></span>

## <a name="message-content"></a><span data-ttu-id="ed288-176">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="ed288-176">Message content</span></span>

<span data-ttu-id="ed288-177">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="ed288-177">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="ed288-178">Benutzer können Rich-Text und Bilder an Ihren Bot senden.</span><span class="sxs-lookup"><span data-stu-id="ed288-178">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="ed288-179">Format</span><span class="sxs-lookup"><span data-stu-id="ed288-179">Format</span></span>    | <span data-ttu-id="ed288-180">Vom Benutzer zum Bot</span><span class="sxs-lookup"><span data-stu-id="ed288-180">From user to bot</span></span> | <span data-ttu-id="ed288-181">Vom Bot zum Benutzer</span><span class="sxs-lookup"><span data-stu-id="ed288-181">From bot to user</span></span> | <span data-ttu-id="ed288-182">Notes</span><span class="sxs-lookup"><span data-stu-id="ed288-182">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="ed288-183">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="ed288-183">Rich text</span></span> | <span data-ttu-id="ed288-184">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-184">✔</span></span>                | <span data-ttu-id="ed288-185">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-185">✔</span></span>                |                                                                                         |
| <span data-ttu-id="ed288-186">Bilder</span><span class="sxs-lookup"><span data-stu-id="ed288-186">Pictures</span></span>  | <span data-ttu-id="ed288-187">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-187">✔</span></span>                | <span data-ttu-id="ed288-188">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-188">✔</span></span>                | <span data-ttu-id="ed288-189">Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format.</span><span class="sxs-lookup"><span data-stu-id="ed288-189">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="ed288-190">Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ed288-190">Animated GIF is not supported.</span></span>  |
| <span data-ttu-id="ed288-191">Karten</span><span class="sxs-lookup"><span data-stu-id="ed288-191">Cards</span></span>     | <span data-ttu-id="ed288-192">✖</span><span class="sxs-lookup"><span data-stu-id="ed288-192">✖</span></span>                | <span data-ttu-id="ed288-193">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-193">✔</span></span>                | <span data-ttu-id="ed288-194">Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Den Teams-Karten.</span><span class="sxs-lookup"><span data-stu-id="ed288-194">See the [Teams card reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards.</span></span> |
| <span data-ttu-id="ed288-195">Emojis</span><span class="sxs-lookup"><span data-stu-id="ed288-195">Emojis</span></span>    | <span data-ttu-id="ed288-196">✖</span><span class="sxs-lookup"><span data-stu-id="ed288-196">✖</span></span>                | <span data-ttu-id="ed288-197">✔</span><span class="sxs-lookup"><span data-stu-id="ed288-197">✔</span></span>                | <span data-ttu-id="ed288-198">Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 zum Schmunzeln des Gesichts.</span><span class="sxs-lookup"><span data-stu-id="ed288-198">Teams currently supports emojis through UTF-16, such as U+1F600 for grinning face.</span></span> |

<span data-ttu-id="ed288-199">Sie können ihrer Nachricht auch mithilfe der -Eigenschaft Benachrichtigungen `Notification.Alert` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ed288-199">You can also add notifications to your message using the `Notification.Alert` property.</span></span>

## <a name="notifications-to-your-message"></a><span data-ttu-id="ed288-200">Benachrichtigungen an Ihre Nachricht</span><span class="sxs-lookup"><span data-stu-id="ed288-200">Notifications to your message</span></span>

<span data-ttu-id="ed288-201">Benachrichtigungen warnen Benutzer über neue Aufgaben, Erwähnungen und Kommentare.</span><span class="sxs-lookup"><span data-stu-id="ed288-201">Notifications alert users about new tasks, mentions, and comments.</span></span> <span data-ttu-id="ed288-202">Diese Warnungen stehen im Zusammenhang mit dem, wofür Benutzer arbeiten oder was sie sehen müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen.</span><span class="sxs-lookup"><span data-stu-id="ed288-202">These alerts are related to what users are working on or what they must look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="ed288-203">Damit Benachrichtigungen von Ihrer Botnachricht ausgelöst werden, legen Sie die `TeamsChannelData` `Notification.Alert` Objects-Eigenschaft auf true.</span><span class="sxs-lookup"><span data-stu-id="ed288-203">For notifications to trigger from your bot message, set the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="ed288-204">Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="ed288-204">Whether or not a notification is raised depends on the individual user's Teams settings and you cannot override these settings.</span></span> <span data-ttu-id="ed288-205">Der Benachrichtigungstyp ist entweder ein Banner oder ein Banner und eine E-Mail.</span><span class="sxs-lookup"><span data-stu-id="ed288-205">The notification type is either a banner or both a banner and an email.</span></span>

<span data-ttu-id="ed288-206">Der folgende Code zeigt ein Beispiel für das Hinzufügen von Benachrichtigungen zu Ihrer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="ed288-206">The following code shows an example of adding notifications to your message:</span></span>

# <a name="c"></a>[<span data-ttu-id="ed288-207">C#</span><span class="sxs-lookup"><span data-stu-id="ed288-207">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[<span data-ttu-id="ed288-208">TypeScript</span><span class="sxs-lookup"><span data-stu-id="ed288-208">TypeScript</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="ed288-209">Python</span><span class="sxs-lookup"><span data-stu-id="ed288-209">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="ed288-210">Json</span><span class="sxs-lookup"><span data-stu-id="ed288-210">JSON</span></span>](#tab/json)

```json
{
  "type": "message",
  "timestamp": "2017-04-24T21:46:00.9663655Z",
  "localTimestamp": "2017-04-24T14:46:00.9663655-07:00",
  "serviceUrl": "https://callback.com",
  "channelId": "msteams",
  "from": {
    "id": "28:e4fda94a-4b80-40eb-9bf0-6314491bc793",
    "name": "The bot"
  },
  "conversation": {
    "id": "a:1pL6i0oY3C0K8oAj8"
  },
  "recipient": {
    "id": "29:1rsVJmSSFMScF0YFyCXpvNWlo",
    "name": "User"
  },
  "text": "John Phillips assigned you a weekly todo",
  "summary": "Don't forget to meet with Marketing next week",
  "channelData": {
    "notification": {
      "alert": true
    }
  },
  "replyToId": "1493070356924"
}
```

---

<span data-ttu-id="ed288-211">Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ed288-211">To enhance your message, you can include pictures as attachments to that message.</span></span>

## <a name="picture-messages"></a><span data-ttu-id="ed288-212">Bildnachrichten</span><span class="sxs-lookup"><span data-stu-id="ed288-212">Picture messages</span></span>

<span data-ttu-id="ed288-213">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="ed288-213">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="ed288-214">Weitere Informationen zu Anlagen finden Sie in [der Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span><span class="sxs-lookup"><span data-stu-id="ed288-214">For more information on attachments, see [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="ed288-215">Bilder können im PNG-, JPEG- oder GIF-Format mindestens 1024×1024 und 1 MB groß sein.</span><span class="sxs-lookup"><span data-stu-id="ed288-215">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="ed288-216">Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ed288-216">Animated GIF is not supported.</span></span>

<span data-ttu-id="ed288-217">Geben Sie die Höhe und Breite der einzelnen Bilder mithilfe von XML an.</span><span class="sxs-lookup"><span data-stu-id="ed288-217">Specify the height and width of each image by using XML.</span></span> <span data-ttu-id="ed288-218">In markdown ist die Bildgröße standardmäßig auf 256×256 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ed288-218">In markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="ed288-219">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ed288-219">For example:</span></span>

* <span data-ttu-id="ed288-220">Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .</span><span class="sxs-lookup"><span data-stu-id="ed288-220">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.</span></span>
* <span data-ttu-id="ed288-221">Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)` .</span><span class="sxs-lookup"><span data-stu-id="ed288-221">Do not use: `![Duck on a rock](http://aka.ms/Fo983c)`.</span></span>

<span data-ttu-id="ed288-222">Ein Unterhaltungsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="ed288-222">A conversational bot can include adaptive cards that simplify business workflows.</span></span> <span data-ttu-id="ed288-223">Adaptive Karten bieten umfangreiche anpassbare Text-, Sprach-, Bild-, Schaltflächen- und Eingabefelder.</span><span class="sxs-lookup"><span data-stu-id="ed288-223">Adaptive cards offer rich customizable text, speech, images, buttons, and input fields.</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="ed288-224">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="ed288-224">Adaptive cards</span></span>

<span data-ttu-id="ed288-225">Adaptive Karten können in einem Bot verfasst und in mehreren Apps wie Teams, Ihrer Website und so weiter angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ed288-225">Adaptive cards can be authored in a bot and shown in multiple apps such as Teams, your website, and so on.</span></span> <span data-ttu-id="ed288-226">Weitere Informationen finden Sie unter [Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="ed288-226">For more information, see [adaptive cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>

<span data-ttu-id="ed288-227">Der folgende Code zeigt ein Beispiel für das Senden einer einfachen adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="ed288-227">The following code shows an example of sending a simple adaptive card:</span></span>

```json
{
    "type": "AdaptiveCard",
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.5",
    "body": [
    {
        "items": [
        {
            "size": "large",
            "text": " Simple Adaptivecard Example with a Textbox",
            "type": "TextBlock",
            "weight": "bolder",
            "wrap": true
        },
        ],
        "spacing": "extraLarge",
        "type": "Container",
        "verticalContentAlignment": "center"
    }
    ]
}
```

<span data-ttu-id="ed288-228">Weitere Informationen zu Karten und Karten in Bots finden Sie in [der Kartendokumentation](~/task-modules-and-cards/what-are-cards.md).</span><span class="sxs-lookup"><span data-stu-id="ed288-228">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="ed288-229">Der nächste Abschnitt enthält Statuscodeantworten für Fehler, die von Bot-APIs generiert werden.</span><span class="sxs-lookup"><span data-stu-id="ed288-229">The next section provides status code responses for errors generated from Bot APIs.</span></span>

## <a name="status-code-responses"></a><span data-ttu-id="ed288-230">Statuscodeantworten</span><span class="sxs-lookup"><span data-stu-id="ed288-230">Status code responses</span></span>

<span data-ttu-id="ed288-231">Im Folgenden finden Sie die Statuscodes und deren Fehlercode- und Meldungswerte:</span><span class="sxs-lookup"><span data-stu-id="ed288-231">Following are the status codes and their error code and message values:</span></span>

| <span data-ttu-id="ed288-232">Statuscode</span><span class="sxs-lookup"><span data-stu-id="ed288-232">Status code</span></span> | <span data-ttu-id="ed288-233">Fehlercode und Nachrichtenwerte</span><span class="sxs-lookup"><span data-stu-id="ed288-233">Error code and message values</span></span> | <span data-ttu-id="ed288-234">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed288-234">Description</span></span> |
|----------------|-----------------|-----------------|
| <span data-ttu-id="ed288-235">403</span><span class="sxs-lookup"><span data-stu-id="ed288-235">403</span></span> | <span data-ttu-id="ed288-236">**Code**: `ConversationBlockedByUser`</span><span class="sxs-lookup"><span data-stu-id="ed288-236">**Code**: `ConversationBlockedByUser`</span></span> <br/> <span data-ttu-id="ed288-237">**Meldung:**"Benutzer hat die Unterhaltung mit dem Bot blockiert."</span><span class="sxs-lookup"><span data-stu-id="ed288-237">**Message**: "User blocked the conversation with the bot."</span></span> | <span data-ttu-id="ed288-238">Der Benutzer hat den Bot im 1:1-Chat oder in einem Kanal über Moderationseinstellungen blockiert.</span><span class="sxs-lookup"><span data-stu-id="ed288-238">User blocked the bot in 1:1 chat or a channel through moderation settings.</span></span> |
| <span data-ttu-id="ed288-239">403</span><span class="sxs-lookup"><span data-stu-id="ed288-239">403</span></span> | <span data-ttu-id="ed288-240">**Code**: `BotNotInConversationRoster`</span><span class="sxs-lookup"><span data-stu-id="ed288-240">**Code**: `BotNotInConversationRoster`</span></span> <br/> <span data-ttu-id="ed288-241">**Meldung:**"Der Bot ist nicht Teil des Unterhaltungsplans."</span><span class="sxs-lookup"><span data-stu-id="ed288-241">**Message**: "The bot is not part of the conversation roster."</span></span> | <span data-ttu-id="ed288-242">Der Bot ist nicht Teil der Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="ed288-242">The bot is not part of the conversation.</span></span> |
| <span data-ttu-id="ed288-243">403</span><span class="sxs-lookup"><span data-stu-id="ed288-243">403</span></span> | <span data-ttu-id="ed288-244">**Code**: `BotDisabledByAdmin`</span><span class="sxs-lookup"><span data-stu-id="ed288-244">**Code**: `BotDisabledByAdmin`</span></span> <br/> <span data-ttu-id="ed288-245">**Meldung:**"Der Mandantenadministrator hat diesen Bot deaktiviert."</span><span class="sxs-lookup"><span data-stu-id="ed288-245">**Message**: "The tenant admin disabled this bot."</span></span> | <span data-ttu-id="ed288-246">Der Mandant hat den Bot blockiert.</span><span class="sxs-lookup"><span data-stu-id="ed288-246">Tenant blocked the bot.</span></span> |
| <span data-ttu-id="ed288-247">401</span><span class="sxs-lookup"><span data-stu-id="ed288-247">401</span></span> | <span data-ttu-id="ed288-248">**Code**: `BotNotRegistered`</span><span class="sxs-lookup"><span data-stu-id="ed288-248">**Code**: `BotNotRegistered`</span></span> <br/> <span data-ttu-id="ed288-249">**Meldung:**"Es wurde keine Registrierung für diesen Bot gefunden."</span><span class="sxs-lookup"><span data-stu-id="ed288-249">**Message**: “No registration found for this bot.”</span></span> | <span data-ttu-id="ed288-250">Die Registrierung für diesen Bot wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed288-250">The registration for this bot was not found.</span></span> |
| <span data-ttu-id="ed288-251">412</span><span class="sxs-lookup"><span data-stu-id="ed288-251">412</span></span> | <span data-ttu-id="ed288-252">**Code**: `PreconditionFailed`</span><span class="sxs-lookup"><span data-stu-id="ed288-252">**Code**: `PreconditionFailed`</span></span> <br/> <span data-ttu-id="ed288-253">**Meldung:**"Vorbedingung fehlgeschlagen, versuchen Sie es bitte erneut."</span><span class="sxs-lookup"><span data-stu-id="ed288-253">**Message**: “Precondition failed, please try again.”</span></span> | <span data-ttu-id="ed288-254">Eine Voraussetzung für eine unserer Abhängigkeiten ist aufgrund mehrerer gleichzeitiger Vorgänge in derselben Unterhaltung fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="ed288-254">A precondition failed on one of our dependencies due to multiple concurrent operations on the same conversation.</span></span> |
| <span data-ttu-id="ed288-255">404</span><span class="sxs-lookup"><span data-stu-id="ed288-255">404</span></span> | <span data-ttu-id="ed288-256">**Code**: `ConversationNotFound`</span><span class="sxs-lookup"><span data-stu-id="ed288-256">**Code**: `ConversationNotFound`</span></span> <br/> <span data-ttu-id="ed288-257">**Meldung**: "Unterhaltung nicht gefunden".</span><span class="sxs-lookup"><span data-stu-id="ed288-257">**Message**: “Conversation not found.”</span></span> | <span data-ttu-id="ed288-258">Die Unterhaltung wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed288-258">The conversation was not found.</span></span> |
| <span data-ttu-id="ed288-259">413</span><span class="sxs-lookup"><span data-stu-id="ed288-259">413</span></span> | <span data-ttu-id="ed288-260">**Code**: `MessageSizeTooBig`</span><span class="sxs-lookup"><span data-stu-id="ed288-260">**Code**: `MessageSizeTooBig`</span></span> <br/> <span data-ttu-id="ed288-261">**Meldung:**"Nachrichtengröße zu groß".</span><span class="sxs-lookup"><span data-stu-id="ed288-261">**Message**: “Message size too large.”</span></span> | <span data-ttu-id="ed288-262">Die Größe der eingehenden Anforderung war zu groß.</span><span class="sxs-lookup"><span data-stu-id="ed288-262">The size on the incoming request was too large.</span></span> |
| <span data-ttu-id="ed288-263">429</span><span class="sxs-lookup"><span data-stu-id="ed288-263">429</span></span> | <span data-ttu-id="ed288-264">**Code**: `Throttled`</span><span class="sxs-lookup"><span data-stu-id="ed288-264">**Code**: `Throttled`</span></span> <br/> <span data-ttu-id="ed288-265">**Meldung**: "Zu viele Anforderungen".</span><span class="sxs-lookup"><span data-stu-id="ed288-265">**Message**: “Too many requests.”</span></span> <span data-ttu-id="ed288-266">Gibt außerdem zurück, wann nach dem Versuch erneut geversucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ed288-266">Also returns when to retry after.</span></span> | <span data-ttu-id="ed288-267">Zu viele Anforderungen wurden vom Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="ed288-267">Too many requests were sent by the bot.</span></span> <span data-ttu-id="ed288-268">Weitere Informationen finden Sie unter [Rate limit](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="ed288-268">For more information, see [rate limit](~/bots/how-to/rate-limit.md).</span></span> |

<span data-ttu-id="ed288-269">Im nächsten Abschnitt wird ein einfaches Codebeispiel veranschaulicht, das den grundlegenden Unterhaltungsfluss in eine Teams-Anwendung integriert.</span><span class="sxs-lookup"><span data-stu-id="ed288-269">The next section illustrates a simple code sample that incorporates basic conversational flow into a Teams application.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ed288-270">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ed288-270">Code sample</span></span>

<span data-ttu-id="ed288-271">Im Folgenden finden Sie die Codebeispiele für den Teams-Unterhaltungsbot:</span><span class="sxs-lookup"><span data-stu-id="ed288-271">Following are the code samples for Teams conversation bot:</span></span>

|<span data-ttu-id="ed288-272">Beispielname</span><span class="sxs-lookup"><span data-stu-id="ed288-272">Sample name</span></span> | <span data-ttu-id="ed288-273">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed288-273">Description</span></span> | <span data-ttu-id="ed288-274">. NETCore</span><span class="sxs-lookup"><span data-stu-id="ed288-274">.NETCore</span></span> | <span data-ttu-id="ed288-275">Node.js</span><span class="sxs-lookup"><span data-stu-id="ed288-275">Node.js</span></span> | <span data-ttu-id="ed288-276">Python</span><span class="sxs-lookup"><span data-stu-id="ed288-276">Python</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="ed288-277">Teams-Unterhaltungsbot</span><span class="sxs-lookup"><span data-stu-id="ed288-277">Teams conversation bot</span></span> | <span data-ttu-id="ed288-278">Nachrichten- und Unterhaltungsereignisbehandlung.</span><span class="sxs-lookup"><span data-stu-id="ed288-278">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="ed288-279">View</span><span class="sxs-lookup"><span data-stu-id="ed288-279">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="ed288-280">View</span><span class="sxs-lookup"><span data-stu-id="ed288-280">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="ed288-281">View</span><span class="sxs-lookup"><span data-stu-id="ed288-281">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a><span data-ttu-id="ed288-282">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ed288-282">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed288-283">Versenden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="ed288-283">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ed288-284">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="ed288-284">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a><span data-ttu-id="ed288-285">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ed288-285">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed288-286">Bot-Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="ed288-286">Bot command menus</span></span>](~/bots/how-to/create-a-bot-commands-menu.md)
