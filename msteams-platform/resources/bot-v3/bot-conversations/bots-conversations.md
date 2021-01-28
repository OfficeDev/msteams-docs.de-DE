---
title: Senden und Empfangen von Nachrichten mit einem Bot
description: Beschreibt das Senden und Empfangen von Nachrichten mit Bots in Microsoft Teams
ms.topic: overview
keywords: Teams bots messages
ms.date: 05/20/2019
ms.openlocfilehash: 20c285a0cd06ac929d628edbc059b2a00b937eec
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014117"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a><span data-ttu-id="90952-104">Unterhaltung mit einem Microsoft Teams-Bot</span><span class="sxs-lookup"><span data-stu-id="90952-104">Have a conversation with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="90952-105">Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="90952-105">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="90952-106">In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):</span><span class="sxs-lookup"><span data-stu-id="90952-106">There are three kinds of conversations (also called scopes) in Teams:</span></span>

* <span data-ttu-id="90952-107">`teams` Auch Kanalunterhaltungen genannt, die für alle Mitglieder des Kanals sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="90952-107">`teams` Also called channel conversations, visible to all members of the channel.</span></span>
* <span data-ttu-id="90952-108">`personal` Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="90952-108">`personal` Conversations between bots and a single user.</span></span>
* <span data-ttu-id="90952-109">`groupChat` Chatten zwischen einem Bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="90952-109">`groupChat` Chat between a bot and two or more users.</span></span>

<span data-ttu-id="90952-110">Ein Bot verhält sich etwas anders, je nachdem, an welcher Art von Unterhaltung er beteiligt ist:</span><span class="sxs-lookup"><span data-stu-id="90952-110">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="90952-111">[Bots in Kanal- und Gruppenchatunterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufrief.</span><span class="sxs-lookup"><span data-stu-id="90952-111">[Bots in channel and group chat conversations](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="90952-112">[Bots in Unterhaltungen einzelner](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) Benutzer erfordern keine @-Erwähnung – der Benutzer kann einfach eingeben.</span><span class="sxs-lookup"><span data-stu-id="90952-112">[Bots in single user conversations](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) do not require an @ mention -  the user can just type.</span></span>

<span data-ttu-id="90952-113">Damit der Bot in einem bestimmten Bereich funktioniert, sollte er als Unterstützung für diesen Bereich im Manifest aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="90952-113">In order for the bot to work in a particular scope it should be listed as supporting that scope in the manifest.</span></span> <span data-ttu-id="90952-114">Bereiche werden in der Manifestreferenz definiert [und weiter erläutert.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="90952-114">Scopes are defined and discussed further in the [Manifest Reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="proactive-messages"></a><span data-ttu-id="90952-115">Proaktive Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-115">Proactive messages</span></span>

<span data-ttu-id="90952-116">Bots können an einer Unterhaltung teilnehmen oder eine Unterhaltung initiieren.</span><span class="sxs-lookup"><span data-stu-id="90952-116">Bots can participate in a conversation or initiate one.</span></span> <span data-ttu-id="90952-117">Die meisten Kommunikationen werden als Reaktion auf eine andere Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="90952-117">Most communication is in response to another message.</span></span> <span data-ttu-id="90952-118">Wenn ein Bot eine Unterhaltung initiiert, wird er als proaktive *Nachricht bezeichnet.*</span><span class="sxs-lookup"><span data-stu-id="90952-118">If a bot initiates a conversation it is called a *proactive message*.</span></span> <span data-ttu-id="90952-119">Dazu gehören:</span><span class="sxs-lookup"><span data-stu-id="90952-119">Examples include:</span></span>

* <span data-ttu-id="90952-120">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-120">Welcome messages</span></span>
* <span data-ttu-id="90952-121">Ereignisbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="90952-121">Event notifications</span></span>
* <span data-ttu-id="90952-122">Abruf von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-122">Polling messages</span></span>

## <a name="conversation-basics"></a><span data-ttu-id="90952-123">Grundlagen zu Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="90952-123">Conversation basics</span></span>

<span data-ttu-id="90952-124">Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`.</span><span class="sxs-lookup"><span data-stu-id="90952-124">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="90952-125">Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots.</span><span class="sxs-lookup"><span data-stu-id="90952-125">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="90952-126">Ihr Bot untersucht die Nachricht, um ihren Typ zu ermitteln, und antwortet entsprechend.</span><span class="sxs-lookup"><span data-stu-id="90952-126">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="90952-127">Bots unterstützen auch Nachrichten im Ereignisstil.</span><span class="sxs-lookup"><span data-stu-id="90952-127">Bots also support event-style messages.</span></span> <span data-ttu-id="90952-128">Weitere [Informationen finden Sie unter Behandeln von Botereignissen in Microsoft Teams.](~/resources/bot-v3/bots-notifications.md)</span><span class="sxs-lookup"><span data-stu-id="90952-128">See [Handle bot events in Microsoft Teams](~/resources/bot-v3/bots-notifications.md) for more details.</span></span> <span data-ttu-id="90952-129">Die Spracherkennung wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90952-129">Speech is currently not supported.</span></span>

<span data-ttu-id="90952-130">Nachrichten sind in den meisten Umfangen gleich, aber es gibt Unterschiede in der Art und Weise, wie auf den Bot in der Benutzeroberfläche zugegriffen wird, und Unterschiede im Hintergrund, die Sie kennen müssen.</span><span class="sxs-lookup"><span data-stu-id="90952-130">Messages are for the most part the same in across all scopes, but there are differences in how the bot is accessed in the UI and differences behind the scenes which you will need to know about.</span></span>

<span data-ttu-id="90952-131">Die grundlegende Unterhaltung wird über den Bot Framework Connector, eine einzelne REST-API, verarbeitet, damit Ihr Bot mit Teams und anderen Kanälen kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="90952-131">Basic conversation is handled through the Bot Framework Connector, a single REST API to enable your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="90952-132">Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungsflusses und -zustands sowie einfache Möglichkeiten zur Integration kognitiver Dienste wie die Verarbeitung natürlicher Sprache (NlP).</span><span class="sxs-lookup"><span data-stu-id="90952-132">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as natural language processing (NLP).</span></span>

## <a name="message-content"></a><span data-ttu-id="90952-133">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="90952-133">Message content</span></span>

<span data-ttu-id="90952-134">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="90952-134">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="90952-135">Benutzer können Rich-Text- und Bilder an Ihren Bot senden.</span><span class="sxs-lookup"><span data-stu-id="90952-135">Users can send rich text and pictures to your bot.</span></span> <span data-ttu-id="90952-136">Auf der Einstellungsseite von Microsoft Teams für Ihren Bot können Sie den Inhaltstyp angeben, den Ihr Bot verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="90952-136">You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.</span></span>

| <span data-ttu-id="90952-137">Format</span><span class="sxs-lookup"><span data-stu-id="90952-137">Format</span></span> | <span data-ttu-id="90952-138">Von Benutzer zu Bot</span><span class="sxs-lookup"><span data-stu-id="90952-138">From user to bot</span></span>  | <span data-ttu-id="90952-139">Vom Bot zum Benutzer</span><span class="sxs-lookup"><span data-stu-id="90952-139">From bot to user</span></span> |  <span data-ttu-id="90952-140">Notes</span><span class="sxs-lookup"><span data-stu-id="90952-140">Notes</span></span> |
| --- | :---: | :---: | --- |
| <span data-ttu-id="90952-141">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="90952-141">Rich text</span></span> | <span data-ttu-id="90952-142">✔</span><span class="sxs-lookup"><span data-stu-id="90952-142">✔</span></span> | <span data-ttu-id="90952-143">✔</span><span class="sxs-lookup"><span data-stu-id="90952-143">✔</span></span> |  |
| <span data-ttu-id="90952-144">Bilder</span><span class="sxs-lookup"><span data-stu-id="90952-144">Pictures</span></span> | <span data-ttu-id="90952-145">✔</span><span class="sxs-lookup"><span data-stu-id="90952-145">✔</span></span> | <span data-ttu-id="90952-146">✔</span><span class="sxs-lookup"><span data-stu-id="90952-146">✔</span></span> | <span data-ttu-id="90952-147">Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; Animierte GIF werden nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="90952-147">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span> |
| <span data-ttu-id="90952-148">Karten</span><span class="sxs-lookup"><span data-stu-id="90952-148">Cards</span></span> | <span data-ttu-id="90952-149">✖</span><span class="sxs-lookup"><span data-stu-id="90952-149">✖</span></span> | <span data-ttu-id="90952-150">✔</span><span class="sxs-lookup"><span data-stu-id="90952-150">✔</span></span> | <span data-ttu-id="90952-151">Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Teams-Karten.</span><span class="sxs-lookup"><span data-stu-id="90952-151">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="90952-152">Emojis</span><span class="sxs-lookup"><span data-stu-id="90952-152">Emojis</span></span> | <span data-ttu-id="90952-153">✖</span><span class="sxs-lookup"><span data-stu-id="90952-153">✖</span></span> | <span data-ttu-id="90952-154">✔</span><span class="sxs-lookup"><span data-stu-id="90952-154">✔</span></span> | <span data-ttu-id="90952-155">Teams unterstützt derzeit Emojis über UTF-16 (z. B. U+1F600 für Das Gesicht)</span><span class="sxs-lookup"><span data-stu-id="90952-155">Teams currently supports emojis via UTF-16 (such as U+1F600 for grinning face)</span></span> |
|

<span data-ttu-id="90952-156">Weitere Informationen zu den Typen von Botinteraktionen, die vom Bot Framework unterstützt werden (auf denen Bots in Teams basieren), finden Sie in der Bot Framework-Dokumentation zum Unterhaltungsfluss und verwandten Konzepten in der Dokumentation für das Bot Builder SDK für [.NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) und das [Bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0). [](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0)</span><span class="sxs-lookup"><span data-stu-id="90952-156">For more information on the types of bot interaction supported by the Bot Framework (which bots in teams are based on), see the Bot Framework documentation on [conversation flow](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) and related concepts in the documentation for [the Bot Builder SDK for .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) and [the Bot Builder SDK for Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).</span></span>

## <a name="message-formatting"></a><span data-ttu-id="90952-157">Mitteilungsformatierung</span><span class="sxs-lookup"><span data-stu-id="90952-157">Message formatting</span></span>

<span data-ttu-id="90952-158">Sie können die optionale Eigenschaft eines Steuerelements festlegen, um zu steuern, wie der Textinhalt [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) `message` Ihrer Nachricht gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="90952-158">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property of a `message` to control how your message's text content is rendered.</span></span> <span data-ttu-id="90952-159">Eine [ausführliche Beschreibung der unterstützten](~/resources/bot-v3/bots-message-format.md) Formatierung in Botnachrichten finden Sie unter "Nachrichtenformatierung".</span><span class="sxs-lookup"><span data-stu-id="90952-159">See [Message formatting](~/resources/bot-v3/bots-message-format.md) for a detailed description of supported formatting in bot messages.</span></span>
<span data-ttu-id="90952-160">Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) Ihrer Nachricht gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="90952-160">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property to control how your message's text content is rendered.</span></span>

<span data-ttu-id="90952-161">Ausführliche Informationen dazu, wie Teams Textformatierungen in Teams unterstützt, finden Sie [unter "Textformatierung" in Botnachrichten.](~/resources/bot-v3/bots-text-formats.md)</span><span class="sxs-lookup"><span data-stu-id="90952-161">For detailed information on how Teams supports text formatting in teams see [Text formatting in bot messages](~/resources/bot-v3/bots-text-formats.md).</span></span>

<span data-ttu-id="90952-162">Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="90952-162">For information on formatting cards in messages, see [Card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="picture-messages"></a><span data-ttu-id="90952-163">Bildmeldungen</span><span class="sxs-lookup"><span data-stu-id="90952-163">Picture messages</span></span>

<span data-ttu-id="90952-164">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="90952-164">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="90952-165">Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0)</span><span class="sxs-lookup"><span data-stu-id="90952-165">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span></span>

<span data-ttu-id="90952-166">Bilder können im PNG-, JPEG- oder #A0 bis zu 1024×1024 und 1 MB groß sein. Animierte GIF wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90952-166">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not supported.</span></span>

<span data-ttu-id="90952-167">Es wird empfohlen, die Höhe und Breite der einzelnen Bilder mithilfe von XML anzugeben.</span><span class="sxs-lookup"><span data-stu-id="90952-167">We recommend that you specify the height and width of each image by using XML.</span></span> <span data-ttu-id="90952-168">Wenn Sie Markdown verwenden, ist die Bildgröße standardmäßig auf 256×256 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="90952-168">If you use Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="90952-169">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="90952-169">For example:</span></span>

* <span data-ttu-id="90952-170">`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` verwenden</span><span class="sxs-lookup"><span data-stu-id="90952-170">Use `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="90952-171">Nicht verwenden `![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="90952-171">Don't use `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="receiving-messages"></a><span data-ttu-id="90952-172">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-172">Receiving messages</span></span>

<span data-ttu-id="90952-173">Je nachdem, welche Bereiche deklariert sind, kann Ihr Bot Nachrichten in den folgenden Kontexten empfangen:</span><span class="sxs-lookup"><span data-stu-id="90952-173">Depending on which scopes are declared, your bot can receive messages in the following contexts:</span></span>

* <span data-ttu-id="90952-174">**Persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem Bot interagieren, indem sie einfach den hinzugefügten Bot im Chatverlauf auswählen oder den Namen oder die App-ID in das Feld "An:" in einem neuen Chat eingeben.</span><span class="sxs-lookup"><span data-stu-id="90952-174">**personal chat** Users can interact in a private conversation with a bot by simply selecting the added bot in the chat history, or typing its name or app ID in the To: box on a new chat.</span></span>
* <span data-ttu-id="90952-175">**Kanäle** Ein Bot kann in einem Kanal ("@_Botname")_ erwähnt werden, wenn er dem Team hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="90952-175">**Channels** A bot can be mentioned ("@_botname_") in a channel if it has been added to the team.</span></span> <span data-ttu-id="90952-176">Beachten Sie, dass für zusätzliche Antworten auf einen Bot in einem Kanal der Bot erwähnt werden muss.</span><span class="sxs-lookup"><span data-stu-id="90952-176">Note that additional replies to a bot in a channel require mentioning the bot.</span></span> <span data-ttu-id="90952-177">Antworten, in denen sie nicht erwähnt wird, werden nicht beantwortet.</span><span class="sxs-lookup"><span data-stu-id="90952-177">It will not respond to replies where it is not mentioned.</span></span>

<span data-ttu-id="90952-178">Bei eingehenden Nachrichten empfängt Ihr Bot ein [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) Objekt vom Typ `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="90952-178">For incoming messages, your bot receives an [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) object of type `messageType: message`.</span></span> <span data-ttu-id="90952-179">Obwohl das Objekt andere Arten von Informationen enthalten kann, z. B. Kanalupdates, die an Ihren Bot gesendet werden, stellt der Typ die Kommunikation `Activity` zwischen Bot und Benutzer [](~/resources/bot-v3/bots-notifications.md#channel-updates) `message` dar.</span><span class="sxs-lookup"><span data-stu-id="90952-179">Although the `Activity` object can contain other types of information, like [channel updates](~/resources/bot-v3/bots-notifications.md#channel-updates) sent to your bot, the `message` type represents communication between bot and user.</span></span>

<span data-ttu-id="90952-180">Ihr Bot empfängt eine Nutzlast, die die Benutzernachricht sowie weitere Informationen über den Benutzer, die Quelle der Nachricht und `Text` Teams-Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="90952-180">Your bot receives a payload that contains the user message `Text` as well as other information about the user, the source of the message, and Teams information.</span></span> <span data-ttu-id="90952-181">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="90952-181">Of note:</span></span>

* <span data-ttu-id="90952-182">`timestamp` Datum und Uhrzeit der Nachricht in koordinierter Weltzeit (UTC)</span><span class="sxs-lookup"><span data-stu-id="90952-182">`timestamp` The date and time of the message in Coordinated Universal Time (UTC)</span></span>
* <span data-ttu-id="90952-183">`localTimestamp` Datum und Uhrzeit der Nachricht in der Zeitzone des Absenders</span><span class="sxs-lookup"><span data-stu-id="90952-183">`localTimestamp` The date and time of the message in the time zone of the sender</span></span>
* <span data-ttu-id="90952-184">`channelId` Immer "msteams".</span><span class="sxs-lookup"><span data-stu-id="90952-184">`channelId` Always "msteams".</span></span> <span data-ttu-id="90952-185">Dies bezieht sich auf einen Bot-Framework-Kanal, nicht auf einen Teams-Kanal.</span><span class="sxs-lookup"><span data-stu-id="90952-185">This refers to a bot framework channel, not a teams channel.</span></span>
* <span data-ttu-id="90952-186">`from.id` Eine eindeutige und verschlüsselte ID für den Benutzer für Ihren Bot; geeignet als Schlüssel, wenn Ihre App Benutzerdaten speichern muss.</span><span class="sxs-lookup"><span data-stu-id="90952-186">`from.id` A unique and encrypted ID for that user for your bot; suitable as a key if your app needs to store user data.</span></span> <span data-ttu-id="90952-187">Sie ist für Ihren Bot einzigartig und kann nicht auf sinnvolle Weise direkt außerhalb Ihrer Botinstanz verwendet werden, um diesen Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="90952-187">It is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user</span></span>
* <span data-ttu-id="90952-188">`channelData.tenant.id` Die Mandanten-ID für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="90952-188">`channelData.tenant.id` The tenant ID for the user.</span></span>

> [!NOTE]
> <span data-ttu-id="90952-189">`from.id` ist für Ihren Bot eindeutig und kann nicht auf sinnvolle Weise direkt außerhalb Ihrer Botinstanz verwendet werden, um diesen Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="90952-189">`from.id` is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user.</span></span>

## <a name="combining-channel-and-private-interactions-with-your-bot"></a><span data-ttu-id="90952-190">Kombinieren von Kanal- und privaten Interaktionen mit Ihrem Bot</span><span class="sxs-lookup"><span data-stu-id="90952-190">Combining channel and private interactions with your bot</span></span>

<span data-ttu-id="90952-191">Bei der Interaktion in einem Kanal sollte Ihr Bot mit dem Offline schalten bestimmter Unterhaltungen mit einem Benutzer intelligent sein.</span><span class="sxs-lookup"><span data-stu-id="90952-191">When interacting in a channel, your bot should be smart about taking certain conversations offline with a user.</span></span> <span data-ttu-id="90952-192">Angenommen, ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, z. B. die Planung mit einer Gruppe von Teammitgliedern.</span><span class="sxs-lookup"><span data-stu-id="90952-192">For instance, suppose a user is trying to coordinate a complex task, such as scheduling with a set of team members.</span></span> <span data-ttu-id="90952-193">Anstatt die gesamte Abfolge von Interaktionen für den Kanal sichtbar zu machen, sollten Sie erwägen, eine persönliche Chatnachricht an den Benutzer zu senden.</span><span class="sxs-lookup"><span data-stu-id="90952-193">Rather than have the entire sequence of interactions visible to the channel, consider sending a personal chat message to the user.</span></span> <span data-ttu-id="90952-194">Ihr Bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen Unterhaltungen und Kanalunterhaltungen zu übertragen, ohne den Status zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="90952-194">Your bot should be able to easily transition the user between personal and channel conversations without losing state.</span></span>

> [!NOTE]
><span data-ttu-id="90952-195">Vergessen Sie nicht, den Kanal zu aktualisieren, wenn die Interaktion abgeschlossen ist, um die anderen Teammitglieder zu benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="90952-195">Don’t forget to update the channel when the interaction is complete to notify the other team members.</span></span>

## <a name="full-inbound-schema-example"></a><span data-ttu-id="90952-196">Beispiel für ein vollständiges eingehendes Schema</span><span class="sxs-lookup"><span data-stu-id="90952-196">Full inbound schema example</span></span>

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

> [!NOTE]
> <span data-ttu-id="90952-197">Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen.</span><span class="sxs-lookup"><span data-stu-id="90952-197">The text field for inbound messages sometimes contains mentions.</span></span> <span data-ttu-id="90952-198">Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu bestreifen.</span><span class="sxs-lookup"><span data-stu-id="90952-198">Be sure to properly check and strip those.</span></span> <span data-ttu-id="90952-199">Weitere Informationen finden Sie unter [Erwähnungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).</span><span class="sxs-lookup"><span data-stu-id="90952-199">For more information, see [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="90952-200">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="90952-200">Teams channel data</span></span>

<span data-ttu-id="90952-201">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die definitive Quelle für Team- und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="90952-201">The `channelData` object contains Teams-specific information and is the definitive source for team and channel IDs.</span></span> <span data-ttu-id="90952-202">Sie sollten diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="90952-202">You should cache and use these ids as keys for local storage.</span></span>

<span data-ttu-id="90952-203">Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="90952-203">The `channelData` object is not included in messages in personal conversations since these take place outside of any channel.</span></span>

<span data-ttu-id="90952-204">Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="90952-204">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="90952-205">`eventType` #A0 Nur bei [Kanaländerungsereignissen übergeben](~/resources/bot-v3/bots-notifications.md#channel-updates)</span><span class="sxs-lookup"><span data-stu-id="90952-205">`eventType` Teams event type; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates)</span></span>
* <span data-ttu-id="90952-206">`tenant.id` Azure Active Directory-Mandanten-ID; In allen Kontexten übergeben</span><span class="sxs-lookup"><span data-stu-id="90952-206">`tenant.id` Azure Active Directory tenant ID; passed in all contexts</span></span>
* <span data-ttu-id="90952-207">`team` Wird nur im Kanalkontext übergeben, nicht im persönlichen Chat.</span><span class="sxs-lookup"><span data-stu-id="90952-207">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="90952-208">`id` GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="90952-208">`id` GUID for the channel</span></span>
  * <span data-ttu-id="90952-209">`name` Name des Teams; Wird nur bei Ereignissen zur [Teambenennung übergeben](~/resources/bot-v3/bots-notifications.md#team-name-updates)</span><span class="sxs-lookup"><span data-stu-id="90952-209">`name` Name of the team; passed only in cases of [team rename events](~/resources/bot-v3/bots-notifications.md#team-name-updates)</span></span>
* <span data-ttu-id="90952-210">`channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde</span><span class="sxs-lookup"><span data-stu-id="90952-210">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added</span></span>
  * <span data-ttu-id="90952-211">`id` GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="90952-211">`id` GUID for the channel</span></span>
  * <span data-ttu-id="90952-212">`name`Kanalname; nur bei [Kanaländerungsereignissen übergeben.](~/resources/bot-v3/bots-notifications.md#channel-updates)</span><span class="sxs-lookup"><span data-stu-id="90952-212">`name` Channel name; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates).</span></span>
* <span data-ttu-id="90952-213">`channelData.teamsTeamId` Veraltet.</span><span class="sxs-lookup"><span data-stu-id="90952-213">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="90952-214">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="90952-214">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="90952-215">`channelData.teamsChannelId` Veraltet.</span><span class="sxs-lookup"><span data-stu-id="90952-215">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="90952-216">Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="90952-216">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="90952-217">Beispiel für ein channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="90952-217">Example channelData object (channelCreated event)</span></span>

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

### <a name="net-example"></a><span data-ttu-id="90952-218">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="90952-218">.NET example</span></span>

<span data-ttu-id="90952-219">Das [Microsoft.Bot.Connector.Teams-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) stellt ein spezielles Objekt zur Verfügung, das Eigenschaften für den Zugriff auf `TeamsChannelData` Teams-spezifische Informationen verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="90952-219">The [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package provides a specialized `TeamsChannelData` object, which exposes properties to access Teams-specific information.</span></span>

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a><span data-ttu-id="90952-220">Senden von Antworten auf Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-220">Sending replies to messages</span></span>

<span data-ttu-id="90952-221">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) in .NET oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) in Node.js.</span><span class="sxs-lookup"><span data-stu-id="90952-221">To reply to an existing message, call [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) in .NET or [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) in Node.js.</span></span> <span data-ttu-id="90952-222">Das Bot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="90952-222">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="90952-223">Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="90952-223">If you choose to use the REST API, you can also call the [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) endpoint.</span></span>

<span data-ttu-id="90952-224">Der Nachrichteninhalt selbst kann einfachen Text oder einige der von Bot Framework bereitgestellten Karten [und Kartenaktionen enthalten.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="90952-224">The message content itself can contain simple text or some of the Bot Framework supplied [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="90952-225">Bitte beachten Sie, dass Sie in Ihrem ausgehenden Schema immer dieselbe Wiesn verwenden sollten, die `serviceUrl` Sie erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="90952-225">Please note that in your outbound schema you should always use the same `serviceUrl` as the one you received.</span></span> <span data-ttu-id="90952-226">Beachten Sie, dass der Wert `serviceUrl` von in der Regel stabil ist, sich aber ändern kann.</span><span class="sxs-lookup"><span data-stu-id="90952-226">Be aware that the value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="90952-227">Wenn eine neue Nachricht eintrifft, sollte Ihr Bot den gespeicherten Wert von `serviceUrl` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="90952-227">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

## <a name="updating-messages"></a><span data-ttu-id="90952-228">Aktualisieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-228">Updating messages</span></span>

<span data-ttu-id="90952-229">Anstatt ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden, kann Ihr Bot Nachrichten nach dem Senden dynamisch inline aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="90952-229">Rather than have your messages be static snapshots of data, your bot can dynamically update messages inline after sending them.</span></span> <span data-ttu-id="90952-230">Sie können dynamische Nachrichtenaktualisierungen für Szenarien wie z. B. Abrufaktualisierungen, Das Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Statusänderung verwenden.</span><span class="sxs-lookup"><span data-stu-id="90952-230">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="90952-231">Die neue Nachricht muss nicht mit dem ursprünglichen Typ übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="90952-231">The new message need not match the original in type.</span></span> <span data-ttu-id="90952-232">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann die neue Nachricht eine einfache Textnachricht sein.</span><span class="sxs-lookup"><span data-stu-id="90952-232">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

> [!NOTE]
> <span data-ttu-id="90952-233">Sie können nur Inhalte aktualisieren, die in Einzelanlagennachrichten und Karusselllayouts gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="90952-233">You can update only content sent in single-attachment messages and carousel layouts.</span></span> <span data-ttu-id="90952-234">Das Veröffentlichen von Aktualisierungen für Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90952-234">Posting updates to messages with multiple attachments in list layout is not supported.</span></span>

### <a name="rest-api"></a><span data-ttu-id="90952-235">REST-API</span><span class="sxs-lookup"><span data-stu-id="90952-235">REST API</span></span>

<span data-ttu-id="90952-236">Um ein Nachrichtenupdate aus senden zu können, führen Sie einfach eine PUT-Anforderung für den Endpunkt mit `/v3/conversations/<conversationId>/activities/<activityId>/` einer bestimmten Aktivitäts-ID aus.</span><span class="sxs-lookup"><span data-stu-id="90952-236">To issue a message update, simply perform a PUT request against the `/v3/conversations/<conversationId>/activities/<activityId>/` endpoint using a given activity ID.</span></span> <span data-ttu-id="90952-237">Zum Abschließen dieses Szenarios sollten Sie die Aktivitäts-ID zwischenspeichern, die vom ursprünglichen POST-Aufruf zurückgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="90952-237">To complete this scenario, you should cache the activity ID returned by the original POST call.</span></span>

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a><span data-ttu-id="90952-238">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="90952-238">.NET example</span></span>

<span data-ttu-id="90952-239">Sie können die Methode im Bot Builder SDK verwenden, `UpdateActivityAsync` um eine vorhandene Nachricht zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="90952-239">You can use the `UpdateActivityAsync` method in the Bot Builder SDK to update an existing message.</span></span>

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
  if (activity.Type == ActivityTypes.Message)
  {
    ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
    Activity reply = activity.CreateReply($"You sent {activity.Text} which was {activity.Text.Length} characters");
    var msgToUpdate = await connector.Conversations.ReplyToActivityAsync(reply);
    Activity updatedReply = activity.CreateReply($"This is an updated message");
    await connector.Conversations.UpdateActivityAsync(reply.Conversation.Id, msgToUpdate.Id, updatedReply);
  }
}
```

### <a name="nodejs-example"></a><span data-ttu-id="90952-240">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="90952-240">Node.js example</span></span>

<span data-ttu-id="90952-241">Sie können die Methode im Bot Builder SDK verwenden, `session.connector.update` um eine vorhandene Nachricht zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="90952-241">You can use the `session.connector.update` method in the Bot Builder SDK to update an existing message.</span></span>

```javascript
function sendCardUpdate(bot, session, originalMessage, address) {

  var origAttachment = originalMessage.data.attachments[0];
  origAttachment.content.subtitle = 'Assigned to Larry Jin';

  var updatedMsg = new builder.Message()
    .address(address)
    .textFormat(builder.TextFormat.markdown)
    .addAttachment(origAttachment)
    .toMessage();

  session.connector.update(updatedMsg, function(err, addresses) {
    if (err) {
      console.log(`Could not update the message`);
    }
  });
}
```

## <a name="starting-a-conversation-proactive-messaging"></a><span data-ttu-id="90952-242">Starten einer Unterhaltung (proaktives Messaging)</span><span class="sxs-lookup"><span data-stu-id="90952-242">Starting a conversation (proactive messaging)</span></span>

<span data-ttu-id="90952-243">Sie können eine persönliche Unterhaltung mit einem Benutzer erstellen oder eine neue Antwortkette in einem Kanal für Ihren Teambot starten.</span><span class="sxs-lookup"><span data-stu-id="90952-243">You can create a personal conversation with a user or start a new reply chain in a channel for your team bot.</span></span> <span data-ttu-id="90952-244">Auf diese Weise können Sie Ihren Oder-Benutzern eine Nachricht senden, ohne dass sie zuerst den Kontakt mit Ihrem Bot initiieren müssen.</span><span class="sxs-lookup"><span data-stu-id="90952-244">This lets you to message your user or users without having them first initiate contact with your bot.</span></span> <span data-ttu-id="90952-245">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="90952-245">For more information, see the following topics:</span></span>

<span data-ttu-id="90952-246">Weitere allgemeine Informationen zu Unterhaltungen, die von Bots gestartet wurden, finden Sie unter [proaktives](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) Messaging für Bots.</span><span class="sxs-lookup"><span data-stu-id="90952-246">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more general information on conversations started by bots.</span></span>

## <a name="deleting-messages"></a><span data-ttu-id="90952-247">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="90952-247">Deleting messages</span></span>

<span data-ttu-id="90952-248">Nachrichten können mit der Connectorsmethode [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) im [BotBuilder SDK gelöscht werden.](/bot-framework/bot-builder-overview-getstarted)</span><span class="sxs-lookup"><span data-stu-id="90952-248">Messages can be deleted using the connectors [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) method in the [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted).</span></span>

```typescript
bot.dialog('BotDeleteMessage', function (session: builder.Session) {
  var msg = new teams.TeamsMessage(session).text("Bot will delete this message in 5 sec.")
  bot.send(msg, function (err, response) {
    if (err) {
      console.log(err);
      session.endDialog();
    }

    console.log('Proactive message response:');
    console.log(response);
    console.log('---------------------------------------------------')
    setTimeout(function () {
      var activityId: string = null;
      var messageAddress: builder.IChatConnectorAddress = null;
      if (response[0]){
        messageAddress = response[0];
        activityId = messageAddress.id;
      }

      if (activityId == null)
      {
        console.log('Message failed to send.');
        session.endDialog();
        return;
      }

      // Bot delete message
      let address: builder.IChatConnectorAddress  = {
        channelId: 'msteams',
        user: messageAddress.user,
        bot: messageAddress.bot,
        id : activityId,
        serviceUrl : (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
        conversation: {
          id: session.message.address.conversation.id
        }
      };

      connector.delete(address, function (err) {
        if (err)
        {
          console.log(err);
        }
        else
        {
          console.log("Message: " + activityId + " deleted successfully.");
        }

        // Try editing deleted message would fail
        var newMsg = new builder.Message().address(address).text("To edit message.");
        connector.update(newMsg.toMessage(), function (err, address) {
          if (err)
          {
            console.log(err);
            console.log('Deleted message can not be edited.');
          }
          else
          {
            console.log("There is something wrong. Message: " + activityId + " edited successfully.");
            console.log(address);
          }

          session.endDialog();
        });
      });
    }, 5000);
  });
})
```
