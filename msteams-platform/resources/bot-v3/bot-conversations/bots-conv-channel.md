---
title: Kanal- und Gruppenchat-Gespräche mit Bots
description: Beschreibt das End-to-End-Szenario einer Unterhaltung mit einem Bot in einem Kanal in Microsoft Teams
keywords: Teams Szenarien Kanäle Konversation Bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: e254302271cf101638c897e1a1952d302705d6a4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566796"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="9a4c5-104">Kanal und Gruppenchatunterhaltungen mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="9a4c5-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="9a4c5-105">Microsoft Teams ermöglicht es Benutzern, Bots in ihren Kanal oder Gruppenchat-Gespräche zu bringen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="9a4c5-106">Durch Hinzufügen eines Bots zu einem Team oder Chat können alle Benutzer der Unterhaltung die Vorteile der Bot-Funktionalität direkt in der Unterhaltung nutzen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="9a4c5-107">Sie können auch auf Teams-spezifische Funktionen innerhalb Ihres Bots wie Abfragen von Teaminformationen und @mentioning Benutzer zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="9a4c5-108">Chat in Kanälen und Gruppenchats unterscheiden sich von persönlichen Chats dadurch, dass der Benutzer den Bot @mention muss.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="9a4c5-109">Wenn ein Bot in mehreren Bereichen wie Personal, Groupchat oder Channel verwendet wird, müssen Sie erkennen, aus welchem Bereich die Bot-Nachrichten stammen, und sie entsprechend verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-109">If a bot is used in multiple scopes such as personal, groupchat, or channel, you need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="9a4c5-110">Entwerfen eines großartigen Bots für Kanäle oder Gruppen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="9a4c5-111">Bots, die einem Team hinzugefügt werden, werden ein weiteres Teammitglied und können als Teil des Gesprächs @mentioned werden.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="9a4c5-112">Tatsächlich empfangen Bots Nachrichten nur, wenn sie @mentioned sind, so dass andere Unterhaltungen auf dem Kanal nicht an den Bot gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="9a4c5-113">Ein Bot in einer Gruppe oder einem Kanal sollte Informationen bereitstellen, die für alle Mitglieder relevant und angemessen sind.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="9a4c5-114">Während Ihr Bot kann sicherlich alle Informationen, die für die Erfahrung relevant, denken Sie daran, Gespräche mit ihm sind für jeden sichtbar.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="9a4c5-115">Daher sollte ein großartiger Bot in einer Gruppe oder einem Kanal allen Benutzern einen Mehrwert verleihen und sicherlich nicht versehentlich Informationen teilen, die für eine Einzelunterhaltung besser geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="9a4c5-116">Ihr Bot, so wie er ist, kann in allen Bereichen völlig relevant sein, ohne dass zusätzliche Arbeit erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="9a4c5-117">In Microsoft Teams gibt es keine Erwartung, dass Ihr Bot in allen Bereichen funktioniert, aber Sie sollten sicherstellen, dass Ihr Bot Benutzerwert in den Bereichen bietet, die Sie unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="9a4c5-118">Weitere Informationen zu Bereichen finden Sie [unter Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="9a4c5-119">Die Entwicklung eines Bots, der in Gruppen oder Kanälen funktioniert, verwendet viele der gleichen Funktionen wie persönliche Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="9a4c5-120">Zusätzliche Ereignisse und Daten in der Nutzlast stellen Teams Gruppen- und Kanalinformationen bereit.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="9a4c5-121">Diese Unterschiede sowie die wichtigsten Unterschiede in der allgemeinen Funktionalität werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="9a4c5-122">Erstellen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="9a4c5-122">Creating messages</span></span>

<span data-ttu-id="9a4c5-123">Weitere Informationen zu Bots, die Nachrichten in Kanälen erstellen, finden Sie unter [Proaktive Nachrichten für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)und speziell [erstellen einer Kanalunterhaltung](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="9a4c5-124">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="9a4c5-124">Receiving messages</span></span>

<span data-ttu-id="9a4c5-125">Für einen Bot in einer Gruppe oder einem Kanal erhält Ihr Bot zusätzlich zum [regulären Nachrichtenschema](https://docs.botframework.com/core-concepts/reference/#activity)auch die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="9a4c5-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="9a4c5-126">`channelData`Siehe [Teams Kanaldaten](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="9a4c5-127">Enthält in einem Gruppenchat spezifische Informationen zu diesem Chat.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="9a4c5-128">`conversation.id` Die Antwortketten-ID, bestehend aus Kanal-ID plus der ID der ersten Nachricht in der Antwortkette.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain.</span></span>
* <span data-ttu-id="9a4c5-129">`conversation.isGroup` Ist `true` für Bot-Nachrichten in Kanälen oder Gruppenchats.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats.</span></span>
* <span data-ttu-id="9a4c5-130">`conversation.conversationType` Entweder `groupChat` oder `channel` .</span><span class="sxs-lookup"><span data-stu-id="9a4c5-130">`conversation.conversationType` Either `groupChat` or `channel`.</span></span>
* <span data-ttu-id="9a4c5-131">`entities` Kann eine oder mehrere Erwähnungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-131">`entities` Can contain one or more mentions.</span></span> <span data-ttu-id="9a4c5-132">Weitere Informationen finden Sie unter [Erwähnungen](#-mentions).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-132">For more information, see [Mentions](#-mentions).</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="9a4c5-133">Antworten auf Nachrichten</span><span class="sxs-lookup"><span data-stu-id="9a4c5-133">Replying to messages</span></span>

<span data-ttu-id="9a4c5-134">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) .NET oder [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js an.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-134">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="9a4c5-135">Das Bot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-135">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="9a4c5-136">Wenn Sie die REST-API verwenden, können Sie auch den [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) Endpunkt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-136">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="9a4c5-137">In einem Kanal wird das Beantworten einer Nachricht als Antwort auf die einleitende Antwortkette angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-137">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="9a4c5-138">Der `conversation.id` enthält den Kanal und die Nachrichten-ID der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-138">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="9a4c5-139">Obwohl das Bot Framework sich um die Details kümmert, können Sie dies `conversation.id` bei Bedarf für zukünftige Antworten auf diesen Unterhaltungsthread zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-139">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="9a4c5-140">Bewährte Verfahren: Willkommensbotschaften in Teams</span><span class="sxs-lookup"><span data-stu-id="9a4c5-140">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="9a4c5-141">Wenn Ihr Bot zum ersten Mal der Gruppe oder dem Team hinzugefügt wird, ist es im Allgemeinen nützlich, eine Willkommensnachricht zu senden, die den Bot an alle Benutzer einführt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-141">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="9a4c5-142">Die Begrüßungsnachricht sollte eine Beschreibung der Funktionalität und der Vorteile des Bots enthalten.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-142">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="9a4c5-143">Idealerweise sollte die Nachricht auch Befehle enthalten, damit der Benutzer mit der App interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-143">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="9a4c5-144">Stellen Sie hierzu sicher, dass Ihr Bot mit dem eventType im Objekt auf die `conversationUpdate` Nachricht `teamsAddMembers` `channelData` reagiert.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-144">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="9a4c5-145">Stellen Sie sicher, dass die `memberAdded` ID die App-ID des Bots selbst ist, da dasselbe Ereignis gesendet wird, wenn ein Benutzer einem Team hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-145">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="9a4c5-146">Weitere Informationen finden Sie unter [Teammitglied oder Bot-Hinzufügen.](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)</span><span class="sxs-lookup"><span data-stu-id="9a4c5-146">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="9a4c5-147">Sie können auch eine persönliche Nachricht an jedes Teammitglied senden, wenn der Bot hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-147">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="9a4c5-148">Dazu können Sie [den Teamdienst abrufen](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) und jedem Benutzer eine [direkte Nachricht](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)senden.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-148">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="9a4c5-149">Wir empfehlen, dass Ihr Bot in den folgenden Situationen *keine* Willkommensnachricht sendet:</span><span class="sxs-lookup"><span data-stu-id="9a4c5-149">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="9a4c5-150">Das Team ist groß (offensichtlich subjektiv, zum Beispiel mehr als 100 Mitglieder).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-150">The team is big (obviously subjective, for example, more than 100 members).</span></span> <span data-ttu-id="9a4c5-151">Ihr Bot kann als "Spammy" angesehen werden und die Person, die ihn hinzugefügt hat, kann Beschwerden erhalten, es sei denn, Sie kommunizieren das Wertversprechen Ihres Bots eindeutig jedem, der die Willkommensnachricht sieht.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-151">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="9a4c5-152">Ihr Bot wird zuerst in einer Gruppe oder einem Kanal erwähnt, im Gegensatz zu einem Team.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-152">Your bot is first mentioned in a group or channel, versus being first added to a team.</span></span>
* <span data-ttu-id="9a4c5-153">Eine Gruppe oder ein Kanal wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-153">A group or channel is renamed.</span></span>
* <span data-ttu-id="9a4c5-154">Ein Teammitglied wird einer Gruppe oder einem Kanal hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-154">A team member is added to a group or channel.</span></span>

## <a name="-mentions"></a><span data-ttu-id="9a4c5-155">• Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-155">@ Mentions</span></span>

<span data-ttu-id="9a4c5-156">Da Bots in einer Gruppe oder einem Kanal nur reagieren, wenn sie in einer Nachricht erwähnt werden _("Botname"),_ enthält jede Nachricht, die von einem Bot in einem Gruppenkanal empfangen wird, ihren eigenen Namen, und Sie müssen sicherstellen, dass Ihre Nachrichtenanalyse dies behandelt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-156">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="9a4c5-157">Darüber hinaus können Bots andere Benutzer analysieren und Benutzer als Teil ihrer Nachrichten erwähnen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-157">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="9a4c5-158">Abrufen von Erwähnungen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-158">Retrieving mentions</span></span>

<span data-ttu-id="9a4c5-159">Erwähnungen werden im `entities` Objekt in der Nutzlast zurückgegeben und enthalten sowohl die eindeutige ID des Benutzers als auch in den meisten Fällen den Namen des genannten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-159">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="9a4c5-160">Sie können alle Erwähnungen in der Nachricht abrufen, indem Sie die `GetMentions` Funktion im Bot Builder SDK für .NET aufrufen, das ein Array von Objekten zurückgibt. `Mentioned`</span><span class="sxs-lookup"><span data-stu-id="9a4c5-160">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="9a4c5-161">.NET-Beispielcode: Überprüfen und Entfernen @bot erwähnen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-161">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="9a4c5-162">Sie können auch die Teams `GetTextWithoutMentions` Erweiterungsfunktion verwenden, die alle Erwähnungen, einschließlich des Bots, entfernt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-162">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="9a4c5-163">Node.js Beispielcode: Überprüfen sie nach und streifen Sie @bot erwähnen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-163">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="9a4c5-164">Sie können auch die Teams `getTextWithoutMentions` Erweiterungsfunktion verwenden, die alle Erwähnungen, einschließlich des Bots, entfernt.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-164">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="9a4c5-165">Konstruktionserwähnungen</span><span class="sxs-lookup"><span data-stu-id="9a4c5-165">Constructing mentions</span></span>

<span data-ttu-id="9a4c5-166">Ihr Bot kann andere Benutzer in Nachrichten erwähnen, die in Kanälen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-166">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="9a4c5-167">Dazu muss Ihre Nachricht wie folgt gehen:</span><span class="sxs-lookup"><span data-stu-id="9a4c5-167">To do this, your message must do the following:</span></span>

* <span data-ttu-id="9a4c5-168">Fügen Sie `<at>@username</at>` den Nachrichtentext ein.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-168">Include `<at>@username</at>` in the message text.</span></span>
* <span data-ttu-id="9a4c5-169">Schließen Sie das `mention` Objekt in die Entitätsauflistung ein.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-169">Include the `mention` object inside the entities collection.</span></span>

#### <a name="net-example"></a><span data-ttu-id="9a4c5-170">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="9a4c5-170">.NET example</span></span>

<span data-ttu-id="9a4c5-171">In diesem Beispiel wird das [NuGet-Paket Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwendet.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="9a4c5-172">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="9a4c5-172">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="9a4c5-173">Beispiel: Ausgehende Nachricht mit erwähntem Benutzer</span><span class="sxs-lookup"><span data-stu-id="9a4c5-173">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="9a4c5-174">Zugriff auf groupChat oder Kanalbereich</span><span class="sxs-lookup"><span data-stu-id="9a4c5-174">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="9a4c5-175">Ihr Bot kann mehr als nur Nachrichten in Gruppen und Teams senden und empfangen.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-175">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="9a4c5-176">Beispielsweise kann es auch die Liste der Mitglieder abrufen, einschließlich ihrer Profilinformationen, sowie die Liste der Kanäle.</span><span class="sxs-lookup"><span data-stu-id="9a4c5-176">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="9a4c5-177">Weitere Informationen finden Sie unter [Kontext abrufen für Ihren Microsoft Teams Bot](~/resources/bot-v3/bots-context.md).</span><span class="sxs-lookup"><span data-stu-id="9a4c5-177">For more information, see [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4c5-178">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9a4c5-178">See also</span></span>

[<span data-ttu-id="9a4c5-179">Bot Framework-Beispiele</span><span class="sxs-lookup"><span data-stu-id="9a4c5-179">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
