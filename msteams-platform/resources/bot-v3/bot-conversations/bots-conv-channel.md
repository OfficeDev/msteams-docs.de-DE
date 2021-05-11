---
title: Kanal- und Gruppenchatunterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: teams scenarios channels conversation bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: 2eac067a75fc75c9991e8b30ec5d693d89ed8228
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019797"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="99569-104">Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="99569-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="99569-105">Microsoft Teams ermöglicht Benutzern, Bots in ihren Kanal oder Gruppenchatunterhaltungen zu bringen.</span><span class="sxs-lookup"><span data-stu-id="99569-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="99569-106">Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Botfunktionalität direkt in der Unterhaltung nutzen.</span><span class="sxs-lookup"><span data-stu-id="99569-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="99569-107">Sie können auch auf Teams-spezifischen Funktionen innerhalb Ihres Bots zugreifen, z. B. das Abfragen von Teaminformationen und @mentioning Benutzern.</span><span class="sxs-lookup"><span data-stu-id="99569-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="99569-108">Chats in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats, da der Benutzer den @mention muss.</span><span class="sxs-lookup"><span data-stu-id="99569-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="99569-109">Wenn ein Bot in mehreren Bereiche (persönlich, Groupchat oder Kanal) verwendet wird, müssen Sie erkennen, aus welchem Bereich die Botnachrichten stammten, und diese entsprechend verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="99569-109">If a bot is used in multiple scopes (personal, groupchat or channel) you will need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="99569-110">Entwerfen eines großartigen Bots für Kanäle oder Gruppen</span><span class="sxs-lookup"><span data-stu-id="99569-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="99569-111">Bots, die einem Team hinzugefügt wurden, werden ein weiteres Teammitglied und können @mentioned Teil der Unterhaltung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="99569-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="99569-112">Bots empfangen nachrichten nur, wenn sie @mentioned werden, sodass andere Unterhaltungen auf dem Kanal nicht an den Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="99569-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="99569-113">Ein Bot in einer Gruppe oder einem Kanal sollte relevante und für alle Mitglieder geeignete Informationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="99569-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="99569-114">Während Ihr Bot sicherlich alle informationen bereitstellen kann, die für die Erfahrung relevant sind, denken Sie daran, dass Unterhaltungen mit ihm für alle sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="99569-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="99569-115">Daher sollte ein großartiger Bot in einer Gruppe oder einem Kanal allen Benutzern einen Mehrwert bringen und sicher nicht versehentlich Informationen freigeben, die besser für eine 1:1-Unterhaltung geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="99569-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="99569-116">Ihr Bot ist möglicherweise in allen Bereiche vollständig relevant, ohne dass zusätzliche Arbeit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="99569-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="99569-117">In Microsoft Teams wird nicht erwartet, dass Ihre Botfunktion in allen Bereiche funktioniert. Sie sollten jedoch sicherstellen, dass Ihr Bot den Benutzerwert in welchem Bereich(n) Sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="99569-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="99569-118">Weitere Informationen zu Bereich finden Sie unter [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="99569-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="99569-119">Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, verwendet viele der gleichen Funktionen wie persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="99569-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="99569-120">Zusätzliche Ereignisse und Daten in der Nutzlast Teams Gruppen- und Kanalinformationen.</span><span class="sxs-lookup"><span data-stu-id="99569-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="99569-121">Diese Unterschiede sowie wichtige Unterschiede bei den allgemeinen Funktionen werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="99569-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="99569-122">Erstellen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="99569-122">Creating messages</span></span>

<span data-ttu-id="99569-123">Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktives Messaging](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)für Bots und insbesondere [Erstellen einer Kanal unterhaltung.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation)</span><span class="sxs-lookup"><span data-stu-id="99569-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="99569-124">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="99569-124">Receiving messages</span></span>

<span data-ttu-id="99569-125">Für einen Bot in einer Gruppe oder [](https://docs.botframework.com/core-concepts/reference/#activity)einem Kanal erhält ihr Bot zusätzlich zum regulären Nachrichtenschema auch die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="99569-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="99569-126">`channelData`Siehe [Teams Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="99569-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="99569-127">Enthält in einem Gruppenchat spezifische Informationen für diesen Chat.</span><span class="sxs-lookup"><span data-stu-id="99569-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="99569-128">`conversation.id` Die Antwortkette-ID, die aus Kanal-ID und der ID der ersten Nachricht in der Antwortkette besteht</span><span class="sxs-lookup"><span data-stu-id="99569-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain</span></span>
* <span data-ttu-id="99569-129">`conversation.isGroup` Ist `true` für Botnachrichten in Kanälen oder Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="99569-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats</span></span>
* <span data-ttu-id="99569-130">`conversation.conversationType` Entweder `groupChat` oder `channel`</span><span class="sxs-lookup"><span data-stu-id="99569-130">`conversation.conversationType` Either `groupChat` or `channel`</span></span>
* <span data-ttu-id="99569-131">`entities` Kann eine oder mehrere Erwähnungen enthalten (siehe [Erwähnungen](#-mentions))</span><span class="sxs-lookup"><span data-stu-id="99569-131">`entities` Can contain one or more mentions (see [Mentions](#-mentions))</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="99569-132">Antworten auf Nachrichten</span><span class="sxs-lookup"><span data-stu-id="99569-132">Replying to messages</span></span>

<span data-ttu-id="99569-133">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span><span class="sxs-lookup"><span data-stu-id="99569-133">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="99569-134">Das Bot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="99569-134">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="99569-135">Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="99569-135">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="99569-136">In einem Kanal wird die Antwort auf eine Nachricht als Antwort auf die initiierende Antwortkette angezeigt.</span><span class="sxs-lookup"><span data-stu-id="99569-136">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="99569-137">Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="99569-137">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="99569-138">Obwohl das Bot Framework sich um die Details kümmert, können Sie dies für zukünftige Antworten auf den `conversation.id` Unterhaltungsthread nach Bedarf zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="99569-138">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="99569-139">Bewährte Methode: Willkommensnachrichten in Teams</span><span class="sxs-lookup"><span data-stu-id="99569-139">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="99569-140">Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es im Allgemeinen hilfreich, eine Willkommensnachricht zu senden, in der der Bot für alle Benutzer eingeführt wird.</span><span class="sxs-lookup"><span data-stu-id="99569-140">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="99569-141">Die Willkommensnachricht sollte eine Beschreibung der Funktionalität und der Benutzervorteile des Bots enthalten.</span><span class="sxs-lookup"><span data-stu-id="99569-141">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="99569-142">Idealerweise sollte die Nachricht auch Befehle enthalten, mit denen der Benutzer mit der App interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="99569-142">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="99569-143">Stellen Sie dazu sicher, dass Ihr Bot auf die Nachricht mit `conversationUpdate` `teamsAddMembers` dem eventType im Objekt `channelData` antwortet.</span><span class="sxs-lookup"><span data-stu-id="99569-143">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="99569-144">Stellen Sie sicher, dass die ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem `memberAdded` Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="99569-144">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="99569-145">Weitere Informationen finden Sie unter [Teammitglied oder](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) Bot-Ergänzung.</span><span class="sxs-lookup"><span data-stu-id="99569-145">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="99569-146">Sie können auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der Bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="99569-146">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="99569-147">Dazu können Sie die [Teamliste](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) abrufen und jedem Benutzer eine direkte [Nachricht senden.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)</span><span class="sxs-lookup"><span data-stu-id="99569-147">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="99569-148">Es wird empfohlen, dass Ihr *Bot* in den folgenden Situationen keine Willkommensnachricht sendet:</span><span class="sxs-lookup"><span data-stu-id="99569-148">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="99569-149">Das Team ist groß (natürlich subjektiv, aber z. B. größer als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="99569-149">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="99569-150">Ihr Bot kann als "Spammy" betrachtet werden, und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen die Wertversprechen Ihres Bots jedem klar mit, der die Willkommensnachricht sieht.</span><span class="sxs-lookup"><span data-stu-id="99569-150">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="99569-151">Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten Hinzufügen zu einem Team)</span><span class="sxs-lookup"><span data-stu-id="99569-151">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="99569-152">Eine Gruppe oder ein Kanal wird umbenannt</span><span class="sxs-lookup"><span data-stu-id="99569-152">A group or channel is renamed</span></span>
* <span data-ttu-id="99569-153">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="99569-153">A team member is added to a group or channel</span></span>

## <a name="-mentions"></a><span data-ttu-id="99569-154">@ Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="99569-154">@ Mentions</span></span>

<span data-ttu-id="99569-155">Da Bots in einer Gruppe oder einem Kanal nur antworten, wenn sie in einer Nachricht ("@_botname")_ erwähnt werden, enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass die Nachrichten parsing dies verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="99569-155">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="99569-156">Darüber hinaus können Bots andere erwähnten Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.</span><span class="sxs-lookup"><span data-stu-id="99569-156">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="99569-157">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="99569-157">Retrieving mentions</span></span>

<span data-ttu-id="99569-158">Erwähnungen werden im Objekt in nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen `entities` des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="99569-158">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="99569-159">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die Funktion `GetMentions` im Bot Builder SDK für .NET aufrufen, das ein Array von Objekten `Mentioned` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="99569-159">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="99569-160">.NET-Beispielcode: Überprüfen sie, ob eine Erwähnung @bot wird.</span><span class="sxs-lookup"><span data-stu-id="99569-160">.NET example code: Check for and strip @bot mention</span></span>

```csharp
Mention[] m = sourceMessage.GetMentions();
var messageText = sourceMessage.Text;

for (int i = 0;i < m.Length;i++)
{
    if (m[i].Mentioned.Id == sourceMessage.Recipient.Id)
    {
        //Bot is in the @mention list.
        //The below example will strip the bot name out of the message, so you can parse it as if it wasn't included. Note that the Text object will contain the full bot name, if applicable.
        if (m[i].Text != null)
            messageText = messageText.Replace(m[i].Text, "");
    }
}
```

> [!NOTE]
> <span data-ttu-id="99569-161">Sie können auch die erweiterungsfunktion Teams, die alle Erwähnungen `GetTextWithoutMentions` ausstreift, einschließlich des Bots.</span><span class="sxs-lookup"><span data-stu-id="99569-161">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="99569-162">Node.js Beispielcode: Überprüfen sie, ob eine Erwähnung @bot wird.</span><span class="sxs-lookup"><span data-stu-id="99569-162">Node.js example code: Check for and strip @bot mention</span></span>

```javascript
var text = message.text;
if (message.entities) {
    message.entities
        .filter(entity => ((entity.type === "mention") && (entity.mentioned.id.toLowerCase() === botId)))
        .forEach(entity => {
            text = text.replace(entity.text, "");
        });
    text = text.trim();
}
```

<span data-ttu-id="99569-163">Sie können auch die erweiterungsfunktion Teams, die alle Erwähnungen `getTextWithoutMentions` ausstreift, einschließlich des Bots.</span><span class="sxs-lookup"><span data-stu-id="99569-163">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="99569-164">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="99569-164">Constructing mentions</span></span>

<span data-ttu-id="99569-165">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet werden.</span><span class="sxs-lookup"><span data-stu-id="99569-165">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="99569-166">Dazu muss Ihre Nachricht folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="99569-166">To do this, your message must do the following:</span></span>

* <span data-ttu-id="99569-167">In `<at>@username</at>` den Nachrichtentext eingeben</span><span class="sxs-lookup"><span data-stu-id="99569-167">Include `<at>@username</at>` in the message text</span></span>
* <span data-ttu-id="99569-168">Schließen Sie `mention` das Objekt in die Entitätssammlung ein.</span><span class="sxs-lookup"><span data-stu-id="99569-168">Include the `mention` object inside the entities collection</span></span>

#### <a name="net-example"></a><span data-ttu-id="99569-169">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="99569-169">.NET example</span></span>

<span data-ttu-id="99569-170">In diesem Beispiel wird das [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet verwendet.</span><span class="sxs-lookup"><span data-stu-id="99569-170">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="99569-171">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="99569-171">Node.js example</span></span>

```javascript
// User to mention
var toMention: builder.IIdentity = {
    name: 'John Doe',
    id: userId
};

// Create a message and add mention to it
var msg = new teams.TeamsMessage(session).text(teams.TeamsMessage.getTenantId(session.message));
var mentionedMsg = msg.addMentionToText(toMention);

// Post the message
var generalMessage = mentionedMsg.routeReplyToGeneralChannel();
session.send(generalMessage);
```

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="99569-172">Beispiel: Ausgehende Nachricht mit erwähnten Benutzern</span><span class="sxs-lookup"><span data-stu-id="99569-172">Example: Outgoing message with user mentioned</span></span>

```json
{
    "type": "message", 
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "28:9e52142b-5e5e-4d7b-bb3e- e82dcf620000",
        "name": "SchemaTestBot"
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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="99569-173">Zugreifen auf groupChat oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="99569-173">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="99569-174">Ihr Bot kann mehr als nachrichten in Gruppen und Teams senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="99569-174">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="99569-175">Beispielsweise kann sie auch die Liste der Mitglieder abrufen, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle.</span><span class="sxs-lookup"><span data-stu-id="99569-175">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="99569-176">Weitere Informationen finden Sie unter Get [context for your Microsoft Teams bot.](~/resources/bot-v3/bots-context.md)</span><span class="sxs-lookup"><span data-stu-id="99569-176">See [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md) to learn more.</span></span>

<span data-ttu-id="99569-177">*Siehe auch* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="99569-177">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
