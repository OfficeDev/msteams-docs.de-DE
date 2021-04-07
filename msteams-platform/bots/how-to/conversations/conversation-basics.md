---
title: Grundlagen zu Unterhaltungen
description: Beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: 193a93dbf775389383e0385207fa4112440bffe5
ms.sourcegitcommit: 82bda0599ba2676ab9348c2f4284f73c7dad0838
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596674"
---
# <a name="conversation-basics"></a><span data-ttu-id="765f8-103">Grundlagen zu Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="765f8-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="765f8-104">Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Microsoft Teams-Bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="765f8-104">A conversation is a series of messages sent between your Microsoft Teams bot and one or more users.</span></span> <span data-ttu-id="765f8-105">Es gibt drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:</span><span class="sxs-lookup"><span data-stu-id="765f8-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="765f8-106">Unterhaltungstyp</span><span class="sxs-lookup"><span data-stu-id="765f8-106">Conversation type</span></span> | <span data-ttu-id="765f8-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="765f8-107">Description</span></span> |
| ------- | ----------- |
| `channel` | <span data-ttu-id="765f8-108">Dieser Unterhaltungstyp ist für alle Mitglieder des Kanals sichtbar.</span><span class="sxs-lookup"><span data-stu-id="765f8-108">This conversation type is visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="765f8-109">Dieser Unterhaltungstyp enthält Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="765f8-109">This conversation type includes conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="765f8-110">Dieser Unterhaltungstyp umfasst Chats zwischen einem Bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="765f8-110">This conversation type includes chat between a bot and two or more users.</span></span> <span data-ttu-id="765f8-111">Es aktiviert ihren Bot auch in Besprechungschats.</span><span class="sxs-lookup"><span data-stu-id="765f8-111">It also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="765f8-112">Ein Bot verhält sich abhängig von der Unterhaltung, an der er beteiligt ist, unterschiedlich:</span><span class="sxs-lookup"><span data-stu-id="765f8-112">A bot behaves differently depending on the conversation it is involved in:</span></span>

* <span data-ttu-id="765f8-113">Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.</span><span class="sxs-lookup"><span data-stu-id="765f8-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="765f8-114">Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung.</span><span class="sxs-lookup"><span data-stu-id="765f8-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="765f8-115">Alle nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="765f8-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="765f8-116">Damit der Bot in einer bestimmten Unterhaltung oder einem bestimmten Bereich funktioniert, fügen Sie diesem Bereich unterstützung im [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="765f8-116">For the bot to work in a particular conversation or scope, add support to that scope in the [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="messages-in-bot-conversations"></a><span data-ttu-id="765f8-117">Nachrichten in Botunterhaltungen</span><span class="sxs-lookup"><span data-stu-id="765f8-117">Messages in bot conversations</span></span>

<span data-ttu-id="765f8-118">Jede Nachricht in einer Unterhaltung ist ein `Activity` Objekt vom Typ `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="765f8-118">Each message in a conversation is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="765f8-119">Wenn ein Benutzer eine Nachricht sendet, sendet Teams die Nachricht an Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="765f8-119">When a user sends a message, Teams posts the message to your bot.</span></span> <span data-ttu-id="765f8-120">Teams sendet ein JSON-Objekt an den Messagingendpunkt Ihres Bots.</span><span class="sxs-lookup"><span data-stu-id="765f8-120">Teams sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="765f8-121">Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen, und antwortet entsprechend.</span><span class="sxs-lookup"><span data-stu-id="765f8-121">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="765f8-122">Grundlegende Unterhaltungen werden über den Bot Framework-Connector, eine einzelne REST-API, behandelt.</span><span class="sxs-lookup"><span data-stu-id="765f8-122">Basic conversations are handled through the Bot Framework connector, a single REST API.</span></span> <span data-ttu-id="765f8-123">Mit dieser API kann Ihr Bot mit Teams und anderen Kanälen kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="765f8-123">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="765f8-124">Das Bot Builder SDK bietet Folgendes:</span><span class="sxs-lookup"><span data-stu-id="765f8-124">The Bot Builder SDK provides the following:</span></span>

* <span data-ttu-id="765f8-125">Einfacher Zugriff auf den Bot Framework-Connector.</span><span class="sxs-lookup"><span data-stu-id="765f8-125">Easy access to the Bot Framework connector.</span></span>
* <span data-ttu-id="765f8-126">Zusätzliche Funktionalität zum Verwalten des Unterhaltungsflusses und -zustands.</span><span class="sxs-lookup"><span data-stu-id="765f8-126">Additional functionality to manage conversation flow and state.</span></span>
* <span data-ttu-id="765f8-127">Einfache Möglichkeiten zum Integrieren von kognitiven Diensten wie der Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP).</span><span class="sxs-lookup"><span data-stu-id="765f8-127">Simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

<span data-ttu-id="765f8-128">Ihr Bot empfängt Nachrichten von Teams mithilfe der Eigenschaft und sendet einzelne oder `Text` mehrere Nachrichtenantworten an die Benutzer.</span><span class="sxs-lookup"><span data-stu-id="765f8-128">Your bot receives messages from Teams using the `Text` property and it sends single or multiple message responses to the users.</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="765f8-129">Empfangen einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="765f8-129">Receive a message</span></span>

<span data-ttu-id="765f8-130">Um eine Textnachricht zu empfangen, verwenden Sie die `Text`-Eigenschaft des `Activity`-Objekts.</span><span class="sxs-lookup"><span data-stu-id="765f8-130">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="765f8-131">Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="765f8-131">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="765f8-132">Der folgende Code zeigt ein Beispiel für den Empfang einer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="765f8-132">The following code shows an example of receiving a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="765f8-133">C#</span><span class="sxs-lookup"><span data-stu-id="765f8-133">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="765f8-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="765f8-134">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="765f8-135">Python</span><span class="sxs-lookup"><span data-stu-id="765f8-135">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="765f8-136">Json</span><span class="sxs-lookup"><span data-stu-id="765f8-136">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="765f8-137">Senden einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="765f8-137">Send a message</span></span>

<span data-ttu-id="765f8-138">Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten.</span><span class="sxs-lookup"><span data-stu-id="765f8-138">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="765f8-139">Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden.</span><span class="sxs-lookup"><span data-stu-id="765f8-139">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="765f8-140">Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten gleichzeitig zu senden.</span><span class="sxs-lookup"><span data-stu-id="765f8-140">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="765f8-141">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn ein Benutzer einer Unterhaltung hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="765f8-141">The following code shows an example of sending a message when a user is added to a conversation:</span></span>

<span data-ttu-id="765f8-142">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="765f8-142">The following code shows an example of sending a message:</span></span>

# <a name="c"></a>[<span data-ttu-id="765f8-143">C#</span><span class="sxs-lookup"><span data-stu-id="765f8-143">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[<span data-ttu-id="765f8-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="765f8-144">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="765f8-145">Python</span><span class="sxs-lookup"><span data-stu-id="765f8-145">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="765f8-146">Json</span><span class="sxs-lookup"><span data-stu-id="765f8-146">JSON</span></span>](#tab/json)

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
> <span data-ttu-id="765f8-147">Die Nachrichtenaufteilung erfolgt, wenn eine Textnachricht und eine Anlage in derselben Aktivitätsnutzlast gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="765f8-147">Message splitting occurs when a text message and an attachment are sent in the same activity payload.</span></span> <span data-ttu-id="765f8-148">Diese Aktivität wird von Microsoft Teams in separate Aktivitäten aufgeteilt, eine mit einer Textnachricht und die andere mit einer Anlage.</span><span class="sxs-lookup"><span data-stu-id="765f8-148">This activity is split into separate activities by Microsoft Teams, one with just a text message and the other with an attachment.</span></span> <span data-ttu-id="765f8-149">Wenn die Aktivität geteilt wird, erhalten Sie nicht die Nachrichten-ID als Antwort, die verwendet wird, um die Nachricht proaktiv zu aktualisieren oder zu löschen. [](~/bots/how-to/update-and-delete-bot-messages.md)</span><span class="sxs-lookup"><span data-stu-id="765f8-149">As the activity is split, you do not receive the message ID in response, which is used to [update or delete](~/bots/how-to/update-and-delete-bot-messages.md) the message proactively.</span></span> <span data-ttu-id="765f8-150">Es wird empfohlen, separate Aktivitäten zu senden, anstatt je nach Nachrichtenteilung.</span><span class="sxs-lookup"><span data-stu-id="765f8-150">It is recommended to send separate activities instead of depending on message splitting.</span></span>

<span data-ttu-id="765f8-151">Nachrichten, die zwischen Benutzern und Bots gesendet werden, enthalten interne Kanaldaten innerhalb der Nachricht.</span><span class="sxs-lookup"><span data-stu-id="765f8-151">Messages sent between users and bots include internal channel data within the message.</span></span> <span data-ttu-id="765f8-152">Diese Daten ermöglichen es dem Bot, ordnungsgemäß auf diesem Kanal zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="765f8-152">This data allows the bot to communicate properly on that channel.</span></span> <span data-ttu-id="765f8-153">Mit dem Bot Builder SDK können Sie die Nachrichtenstruktur ändern.</span><span class="sxs-lookup"><span data-stu-id="765f8-153">The Bot Builder SDK allows you to modify the message structure.</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="765f8-154">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="765f8-154">Teams channel data</span></span>

<span data-ttu-id="765f8-155">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="765f8-155">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="765f8-156">Optional können Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="765f8-156">Optionally, you can cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="765f8-157">Im SDK werden in der Regel wichtige Informationen aus dem Objekt `TeamsActivityHandler` `channelData` herausgeziehen, um leicht darauf zu barrierefrei zu werden.</span><span class="sxs-lookup"><span data-stu-id="765f8-157">The `TeamsActivityHandler` in the SDK typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="765f8-158">Sie können jedoch immer über das Objekt auf die ursprünglichen Daten `turnContext` zugreifen.</span><span class="sxs-lookup"><span data-stu-id="765f8-158">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="765f8-159">Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="765f8-159">The `channelData` object is not included in messages in personal conversations, as these take place outside of a channel.</span></span>

<span data-ttu-id="765f8-160">Ein `channelData` typisches Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="765f8-160">A typical `channelData` object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="765f8-161">`eventType`: Teams-Ereignistyp, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="765f8-161">`eventType`: Teams event type passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="765f8-162">`tenant.id`: Azure Active Directory-Mandanten-ID, die in allen Kontexten übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="765f8-162">`tenant.id`: Azure Active Directory tenant ID passed in all contexts.</span></span>
* <span data-ttu-id="765f8-163">`team`: Wird nur in Kanalkontexten übergeben, nicht in persönlichen Chats.</span><span class="sxs-lookup"><span data-stu-id="765f8-163">`team`: Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="765f8-164">`id`: GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="765f8-164">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="765f8-165">`name`: Name des Teams, das nur in Fällen von [Teambenennungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="765f8-165">`name`: Name of the team passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="765f8-166">`channel`: Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="765f8-166">`channel`: Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="765f8-167">`id`: GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="765f8-167">`id`: GUID for the channel.</span></span>
  * <span data-ttu-id="765f8-168">`name`: Kanalname, der nur bei [Kanaländerungsereignissen übergeben wird.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="765f8-168">`name`: Channel name passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="765f8-169">`channelData.teamsTeamId`: Veraltet.</span><span class="sxs-lookup"><span data-stu-id="765f8-169">`channelData.teamsTeamId`: Deprecated.</span></span> <span data-ttu-id="765f8-170">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="765f8-170">This property is only included for backward compatibility.</span></span>
* <span data-ttu-id="765f8-171">`channelData.teamsChannelId`: Veraltet.</span><span class="sxs-lookup"><span data-stu-id="765f8-171">`channelData.teamsChannelId`: Deprecated.</span></span> <span data-ttu-id="765f8-172">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="765f8-172">This property is only included for backward compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="765f8-173">Beispiel-channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="765f8-173">Example channelData object (channelCreated event)</span></span>

<span data-ttu-id="765f8-174">Der folgende Code zeigt ein Beispiel für ein channelData-Objekt:</span><span class="sxs-lookup"><span data-stu-id="765f8-174">The following code shows an example of channelData object:</span></span>

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

<span data-ttu-id="765f8-175">Nachrichten, die von Ihrem Bot empfangen oder an diesen gesendet werden, können verschiedene Arten von Nachrichteninhalten enthalten.</span><span class="sxs-lookup"><span data-stu-id="765f8-175">Messages received from or sent to your bot can include different types of message content.</span></span>

## <a name="message-content"></a><span data-ttu-id="765f8-176">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="765f8-176">Message content</span></span>

<span data-ttu-id="765f8-177">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="765f8-177">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="765f8-178">Benutzer können Rich-Text und Bilder an Ihren Bot senden.</span><span class="sxs-lookup"><span data-stu-id="765f8-178">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="765f8-179">Format</span><span class="sxs-lookup"><span data-stu-id="765f8-179">Format</span></span>    | <span data-ttu-id="765f8-180">Vom Benutzer zum Bot</span><span class="sxs-lookup"><span data-stu-id="765f8-180">From user to bot</span></span> | <span data-ttu-id="765f8-181">Vom Bot zum Benutzer</span><span class="sxs-lookup"><span data-stu-id="765f8-181">From bot to user</span></span> | <span data-ttu-id="765f8-182">Notes</span><span class="sxs-lookup"><span data-stu-id="765f8-182">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="765f8-183">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="765f8-183">Rich text</span></span> | <span data-ttu-id="765f8-184">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-184">✔</span></span>                | <span data-ttu-id="765f8-185">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-185">✔</span></span>                |                                                                                         |
| <span data-ttu-id="765f8-186">Bilder</span><span class="sxs-lookup"><span data-stu-id="765f8-186">Pictures</span></span>  | <span data-ttu-id="765f8-187">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-187">✔</span></span>                | <span data-ttu-id="765f8-188">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-188">✔</span></span>                | <span data-ttu-id="765f8-189">Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format.</span><span class="sxs-lookup"><span data-stu-id="765f8-189">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="765f8-190">Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="765f8-190">Animated GIF is not supported.</span></span>  |
| <span data-ttu-id="765f8-191">Karten</span><span class="sxs-lookup"><span data-stu-id="765f8-191">Cards</span></span>     | <span data-ttu-id="765f8-192">✖</span><span class="sxs-lookup"><span data-stu-id="765f8-192">✖</span></span>                | <span data-ttu-id="765f8-193">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-193">✔</span></span>                | <span data-ttu-id="765f8-194">Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Den Teams-Karten.</span><span class="sxs-lookup"><span data-stu-id="765f8-194">See the [Teams card reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards.</span></span> |
| <span data-ttu-id="765f8-195">Emojis</span><span class="sxs-lookup"><span data-stu-id="765f8-195">Emojis</span></span>    | <span data-ttu-id="765f8-196">✖</span><span class="sxs-lookup"><span data-stu-id="765f8-196">✖</span></span>                | <span data-ttu-id="765f8-197">✔</span><span class="sxs-lookup"><span data-stu-id="765f8-197">✔</span></span>                | <span data-ttu-id="765f8-198">Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 zum Schmunzeln des Gesichts.</span><span class="sxs-lookup"><span data-stu-id="765f8-198">Teams currently supports emojis through UTF-16, such as U+1F600 for grinning face.</span></span> |

<span data-ttu-id="765f8-199">Sie können ihrer Nachricht auch mithilfe der -Eigenschaft Benachrichtigungen `Notification.Alert` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="765f8-199">You can also add notifications to your message using the `Notification.Alert` property.</span></span>

## <a name="notifications-to-your-message"></a><span data-ttu-id="765f8-200">Benachrichtigungen an Ihre Nachricht</span><span class="sxs-lookup"><span data-stu-id="765f8-200">Notifications to your message</span></span>

<span data-ttu-id="765f8-201">Benachrichtigungen warnen Benutzer über neue Aufgaben, Erwähnungen und Kommentare.</span><span class="sxs-lookup"><span data-stu-id="765f8-201">Notifications alert users about new tasks, mentions, and comments.</span></span> <span data-ttu-id="765f8-202">Diese Warnungen stehen im Zusammenhang mit dem, wofür Benutzer arbeiten oder was sie sehen müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen.</span><span class="sxs-lookup"><span data-stu-id="765f8-202">These alerts are related to what users are working on or what they must look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="765f8-203">Damit Benachrichtigungen von Ihrer Botnachricht ausgelöst werden, legen Sie die `TeamsChannelData` `Notification.Alert` Objects-Eigenschaft auf true.</span><span class="sxs-lookup"><span data-stu-id="765f8-203">For notifications to trigger from your bot message, set the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="765f8-204">Ob eine Benachrichtigung ausgelöst wird, hängt von den Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="765f8-204">Whether or not a notification is raised depends on the individual user's Teams settings and you cannot override these settings.</span></span> <span data-ttu-id="765f8-205">Der Benachrichtigungstyp ist entweder ein Banner oder ein Banner und eine E-Mail.</span><span class="sxs-lookup"><span data-stu-id="765f8-205">The notification type is either a banner or both a banner and an email.</span></span>

> [!NOTE]
> <span data-ttu-id="765f8-206">Im **Feld Zusammenfassung** wird ein beliebiger Text des Benutzers als Benachrichtigung im Feed angezeigt.</span><span class="sxs-lookup"><span data-stu-id="765f8-206">The **Summary** field displays any text from the user as a notification message in the feed.</span></span>

<span data-ttu-id="765f8-207">Der folgende Code zeigt ein Beispiel für das Hinzufügen von Benachrichtigungen zu Ihrer Nachricht:</span><span class="sxs-lookup"><span data-stu-id="765f8-207">The following code shows an example of adding notifications to your message:</span></span>

# <a name="c"></a>[<span data-ttu-id="765f8-208">C#</span><span class="sxs-lookup"><span data-stu-id="765f8-208">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[<span data-ttu-id="765f8-209">TypeScript</span><span class="sxs-lookup"><span data-stu-id="765f8-209">TypeScript</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="765f8-210">Python</span><span class="sxs-lookup"><span data-stu-id="765f8-210">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="765f8-211">Json</span><span class="sxs-lookup"><span data-stu-id="765f8-211">JSON</span></span>](#tab/json)

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

<span data-ttu-id="765f8-212">Um Ihre Nachricht zu verbessern, können Sie Bilder als Anlagen zu dieser Nachricht hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="765f8-212">To enhance your message, you can include pictures as attachments to that message.</span></span>

## <a name="picture-messages"></a><span data-ttu-id="765f8-213">Bildnachrichten</span><span class="sxs-lookup"><span data-stu-id="765f8-213">Picture messages</span></span>

<span data-ttu-id="765f8-214">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="765f8-214">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="765f8-215">Weitere Informationen zu Anlagen finden Sie in [der Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span><span class="sxs-lookup"><span data-stu-id="765f8-215">For more information on attachments, see [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="765f8-216">Bilder können im PNG-, JPEG- oder GIF-Format mindestens 1024×1024 und 1 MB groß sein.</span><span class="sxs-lookup"><span data-stu-id="765f8-216">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="765f8-217">Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="765f8-217">Animated GIF is not supported.</span></span>

<span data-ttu-id="765f8-218">Geben Sie die Höhe und Breite der einzelnen Bilder mithilfe von XML an.</span><span class="sxs-lookup"><span data-stu-id="765f8-218">Specify the height and width of each image by using XML.</span></span> <span data-ttu-id="765f8-219">In markdown ist die Bildgröße standardmäßig auf 256×256 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="765f8-219">In markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="765f8-220">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="765f8-220">For example:</span></span>

* <span data-ttu-id="765f8-221">Verwenden Sie: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .</span><span class="sxs-lookup"><span data-stu-id="765f8-221">Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.</span></span>
* <span data-ttu-id="765f8-222">Verwenden Sie nicht: `![Duck on a rock](http://aka.ms/Fo983c)` .</span><span class="sxs-lookup"><span data-stu-id="765f8-222">Do not use: `![Duck on a rock](http://aka.ms/Fo983c)`.</span></span>

<span data-ttu-id="765f8-223">Ein Unterhaltungsbot kann adaptive Karten enthalten, die Geschäftsworkflows vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="765f8-223">A conversational bot can include adaptive cards that simplify business workflows.</span></span> <span data-ttu-id="765f8-224">Adaptive Karten bieten umfangreiche anpassbare Text-, Sprach-, Bild-, Schaltflächen- und Eingabefelder.</span><span class="sxs-lookup"><span data-stu-id="765f8-224">Adaptive cards offer rich customizable text, speech, images, buttons, and input fields.</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="765f8-225">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="765f8-225">Adaptive cards</span></span>

<span data-ttu-id="765f8-226">Adaptive Karten können in einem Bot verfasst und in mehreren Apps wie Teams, Ihrer Website und so weiter angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="765f8-226">Adaptive cards can be authored in a bot and shown in multiple apps such as Teams, your website, and so on.</span></span> <span data-ttu-id="765f8-227">Weitere Informationen finden Sie unter [Adaptive Karten](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="765f8-227">For more information, see [adaptive cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>

<span data-ttu-id="765f8-228">Der folgende Code zeigt ein Beispiel für das Senden einer einfachen adaptiven Karte:</span><span class="sxs-lookup"><span data-stu-id="765f8-228">The following code shows an example of sending a simple adaptive card:</span></span>

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

<span data-ttu-id="765f8-229">Weitere Informationen zu Karten und Karten in Bots finden Sie in [der Kartendokumentation](~/task-modules-and-cards/what-are-cards.md).</span><span class="sxs-lookup"><span data-stu-id="765f8-229">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="765f8-230">Der nächste Abschnitt enthält Statuscodeantworten für Fehler, die von Bot-APIs generiert werden.</span><span class="sxs-lookup"><span data-stu-id="765f8-230">The next section provides status code responses for errors generated from Bot APIs.</span></span>

## <a name="status-code-responses"></a><span data-ttu-id="765f8-231">Statuscodeantworten</span><span class="sxs-lookup"><span data-stu-id="765f8-231">Status code responses</span></span>

<span data-ttu-id="765f8-232">Im Folgenden finden Sie die Statuscodes und deren Fehlercode- und Meldungswerte:</span><span class="sxs-lookup"><span data-stu-id="765f8-232">Following are the status codes and their error code and message values:</span></span>

| <span data-ttu-id="765f8-233">Statuscode</span><span class="sxs-lookup"><span data-stu-id="765f8-233">Status code</span></span> | <span data-ttu-id="765f8-234">Fehlercode und Nachrichtenwerte</span><span class="sxs-lookup"><span data-stu-id="765f8-234">Error code and message values</span></span> | <span data-ttu-id="765f8-235">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="765f8-235">Description</span></span> |
|----------------|-----------------|-----------------|
| <span data-ttu-id="765f8-236">403</span><span class="sxs-lookup"><span data-stu-id="765f8-236">403</span></span> | <span data-ttu-id="765f8-237">**Code**: `ConversationBlockedByUser`</span><span class="sxs-lookup"><span data-stu-id="765f8-237">**Code**: `ConversationBlockedByUser`</span></span> <br/> <span data-ttu-id="765f8-238">**Meldung:**"Benutzer hat die Unterhaltung mit dem Bot blockiert."</span><span class="sxs-lookup"><span data-stu-id="765f8-238">**Message**: "User blocked the conversation with the bot."</span></span> | <span data-ttu-id="765f8-239">Der Benutzer hat den Bot im 1:1-Chat oder in einem Kanal über Moderationseinstellungen blockiert.</span><span class="sxs-lookup"><span data-stu-id="765f8-239">User blocked the bot in 1:1 chat or a channel through moderation settings.</span></span> |
| <span data-ttu-id="765f8-240">403</span><span class="sxs-lookup"><span data-stu-id="765f8-240">403</span></span> | <span data-ttu-id="765f8-241">**Code**: `BotNotInConversationRoster`</span><span class="sxs-lookup"><span data-stu-id="765f8-241">**Code**: `BotNotInConversationRoster`</span></span> <br/> <span data-ttu-id="765f8-242">**Meldung:**"Der Bot ist nicht Teil des Unterhaltungsplans."</span><span class="sxs-lookup"><span data-stu-id="765f8-242">**Message**: "The bot is not part of the conversation roster."</span></span> | <span data-ttu-id="765f8-243">Der Bot ist nicht Teil der Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="765f8-243">The bot is not part of the conversation.</span></span> |
| <span data-ttu-id="765f8-244">403</span><span class="sxs-lookup"><span data-stu-id="765f8-244">403</span></span> | <span data-ttu-id="765f8-245">**Code**: `BotDisabledByAdmin`</span><span class="sxs-lookup"><span data-stu-id="765f8-245">**Code**: `BotDisabledByAdmin`</span></span> <br/> <span data-ttu-id="765f8-246">**Meldung:**"Der Mandantenadministrator hat diesen Bot deaktiviert."</span><span class="sxs-lookup"><span data-stu-id="765f8-246">**Message**: "The tenant admin disabled this bot."</span></span> | <span data-ttu-id="765f8-247">Der Mandant hat den Bot blockiert.</span><span class="sxs-lookup"><span data-stu-id="765f8-247">Tenant blocked the bot.</span></span> |
| <span data-ttu-id="765f8-248">401</span><span class="sxs-lookup"><span data-stu-id="765f8-248">401</span></span> | <span data-ttu-id="765f8-249">**Code**: `BotNotRegistered`</span><span class="sxs-lookup"><span data-stu-id="765f8-249">**Code**: `BotNotRegistered`</span></span> <br/> <span data-ttu-id="765f8-250">**Meldung:**"Es wurde keine Registrierung für diesen Bot gefunden."</span><span class="sxs-lookup"><span data-stu-id="765f8-250">**Message**: “No registration found for this bot.”</span></span> | <span data-ttu-id="765f8-251">Die Registrierung für diesen Bot wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="765f8-251">The registration for this bot was not found.</span></span> |
| <span data-ttu-id="765f8-252">412</span><span class="sxs-lookup"><span data-stu-id="765f8-252">412</span></span> | <span data-ttu-id="765f8-253">**Code**: `PreconditionFailed`</span><span class="sxs-lookup"><span data-stu-id="765f8-253">**Code**: `PreconditionFailed`</span></span> <br/> <span data-ttu-id="765f8-254">**Meldung:**"Vorbedingung fehlgeschlagen, versuchen Sie es bitte erneut."</span><span class="sxs-lookup"><span data-stu-id="765f8-254">**Message**: “Precondition failed, please try again.”</span></span> | <span data-ttu-id="765f8-255">Eine Voraussetzung für eine unserer Abhängigkeiten ist aufgrund mehrerer gleichzeitiger Vorgänge in derselben Unterhaltung fehlgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="765f8-255">A precondition failed on one of our dependencies due to multiple concurrent operations on the same conversation.</span></span> |
| <span data-ttu-id="765f8-256">404</span><span class="sxs-lookup"><span data-stu-id="765f8-256">404</span></span> | <span data-ttu-id="765f8-257">**Code**: `ConversationNotFound`</span><span class="sxs-lookup"><span data-stu-id="765f8-257">**Code**: `ConversationNotFound`</span></span> <br/> <span data-ttu-id="765f8-258">**Meldung**: "Unterhaltung nicht gefunden".</span><span class="sxs-lookup"><span data-stu-id="765f8-258">**Message**: “Conversation not found.”</span></span> | <span data-ttu-id="765f8-259">Die Unterhaltung wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="765f8-259">The conversation was not found.</span></span> |
| <span data-ttu-id="765f8-260">413</span><span class="sxs-lookup"><span data-stu-id="765f8-260">413</span></span> | <span data-ttu-id="765f8-261">**Code**: `MessageSizeTooBig`</span><span class="sxs-lookup"><span data-stu-id="765f8-261">**Code**: `MessageSizeTooBig`</span></span> <br/> <span data-ttu-id="765f8-262">**Meldung:**"Nachrichtengröße zu groß".</span><span class="sxs-lookup"><span data-stu-id="765f8-262">**Message**: “Message size too large.”</span></span> | <span data-ttu-id="765f8-263">Die Größe der eingehenden Anforderung war zu groß.</span><span class="sxs-lookup"><span data-stu-id="765f8-263">The size on the incoming request was too large.</span></span> |
| <span data-ttu-id="765f8-264">429</span><span class="sxs-lookup"><span data-stu-id="765f8-264">429</span></span> | <span data-ttu-id="765f8-265">**Code**: `Throttled`</span><span class="sxs-lookup"><span data-stu-id="765f8-265">**Code**: `Throttled`</span></span> <br/> <span data-ttu-id="765f8-266">**Meldung**: "Zu viele Anforderungen".</span><span class="sxs-lookup"><span data-stu-id="765f8-266">**Message**: “Too many requests.”</span></span> <span data-ttu-id="765f8-267">Gibt außerdem zurück, wann nach dem Versuch erneut geversucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="765f8-267">Also returns when to retry after.</span></span> | <span data-ttu-id="765f8-268">Zu viele Anforderungen wurden vom Bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="765f8-268">Too many requests were sent by the bot.</span></span> <span data-ttu-id="765f8-269">Weitere Informationen finden Sie unter [Rate limit](~/bots/how-to/rate-limit.md).</span><span class="sxs-lookup"><span data-stu-id="765f8-269">For more information, see [rate limit](~/bots/how-to/rate-limit.md).</span></span> |

<span data-ttu-id="765f8-270">Im nächsten Abschnitt wird ein einfaches Codebeispiel veranschaulicht, das den grundlegenden Unterhaltungsfluss in eine Teams-Anwendung integriert.</span><span class="sxs-lookup"><span data-stu-id="765f8-270">The next section illustrates a simple code sample that incorporates basic conversational flow into a Teams application.</span></span>

## <a name="code-sample"></a><span data-ttu-id="765f8-271">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="765f8-271">Code sample</span></span>

<span data-ttu-id="765f8-272">Im Folgenden finden Sie die Codebeispiele für den Teams-Unterhaltungsbot:</span><span class="sxs-lookup"><span data-stu-id="765f8-272">Following are the code samples for Teams conversation bot:</span></span>

|<span data-ttu-id="765f8-273">Beispielname</span><span class="sxs-lookup"><span data-stu-id="765f8-273">Sample name</span></span> | <span data-ttu-id="765f8-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="765f8-274">Description</span></span> | <span data-ttu-id="765f8-275">. NETCore</span><span class="sxs-lookup"><span data-stu-id="765f8-275">.NETCore</span></span> | <span data-ttu-id="765f8-276">Node.js</span><span class="sxs-lookup"><span data-stu-id="765f8-276">Node.js</span></span> | <span data-ttu-id="765f8-277">Python</span><span class="sxs-lookup"><span data-stu-id="765f8-277">Python</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="765f8-278">Teams-Unterhaltungsbot</span><span class="sxs-lookup"><span data-stu-id="765f8-278">Teams conversation bot</span></span> | <span data-ttu-id="765f8-279">Nachrichten- und Unterhaltungsereignisbehandlung.</span><span class="sxs-lookup"><span data-stu-id="765f8-279">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="765f8-280">View</span><span class="sxs-lookup"><span data-stu-id="765f8-280">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="765f8-281">View</span><span class="sxs-lookup"><span data-stu-id="765f8-281">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="765f8-282">View</span><span class="sxs-lookup"><span data-stu-id="765f8-282">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a><span data-ttu-id="765f8-283">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="765f8-283">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="765f8-284">Versenden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="765f8-284">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="765f8-285">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="765f8-285">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a><span data-ttu-id="765f8-286">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="765f8-286">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="765f8-287">Bot-Befehlsmenüs</span><span class="sxs-lookup"><span data-stu-id="765f8-287">Bot command menus</span></span>](~/bots/how-to/create-a-bot-commands-menu.md)
