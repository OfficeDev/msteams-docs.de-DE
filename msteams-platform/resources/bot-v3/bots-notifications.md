---
title: Behandeln von Botereignissen
description: Beschreibt, wie Ereignisse in Bots für Microsoft Teams behandelt werden
keywords: Teams-Bots-Ereignisse
ms.date: 05/20/2019
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 6a9eaab388927fcff51d7883e1a61ca1cec81fac
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069076"
---
# <a name="handle-bot-events-in-microsoft-teams"></a><span data-ttu-id="7dde1-104">Behandeln von Botereignissen in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7dde1-104">Handle bot events in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="7dde1-105">Microsoft Teams sendet Benachrichtigungen an Ihren Bot für Änderungen oder Ereignisse, die in Bereichen auftreten, in denen Ihr Bot aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="7dde1-105">Microsoft Teams sends notifications to your bot for changes or events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="7dde1-106">Sie können diese Ereignisse verwenden, um Dienstlogik auszulösen, z. B.:</span><span class="sxs-lookup"><span data-stu-id="7dde1-106">You can use these events to trigger service logic, such as the following:</span></span>

* <span data-ttu-id="7dde1-107">Lösen Sie eine Willkommensnachricht aus, wenn Ihr Bot zu einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="7dde1-108">Abfragen und Zwischenspeichern von Gruppeninformationen, wenn der Bot einem Gruppenchat hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-108">Query and cache group information when the bot is added to a group chat.</span></span>
* <span data-ttu-id="7dde1-109">Aktualisieren sie zwischengespeicherte Informationen zur Teammitgliedschaft oder Kanalinformationen.</span><span class="sxs-lookup"><span data-stu-id="7dde1-109">Update cached information on team membership or channel information.</span></span>
* <span data-ttu-id="7dde1-110">Entfernt zwischengespeicherte Informationen für ein Team, wenn der Bot entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-110">Remove cached information for a team if the bot is removed.</span></span>
* <span data-ttu-id="7dde1-111">Wenn eine Bot-Nachricht von einem Benutzer gefällt.</span><span class="sxs-lookup"><span data-stu-id="7dde1-111">When a bot message is liked by a user.</span></span>

<span data-ttu-id="7dde1-112">Jedes Bot-Ereignis wird als `Activity` Objekt gesendet, in dem `messageType` definiert wird, welche Informationen im Objekt enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="7dde1-112">Each bot event is sent as an `Activity` object in which `messageType` defines what information is in the object.</span></span> <span data-ttu-id="7dde1-113">Nachrichten vom Typ finden Sie unter Senden und Empfangen von `message` [Nachrichten.](~/resources/bot-v3/bot-conversations/bots-conversations.md)</span><span class="sxs-lookup"><span data-stu-id="7dde1-113">For messages of type `message`, see [Sending and receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span></span>

<span data-ttu-id="7dde1-114">Teams- und Gruppenereignisse, die in der Regel vom Typ ausgelöst werden, verfügen über `conversationUpdate` zusätzliche Teams Ereignisinformationen, die als Teil des Objekts übergeben `channelData` werden. Daher muss der Ereignishandler die `channelData` Nutzlast nach der Teams und `eventType` zusätzlichen ereignisspezifischen Metadaten abfragen.</span><span class="sxs-lookup"><span data-stu-id="7dde1-114">Teams and group events, usually triggered off the `conversationUpdate` type, have additional Teams event information passed as part of the `channelData` object, and therefore your event handler must query the `channelData` payload for the Teams `eventType` and additional event-specific metadata.</span></span>

<span data-ttu-id="7dde1-115">In der folgenden Tabelle sind die Ereignisse aufgeführt, die Ihr Bot empfangen und entsprechende Maßnahmen ergreifen kann.</span><span class="sxs-lookup"><span data-stu-id="7dde1-115">The following table lists the events that your bot can receive and take action on.</span></span>

|<span data-ttu-id="7dde1-116">Typ</span><span class="sxs-lookup"><span data-stu-id="7dde1-116">Type</span></span>|<span data-ttu-id="7dde1-117">Payload-Objekt</span><span class="sxs-lookup"><span data-stu-id="7dde1-117">Payload object</span></span>|<span data-ttu-id="7dde1-118">Teams eventType</span><span class="sxs-lookup"><span data-stu-id="7dde1-118">Teams eventType</span></span> |<span data-ttu-id="7dde1-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dde1-119">Description</span></span>|<span data-ttu-id="7dde1-120">Bereich</span><span class="sxs-lookup"><span data-stu-id="7dde1-120">Scope</span></span>|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[<span data-ttu-id="7dde1-121">Mitglied zum Team hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7dde1-121">Member added to team</span></span>](#team-member-or-bot-addition)| <span data-ttu-id="7dde1-122">Alle</span><span class="sxs-lookup"><span data-stu-id="7dde1-122">all</span></span> |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[<span data-ttu-id="7dde1-123">Mitglied wurde aus Team entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-123">Member was removed from team</span></span>](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [<span data-ttu-id="7dde1-124">Team wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="7dde1-124">Team was renamed</span></span>](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [<span data-ttu-id="7dde1-125">Ein Kanal wurde erstellt</span><span class="sxs-lookup"><span data-stu-id="7dde1-125">A channel was created</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [<span data-ttu-id="7dde1-126">Ein Kanal wurde umbenannt</span><span class="sxs-lookup"><span data-stu-id="7dde1-126">A channel was renamed</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [<span data-ttu-id="7dde1-127">Ein Kanal wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="7dde1-127">A channel was deleted</span></span>](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [<span data-ttu-id="7dde1-128">Reaktion auf Bot-Nachricht</span><span class="sxs-lookup"><span data-stu-id="7dde1-128">Reaction to bot message</span></span>](#reactions)| <span data-ttu-id="7dde1-129">Alle</span><span class="sxs-lookup"><span data-stu-id="7dde1-129">all</span></span> |
| `messageReaction` |`reactionsRemoved`|| [<span data-ttu-id="7dde1-130">Reaktion aus Botnachricht entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-130">Reaction removed from bot message</span></span>](#reactions)| <span data-ttu-id="7dde1-131">Alle</span><span class="sxs-lookup"><span data-stu-id="7dde1-131">all</span></span> |

## <a name="team-member-or-bot-addition"></a><span data-ttu-id="7dde1-132">Hinzufügen eines Teammitglieds oder Bots</span><span class="sxs-lookup"><span data-stu-id="7dde1-132">Team member or bot addition</span></span>

<span data-ttu-id="7dde1-133">Das [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) Ereignis wird an Ihren Bot gesendet, wenn er Informationen zu Mitgliedschaftsupdates für Teams empfängt, in denen es hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-133">The [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="7dde1-134">Er empfängt außerdem eine Aktualisierung, wenn er zum ersten Mal hinzugefügt wurde, speziell für persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="7dde1-134">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span> <span data-ttu-id="7dde1-135">Beachten Sie, dass die Benutzerinformationen ( `Id` ) für Ihren Bot eindeutig sind und für die zukünftige Verwendung durch Ihren Dienst zwischengespeichert werden können, z. B. das Senden einer Nachricht an einen bestimmten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7dde1-135">Note that the user information (`Id`) is unique for your bot and can be cached for future use by your service, such as, sending a message to a specific user.</span></span>

### <a name="bot-or-user-added-to-a-team"></a><span data-ttu-id="7dde1-136">Bot oder Benutzer, der einem Team hinzugefügt wurde</span><span class="sxs-lookup"><span data-stu-id="7dde1-136">Bot or user added to a team</span></span>

<span data-ttu-id="7dde1-137">Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersAdded` gesendet, wenn einem Team entweder ein Bot oder ein neuer Benutzer zu einem Team hinzugefügt wird, in dem ein Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-137">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when either a bot is added to a team or a new user is added to a team where a bot has been added.</span></span> <span data-ttu-id="7dde1-138">Microsoft Teams fügt `eventType.teamMemberAdded` auch das Objekt `channelData` hinzu.</span><span class="sxs-lookup"><span data-stu-id="7dde1-138">Microsoft Teams also adds `eventType.teamMemberAdded` in the `channelData` object.</span></span>

<span data-ttu-id="7dde1-139">Da dieses Ereignis in beiden Fällen gesendet wird, sollten Sie das `membersAdded` Objekt analysieren, um zu bestimmen, ob der Zusatz ein Benutzer oder der Bot selbst war.</span><span class="sxs-lookup"><span data-stu-id="7dde1-139">Because this event is sent in both cases, you should parse the `membersAdded` object to determine whether the addition was a user or the bot itself.</span></span> <span data-ttu-id="7dde1-140">Für Letzteres empfiehlt es sich, eine [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) an den Kanal zu senden, damit Benutzer die Features verstehen können, die Ihr Bot bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="7dde1-140">For the latter, a best practice is to send a [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) to the channel so users can understand the features your bot provides.</span></span>

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a><span data-ttu-id="7dde1-141">Beispielcode: Überprüfen, ob bot das hinzugefügte Mitglied war</span><span class="sxs-lookup"><span data-stu-id="7dde1-141">Example code: Checking whether bot was the added member</span></span>

##### <a name="net"></a><span data-ttu-id="7dde1-142">.NET</span><span class="sxs-lookup"><span data-stu-id="7dde1-142">.NET</span></span>

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

##### <a name="nodejs"></a><span data-ttu-id="7dde1-143">Node.js</span><span class="sxs-lookup"><span data-stu-id="7dde1-143">Node.js</span></span>

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

#### <a name="schema-example-bot-added-to-team"></a><span data-ttu-id="7dde1-144">Schemabeispiel: Bot zum Team hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7dde1-144">Schema example: Bot added to team</span></span>

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

### <a name="user-added-to-a-meeting"></a><span data-ttu-id="7dde1-145">Zu einer Besprechung hinzugefügter Benutzer</span><span class="sxs-lookup"><span data-stu-id="7dde1-145">User Added to a meeting</span></span>

<span data-ttu-id="7dde1-146">Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersAdded` gesendet, wenn ein Benutzer zu einer privaten geplanten Besprechung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-146">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when a user is added to a private scheduled meeting.</span></span> <span data-ttu-id="7dde1-147">Die Ereignisdetails werden auch gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="7dde1-147">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="7dde1-148">Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, verfügt das MembersAdded-Nutzlastobjekt nicht über `aadObjectId` ein Feld.</span><span class="sxs-lookup"><span data-stu-id="7dde1-148">When an anonymous user is added to a meeting, membersAdded payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="7dde1-149">Wenn ein anonymer Benutzer zu einer Besprechung hinzugefügt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-149">When an anonymous user is added to a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was added by another presenter.</span></span>

#### <a name="schema-example-user-added-to-meeting"></a><span data-ttu-id="7dde1-150">Schemabeispiel: Benutzer zur Besprechung hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7dde1-150">Schema example: User added to meeting</span></span>

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

### <a name="bot-added-for-personal-context-only"></a><span data-ttu-id="7dde1-151">Bot nur für persönlichen Kontext hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7dde1-151">Bot added for personal context only</span></span>

<span data-ttu-id="7dde1-152">Ihr Bot erhält ein `conversationUpdate` `membersAdded` With, wenn ein Benutzer ihn direkt für den persönlichen Chat hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="7dde1-152">Your bot receives a `conversationUpdate` with `membersAdded` when a user adds it directly for personal chat.</span></span> <span data-ttu-id="7dde1-153">In diesem Fall enthält die Nutzlast, die Ihr Bot empfängt, das `channelData.team` Objekt nicht.</span><span class="sxs-lookup"><span data-stu-id="7dde1-153">In this case, the payload that your bot receives doesn't contain the `channelData.team` object.</span></span> <span data-ttu-id="7dde1-154">Sie sollten dies als Filter verwenden, falls Ihr Bot je nach Umfang eine andere [Willkommensnachricht](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) anbieten soll.</span><span class="sxs-lookup"><span data-stu-id="7dde1-154">You should use this as a filter in case you want your bot to offer a different [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) depending on scope.</span></span>

> [!NOTE]
> <span data-ttu-id="7dde1-155">Bei bots mit persönlichem Bereich empfängt Ihr Bot das `conversationUpdate` Ereignis mehrmals, auch wenn der Bot entfernt und erneut hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-155">For personal scoped bots, your bot will  receive the `conversationUpdate` event multiple times, even if the bot is removed and re-added.</span></span> <span data-ttu-id="7dde1-156">Für Entwicklung und Tests kann es hilfreich sein, eine Hilfsfunktion hinzuzufügen, mit der Sie Ihren Bot vollständig zurücksetzen können.</span><span class="sxs-lookup"><span data-stu-id="7dde1-156">For development and testing you may find it useful to add a helper function that will allow you to reset your bot completely.</span></span> <span data-ttu-id="7dde1-157">Weitere Informationen zur Implementierung finden Sie in einem [Node.js Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) oder [C#-Beispiel.](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238)</span><span class="sxs-lookup"><span data-stu-id="7dde1-157">See a [Node.js example](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) or [C# example](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) for more details on implementing this.</span></span>

#### <a name="schema-example-bot-added-to-personal-context"></a><span data-ttu-id="7dde1-158">Schemabeispiel: Bot zum persönlichen Kontext hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="7dde1-158">Schema example: bot added to personal context</span></span>

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
    "aadObjectId": "***"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "***"
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

## <a name="team-member-or-bot-removed"></a><span data-ttu-id="7dde1-159">Teammitglied oder Bot entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-159">Team member or bot removed</span></span>

<span data-ttu-id="7dde1-160">Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersRemoved` gesendet, wenn entweder Ihr Bot aus einem Team oder ein Benutzer aus einem Team entfernt wird, in dem ein Bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-160">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when either your bot is removed from a team, or a user is removed from a team where a bot has been added.</span></span> <span data-ttu-id="7dde1-161">Microsoft Teams fügt `eventType.teamMemberRemoved` auch das Objekt `channelData` hinzu.</span><span class="sxs-lookup"><span data-stu-id="7dde1-161">Microsoft Teams also adds `eventType.teamMemberRemoved` in the `channelData` object.</span></span> <span data-ttu-id="7dde1-162">Wie beim `membersAdded` Objekt sollten Sie das Objekt für die `membersRemoved` App-ID Ihres Bots analysieren, um zu bestimmen, wer entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-162">As with the `membersAdded` object, you should parse the `membersRemoved` object for your bot's App ID to determine who was removed.</span></span>

### <a name="schema-example-team-member-removed"></a><span data-ttu-id="7dde1-163">Schemabeispiel: Teammitglied entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-163">Schema example: Team member removed</span></span>

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

### <a name="user-removed-from-a-meeting"></a><span data-ttu-id="7dde1-164">Benutzer aus einer Besprechung entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-164">User removed from a meeting</span></span>

<span data-ttu-id="7dde1-165">Das `conversationUpdate` Ereignis mit dem Objekt in der Nutzlast wird `membersRemoved` gesendet, wenn ein Benutzer aus einer privaten geplanten Besprechung entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="7dde1-165">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when a user is removed from a private scheduled meeting.</span></span> <span data-ttu-id="7dde1-166">Die Ereignisdetails werden auch gesendet, wenn anonyme Benutzer an der Besprechung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="7dde1-166">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="7dde1-167">Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, hat das membersRemoved-Nutzlastobjekt kein `aadObjectId` Feld.</span><span class="sxs-lookup"><span data-stu-id="7dde1-167">When an anonymous user is removed from a meeting, membersRemoved payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="7dde1-168">Wenn ein anonymer Benutzer aus einer Besprechung entfernt wird, `from` hat das Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn der anonyme Benutzer von einem anderen Referenten entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-168">When an anonymous user is removed from a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was removed by another presenter.</span></span>

#### <a name="schema-example-user-removed-from-meeting"></a><span data-ttu-id="7dde1-169">Schemabeispiel: Benutzer aus Besprechung entfernt</span><span class="sxs-lookup"><span data-stu-id="7dde1-169">Schema example: User removed from meeting</span></span>

```
{   
      "membersRemoved": 
        {  
          "id": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"   
        }   
      ],   
      "type": "conversationUpdate",   
      "timestamp": "2020-09-29T21:15:08.6391139Z",   
      "id": "f:ee8dfdf3-54ac-51de-05da-9d49514974bb",   
      "channelId": "msteams",   
      "serviceUrl": "https://canary.botapi.skype.com/amer/",   
      "from": {   
        "id": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",   
        "aadObjectId": "f30ba569-abef-4e97-8762-35f85cbae706"   
      },   
      "conversation": {    
        "isGroup": true,   
        "tenantId": "e15762ef-a8d8-416b-871c-25516354f1fe",   
        "id": "19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"   
      },   
      "recipient": {   
        "id": "28:3af3604a-d4fc-486b-911e-86fab41aa91c",   
        "name": "EchoBot1_Rename"   
      },   
      "channelData": {   
        "tenant": {   
          "id": "e15762ef-a8d8-416b-871c-25516354f1fe"   
        },   
        "source": null,   
        "meeting": {   
          "id": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="   
        }   
      }   
}
```

## <a name="team-name-updates"></a><span data-ttu-id="7dde1-170">Aktualisierungen von Teamnamen</span><span class="sxs-lookup"><span data-stu-id="7dde1-170">Team name updates</span></span>

> [!NOTE]
> <span data-ttu-id="7dde1-171">Es gibt keine Funktion zum Abfragen aller Teamnamen, und teamname wird nicht in Nutzlasten von anderen Ereignissen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7dde1-171">There is no functionality to query all team names, and team name is not returned in payloads from other events.</span></span>

<span data-ttu-id="7dde1-172">Ihr Bot wird benachrichtigt, wenn das Team, in dem er sich befindet, umbenannt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-172">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="7dde1-173">Es empfängt ein `conversationUpdate` Ereignis mit `eventType.teamRenamed` im `channelData` Objekt.</span><span class="sxs-lookup"><span data-stu-id="7dde1-173">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span> <span data-ttu-id="7dde1-174">Bitte beachten Sie, dass es keine Benachrichtigungen für die Erstellung oder Löschung von Teams gibt, da Bots nur als Teil von Teams vorhanden sind und keine Sichtbarkeit außerhalb des Bereichs haben, in dem sie hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="7dde1-174">Please note that there are no notifications for team creation or deletion, because bots exist only as part of teams and have no visibility outside the scope in which they have been added.</span></span>

### <a name="schema-example-team-renamed"></a><span data-ttu-id="7dde1-175">Schemabeispiel: Team umbenannt</span><span class="sxs-lookup"><span data-stu-id="7dde1-175">Schema example: Team renamed</span></span>

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

## <a name="channel-updates"></a><span data-ttu-id="7dde1-176">Kanalupdates</span><span class="sxs-lookup"><span data-stu-id="7dde1-176">Channel updates</span></span>

<span data-ttu-id="7dde1-177">Ihr Bot wird benachrichtigt, wenn ein Kanal in einem Team erstellt, umbenannt oder gelöscht wird, in dem er hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="7dde1-177">Your bot is notified when a channel is created, renamed, or deleted in a team where it has been added.</span></span> <span data-ttu-id="7dde1-178">Auch hier wird das `conversationUpdate` Ereignis empfangen, und ein Teams-spezifischer Ereignisbezeichner wird als Teil des `channelData.eventType` Objekts gesendet, wobei die Kanaldaten `channel.id` die GUID für den Kanal sind und den `channel.name` Kanalnamen selbst enthält.</span><span class="sxs-lookup"><span data-stu-id="7dde1-178">Again, the `conversationUpdate` event is received, and a Teams-specific event identifier is sent as part of the `channelData.eventType` object, where the channel data's  `channel.id` is the GUID for the channel, and `channel.name` contains the channel name itself.</span></span>

<span data-ttu-id="7dde1-179">Die Kanalereignisse sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7dde1-179">The channel events are as follows:</span></span>

* <span data-ttu-id="7dde1-180">**channelCreated** &emsp; Ein Benutzer fügt dem Team einen neuen Kanal hinzu.</span><span class="sxs-lookup"><span data-stu-id="7dde1-180">**channelCreated**&emsp;A user adds a new channel to the team.</span></span>
* <span data-ttu-id="7dde1-181">**channelRenamed** &emsp; Ein Benutzer benennt einen vorhandenen Kanal um.</span><span class="sxs-lookup"><span data-stu-id="7dde1-181">**channelRenamed**&emsp;A user renames an existing channel.</span></span>
* <span data-ttu-id="7dde1-182">**channelDeleted** &emsp; Ein Benutzer entfernt einen Kanal.</span><span class="sxs-lookup"><span data-stu-id="7dde1-182">**channelDeleted**&emsp;A user removes a channel.</span></span>

### <a name="full-schema-example-channelcreated"></a><span data-ttu-id="7dde1-183">Vollständiges Schemabeispiel: channelCreated</span><span class="sxs-lookup"><span data-stu-id="7dde1-183">Full schema example: channelCreated</span></span>

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

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a><span data-ttu-id="7dde1-184">Schemaauszug: channelData für channelRenamed</span><span class="sxs-lookup"><span data-stu-id="7dde1-184">Schema excerpt: channelData for channelRenamed</span></span>

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

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a><span data-ttu-id="7dde1-185">Schemaauszug: channelData for channelDeleted</span><span class="sxs-lookup"><span data-stu-id="7dde1-185">Schema excerpt: channelData for channelDeleted</span></span>

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

## <a name="reactions"></a><span data-ttu-id="7dde1-186">Reaktionen</span><span class="sxs-lookup"><span data-stu-id="7dde1-186">Reactions</span></span>

<span data-ttu-id="7dde1-187">Das `messageReaction` Ereignis wird gesendet, wenn ein Benutzer seine Reaktion auf eine Nachricht, die ursprünglich von Ihrem Bot gesendet wurde, hinzufügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="7dde1-187">The `messageReaction` event is sent when a user adds or removes his or her reaction to a message which was originally sent by your bot.</span></span> <span data-ttu-id="7dde1-188">`replyToId` enthält die ID der bestimmten Nachricht.</span><span class="sxs-lookup"><span data-stu-id="7dde1-188">`replyToId` contains the ID of the specific message.</span></span>

### <a name="schema-example-a-user-likes-a-message"></a><span data-ttu-id="7dde1-189">Schemabeispiel: Einem Benutzer gefällt eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="7dde1-189">Schema example: A user likes a message</span></span>

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

### <a name="schema-example-a-user-un-likes-a-message"></a><span data-ttu-id="7dde1-190">Schemabeispiel: Ein Benutzer hebt die Gefällt mir einer Nachricht auf</span><span class="sxs-lookup"><span data-stu-id="7dde1-190">Schema example: A user un-likes a message</span></span>

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
