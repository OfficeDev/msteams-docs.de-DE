---
title: Grundlagen zu Unterhaltungen
description: beschreibt Möglichkeiten für eine Unterhaltung mit einem Microsoft Teams-Bot
ms.topic: overview
ms.author: anclear
keyword: conversations basics receive message send message picture message channel data adaptive cards
ms.openlocfilehash: a045f02a146782ebdbbbb14fe5f4187cb517a109
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093957"
---
# <a name="conversation-basics"></a><span data-ttu-id="27b5c-103">Grundlagen zu Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="27b5c-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="27b5c-104">Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-104">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="27b5c-105">Es gibt drei Arten von Unterhaltungen, die auch als Bereiche in Teams bezeichnet werden:</span><span class="sxs-lookup"><span data-stu-id="27b5c-105">There are three types of conversations, also called scopes in Teams:</span></span>

| <span data-ttu-id="27b5c-106">Unterhaltungstyp</span><span class="sxs-lookup"><span data-stu-id="27b5c-106">Conversation type</span></span> | <span data-ttu-id="27b5c-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="27b5c-107">Description</span></span> |
| ------- | ----------- |
|  `teams` | <span data-ttu-id="27b5c-108">Auch Kanalunterhaltungen genannt, die für alle Mitglieder des Kanals sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="27b5c-108">Also called channel conversations, visible to all members of the channel.</span></span> |
| `personal` | <span data-ttu-id="27b5c-109">Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="27b5c-109">Conversations between bots and a single user.</span></span> |
| `groupChat` | <span data-ttu-id="27b5c-110">Chatten zwischen einem Bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="27b5c-110">Chat between a bot and two or more users.</span></span> <span data-ttu-id="27b5c-111">Aktiviert auch Ihren Bot in Besprechungschats.</span><span class="sxs-lookup"><span data-stu-id="27b5c-111">Also enables your bot in meeting chats.</span></span> |

<span data-ttu-id="27b5c-112">Ein Bot verhält sich etwas anders, je nachdem, an welcher Art von Unterhaltung er beteiligt ist:</span><span class="sxs-lookup"><span data-stu-id="27b5c-112">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="27b5c-113">Bots in Kanal- und Gruppenchatunterhaltungen erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufrief.</span><span class="sxs-lookup"><span data-stu-id="27b5c-113">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="27b5c-114">Bots in einer 1:1-Unterhaltung erfordern keine @-Erwähnung.</span><span class="sxs-lookup"><span data-stu-id="27b5c-114">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="27b5c-115">Alle Nachrichten, die vom Benutzer gesendet werden, werden an Ihren Bot weitergeschickt.</span><span class="sxs-lookup"><span data-stu-id="27b5c-115">All messages sent by the user routes to your bot.</span></span>

<span data-ttu-id="27b5c-116">Um Ihren Bot in einem bestimmten Bereich zu aktivieren, fügen Sie diesen Bereich ihrem [App-Manifest hinzu.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="27b5c-116">To enable your bot in a particular scope, add that scope to your [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="activities"></a><span data-ttu-id="27b5c-117">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="27b5c-117">Activities</span></span>

<span data-ttu-id="27b5c-118">Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`.</span><span class="sxs-lookup"><span data-stu-id="27b5c-118">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="27b5c-119">Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots.</span><span class="sxs-lookup"><span data-stu-id="27b5c-119">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="27b5c-120">Ihr Bot untersucht die Nachricht, um ihren Typ zu ermitteln, und antwortet entsprechend.</span><span class="sxs-lookup"><span data-stu-id="27b5c-120">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="27b5c-121">Grundlegende Unterhaltungen werden über den Bot Framework Connector, eine einzelne REST-API, behandelt.</span><span class="sxs-lookup"><span data-stu-id="27b5c-121">Basic conversations are handled through the Bot Framework Connector, a single REST API.</span></span> <span data-ttu-id="27b5c-122">Diese API ermöglicht Es Ihrem Bot, mit Teams und anderen Kanälen zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="27b5c-122">This API enables your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="27b5c-123">Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungsflusses und -zustands sowie einfache Möglichkeiten zur Integration kognitiver Dienste wie der Verarbeitung natürlicher Sprache (Natural Language Processing, NLP).</span><span class="sxs-lookup"><span data-stu-id="27b5c-123">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as Natural Language Processing (NLP).</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="27b5c-124">Empfangen einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="27b5c-124">Receive a message</span></span>

<span data-ttu-id="27b5c-125">Um eine Textnachricht zu empfangen, verwenden Sie die `Text`-Eigenschaft des `Activity`-Objekts.</span><span class="sxs-lookup"><span data-stu-id="27b5c-125">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="27b5c-126">Verwenden Sie im Aktivitäts-Handler des Bots die `Activity` des Turn-Kontextobjekts, um eine einzelne Nachrichtenanforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-126">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="27b5c-127">Im folgenden Code ist ein Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="27b5c-127">The following code shows an example.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="27b5c-128">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="27b5c-128">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="27b5c-129">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="27b5c-129">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="27b5c-130">Python</span><span class="sxs-lookup"><span data-stu-id="27b5c-130">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[<span data-ttu-id="27b5c-131">Json</span><span class="sxs-lookup"><span data-stu-id="27b5c-131">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="27b5c-132">Senden einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="27b5c-132">Send a message</span></span>

<span data-ttu-id="27b5c-133">Um eine Textnachricht zu senden, geben Sie die Zeichenfolge an, die Sie als Aktivität senden möchten.</span><span class="sxs-lookup"><span data-stu-id="27b5c-133">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="27b5c-134">Verwenden Sie im Aktivitätshandler des Bots die Methode des Turn-Kontextobjekts, `SendActivityAsync` um eine einzelne Nachrichtenantwort zu senden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-134">In the bot's activity handler, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="27b5c-135">Verwenden Sie die Methode des `SendActivitiesAsync` Objekts, um mehrere Antworten auf einmal zu senden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-135">Use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="27b5c-136">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn einer Unterhaltung eine Person hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="27b5c-136">The following code shows an example of sending a message when someone is added to a conversation.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="27b5c-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="27b5c-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="27b5c-138">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="27b5c-138">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="27b5c-139">Python</span><span class="sxs-lookup"><span data-stu-id="27b5c-139">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[<span data-ttu-id="27b5c-140">Json</span><span class="sxs-lookup"><span data-stu-id="27b5c-140">JSON</span></span>](#tab/json)

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

## <a name="teams-channel-data"></a><span data-ttu-id="27b5c-141">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="27b5c-141">Teams channel data</span></span>

<span data-ttu-id="27b5c-142">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist eine definitive Quelle für Team- und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="27b5c-142">The `channelData` object contains Teams-specific information and is a definitive source for team and channel IDs.</span></span> <span data-ttu-id="27b5c-143">Möglicherweise müssen Sie diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-143">You may need to cache and use these IDs as keys for local storage.</span></span> <span data-ttu-id="27b5c-144">Im SDK werden in der Regel wichtige Informationen aus dem Objekt herausgezieht, um `TeamsActivityHandler` `channelData` einen einfachen Zugriff zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-144">The `TeamsActivityHandler` in the SDK, typically pulls out important information from the `channelData` object to make it easily accessible.</span></span> <span data-ttu-id="27b5c-145">Sie können jedoch immer über das Objekt auf die ursprünglichen Daten `turnContext` zugreifen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-145">However, you can always access the original data from the `turnContext` object.</span></span>

<span data-ttu-id="27b5c-146">Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-146">The `channelData` object is not included in messages in personal conversations, as these take place outside of any channel.</span></span>

<span data-ttu-id="27b5c-147">Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="27b5c-147">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="27b5c-148">`eventType`#A0 nur bei [Kanaländerungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="27b5c-148">`eventType` Teams event type; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="27b5c-149">`tenant.id` Azure Active Directory-Mandanten-ID, die in allen Kontexten übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="27b5c-149">`tenant.id` Azure Active Directory tenant ID, passed in all contexts.</span></span>
* <span data-ttu-id="27b5c-150">`team` Wird nur im Kanalkontext übergeben, nicht im persönlichen Chat.</span><span class="sxs-lookup"><span data-stu-id="27b5c-150">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="27b5c-151">`id` GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="27b5c-151">`id` GUID for the channel.</span></span>
  * <span data-ttu-id="27b5c-152">`name`Name des Teams; wird nur in Fällen von [Teambenennungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="27b5c-152">`name` Name of the team; passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="27b5c-153">`channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="27b5c-153">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added.</span></span>
  * <span data-ttu-id="27b5c-154">`id` GUID für den Kanal.</span><span class="sxs-lookup"><span data-stu-id="27b5c-154">`id` GUID for the channel.</span></span>
  * <span data-ttu-id="27b5c-155">`name`Kanalname; nur bei [Kanaländerungsereignissen übergeben.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span><span class="sxs-lookup"><span data-stu-id="27b5c-155">`name` Channel name; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="27b5c-156">`channelData.teamsTeamId` Veraltet.</span><span class="sxs-lookup"><span data-stu-id="27b5c-156">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="27b5c-157">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="27b5c-157">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="27b5c-158">`channelData.teamsChannelId` Veraltet.</span><span class="sxs-lookup"><span data-stu-id="27b5c-158">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="27b5c-159">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="27b5c-159">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="27b5c-160">Beispiel für ein channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="27b5c-160">Example channelData object (channelCreated event)</span></span>

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

## <a name="message-content"></a><span data-ttu-id="27b5c-161">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="27b5c-161">Message content</span></span>

<span data-ttu-id="27b5c-162">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-162">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="27b5c-163">Benutzer können Rich-Text- und Bilder an Ihren Bot senden.</span><span class="sxs-lookup"><span data-stu-id="27b5c-163">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="27b5c-164">Format</span><span class="sxs-lookup"><span data-stu-id="27b5c-164">Format</span></span>    | <span data-ttu-id="27b5c-165">Von Benutzer zu Bot</span><span class="sxs-lookup"><span data-stu-id="27b5c-165">From user to bot</span></span> | <span data-ttu-id="27b5c-166">Vom Bot zum Benutzer</span><span class="sxs-lookup"><span data-stu-id="27b5c-166">From bot to user</span></span> | <span data-ttu-id="27b5c-167">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="27b5c-167">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="27b5c-168">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="27b5c-168">Rich text</span></span> | <span data-ttu-id="27b5c-169">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-169">✔</span></span>                | <span data-ttu-id="27b5c-170">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-170">✔</span></span>                |                                                                                         |
| <span data-ttu-id="27b5c-171">Bilder</span><span class="sxs-lookup"><span data-stu-id="27b5c-171">Pictures</span></span>  | <span data-ttu-id="27b5c-172">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-172">✔</span></span>                | <span data-ttu-id="27b5c-173">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-173">✔</span></span>                | <span data-ttu-id="27b5c-174">Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; Animierte GIF werden nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="27b5c-174">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span>  |
| <span data-ttu-id="27b5c-175">Karten</span><span class="sxs-lookup"><span data-stu-id="27b5c-175">Cards</span></span>     | <span data-ttu-id="27b5c-176">✖</span><span class="sxs-lookup"><span data-stu-id="27b5c-176">✖</span></span>                | <span data-ttu-id="27b5c-177">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-177">✔</span></span>                | <span data-ttu-id="27b5c-178">Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Teams-Karten.</span><span class="sxs-lookup"><span data-stu-id="27b5c-178">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="27b5c-179">Emojis</span><span class="sxs-lookup"><span data-stu-id="27b5c-179">Emojis</span></span>    | <span data-ttu-id="27b5c-180">✖</span><span class="sxs-lookup"><span data-stu-id="27b5c-180">✖</span></span>                | <span data-ttu-id="27b5c-181">✔</span><span class="sxs-lookup"><span data-stu-id="27b5c-181">✔</span></span>                | <span data-ttu-id="27b5c-182">Teams unterstützt derzeit Emojis über UTF-16 (z. B. U+1F600 für Das Gesicht)</span><span class="sxs-lookup"><span data-stu-id="27b5c-182">Teams currently supports emojis via UTF-16 (such as U+1F600 for grinning face)</span></span>          |

## <a name="adding-notifications-to-your-message"></a><span data-ttu-id="27b5c-183">Hinzufügen von Benachrichtigungen zu Ihrer Nachricht</span><span class="sxs-lookup"><span data-stu-id="27b5c-183">Adding notifications to your message</span></span>

<span data-ttu-id="27b5c-184">Benachrichtigungen warnen Benutzer über neue Aufgaben, Erwähnungen und Kommentare im Zusammenhang mit dem, wofür sie arbeiten oder die sie betrachten müssen, indem sie einen Hinweis in ihren Aktivitätsfeed einfügen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-184">Notifications alert users about new tasks, mentions, and comments related to what they are working on or need to look at by inserting a notice into their activity feed.</span></span> <span data-ttu-id="27b5c-185">Sie können festlegen, dass Benachrichtigungen von Ihrer Botnachricht ausgelöst werden, indem Sie die `TeamsChannelData` Eigenschaft `Notification.Alert` "objects" auf "true" festlegen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-185">You can set notifications to trigger from your bot-message by setting the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="27b5c-186">Ob eine Benachrichtigung ausgelöst wird oder nicht, hängt letztlich von den Teams-Einstellungen des jeweiligen Benutzers ab, und Sie können diese Einstellungen nicht programmgesteuert außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="27b5c-186">Whether or not a notification is raised ultimately depends on the individual user's Teams settings and you cannot programmatically override these settings.</span></span> <span data-ttu-id="27b5c-187">Die Art der Benachrichtigung ist entweder ein Banner oder ein Banner und eine E-Mail.</span><span class="sxs-lookup"><span data-stu-id="27b5c-187">The type of notification is either a banner or both a banner and an email.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="27b5c-188">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="27b5c-188">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="27b5c-189">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="27b5c-189">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[<span data-ttu-id="27b5c-190">Python</span><span class="sxs-lookup"><span data-stu-id="27b5c-190">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[<span data-ttu-id="27b5c-191">Json</span><span class="sxs-lookup"><span data-stu-id="27b5c-191">JSON</span></span>](#tab/json)

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

## <a name="picture-messages"></a><span data-ttu-id="27b5c-192">Bildmeldungen</span><span class="sxs-lookup"><span data-stu-id="27b5c-192">Picture messages</span></span>

<span data-ttu-id="27b5c-193">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="27b5c-193">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="27b5c-194">Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)</span><span class="sxs-lookup"><span data-stu-id="27b5c-194">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).</span></span>

<span data-ttu-id="27b5c-195">Bilder können mindestens 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format sein.</span><span class="sxs-lookup"><span data-stu-id="27b5c-195">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="27b5c-196">Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="27b5c-196">Animated GIF is not supported.</span></span>

<span data-ttu-id="27b5c-197">Geben Sie immer die Höhe und Breite jedes Bilds mithilfe von XML an.</span><span class="sxs-lookup"><span data-stu-id="27b5c-197">Always specify the height and width of each image by using XML.</span></span> <span data-ttu-id="27b5c-198">In Markdown ist die Bildgröße standardmäßig auf 256×256 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="27b5c-198">In Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="27b5c-199">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="27b5c-199">For example:</span></span>

* <span data-ttu-id="27b5c-200">Verwenden – `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span><span class="sxs-lookup"><span data-stu-id="27b5c-200">Use - `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="27b5c-201">Nicht verwenden – `![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="27b5c-201">Don't use - `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="adaptive-cards"></a><span data-ttu-id="27b5c-202">Adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="27b5c-202">Adaptive cards</span></span>

<span data-ttu-id="27b5c-203">Verwenden Sie den folgenden Code, um eine einfache adaptive Karte zu senden:</span><span class="sxs-lookup"><span data-stu-id="27b5c-203">Use the following code to send a simple adaptive card:</span></span>

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

<span data-ttu-id="27b5c-204">Weitere Informationen zu Karten und Karten in Bots finden Sie in [der Kartendokumentation.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="27b5c-204">To know more about cards and cards in bots, see [cards documentation](~/task-modules-and-cards/what-are-cards.md).</span></span>
<span data-ttu-id="27b5c-205">Wenn eine Antwort Textnachrichten und Anlagen enthält, werden beide Antworten separat gesendet.</span><span class="sxs-lookup"><span data-stu-id="27b5c-205">When a response contains text messages and attachments, both responses are sent separately.</span></span> <span data-ttu-id="27b5c-206">Die Anlage wird nach der Textnachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="27b5c-206">The attachment is sent after the text message.</span></span>

## <a name="code-sample"></a><span data-ttu-id="27b5c-207">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="27b5c-207">Code sample</span></span>
|<span data-ttu-id="27b5c-208">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="27b5c-208">**Sample name**</span></span> | <span data-ttu-id="27b5c-209">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="27b5c-209">**Description**</span></span> | <span data-ttu-id="27b5c-210">**. NETCore**</span><span class="sxs-lookup"><span data-stu-id="27b5c-210">**.NETCore**</span></span> | <span data-ttu-id="27b5c-211">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="27b5c-211">**JavaScript**</span></span> | <span data-ttu-id="27b5c-212">**Python**</span><span class="sxs-lookup"><span data-stu-id="27b5c-212">**Python**</span></span>|
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="27b5c-213">Teams Conversation Bot</span><span class="sxs-lookup"><span data-stu-id="27b5c-213">Teams Conversation Bot</span></span> | <span data-ttu-id="27b5c-214">Behandlung von Nachrichten- und Unterhaltungsereignis.</span><span class="sxs-lookup"><span data-stu-id="27b5c-214">Messaging and conversation event handling.</span></span> |[<span data-ttu-id="27b5c-215">View</span><span class="sxs-lookup"><span data-stu-id="27b5c-215">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="27b5c-216">View</span><span class="sxs-lookup"><span data-stu-id="27b5c-216">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [<span data-ttu-id="27b5c-217">View</span><span class="sxs-lookup"><span data-stu-id="27b5c-217">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-steps"></a><span data-ttu-id="27b5c-218">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="27b5c-218">Next steps</span></span>

* [<span data-ttu-id="27b5c-219">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="27b5c-219">Sending proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
* [<span data-ttu-id="27b5c-220">Abonnieren von Unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="27b5c-220">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
