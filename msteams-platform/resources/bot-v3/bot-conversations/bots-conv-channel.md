---
title: Kanal-und Gruppenchat Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario, dass eine Unterhaltung mit einem bot in einem Kanal in Microsoft Teams vorliegt.
keywords: Teams Szenarien Kanäle Conversation bot
ms.date: 06/25/2019
ms.openlocfilehash: f44db4a88ab5e6541c52395a58fc643cb07df606
ms.sourcegitcommit: b3962a7b36f260aef1af9124d14d71ae08b01ac4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "47303724"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="3798f-104">Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="3798f-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="3798f-105">Microsoft Teams ermöglicht es Benutzern, Bots in Ihren Kanal-oder Gruppenchat-Unterhaltungen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="3798f-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="3798f-106">Durch Hinzufügen eines bot zu einem Team oder Chat können alle Benutzer der Unterhaltung die bot-Funktionalität direkt in der Unterhaltung nutzen.</span><span class="sxs-lookup"><span data-stu-id="3798f-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="3798f-107">Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres bot zugreifen, wie Team Informationen Abfragen und @mentioning Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3798f-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="3798f-108">Chat in Kanälen und Gruppenchats unterscheiden sich vom persönlichen Chat dadurch, dass der Benutzer den bot @mention muss.</span><span class="sxs-lookup"><span data-stu-id="3798f-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="3798f-109">Wenn ein bot in mehreren Bereichen (Personal, Groupchat oder Kanal) verwendet wird, müssen Sie ermitteln, von welchem Bereich die bot-Nachrichten stammen, und diese entsprechend verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="3798f-109">If a bot is used in multiple scopes (personal, groupchat or channel) you will need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="3798f-110">Entwerfen eines großen bot für Kanäle oder Gruppen</span><span class="sxs-lookup"><span data-stu-id="3798f-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="3798f-111">Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied und können als Teil der Unterhaltung @mentioned werden.</span><span class="sxs-lookup"><span data-stu-id="3798f-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="3798f-112">Bots empfangen tatsächlich nur Nachrichten, wenn Sie @mentioned sind, sodass andere Unterhaltungen im Kanal nicht an den bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="3798f-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="3798f-113">Ein bot in einer Gruppe oder einem Kanal sollte Informationen enthalten, die für alle Mitglieder relevant und angemessen sind.</span><span class="sxs-lookup"><span data-stu-id="3798f-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="3798f-114">Während Ihr bot sicherlich alle Informationen zur Verfügung stellen kann, die für die Benutzeroberfläche relevant sind, sollten Sie berücksichtigen, dass die Unterhaltungen für alle sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="3798f-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="3798f-115">Ein großer bot in einer Gruppe oder einem Kanal sollte daher allen Benutzern einen Mehrwert geben und sicherlich nicht versehentlich Informationen für eine 1:1-Unterhaltung freigeben.</span><span class="sxs-lookup"><span data-stu-id="3798f-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="3798f-116">Ihr Bot kann, so wie er ist, in allen Bereichen ganz relevant sein, ohne dass zusätzliche Arbeit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3798f-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="3798f-117">In Microsoft Teams wird nicht davon ausgegangen, dass Ihre bot-Funktion in allen Bereichen, aber Sie sollten sicherstellen, dass Ihr bot Benutzerwert in welchem Bereich (n), die Sie zur Unterstützung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="3798f-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="3798f-118">Weitere Informationen zu Bereichen finden Sie unter [apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3798f-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="3798f-119">Die Entwicklung eines bot, der in Gruppen oder Kanälen funktioniert, verwendet einen Großteil derselben Funktionalität wie persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="3798f-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="3798f-120">Zusätzliche Ereignisse und Daten in der Nutzlast bieten Teams-Gruppen-und Kanalinformationen.</span><span class="sxs-lookup"><span data-stu-id="3798f-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="3798f-121">Diese Unterschiede sowie wesentliche Unterschiede in der allgemeinen Funktionalität werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3798f-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="3798f-122">Erstellen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3798f-122">Creating messages</span></span>

<span data-ttu-id="3798f-123">Weitere Informationen zu Bots zum Erstellen von Nachrichten in Kanälen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)und speziell [Erstellen einer Kanal Unterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="3798f-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="3798f-124">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3798f-124">Receiving messages</span></span>

<span data-ttu-id="3798f-125">Für einen bot in einer Gruppe oder einem Kanal erhält Ihr bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity)auch die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="3798f-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="3798f-126">`channelData` Weitere Informationen finden Sie unter [Teams-Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="3798f-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="3798f-127">In einem Gruppenchat enthält Informationen, die für diesen Chat spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="3798f-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="3798f-128">`conversation.id` Die Antwortketten-ID, bestehend aus Kanal-ID und der ID der ersten Nachricht in der Antwort Kette</span><span class="sxs-lookup"><span data-stu-id="3798f-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain</span></span>
* <span data-ttu-id="3798f-129">`conversation.isGroup` Ist `true` für bot-Nachrichten in Kanälen oder Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="3798f-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats</span></span>
* <span data-ttu-id="3798f-130">`conversation.conversationType` Entweder `groupChat` oder `channel`</span><span class="sxs-lookup"><span data-stu-id="3798f-130">`conversation.conversationType` Either `groupChat` or `channel`</span></span>
* <span data-ttu-id="3798f-131">`entities` Kann ein oder mehrere Erwähnungen enthalten (siehe [Erwähnungen](#-mentions))</span><span class="sxs-lookup"><span data-stu-id="3798f-131">`entities` Can contain one or more mentions (see [Mentions](#-mentions))</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="3798f-132">Antworten auf Nachrichten</span><span class="sxs-lookup"><span data-stu-id="3798f-132">Replying to messages</span></span>

<span data-ttu-id="3798f-133">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) .net oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js auf.</span><span class="sxs-lookup"><span data-stu-id="3798f-133">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="3798f-134">Das Robot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="3798f-134">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="3798f-135">Wenn Sie sich für die Verwendung der Rest-API entscheiden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3798f-135">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="3798f-136">In einem Kanal wird eine Antwort auf eine Nachricht als Antwort auf die initiierende Antwort Kette angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3798f-136">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="3798f-137">Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="3798f-137">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="3798f-138">Obwohl sich das bot-Framework um die Details kümmert, können Sie dieses `conversation.id` bei Bedarf für zukünftige Antworten auf diesen Gesprächs Thread Zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="3798f-138">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="3798f-139">Bewährte Methode: Willkommensnachrichten in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3798f-139">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="3798f-140">Wenn Ihr bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es generell sinnvoll, eine Willkommensnachricht zu senden, die den bot allen Benutzern vorstellt.</span><span class="sxs-lookup"><span data-stu-id="3798f-140">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="3798f-141">Die Willkommensnachricht sollte eine Beschreibung der Funktionen und Benutzer Vorteile des bot enthalten.</span><span class="sxs-lookup"><span data-stu-id="3798f-141">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="3798f-142">Im Idealfall sollte die Nachricht auch Befehle enthalten, damit der Benutzer mit der APP interagieren können.</span><span class="sxs-lookup"><span data-stu-id="3798f-142">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="3798f-143">Stellen Sie dazu sicher, dass Ihr bot auf die `conversationUpdate` Nachricht reagiert, wobei der `teamsAddMembers` eventType im `channelData` Objekt ist.</span><span class="sxs-lookup"><span data-stu-id="3798f-143">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="3798f-144">Stellen Sie sicher, dass die `memberAdded` ID die APP-ID des bot selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="3798f-144">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="3798f-145">Weitere Informationen finden Sie unter [Team Mitglied oder bot-Erweiterung](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) .</span><span class="sxs-lookup"><span data-stu-id="3798f-145">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="3798f-146">Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="3798f-146">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="3798f-147">Dazu können Sie [das Team-Dienstplan abrufen](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)senden.</span><span class="sxs-lookup"><span data-stu-id="3798f-147">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="3798f-148">Es wird empfohlen, dass Ihr bot in den folgenden Situationen *keine* Willkommensnachricht sendet:</span><span class="sxs-lookup"><span data-stu-id="3798f-148">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="3798f-149">Das Team ist groß (offensichtlich subjektiv, aber zum Beispiel größer als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="3798f-149">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="3798f-150">Ihr bot wird möglicherweise als "spammy" angesehen, und die Person, die Sie hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen dem Benutzer, der die Willkommensnachricht sieht, eindeutig den Wert Vorschlag Ihres bot mit.</span><span class="sxs-lookup"><span data-stu-id="3798f-150">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="3798f-151">Ihr bot wird erstmals in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten hinzufügen zu einem Team).</span><span class="sxs-lookup"><span data-stu-id="3798f-151">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="3798f-152">Eine Gruppe oder ein Kanal wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="3798f-152">A group or channel is renamed</span></span>
* <span data-ttu-id="3798f-153">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3798f-153">A team member is added to a group or channel</span></span>

## <a name="-mentions"></a><span data-ttu-id="3798f-154">@ Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="3798f-154">@ Mentions</span></span>

<span data-ttu-id="3798f-155">Da Bots in einer Gruppe oder einem Kanal nur dann reagieren, wenn Sie in einer Nachricht erwähnt werden ("@_botname_"), enthält jede Nachricht, die von einem bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass Ihre Nachrichten Analyse diese behandelt.</span><span class="sxs-lookup"><span data-stu-id="3798f-155">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="3798f-156">Darüber hinaus können Bots andere Benutzer, die erwähnt werden, analysieren und Benutzer als Teil Ihrer Nachrichten erwähnen.</span><span class="sxs-lookup"><span data-stu-id="3798f-156">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="3798f-157">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="3798f-157">Retrieving mentions</span></span>

<span data-ttu-id="3798f-158">Erwähnungen werden im `entities` Objekt in Payload zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="3798f-158">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="3798f-159">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im bot Builder SDK für .net aufrufen, wodurch ein Array von Objekten zurückgegeben wird `Mentioned` .</span><span class="sxs-lookup"><span data-stu-id="3798f-159">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="3798f-160">.NET-Beispielcode: überprüfen und entfernen @bot Erwähnung</span><span class="sxs-lookup"><span data-stu-id="3798f-160">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="3798f-161">Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `GetTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.</span><span class="sxs-lookup"><span data-stu-id="3798f-161">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="3798f-162">Node.js Beispielcode: überprüfen und entfernen @bot Erwähnung</span><span class="sxs-lookup"><span data-stu-id="3798f-162">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="3798f-163">Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `getTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.</span><span class="sxs-lookup"><span data-stu-id="3798f-163">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="3798f-164">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="3798f-164">Constructing mentions</span></span>

<span data-ttu-id="3798f-165">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden.</span><span class="sxs-lookup"><span data-stu-id="3798f-165">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="3798f-166">Hierzu muss Ihre Nachricht folgendermaßen vorgehen:</span><span class="sxs-lookup"><span data-stu-id="3798f-166">To do this, your message must do the following:</span></span>

* <span data-ttu-id="3798f-167">`<at>@username</at>`In den Nachrichtentext einbeziehen</span><span class="sxs-lookup"><span data-stu-id="3798f-167">Include `<at>@username</at>` in the message text</span></span>
* <span data-ttu-id="3798f-168">Einschließen des `mention` Objekts in die Entities-Auflistung</span><span class="sxs-lookup"><span data-stu-id="3798f-168">Include the `mention` object inside the entities collection</span></span>

#### <a name="net-example"></a><span data-ttu-id="3798f-169">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="3798f-169">.NET example</span></span>

<span data-ttu-id="3798f-170">In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.</span><span class="sxs-lookup"><span data-stu-id="3798f-170">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="3798f-171">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="3798f-171">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="3798f-172">Beispiel: ausgehende Nachricht mit erwähntem Benutzer</span><span class="sxs-lookup"><span data-stu-id="3798f-172">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="3798f-173">Zugreifen auf groupChat oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="3798f-173">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="3798f-174">Ihr Bot kann mehr als senden und empfangen von Nachrichten in Gruppen und Teams.</span><span class="sxs-lookup"><span data-stu-id="3798f-174">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="3798f-175">Beispielsweise kann es auch die Liste der Mitglieder, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle abrufen.</span><span class="sxs-lookup"><span data-stu-id="3798f-175">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="3798f-176">Weitere Informationen finden Sie unter [Kontext für Ihren Microsoft Teams-bot abrufen](~/resources/bot-v3/bots-context.md) .</span><span class="sxs-lookup"><span data-stu-id="3798f-176">See [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md) to learn more.</span></span>

<span data-ttu-id="3798f-177">*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="3798f-177">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
