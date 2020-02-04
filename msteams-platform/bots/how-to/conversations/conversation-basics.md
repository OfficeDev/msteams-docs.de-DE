---
title: Grundlagen der Unterhaltung
author: clearab
description: Vorgehensweise bei einer Unterhaltung mit einem Microsoft Teams-bot
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2d241ad04509c596e97647138bab2a749fa0f74c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674225"
---
# <a name="conversation-basics"></a><span data-ttu-id="a1b73-103">Grundlagen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="a1b73-103">Conversation basics</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="a1b73-104">Bei einer Unterhaltung handelt es sich um eine Reihe von Nachrichten, die zwischen Ihrem bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-104">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="a1b73-105">Es gibt drei Arten von Unterhaltungen (auch als Bereiche bezeichnet) in Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="a1b73-105">There are three kinds of conversations (also called scopes) in Teams:</span></span>

* <span data-ttu-id="a1b73-106">`teams`Wird auch als Kanal Unterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="a1b73-106">`teams` Also called channel conversations, visible to all members of the channel.</span></span>
* <span data-ttu-id="a1b73-107">`personal`Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a1b73-107">`personal` Conversations between bots and a single user.</span></span>
* <span data-ttu-id="a1b73-108">`groupChat`Chat zwischen einem bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="a1b73-108">`groupChat` Chat between a bot and two or more users.</span></span> <span data-ttu-id="a1b73-109">Aktiviert ihren bot auch in Besprechungs Chats.</span><span class="sxs-lookup"><span data-stu-id="a1b73-109">Also enables your bot in meeting chats.</span></span>

<span data-ttu-id="a1b73-110">Ein bot verhält sich je nach Art der Unterhaltung, in der er beteiligt ist, etwas anders:</span><span class="sxs-lookup"><span data-stu-id="a1b73-110">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="a1b73-111">Bots in Kanal-und Gruppenchat Unterhaltungen erfordern, dass der Benutzer @ den bot erwähnt, um ihn in einem Kanal aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="a1b73-111">Bots in channel and group chat conversations require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="a1b73-112">Bots in einer 1:1-Unterhaltung benötigen keine @ mention.</span><span class="sxs-lookup"><span data-stu-id="a1b73-112">Bots in a one-to-one conversation do not require an @ mention.</span></span> <span data-ttu-id="a1b73-113">Alle Nachrichten, die vom Benutzer gesendet werden, werden an Ihren bot weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="a1b73-113">All messages sent by the user will be routed to your bot.</span></span>

<span data-ttu-id="a1b73-114">Um Ihren bot in einem bestimmten Bereich zu aktivieren, fügen Sie diesen Bereich Ihrem [App-Manifest](~/resources/schema/manifest-schema.md)hinzu.</span><span class="sxs-lookup"><span data-stu-id="a1b73-114">To enable your bot in a particular scope, add that scope to your [app manifest](~/resources/schema/manifest-schema.md).</span></span>

## <a name="activities"></a><span data-ttu-id="a1b73-115">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="a1b73-115">Activities</span></span>

<span data-ttu-id="a1b73-116">Jede Nachricht ist ein `Activity` Objekt vom Typ `messageType: message`.</span><span class="sxs-lookup"><span data-stu-id="a1b73-116">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="a1b73-117">Wenn ein Benutzer eine Nachricht sendet, stellt Microsoft Teams die Nachricht an Ihren bot. insbesondere wird ein JSON-Objekt an den Messaging Endpunkt Ihres bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="a1b73-117">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="a1b73-118">Ihr bot überprüft die Nachricht, um den Typ zu bestimmen, und antwortet dementsprechend.</span><span class="sxs-lookup"><span data-stu-id="a1b73-118">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="a1b73-119">Grundlegende Unterhaltungen werden über den bot-Framework-Konnektor behandelt, eine einzelne Rest-API, mit der ihr bot mit Teams und anderen Kanälen kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="a1b73-119">Basic conversation is handled through the Bot Framework Connector, a single REST API to enable your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="a1b73-120">Das bot-Generator-SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungs Flusses und-Zustands sowie einfache Methoden zum Integrieren von kognitiven Diensten wie etwa die Natural Language Processing (NLP).</span><span class="sxs-lookup"><span data-stu-id="a1b73-120">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as natural language processing (NLP).</span></span>

## <a name="receive-a-message"></a><span data-ttu-id="a1b73-121">Empfangen einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="a1b73-121">Receive a message</span></span>

<span data-ttu-id="a1b73-122">Verwenden Sie die `Text` -Eigenschaft des- `Activity` Objekts, um eine Textnachricht zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a1b73-122">To receive a text message, use the `Text` property of the `Activity` object.</span></span> <span data-ttu-id="a1b73-123">Verwenden Sie im Aktivitäts Handler des bot-Objekts das Turn-Kontext `Activity` Objekt, um eine einzelne Nachrichtenanforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="a1b73-123">In the bot's activity handler, use the turn context object's `Activity` to read a single message request.</span></span>

<span data-ttu-id="a1b73-124">Der folgende Code zeigt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="a1b73-124">The code below shows an example.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="a1b73-125">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="a1b73-125">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="a1b73-126">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="a1b73-126">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="pythontabpython"></a>[<span data-ttu-id="a1b73-127">Python</span><span class="sxs-lookup"><span data-stu-id="a1b73-127">Python</span></span>](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="jsontabjson"></a>[<span data-ttu-id="a1b73-128">Json</span><span class="sxs-lookup"><span data-stu-id="a1b73-128">JSON</span></span>](#tab/json)

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

## <a name="send-a-message"></a><span data-ttu-id="a1b73-129">Senden einer Nachricht</span><span class="sxs-lookup"><span data-stu-id="a1b73-129">Send a message</span></span>

<span data-ttu-id="a1b73-130">Geben Sie zum Senden einer Textnachricht die Zeichenfolge an, die Sie als Aktivität senden möchten.</span><span class="sxs-lookup"><span data-stu-id="a1b73-130">To send a text message, specify the string you want to send as the activity.</span></span> <span data-ttu-id="a1b73-131">Verwenden Sie in den Aktivitäts Handlern des bot die `SendActivityAsync` Methode zum Drehen des Kontextobjekts, um eine einzelne Nachrichten Antwort zu senden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-131">In the bot's activity handlers, use the turn context object's `SendActivityAsync` method to send a single message response.</span></span> <span data-ttu-id="a1b73-132">Sie können auch die `SendActivitiesAsync` Methode des Objekts verwenden, um mehrere Antworten gleichzeitig zu senden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-132">You can also use the object's `SendActivitiesAsync` method to send multiple responses at once.</span></span> <span data-ttu-id="a1b73-133">Der folgende Code zeigt ein Beispiel für das Senden einer Nachricht, wenn jemand einer Unterhaltung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a1b73-133">The code below shows an example of sending a message when someone is added to a conversation</span></span>  

# <a name="cnettabdotnet"></a>[<span data-ttu-id="a1b73-134">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="a1b73-134">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="a1b73-135">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="a1b73-135">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="pythontabpython"></a>[<span data-ttu-id="a1b73-136">Python</span><span class="sxs-lookup"><span data-stu-id="a1b73-136">Python</span></span>](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="jsontabjson"></a>[<span data-ttu-id="a1b73-137">Json</span><span class="sxs-lookup"><span data-stu-id="a1b73-137">JSON</span></span>](#tab/json)

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

## <a name="teams-channel-data"></a><span data-ttu-id="a1b73-138">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="a1b73-138">Teams channel data</span></span>

<span data-ttu-id="a1b73-139">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team-und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="a1b73-139">The `channelData` object contains Teams-specific information and is the definitive source for team and channel IDs.</span></span> <span data-ttu-id="a1b73-140">Sie müssen möglicherweise Zwischenspeichern und diese IDs als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-140">You may need to cache and use these ids as keys for local storage.</span></span> <span data-ttu-id="a1b73-141">`TeamsActivityHandler` Im SDK werden normalerweise wichtige Informationen aus dem `channelData` Objekt herausgezogen, damit es leichter zugänglich ist, Sie können jedoch jederzeit auf die ursprünglichen Informationen des `turnContext` Objekts zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a1b73-141">The `TeamsActivityHandler` in the SDK will typically pull out important information from the `channelData` object to make it more easily accessible, however you can always access the original information from the `turnContext` object.</span></span>

<span data-ttu-id="a1b73-142">Das `channelData` Objekt wird nicht in Nachrichten in persönlichen Unterhaltungen eingeschlossen, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-142">The `channelData` object is not included in messages in personal conversations since these take place outside of any channel.</span></span>

<span data-ttu-id="a1b73-143">Ein typisches channelData-Objekt in einer an Ihren bot gesendeten Aktivität enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="a1b73-143">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="a1b73-144">`eventType`Teams-Ereignistyp; nur in Fällen von [Kanal Änderungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben</span><span class="sxs-lookup"><span data-stu-id="a1b73-144">`eventType` Teams event type; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span></span>
* <span data-ttu-id="a1b73-145">`tenant.id`Azure Active Directory-Mandanten-ID; in allen Kontexten übergeben</span><span class="sxs-lookup"><span data-stu-id="a1b73-145">`tenant.id` Azure Active Directory tenant ID; passed in all contexts</span></span>
* <span data-ttu-id="a1b73-146">`team`Wird nur in Kanal Kontexten übergeben, nicht im persönlichen Chat.</span><span class="sxs-lookup"><span data-stu-id="a1b73-146">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="a1b73-147">`id`GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="a1b73-147">`id` GUID for the channel</span></span>
  * <span data-ttu-id="a1b73-148">`name`Name des Teams; nur in Fällen von [Team Umbenennungs Ereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md) übergeben</span><span class="sxs-lookup"><span data-stu-id="a1b73-148">`name` Name of the team; passed only in cases of [team rename events](~/bots/how-to/conversations/subscribe-to-conversation-events.md)</span></span>
* <span data-ttu-id="a1b73-149">`channel`Wird nur in Kanal Kontexten übergeben, wenn der bot erwähnt wird, oder für Ereignisse in Kanälen in Microsoft Teams, in denen der bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a1b73-149">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added</span></span>
  * <span data-ttu-id="a1b73-150">`id`GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="a1b73-150">`id` GUID for the channel</span></span>
  * <span data-ttu-id="a1b73-151">`name`Kanal Name; nur in Fällen von [Kanal Änderungsereignissen](~/bots/how-to/conversations/subscribe-to-conversation-events.md)übergeben.</span><span class="sxs-lookup"><span data-stu-id="a1b73-151">`name` Channel name; passed only in cases of [channel modification events](~/bots/how-to/conversations/subscribe-to-conversation-events.md).</span></span>
* <span data-ttu-id="a1b73-152">`channelData.teamsTeamId`Veraltet.</span><span class="sxs-lookup"><span data-stu-id="a1b73-152">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="a1b73-153">Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="a1b73-153">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="a1b73-154">`channelData.teamsChannelId`Veraltet.</span><span class="sxs-lookup"><span data-stu-id="a1b73-154">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="a1b73-155">Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="a1b73-155">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="a1b73-156">Beispiel für ein channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="a1b73-156">Example channelData object (channelCreated event)</span></span>

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

## <a name="message-content"></a><span data-ttu-id="a1b73-157">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="a1b73-157">Message content</span></span>

<span data-ttu-id="a1b73-158">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-158">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="a1b73-159">Benutzer können Rich-Text und Bilder an Ihren bot senden.</span><span class="sxs-lookup"><span data-stu-id="a1b73-159">Users can send rich text and pictures to your bot.</span></span>

| <span data-ttu-id="a1b73-160">Format</span><span class="sxs-lookup"><span data-stu-id="a1b73-160">Format</span></span>    | <span data-ttu-id="a1b73-161">Von Benutzer zu bot</span><span class="sxs-lookup"><span data-stu-id="a1b73-161">From user to bot</span></span> | <span data-ttu-id="a1b73-162">Von bot zu Benutzer</span><span class="sxs-lookup"><span data-stu-id="a1b73-162">From bot to user</span></span> | <span data-ttu-id="a1b73-163">Notes</span><span class="sxs-lookup"><span data-stu-id="a1b73-163">Notes</span></span>                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| <span data-ttu-id="a1b73-164">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="a1b73-164">Rich text</span></span> | <span data-ttu-id="a1b73-165">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-165">✔</span></span>                | <span data-ttu-id="a1b73-166">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-166">✔</span></span>                |                                                                                         |
| <span data-ttu-id="a1b73-167">Bilder</span><span class="sxs-lookup"><span data-stu-id="a1b73-167">Pictures</span></span>  | <span data-ttu-id="a1b73-168">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-168">✔</span></span>                | <span data-ttu-id="a1b73-169">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-169">✔</span></span>                | <span data-ttu-id="a1b73-170">Maximal 1024 × 1024 und 1 MB im PNG-, JPEG-oder GIF-Format; animierte GIF-Zeichen werden nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="a1b73-170">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span>  |
| <span data-ttu-id="a1b73-171">Karten</span><span class="sxs-lookup"><span data-stu-id="a1b73-171">Cards</span></span>     | <span data-ttu-id="a1b73-172">✖</span><span class="sxs-lookup"><span data-stu-id="a1b73-172">✖</span></span>                | <span data-ttu-id="a1b73-173">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-173">✔</span></span>                | <span data-ttu-id="a1b73-174">Siehe die Microsoft [Teams-Karten Referenz](~/task-modules-and-cards/cards/cards-reference.md) für unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="a1b73-174">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="a1b73-175">Emojis</span><span class="sxs-lookup"><span data-stu-id="a1b73-175">Emojis</span></span>    | <span data-ttu-id="a1b73-176">✖</span><span class="sxs-lookup"><span data-stu-id="a1b73-176">✖</span></span>                | <span data-ttu-id="a1b73-177">✔</span><span class="sxs-lookup"><span data-stu-id="a1b73-177">✔</span></span>                | <span data-ttu-id="a1b73-178">Teams unterstützen derzeit Emojis über UTF-16 (wie U + 1F600 für grinsende Fläche)</span><span class="sxs-lookup"><span data-stu-id="a1b73-178">Teams currently supports emojis via UTF-16 (such as U+1F600 for grinning face)</span></span>          |

## <a name="adding-notifications-to-your-message"></a><span data-ttu-id="a1b73-179">Hinzufügen von Benachrichtigungen zu Ihrer Nachricht</span><span class="sxs-lookup"><span data-stu-id="a1b73-179">Adding notifications to your message</span></span>

<span data-ttu-id="a1b73-180">Benachrichtigungen benachrichtigen Benutzer über neue Aufgaben, Erwähnungen und Kommentare im Zusammenhang mit dem, woran Sie gerade arbeiten, oder müssen sich durch Einfügen eines Hinweises in ihren Aktivitäts Feed informieren.</span><span class="sxs-lookup"><span data-stu-id="a1b73-180">Notifications alert users about new tasks, mentions and comments related to what they are working on, or need to look at by inserting a notice into their Activity Feed.</span></span> <span data-ttu-id="a1b73-181">Sie können Benachrichtigungen so festlegen, dass Sie aus ihrer bot-Nachricht `TeamsChannelData` ausgelöst `Notification.Alert` werden, indem Sie die Objects-Eigenschaft auf true festlegen.</span><span class="sxs-lookup"><span data-stu-id="a1b73-181">You can set notifications to trigger from your bot message by setting the `TeamsChannelData` objects `Notification.Alert` property to true.</span></span> <span data-ttu-id="a1b73-182">Unabhängig davon, ob eine Benachrichtigung ausgelöst wird, hängt letztlich von den Microsoft Teams-Einstellungen des einzelnen Benutzers ab, und Sie können diese Einstellungen nicht programmgesteuert außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="a1b73-182">Whether or not a notification is raised will ultimately depend on the individual user's Teams settings and you cannot programmatically override these settings.</span></span> <span data-ttu-id="a1b73-183">Der Typ der Benachrichtigung ist entweder ein Banner oder sowohl ein Banner als auch eine e-Mail.</span><span class="sxs-lookup"><span data-stu-id="a1b73-183">The type of notification will be either a banner or both a banner and an email.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="a1b73-184">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="a1b73-184">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="a1b73-185">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="a1b73-185">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="pythontabpython"></a>[<span data-ttu-id="a1b73-186">Python</span><span class="sxs-lookup"><span data-stu-id="a1b73-186">Python</span></span>](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="jsontabjson"></a>[<span data-ttu-id="a1b73-187">Json</span><span class="sxs-lookup"><span data-stu-id="a1b73-187">JSON</span></span>](#tab/json)

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

## <a name="picture-messages"></a><span data-ttu-id="a1b73-188">Bildnachrichten</span><span class="sxs-lookup"><span data-stu-id="a1b73-188">Picture messages</span></span>

<span data-ttu-id="a1b73-189">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="a1b73-189">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="a1b73-190">Weitere Informationen zu Anlagen finden Sie in der [bot-Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span><span class="sxs-lookup"><span data-stu-id="a1b73-190">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span></span>

<span data-ttu-id="a1b73-191">Bilder können im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a1b73-191">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not supported.</span></span>

<span data-ttu-id="a1b73-192">Es wird empfohlen, die Höhe und Breite jedes Bilds mithilfe von XML anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a1b73-192">We recommend that you specify the height and width of each image by using XML.</span></span> <span data-ttu-id="a1b73-193">Wenn Sie den Abschlag verwenden, beträgt die Bildgröße standardmäßig 256 × 256.</span><span class="sxs-lookup"><span data-stu-id="a1b73-193">If you use Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="a1b73-194">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="a1b73-194">For example:</span></span>

* <span data-ttu-id="a1b73-195">Verwenden`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span><span class="sxs-lookup"><span data-stu-id="a1b73-195">Use - `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="a1b73-196">Nicht verwenden-`![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="a1b73-196">Don't use - `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="next-steps"></a><span data-ttu-id="a1b73-197">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="a1b73-197">Next steps</span></span>

* [<span data-ttu-id="a1b73-198">Senden proaktiver Nachrichten</span><span class="sxs-lookup"><span data-stu-id="a1b73-198">Sending proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
* [<span data-ttu-id="a1b73-199">Abonnieren von unterhaltungsereignissen</span><span class="sxs-lookup"><span data-stu-id="a1b73-199">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
