---
title: Behandeln von bot-Ereignissen
description: Beschreibt das Behandeln von Ereignissen in Bots für Microsoft Teams
keywords: Teams-Bots-Ereignisse
ms.date: 05/20/2019
ms.author: lajanuar
author: laujan
ms.openlocfilehash: e15629ef2f178c0498e33518f5976ff2b2bdf776
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346728"
---
# <a name="handle-bot-events-in-microsoft-teams"></a><span data-ttu-id="a0b4e-104">Behandeln von bot-Ereignissen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a0b4e-104">Handle bot events in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="a0b4e-105">Microsoft Teams sendet Benachrichtigungen an Ihren bot für Änderungen oder Ereignisse, die in Bereichen auftreten, in denen Ihr bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-105">Microsoft Teams sends notifications to your bot for changes or events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="a0b4e-106">Sie können diese Ereignisse verwenden, um Dienstlogik auszulösen, beispielsweise die folgenden:</span><span class="sxs-lookup"><span data-stu-id="a0b4e-106">You can use these events to trigger service logic, such as the following:</span></span>

* <span data-ttu-id="a0b4e-107">Auslösen einer Willkommensnachricht, wenn Ihr bot einem Team hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="a0b4e-107">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="a0b4e-108">Abfrage-und Cache Gruppeninformationen, wenn der bot einem Gruppenchat hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="a0b4e-108">Query and cache group information when the bot is added to a group chat</span></span>
* <span data-ttu-id="a0b4e-109">Aktualisieren zwischengespeicherter Informationen zu Teammitgliedschaften oder Kanalinformationen</span><span class="sxs-lookup"><span data-stu-id="a0b4e-109">Update cached information on team membership or channel information</span></span>
* <span data-ttu-id="a0b4e-110">Entfernen zwischengespeicherter Informationen für ein Team, wenn der bot entfernt wird</span><span class="sxs-lookup"><span data-stu-id="a0b4e-110">Remove cached information for a team if the bot is removed</span></span>
* <span data-ttu-id="a0b4e-111">Wenn eine bot-Nachricht von einem Benutzer gefällt wird</span><span class="sxs-lookup"><span data-stu-id="a0b4e-111">When a bot message is liked by a user</span></span>

<span data-ttu-id="a0b4e-112">Jedes bot-Ereignis wird als `Activity` Objekt gesendet, in dem `messageType` definiert wird, welche Informationen das Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-112">Each bot event is sent as an `Activity` object in which `messageType` defines what information is in the object.</span></span> <span data-ttu-id="a0b4e-113">`message`Informationen zum [senden und empfangen](~/resources/bot-v3/bot-conversations/bots-conversations.md)von Nachrichten vom Typ.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-113">For messages of type `message`, see [Sending and receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span></span>

<span data-ttu-id="a0b4e-114">Teams und Gruppen Ereignisse, die in der Regel vom `conversationUpdate` Typ ausgelöst werden, haben zusätzliche Teams-Ereignisinformationen, die als Teil des `channelData` Objekts übergeben werden, und daher muss Ihr Ereignishandler die `channelData` Nutzlast für die Teams `eventType` und zusätzliche ereignisspezifische Metadaten Abfragen.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-114">Teams and group events, usually triggered off the `conversationUpdate` type, have additional Teams event information passed as part of the `channelData` object, and therefore your event handler must query the `channelData` payload for the Teams `eventType` and additional event-specific metadata.</span></span>

<span data-ttu-id="a0b4e-115">In der folgenden Tabelle sind die Ereignisse aufgeführt, die ihr bot empfangen kann, und Aktionen für ausführen.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-115">The following table lists the events that your bot can receive and take action on.</span></span>

|<span data-ttu-id="a0b4e-116">Typ</span><span class="sxs-lookup"><span data-stu-id="a0b4e-116">Type</span></span>|<span data-ttu-id="a0b4e-117">Payload-Objekt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-117">Payload object</span></span>|<span data-ttu-id="a0b4e-118">Teams-Ereignistyp</span><span class="sxs-lookup"><span data-stu-id="a0b4e-118">Teams eventType</span></span> |<span data-ttu-id="a0b4e-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a0b4e-119">Description</span></span>|<span data-ttu-id="a0b4e-120">Bereich</span><span class="sxs-lookup"><span data-stu-id="a0b4e-120">Scope</span></span>|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[<span data-ttu-id="a0b4e-121">Mitglied zum Team hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-121">Member added to team</span></span>](#team-member-or-bot-addition)| <span data-ttu-id="a0b4e-122">Alle</span><span class="sxs-lookup"><span data-stu-id="a0b4e-122">all</span></span> |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[<span data-ttu-id="a0b4e-123">Das Mitglied wurde aus dem Team entfernt.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-123">Member was removed from team</span></span>](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [<span data-ttu-id="a0b4e-124">Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-124">Team was renamed</span></span>](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [<span data-ttu-id="a0b4e-125">Es wurde ein Kanal erstellt.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-125">A channel was created</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [<span data-ttu-id="a0b4e-126">Ein Kanal wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-126">A channel was renamed</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [<span data-ttu-id="a0b4e-127">Ein Kanal wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-127">A channel was deleted</span></span>](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [<span data-ttu-id="a0b4e-128">Reaktion auf bot-Nachricht</span><span class="sxs-lookup"><span data-stu-id="a0b4e-128">Reaction to bot message</span></span>](#reactions)| <span data-ttu-id="a0b4e-129">Alle</span><span class="sxs-lookup"><span data-stu-id="a0b4e-129">all</span></span> |
| `messageReaction` |`reactionsRemoved`|| [<span data-ttu-id="a0b4e-130">Reaktion aus bot-Nachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-130">Reaction removed from bot message</span></span>](#reactions)| <span data-ttu-id="a0b4e-131">Alle</span><span class="sxs-lookup"><span data-stu-id="a0b4e-131">all</span></span> |

## <a name="team-member-or-bot-addition"></a><span data-ttu-id="a0b4e-132">Team Mitglied oder bot-Addition</span><span class="sxs-lookup"><span data-stu-id="a0b4e-132">Team member or bot addition</span></span>

<span data-ttu-id="a0b4e-133">Das [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) Ereignis wird an Ihren bot gesendet, wenn es Informationen über Mitgliedschafts Aktualisierungen für Teams erhält, in denen es hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-133">The [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="a0b4e-134">Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-134">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span> <span data-ttu-id="a0b4e-135">Beachten Sie, dass die Benutzerinformationen ( `Id` ) für Ihren bot eindeutig sind und für die zukünftige Verwendung durch ihren Dienst zwischengespeichert werden können (beispielsweise das Senden einer Nachricht an einen bestimmten Benutzer).</span><span class="sxs-lookup"><span data-stu-id="a0b4e-135">Note that the user information (`Id`) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

### <a name="bot-or-user-added-to-a-team"></a><span data-ttu-id="a0b4e-136">Bot oder Benutzer, der einem Team hinzugefügt wurde</span><span class="sxs-lookup"><span data-stu-id="a0b4e-136">Bot or user added to a team</span></span>

<span data-ttu-id="a0b4e-137">Das `conversationUpdate` Ereignis mit dem `membersAdded` Objekt in der Nutzlast wird gesendet, wenn entweder ein bot einem Team hinzugefügt wird oder ein neuer Benutzer einem Team hinzugefügt wird, in dem ein bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-137">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when either a bot is added to a team or a new user is added to a team where a bot has been added.</span></span> <span data-ttu-id="a0b4e-138">Microsoft Teams fügt `eventType.teamMemberAdded` das Objekt ebenfalls hinzu `channelData` .</span><span class="sxs-lookup"><span data-stu-id="a0b4e-138">Microsoft Teams also adds `eventType.teamMemberAdded` in the `channelData` object.</span></span>

<span data-ttu-id="a0b4e-139">Da dieses Ereignis in beiden Fällen gesendet wird, sollten Sie das Objekt analysieren, `membersAdded` um festzustellen, ob es sich bei dem Zusatz um einen Benutzer oder den bot selbst handelt.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-139">Because this event is sent in both cases, you should parse the `membersAdded` object to determine whether the addition was a user or the bot itself.</span></span> <span data-ttu-id="a0b4e-140">Für letztere empfiehlt es sich, eine [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) an den Kanal zu senden, damit Benutzer die von Ihrem bot bereitgestellten Funktionen verstehen können.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-140">For the latter, a best practice is to send a [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) to the channel so users can understand the features your bot provides.</span></span>

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a><span data-ttu-id="a0b4e-141">Beispielcode: überprüfen, ob bot das hinzugefügte Mitglied war</span><span class="sxs-lookup"><span data-stu-id="a0b4e-141">Example code: Checking whether bot was the added member</span></span>

##### <a name="net"></a><span data-ttu-id="a0b4e-142">.NET</span><span class="sxs-lookup"><span data-stu-id="a0b4e-142">.NET</span></span>

```csharp
    for (int i = 0; i < sourceMessage.MembersAdded.Count; i++)
    {
        if (sourceMessage.MembersAdded[i].Id == sourceMessage.Recipient.Id)
        {
            addedBot = true;
            break;
        }
    }
```

##### <a name="nodejs"></a><span data-ttu-id="a0b4e-143">Node.js</span><span class="sxs-lookup"><span data-stu-id="a0b4e-143">Node.js</span></span>

```javascript
const builder = require('botbuilder');

var c = new builder.ChatConnector({appId: BOT_APP_ID, appPassword: .BOT_SECRET});
var bot = new builder.UniversalBot(c);

bot.on('conversationUpdate', (msg) => {
    var members = msg.membersAdded;
    // Loop through all members that were just added to the team
    for (var i = 0; i < members.length; i++) {

        // See if the member added was our bot
        if (members[i].id.includes(BOT_APP_ID)) {
            var botmessage = new builder.Message()
                .address(msg.address)
                .text('Hello World!');

            bot.send(botmessage, function(err) {});
        }
    }
});
```

#### <a name="schema-example-bot-added-to-team"></a><span data-ttu-id="a0b4e-144">Schema Beispiel: bot zum Team hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-144">Schema example: Bot added to team</span></span>

```json
{
   "membersAdded":[
      {
         "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2017-02-23T12:38:35.312-07:00",
   "id":"f:5f85c2ad",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
   },
   "conversation":{
      "isGroup":true,
      "conversationType":"channel",
      "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
   },
   "recipient":{
      "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
      "name":"SongsuggesterBot"
   },
   "channelData":{
      "team":{
         "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
      },
      "eventType":"teamMemberAdded",
      "tenant":{
         "id":"72f988bf-86f1-41af-91ab-2d7cd011db47"
      }
   }
}
```

### <a name="user-added-to-a-meeting"></a><span data-ttu-id="a0b4e-145">Benutzer, der einer Besprechung hinzugefügt wurde</span><span class="sxs-lookup"><span data-stu-id="a0b4e-145">User Added to a meeting</span></span>

<span data-ttu-id="a0b4e-146">Das `conversationUpdate` Ereignis mit dem `membersAdded` Objekt in der Nutzlast wird gesendet, wenn ein Benutzer zu einer privaten geplanten Besprechung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-146">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when a user is added to a private scheduled meeting.</span></span> <span data-ttu-id="a0b4e-147">Die Ereignisdetails werden auch dann gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-147">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="a0b4e-148">Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, verfügt das membersAdded-Payload-Objekt nicht über `aadObjectId` field.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-148">When an anonymous user is added to a meeting, membersAdded payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="a0b4e-149">Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-149">When an anonymous user is added to a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was added by another presenter.</span></span>

#### <a name="schema-example-user-added-to-meeting"></a><span data-ttu-id="a0b4e-150">Schema Beispiel: zu Besprechung hinzugefügter Benutzer</span><span class="sxs-lookup"><span data-stu-id="a0b4e-150">Schema example: User added to meeting</span></span>

```json
{
   "membersAdded":[
      {
         "id":"229:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2020-09-29T21:11:38.6542339Z",
   "id":"f:a8cd1b51-9ddb-bd35-624b-7f7474165df8",
   "channelId":"msteams",
   "serviceUrl":"https://canary.botapi.skype.com/amer/",
   "from":{
      "id":"29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",
      "aadObjectId":"f30ba569-abef-4e97-8762-35f85cbae706"
   },
   "conversation":{
      "isGroup":true,
      "tenantId":"e15762ef-a8d8-416b-871c-25516354f1fe",
      "id":"19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"
   },
   "recipient":{
      "id":"28:3af3604a-d4fc-486b-911e-86fab41aa91c",
      "name":"EchoBot1_Rename"
   },
   "channelData":{
      "tenant":{
         "id":"e15762ef-a8d8-416b-871c-25516354f1fe"
      },
      "source":null,
      "meeting":{
         "id":"MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="
      }
   }
}

```

### <a name="bot-added-for-personal-context-only"></a><span data-ttu-id="a0b4e-151">Bot nur für persönlichen Kontext hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-151">Bot added for personal context only</span></span>

<span data-ttu-id="a0b4e-152">Ihr bot erhält ein `conversationUpdate` mit `membersAdded` , wenn ein Benutzer es direkt für persönlichen Chat hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-152">Your bot receives a `conversationUpdate` with `membersAdded` when a user adds it directly for personal chat.</span></span> <span data-ttu-id="a0b4e-153">In diesem Fall enthält die von Ihrem bot empfangene Nutzlast das `channelData.team` Objekt nicht.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-153">In this case, the payload that your bot receives doesn't contain the `channelData.team` object.</span></span> <span data-ttu-id="a0b4e-154">Sie sollten dies als Filter verwenden, falls Ihr bot je nach Bereich eine andere [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) anbieten soll.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-154">You should use this as a filter in case you want your bot to offer a different [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) depending on scope.</span></span>

> [!NOTE]
> <span data-ttu-id="a0b4e-155">Für Bots mit persönlicher Reichweite empfängt Ihr bot das `conversationUpdate` Ereignis mehrmals, auch wenn der bot entfernt und erneut hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-155">For personal scoped bots, your bot will  receive the `conversationUpdate` event multiple times, even if the bot is removed and re-added.</span></span> <span data-ttu-id="a0b4e-156">Für die Entwicklung und das Testen kann es hilfreich sein, eine Hilfsfunktion hinzuzufügen, mit der Sie Ihren bot vollständig zurücksetzen können.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-156">For development and testing you may find it useful to add a helper function that will allow you to reset your bot completely.</span></span> <span data-ttu-id="a0b4e-157">Weitere Informationen zur Implementierung dieses Beispiels finden Sie unter [Node.js Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) oder [C#-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) .</span><span class="sxs-lookup"><span data-stu-id="a0b4e-157">See a [Node.js example](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) or [C# example](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) for more details on implementing this.</span></span>

#### <a name="schema-example-bot-added-to-personal-context"></a><span data-ttu-id="a0b4e-158">Schema Beispiel: bot zum persönlichen Kontext hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-158">Schema example: bot added to personal context</span></span>

```json
{
  "membersAdded": [{
      "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
    },
    {
      "id": "29:<userID>",
      "aadObjectId": "***"
    }
  ],
  "type": "conversationUpdate",
  "timestamp": "2019-04-23T10:17:44.349Z",
  "id": "f:5f85c2ad",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:<USERID>",
    "aadObjectId": "**_"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "_*_"
  },
  "recipient": {
    "id": "28:<BOT ID>",
    "name": "<BOT NAME>"
  },
  "channelData": {
    "tenant": {
      "id": "<TENANT ID>"
    }
  }
}
```

## <a name="team-member-or-bot-removed"></a><span data-ttu-id="a0b4e-159">Team Mitglied oder bot entfernt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-159">Team member or bot removed</span></span>

<span data-ttu-id="a0b4e-160">Das `conversationUpdate` Ereignis mit dem `membersRemoved` Objekt in der Nutzlast wird gesendet, wenn entweder Ihr bot aus einem Team entfernt wird oder ein Benutzer aus einem Team entfernt wird, in dem ein bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-160">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when either your bot is removed from a team, or a user is removed from a team where a bot has been added.</span></span> <span data-ttu-id="a0b4e-161">Microsoft Teams fügt `eventType.teamMemberRemoved` das Objekt ebenfalls hinzu `channelData` .</span><span class="sxs-lookup"><span data-stu-id="a0b4e-161">Microsoft Teams also adds `eventType.teamMemberRemoved` in the `channelData` object.</span></span> <span data-ttu-id="a0b4e-162">Wie beim `membersAdded` Objekt sollten Sie das `membersRemoved` Objekt für die APP-ID Ihres bot analysieren, um festzustellen, wer entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-162">As with the `membersAdded` object, you should parse the `membersRemoved` object for your bot's App ID to determine who was removed.</span></span>

### <a name="schema-example-team-member-removed"></a><span data-ttu-id="a0b4e-163">Schema Beispiel: entferntes Team Mitglied</span><span class="sxs-lookup"><span data-stu-id="a0b4e-163">Schema example: Team member removed</span></span>

```json
{
    "membersRemoved": [
        {
            "id": "29:1_LCi5Up14pAy65yZuaJzG1uIT7ujYhjjSTsUNqjORsZHjLHKiQIBJa4cX2XsAsRoaY7va2w6ZymA9-1VtSY_g"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:37:06.96Z",
    "localTimestamp": "2017-02-23T12:37:06.96-07:00",
    "id": "f:d8a6a4aa",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient":
    {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberRemoved",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="user-removed-from-a-meeting"></a><span data-ttu-id="a0b4e-164">Benutzer wurde aus einer Besprechung entfernt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-164">User removed from a meeting</span></span>

<span data-ttu-id="a0b4e-165">Das `conversationUpdate` Ereignis mit dem `membersRemoved` Objekt in der Nutzlast wird gesendet, wenn ein Benutzer aus einer privaten geplanten Besprechung entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-165">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when a user is removed from a private scheduled meeting.</span></span> <span data-ttu-id="a0b4e-166">Die Ereignisdetails werden auch dann gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-166">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
><span data-ttu-id="a0b4e-167">_ Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, verfügt das membersRemoved-Payload-Objekt nicht über `aadObjectId` field.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-167">_ When an anonymous user is removed from a meeting, membersRemoved payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="a0b4e-168">Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-168">When an anonymous user is removed from a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was removed by another presenter.</span></span>

#### <a name="schema-example-user-removed-from-meeting"></a><span data-ttu-id="a0b4e-169">Schema Beispiel: Benutzer wurde aus Besprechung entfernt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-169">Schema example: User removed from meeting</span></span>

<span data-ttu-id="a0b4e-170">{       "membersRemoved":        {           "ID": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"         }       ],       "Typ": "conversationUpdate",       "timestamp": "2020-09-29T21:15:08.6391139 z",       "ID": "f:ee8dfdf3-54AC-51de-05da-9d49514974bb",       "Kanalfactory": "msteams",       "serviceUrl": " https://canary.botapi.skype.com/amer/ ",       "from": {         "ID": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",         "aadObjectId": "f30ba569-ABEF-4e97-8762-35f85cbae706"       },       "Conversation": {  </span><span class="sxs-lookup"><span data-stu-id="a0b4e-170">{     "membersRemoved":      {         "id": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"       }     ],     "type": "conversationUpdate",     "timestamp": "2020-09-29T21:15:08.6391139Z",     "id": "f:ee8dfdf3-54ac-51de-05da-9d49514974bb",     "channelId": "msteams",     "serviceUrl": "https://canary.botapi.skype.com/amer/",     "from": {       "id": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",       "aadObjectId": "f30ba569-abef-4e97-8762-35f85cbae706"     },     "conversation": {  </span></span>  
    <span data-ttu-id="a0b4e-171">    "isGroup": true,         "Mandantenkennung": "e15762ef-a8d8-416b-871C-25516354f1fe",         "ID": "19: meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@Thread. v2"       },       "Recipient": {         "ID": "28:3af3604a-D4FC-486b-911e-86fab41aa91c",         "Name": "EchoBot1_Rename"       },       "channelData": {         "Mandant": {           "ID": "e15762ef-a8d8-416b-871C-25516354f1fe"         },         "Source": NULL,         "Besprechung": {           "ID": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA = ="         }       }    }</span><span class="sxs-lookup"><span data-stu-id="a0b4e-171">    "isGroup": true,       "tenantId": "e15762ef-a8d8-416b-871c-25516354f1fe",       "id": "19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"     },     "recipient": {       "id": "28:3af3604a-d4fc-486b-911e-86fab41aa91c",       "name": "EchoBot1_Rename"     },     "channelData": {       "tenant": {         "id": "e15762ef-a8d8-416b-871c-25516354f1fe"       },       "source": null,       "meeting": {         "id": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="       }     }   }</span></span>   

## <a name="team-name-updates"></a><span data-ttu-id="a0b4e-172">Team namens Updates</span><span class="sxs-lookup"><span data-stu-id="a0b4e-172">Team name updates</span></span>

> [!NOTE]
> <span data-ttu-id="a0b4e-173">Es gibt keine Funktionen zum Abfragen aller Team Namen, und der Teamname wird nicht in Nutzdaten von anderen Ereignissen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-173">There is no functionality to query all team names, and team name is not returned in payloads from other events.</span></span>

<span data-ttu-id="a0b4e-174">Ihr bot wird benachrichtigt, wenn das Team, in dem es sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-174">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="a0b4e-175">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` -Objekt.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-175">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span> <span data-ttu-id="a0b4e-176">Beachten Sie, dass es keine Benachrichtigungen zum Erstellen oder Löschen von Teams gibt, da Bots nur als Teil von Teams vorhanden sind und keine Sichtbarkeit außerhalb des Bereichs haben, in dem Sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-176">Please note that there are no notifications for team creation or deletion, because bots exist only as part of teams and have no visibility outside the scope in which they have been added.</span></span>

### <a name="schema-example-team-renamed"></a><span data-ttu-id="a0b4e-177">Schema Beispiel: Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="a0b4e-177">Schema example: Team renamed</span></span>

```json
{ 
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:35:56.825Z",
    "localTimestamp": "2017-02-23T12:35:56.825-07:00",
    "id": "f:1406033e",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/", 
    "from": { 
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    }, 
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": { 
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype",
            "name": "New Team Name"
        },
        "eventType": "teamRenamed",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

## <a name="channel-updates"></a><span data-ttu-id="a0b4e-178">Kanal Aktualisierungen</span><span class="sxs-lookup"><span data-stu-id="a0b4e-178">Channel updates</span></span>

<span data-ttu-id="a0b4e-179">Ihr bot wird benachrichtigt, wenn ein Kanal in einem Team erstellt, umbenannt oder gelöscht wurde, in dem er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-179">Your bot is notified when a channel is created, renamed, or deleted in a team where it has been added.</span></span> <span data-ttu-id="a0b4e-180">Erneut wird das `conversationUpdate` Ereignis empfangen, und eine Teams-spezifische Ereignis-ID wird als Teil des Objekts gesendet `channelData.eventType` , wobei die Kanaldaten  `channel.id` die GUID für den Kanal ist und `channel.name` den Kanalnamen selbst enthält.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-180">Again, the `conversationUpdate` event is received, and a Teams-specific event identifier is sent as part of the `channelData.eventType` object, where the channel data's  `channel.id` is the GUID for the channel, and `channel.name` contains the channel name itself.</span></span>

<span data-ttu-id="a0b4e-181">Die Kanal Ereignisse lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a0b4e-181">The channel events are as follows:</span></span>

* <span data-ttu-id="a0b4e-182">**channelCreated** &emsp; Ein Benutzer fügt dem Team einen neuen Kanal hinzu.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-182">**channelCreated**&emsp;A user adds a new channel to the team</span></span>
* <span data-ttu-id="a0b4e-183">**channelRenamed** &emsp; Ein Benutzer benennt einen vorhandenen Kanal um</span><span class="sxs-lookup"><span data-stu-id="a0b4e-183">**channelRenamed**&emsp;A user renames an existing channel</span></span>
* <span data-ttu-id="a0b4e-184">**channelDeleted** &emsp; Ein Benutzer entfernt einen Kanal</span><span class="sxs-lookup"><span data-stu-id="a0b4e-184">**channelDeleted**&emsp;A user removes a channel</span></span>

### <a name="full-schema-example-channelcreated"></a><span data-ttu-id="a0b4e-185">Vollständiges Schemabeispiel: channelCreated</span><span class="sxs-lookup"><span data-stu-id="a0b4e-185">Full schema example: channelCreated</span></span>

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "FunDiscussions"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelCreated",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a><span data-ttu-id="a0b4e-186">Schema Auszug: channelData für channelRenamed</span><span class="sxs-lookup"><span data-stu-id="a0b4e-186">Schema excerpt: channelData for channelRenamed</span></span>

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelRenamed",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a><span data-ttu-id="a0b4e-187">Schema Auszug: channelData für channelDeleted</span><span class="sxs-lookup"><span data-stu-id="a0b4e-187">Schema excerpt: channelData for channelDeleted</span></span>

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelDeleted",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

## <a name="reactions"></a><span data-ttu-id="a0b4e-188">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="a0b4e-188">Reactions</span></span>

<span data-ttu-id="a0b4e-189">Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer seine Reaktion auf eine Nachricht hinzufügt oder entfernt, die ursprünglich von Ihrem bot gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-189">The `messageReaction` event is sent when a user adds or removes his or her reaction to a message which was originally sent by your bot.</span></span> <span data-ttu-id="a0b4e-190">`replyToId` enthält die ID der jeweiligen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="a0b4e-190">`replyToId` contains the ID of the specific message.</span></span>

### <a name="schema-example-a-user-likes-a-message"></a><span data-ttu-id="a0b4e-191">Schema Beispiel: ein Benutzer mag eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="a0b4e-191">Schema example: A user likes a message</span></span>

```json
{
    "reactionsAdded": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

### <a name="schema-example-a-user-un-likes-a-message"></a><span data-ttu-id="a0b4e-192">Schema Beispiel: ein Benutzer Unlike a Message</span><span class="sxs-lookup"><span data-stu-id="a0b4e-192">Schema example: A user un-likes a message</span></span>

```json
{
    "reactionsRemoved": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```
