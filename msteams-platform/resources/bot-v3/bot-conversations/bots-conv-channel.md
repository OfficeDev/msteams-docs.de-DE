---
title: Kanal-und Gruppenchat Unterhaltungen mit Bots
description: Beschreibt das End-to-End-Szenario, dass eine Unterhaltung mit einem bot in einem Kanal in Microsoft Teams vorliegt.
keywords: Teams Szenarien Kanäle Conversation bot
ms.date: 06/25/2019
ms.openlocfilehash: d2d72bdba43de6ebb10c7504dd309459cb09d56c
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "44801279"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="1c4d9-104">Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="1c4d9-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="1c4d9-105">Microsoft Teams ermöglicht es Benutzern, Bots in Ihren Kanal-oder Gruppenchat-Unterhaltungen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="1c4d9-106">Durch Hinzufügen eines bot zu einem Team oder Chat können alle Benutzer der Unterhaltung die bot-Funktionalität direkt in der Unterhaltung nutzen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="1c4d9-107">Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres bot zugreifen, wie Team Informationen Abfragen und @mentioning Benutzer.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="1c4d9-108">Chat in Kanälen und Gruppenchats unterscheiden sich vom persönlichen Chat dadurch, dass der Benutzer den bot @mention muss.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="1c4d9-109">Wenn ein bot in mehreren Bereichen (Personal, Groupchat oder Kanal) verwendet wird, müssen Sie ermitteln, von welchem Bereich die bot-Nachrichten stammen, und diese entsprechend verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-109">If a bot is used in multiple scopes (personal, groupchat or channel) you will need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="1c4d9-110">Entwerfen eines großen bot für Kanäle oder Gruppen</span><span class="sxs-lookup"><span data-stu-id="1c4d9-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="1c4d9-111">Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied, das als Teil der Unterhaltung @mentioned werden kann.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-111">Bots added to a team become another team member, who can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="1c4d9-112">Bots empfangen tatsächlich nur Nachrichten, wenn Sie @mentioned sind, sodass andere Unterhaltungen im Kanal nicht an den bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

> [!NOTE]
> <span data-ttu-id="1c4d9-113">Zur Vereinfachung beim Antworten auf bot-Nachrichten in einem Kanal wird der Name des bot automatisch im Meldungsfeld verfassen vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-113">For convenience when replying to bot messages in a channel, the bot name is prepended in the compose message box automatically.</span></span>

<span data-ttu-id="1c4d9-114">Ein bot in einer Gruppe oder einem Kanal sollte Informationen enthalten, die für alle Mitglieder relevant und angemessen sind.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-114">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="1c4d9-115">Während Ihr bot sicherlich alle Informationen zur Verfügung stellen kann, die für die Benutzeroberfläche relevant sind, sollten Sie berücksichtigen, dass die Unterhaltungen für alle sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-115">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="1c4d9-116">Ein großer bot in einer Gruppe oder einem Kanal sollte daher allen Benutzern einen Mehrwert geben und sicherlich nicht versehentlich Informationen in einer 1:1-Unterhaltung besser austauschen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-116">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate in a one-to-one conversation.</span></span>

<span data-ttu-id="1c4d9-117">Ihr bot ist möglicherweise vollständig relevant in allen Bereichen, und es ist keine nennenswerte zusätzliche Arbeit erforderlich, damit Ihr bot über diese hinweg arbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-117">Your bot might be entirely relevant in all scopes as is, and no significant extra work is required to allow your bot to work across them.</span></span> <span data-ttu-id="1c4d9-118">In Microsoft Teams wird nicht davon ausgegangen, dass Ihre bot-Funktion in allen Bereichen, aber Sie sollten sicherstellen, dass Ihr bot Benutzerwert in welchem Bereich (n), die Sie zur Unterstützung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-118">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="1c4d9-119">Weitere Informationen zu Bereichen finden Sie unter [apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-119">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="1c4d9-120">Die Entwicklung eines bot, der in Gruppen oder Kanälen funktioniert, verwendet einen Großteil der gleichen Funktionalität aus persönlichen Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-120">Developing a bot that works in groups or channels uses much of the same functionality from personal conversations.</span></span> <span data-ttu-id="1c4d9-121">Zusätzliche Ereignisse und Daten in der Nutzlast bieten Teams-Gruppen-und Kanalinformationen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-121">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="1c4d9-122">Diese Unterschiede sowie wesentliche Unterschiede in der allgemeinen Funktionalität werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-122">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="1c4d9-123">Erstellen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1c4d9-123">Creating messages</span></span>

<span data-ttu-id="1c4d9-124">Weitere Informationen zu Bots zum Erstellen von Nachrichten in Kanälen finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)und speziell [Erstellen einer Kanal Unterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-124">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="1c4d9-125">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1c4d9-125">Receiving messages</span></span>

<span data-ttu-id="1c4d9-126">Für einen bot in einer Gruppe oder einem Kanal erhält Ihr bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity)auch die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="1c4d9-126">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="1c4d9-127">`channelData`Weitere Informationen finden Sie unter [Teams-Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-127">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="1c4d9-128">In einem Gruppenchat enthält Informationen, die für diesen Chat spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-128">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="1c4d9-129">`conversation.id`Die Antwortketten-ID, bestehend aus Kanal-ID und der ID der ersten Nachricht in der Antwort Kette</span><span class="sxs-lookup"><span data-stu-id="1c4d9-129">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain</span></span>
* <span data-ttu-id="1c4d9-130">`conversation.isGroup`Ist `true` für bot-Nachrichten in Kanälen oder Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="1c4d9-130">`conversation.isGroup` Is `true` for bot messages in channels or group chats</span></span>
* <span data-ttu-id="1c4d9-131">`conversation.conversationType`Entweder `groupChat` oder`channel`</span><span class="sxs-lookup"><span data-stu-id="1c4d9-131">`conversation.conversationType` Either `groupChat` or `channel`</span></span>
* <span data-ttu-id="1c4d9-132">`entities`Kann ein oder mehrere Erwähnungen enthalten (siehe [Erwähnungen](#-mentions))</span><span class="sxs-lookup"><span data-stu-id="1c4d9-132">`entities` Can contain one or more mentions (see [Mentions](#-mentions))</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="1c4d9-133">Antworten auf Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1c4d9-133">Replying to messages</span></span>

<span data-ttu-id="1c4d9-134">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) .net oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js auf.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-134">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="1c4d9-135">Das Robot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-135">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="1c4d9-136">Wenn Sie sich für die Verwendung der Rest-API entscheiden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-136">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="1c4d9-137">In einem Kanal wird eine Antwort auf eine Nachricht als Antwort auf die initiierende Antwort Kette angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-137">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="1c4d9-138">Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-138">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="1c4d9-139">Obwohl sich das bot-Framework um die Details kümmert, können Sie dieses `conversation.id` bei Bedarf für zukünftige Antworten auf diesen Gesprächs Thread Zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-139">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="1c4d9-140">Bewährte Methode: Willkommensnachrichten in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1c4d9-140">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="1c4d9-141">Wenn Ihr bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es generell sinnvoll, eine Willkommensnachricht zu senden, die den bot allen Benutzern vorstellt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-141">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="1c4d9-142">Die Willkommensnachricht sollte eine Beschreibung der Funktionen und Benutzer Vorteile des bot enthalten.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-142">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="1c4d9-143">Im Idealfall sollte die Nachricht auch Befehle enthalten, damit der Benutzer mit der APP interagieren können.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-143">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="1c4d9-144">Stellen Sie dazu sicher, dass Ihr bot auf die `conversationUpdate` Nachricht reagiert, wobei der `teamsAddMembers` eventType im `channelData` Objekt ist.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-144">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="1c4d9-145">Stellen Sie sicher, dass die `memberAdded` ID die APP-ID des bot selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-145">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="1c4d9-146">Weitere Informationen finden Sie unter [Team Mitglied oder bot-Erweiterung](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) .</span><span class="sxs-lookup"><span data-stu-id="1c4d9-146">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="1c4d9-147">Möglicherweise möchten Sie auch eine persönliche Nachricht an jedes Mitglied des Teams senden, wenn der bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-147">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="1c4d9-148">Dazu können Sie [das Team-Dienstplan abrufen](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)senden.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-148">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="1c4d9-149">Es wird empfohlen, dass Ihr bot in den folgenden Situationen *keine* Willkommensnachricht sendet:</span><span class="sxs-lookup"><span data-stu-id="1c4d9-149">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="1c4d9-150">Das Team ist groß (offensichtlich subjektiv, aber zum Beispiel größer als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-150">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="1c4d9-151">Ihr bot wird möglicherweise als "spammy" angesehen, und die Person, die Sie hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie teilen dem Benutzer, der die Willkommensnachricht sieht, eindeutig den Wert Vorschlag Ihres bot mit.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-151">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="1c4d9-152">Ihr bot wird erstmals in einer Gruppe oder einem Kanal erwähnt (im Gegensatz zum ersten hinzufügen zu einem Team).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-152">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="1c4d9-153">Eine Gruppe oder ein Kanal wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-153">A group or channel is renamed</span></span>
* <span data-ttu-id="1c4d9-154">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-154">A team member is added to a group or channel</span></span>

## <a name="-mentions"></a><span data-ttu-id="1c4d9-155">@ Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="1c4d9-155">@ Mentions</span></span>

<span data-ttu-id="1c4d9-156">Da Bots in einer Gruppe oder einem Kanal nur dann reagieren, wenn Sie in einer Nachricht erwähnt werden ("@_botname_"), enthält jede Nachricht, die von einem bot in einem Gruppenkanal empfangen wird, einen eigenen Namen, und Sie müssen sicherstellen, dass Ihre Nachrichten Analyse diese behandelt.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-156">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="1c4d9-157">Darüber hinaus können Bots andere Benutzer, die erwähnt werden, analysieren und Benutzer als Teil Ihrer Nachrichten erwähnen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-157">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="1c4d9-158">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="1c4d9-158">Retrieving mentions</span></span>

<span data-ttu-id="1c4d9-159">Erwähnungen werden im `entities` Objekt in Payload zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des erwähnten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-159">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="1c4d9-160">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im bot Builder SDK für .net aufrufen, wodurch ein Array von Objekten zurückgegeben wird `Mentioned` .</span><span class="sxs-lookup"><span data-stu-id="1c4d9-160">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="1c4d9-161">.NET-Beispielcode: überprüfen und entfernen @bot Erwähnung</span><span class="sxs-lookup"><span data-stu-id="1c4d9-161">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="1c4d9-162">Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `GetTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-162">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="1c4d9-163">Node.js Beispielcode: überprüfen und entfernen @bot Erwähnung</span><span class="sxs-lookup"><span data-stu-id="1c4d9-163">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="1c4d9-164">Sie können auch die Microsoft Teams-Erweiterungsfunktion verwenden `getTextWithoutMentions` , die alle Erwähnungen, einschließlich des bot, abstreift.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-164">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="1c4d9-165">Erstellen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="1c4d9-165">Constructing mentions</span></span>

<span data-ttu-id="1c4d9-166">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gepostet wurden.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-166">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="1c4d9-167">Hierzu muss Ihre Nachricht folgendermaßen vorgehen:</span><span class="sxs-lookup"><span data-stu-id="1c4d9-167">To do this, your message must do the following:</span></span>

* <span data-ttu-id="1c4d9-168">`<at>@username</at>`In den Nachrichtentext einbeziehen</span><span class="sxs-lookup"><span data-stu-id="1c4d9-168">Include `<at>@username</at>` in the message text</span></span>
* <span data-ttu-id="1c4d9-169">Einschließen des `mention` Objekts in die Entities-Auflistung</span><span class="sxs-lookup"><span data-stu-id="1c4d9-169">Include the `mention` object inside the entities collection</span></span>

#### <a name="net-example"></a><span data-ttu-id="1c4d9-170">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="1c4d9-170">.NET example</span></span>

<span data-ttu-id="1c4d9-171">In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="1c4d9-172">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="1c4d9-172">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="1c4d9-173">Beispiel: ausgehende Nachricht mit erwähntem Benutzer</span><span class="sxs-lookup"><span data-stu-id="1c4d9-173">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="1c4d9-174">Zugreifen auf groupChat oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="1c4d9-174">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="1c4d9-175">Ihr Bot kann mehr als senden und empfangen von Nachrichten in Gruppen und Teams.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-175">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="1c4d9-176">Beispielsweise kann es auch die Liste der Mitglieder, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle abrufen.</span><span class="sxs-lookup"><span data-stu-id="1c4d9-176">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="1c4d9-177">Weitere Informationen finden Sie unter [Kontext für Ihren Microsoft Teams-bot abrufen](~/resources/bot-v3/bots-context.md) .</span><span class="sxs-lookup"><span data-stu-id="1c4d9-177">See [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md) to learn more.</span></span>

<span data-ttu-id="1c4d9-178">*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="1c4d9-178">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
