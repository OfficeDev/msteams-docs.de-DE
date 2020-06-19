---
title: Senden und empfangen von Nachrichten mit einem bot
description: Beschreibt das Senden und empfangen von Nachrichten mit Bots in Microsoft Teams
keywords: Teams-Bots-Nachrichten
ms.date: 05/20/2019
ms.openlocfilehash: 4a15bb9b4ae8c0ede3214d3a534649e2769baf6e
ms.sourcegitcommit: 2b1fd50466d807869fd173371ba7dfd82a0064ac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "44801324"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a><span data-ttu-id="f8f89-104">Unterhaltung mit einem Microsoft Teams-bot</span><span class="sxs-lookup"><span data-stu-id="f8f89-104">Have a conversation with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="f8f89-105">Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-105">A conversation is a series of messages sent between your bot and one or more users.</span></span> <span data-ttu-id="f8f89-106">In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):</span><span class="sxs-lookup"><span data-stu-id="f8f89-106">There are three kinds of conversations (also called scopes) in Teams:</span></span>

* <span data-ttu-id="f8f89-107">`teams`Wird auch als Kanal Unterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="f8f89-107">`teams` Also called channel conversations, visible to all members of the channel.</span></span>
* <span data-ttu-id="f8f89-108">`personal`Unterhaltungen zwischen Bots und einem einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="f8f89-108">`personal` Conversations between bots and a single user.</span></span>
* <span data-ttu-id="f8f89-109">`groupChat`Chat zwischen einem bot und zwei oder mehr Benutzern.</span><span class="sxs-lookup"><span data-stu-id="f8f89-109">`groupChat` Chat between a bot and two or more users.</span></span>

<span data-ttu-id="f8f89-110">Ein bot verhält sich je nach Art der Unterhaltung, in der er beteiligt ist, etwas anders:</span><span class="sxs-lookup"><span data-stu-id="f8f89-110">A bot behaves slightly differently depending on what kind of conversation it is involved in:</span></span>

* <span data-ttu-id="f8f89-111">[Bots in Kanal-und Gruppenchat Unterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer @ den bot erwähnt, um ihn in einem Kanal aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-111">[Bots in channel and group chat conversations](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) require the user to @ mention the bot to invoke it in a channel.</span></span>
* <span data-ttu-id="f8f89-112">[Bots in einzelnen Benutzer Unterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) erfordern keine @ mention-der Benutzer kann einfach eingeben.</span><span class="sxs-lookup"><span data-stu-id="f8f89-112">[Bots in single user conversations](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) do not require an @ mention -  the user can just type.</span></span>

<span data-ttu-id="f8f89-113">Damit der bot in einem bestimmten Bereich funktioniert, sollte er als Unterstützung für diesen Bereich im Manifest aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-113">In order for the bot to work in a particular scope it should be listed as supporting that scope in the manifest.</span></span> <span data-ttu-id="f8f89-114">Bereiche werden im [Manifest-Verweis](~/resources/schema/manifest-schema.md)definiert und weiter behandelt.</span><span class="sxs-lookup"><span data-stu-id="f8f89-114">Scopes are defined and discussed further in the [Manifest Reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="proactive-messages"></a><span data-ttu-id="f8f89-115">Proaktive Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-115">Proactive messages</span></span>

<span data-ttu-id="f8f89-116">Bots können an einer Unterhaltung teilnehmen oder eine initiieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-116">Bots can participate in a conversation or initiate one.</span></span> <span data-ttu-id="f8f89-117">Die meiste Kommunikation erfolgt als Reaktion auf eine andere Nachricht.</span><span class="sxs-lookup"><span data-stu-id="f8f89-117">Most communication is in response to another message.</span></span> <span data-ttu-id="f8f89-118">Wenn ein bot eine Unterhaltung initiiert, wird er als *proaktive Nachricht*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="f8f89-118">If a bot initiates a conversation it is called a *proactive message*.</span></span> <span data-ttu-id="f8f89-119">Beispiele sind:</span><span class="sxs-lookup"><span data-stu-id="f8f89-119">Examples include:</span></span>

* <span data-ttu-id="f8f89-120">Willkommensnachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-120">Welcome messages</span></span>
* <span data-ttu-id="f8f89-121">Ereignisbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f8f89-121">Event notifications</span></span>
* <span data-ttu-id="f8f89-122">Abrufen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-122">Polling messages</span></span>

## <a name="conversation-basics"></a><span data-ttu-id="f8f89-123">Grundlagen der Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="f8f89-123">Conversation basics</span></span>

<span data-ttu-id="f8f89-124">Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`.</span><span class="sxs-lookup"><span data-stu-id="f8f89-124">Each message is an `Activity` object of type `messageType: message`.</span></span> <span data-ttu-id="f8f89-125">Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots.</span><span class="sxs-lookup"><span data-stu-id="f8f89-125">When a user sends a message, Teams posts the message to your bot; specifically, it sends a JSON object to your bot's messaging endpoint.</span></span> <span data-ttu-id="f8f89-126">Ihr bot überprüft die Nachricht, um den Typ zu bestimmen, und antwortet dementsprechend.</span><span class="sxs-lookup"><span data-stu-id="f8f89-126">Your bot examines the message to determine its type and responds accordingly.</span></span>

<span data-ttu-id="f8f89-127">Bots unterstützen auch Nachrichten im Ereignis Stil.</span><span class="sxs-lookup"><span data-stu-id="f8f89-127">Bots also support event-style messages.</span></span> <span data-ttu-id="f8f89-128">Weitere Informationen finden Sie unter [Behandeln von bot-Ereignissen in Microsoft Teams](~/resources/bot-v3/bots-notifications.md) .</span><span class="sxs-lookup"><span data-stu-id="f8f89-128">See [Handle bot events in Microsoft Teams](~/resources/bot-v3/bots-notifications.md) for more details.</span></span> <span data-ttu-id="f8f89-129">Die Sprache wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f8f89-129">Speech is currently not supported.</span></span>

<span data-ttu-id="f8f89-130">Nachrichten sind größtenteils in allen Bereichen gleich, aber es gibt Unterschiede in der Art und Weise, wie der bot auf der Benutzeroberfläche aufgerufen wird, und Unterschiede hinter den Szenen, über die Sie Bescheid wissen müssen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-130">Messages are for the most part the same in across all scopes, but there are differences in how the bot is accessed in the UI and differences behind the scenes which you will need to know about.</span></span>

<span data-ttu-id="f8f89-131">Grundlegende Unterhaltungen werden über den bot-Framework-Konnektor behandelt, eine einzelne Rest-API, mit der ihr bot mit Teams und anderen Kanälen kommunizieren kann.</span><span class="sxs-lookup"><span data-stu-id="f8f89-131">Basic conversation is handled through the Bot Framework Connector, a single REST API to enable your bot to communicate with Teams and other channels.</span></span> <span data-ttu-id="f8f89-132">Das bot-Generator-SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungs Flusses und-Zustands sowie einfache Methoden zum Integrieren von kognitiven Diensten wie etwa die Natural Language Processing (NLP).</span><span class="sxs-lookup"><span data-stu-id="f8f89-132">The Bot Builder SDK provides easy access to this API, additional functionality to manage conversation flow and state, and simple ways to incorporate cognitive services such as natural language processing (NLP).</span></span>

## <a name="message-content"></a><span data-ttu-id="f8f89-133">Nachrichteninhalt</span><span class="sxs-lookup"><span data-stu-id="f8f89-133">Message content</span></span>

<span data-ttu-id="f8f89-134">Ihr Bot kann Rich-Text, Bilder und Karten senden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-134">Your bot can send rich text, pictures, and cards.</span></span> <span data-ttu-id="f8f89-135">Benutzer können Rich-Text und Bilder an Ihren bot senden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-135">Users can send rich text and pictures to your bot.</span></span> <span data-ttu-id="f8f89-136">Sie können den Typ des Inhalts angeben, den Ihr bot auf der Seite Microsoft Teams-Einstellungen für Ihren bot verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="f8f89-136">You can specify the type of content your bot can handle in the Microsoft Teams settings page for your bot.</span></span>

| <span data-ttu-id="f8f89-137">Format</span><span class="sxs-lookup"><span data-stu-id="f8f89-137">Format</span></span> | <span data-ttu-id="f8f89-138">Von Benutzer zu bot</span><span class="sxs-lookup"><span data-stu-id="f8f89-138">From user to bot</span></span>  | <span data-ttu-id="f8f89-139">Von bot zu Benutzer</span><span class="sxs-lookup"><span data-stu-id="f8f89-139">From bot to user</span></span> |  <span data-ttu-id="f8f89-140">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="f8f89-140">Notes</span></span> |
| --- | :---: | :---: | --- |
| <span data-ttu-id="f8f89-141">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="f8f89-141">Rich text</span></span> | <span data-ttu-id="f8f89-142">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-142">✔</span></span> | <span data-ttu-id="f8f89-143">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-143">✔</span></span> |  |
| <span data-ttu-id="f8f89-144">Bilder</span><span class="sxs-lookup"><span data-stu-id="f8f89-144">Pictures</span></span> | <span data-ttu-id="f8f89-145">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-145">✔</span></span> | <span data-ttu-id="f8f89-146">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-146">✔</span></span> | <span data-ttu-id="f8f89-147">Maximal 1024 × 1024 und 1 MB im PNG-, JPEG-oder GIF-Format; animierte GIF-Zeichen werden nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="f8f89-147">Maximum 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF are not supported</span></span> |
| <span data-ttu-id="f8f89-148">Karten</span><span class="sxs-lookup"><span data-stu-id="f8f89-148">Cards</span></span> | <span data-ttu-id="f8f89-149">✖</span><span class="sxs-lookup"><span data-stu-id="f8f89-149">✖</span></span> | <span data-ttu-id="f8f89-150">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-150">✔</span></span> | <span data-ttu-id="f8f89-151">Siehe die Microsoft [Teams-Karten Referenz](~/task-modules-and-cards/cards/cards-reference.md) für unterstützte Karten</span><span class="sxs-lookup"><span data-stu-id="f8f89-151">See the [Teams Card Reference](~/task-modules-and-cards/cards/cards-reference.md) for supported cards</span></span> |
| <span data-ttu-id="f8f89-152">Emojis</span><span class="sxs-lookup"><span data-stu-id="f8f89-152">Emojis</span></span> | <span data-ttu-id="f8f89-153">✖</span><span class="sxs-lookup"><span data-stu-id="f8f89-153">✖</span></span> | <span data-ttu-id="f8f89-154">✔</span><span class="sxs-lookup"><span data-stu-id="f8f89-154">✔</span></span> | <span data-ttu-id="f8f89-155">Teams unterstützen derzeit Emojis über UTF-16 (wie U + 1F600 für grinsende Fläche)</span><span class="sxs-lookup"><span data-stu-id="f8f89-155">Teams currently supports emojis via UTF-16 (such as U+1F600 for grinning face)</span></span> |
|

<span data-ttu-id="f8f89-156">Weitere Informationen zu den Typen von bot-Interaktionen, die vom bot-Framework unterstützt werden (die Bots in Microsoft Teams basieren), finden Sie in der Dokumentation zum bot-Framework zu [Unterhaltungs Fluss](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) und verwandten Konzepten in der Dokumentation für [das bot Builder SDK für .net](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) und [das bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).</span><span class="sxs-lookup"><span data-stu-id="f8f89-156">For more information on the types of bot interaction supported by the Bot Framework (which bots in teams are based on), see the Bot Framework documentation on [conversation flow](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) and related concepts in the documentation for [the Bot Builder SDK for .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) and [the Bot Builder SDK for Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).</span></span>

## <a name="message-formatting"></a><span data-ttu-id="f8f89-157">Mitteilungsformatierung</span><span class="sxs-lookup"><span data-stu-id="f8f89-157">Message formatting</span></span>

<span data-ttu-id="f8f89-158">Sie können die optionale Eigenschaft eines festlegen [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) `message` , um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="f8f89-158">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property of a `message` to control how your message's text content is rendered.</span></span> <span data-ttu-id="f8f89-159">Eine detaillierte Beschreibung der unterstützten Formatierung in bot-Nachrichten finden Sie unter [Nachrichtenformatierung](~/resources/bot-v3/bots-message-format.md) .</span><span class="sxs-lookup"><span data-stu-id="f8f89-159">See [Message formatting](~/resources/bot-v3/bots-message-format.md) for a detailed description of supported formatting in bot messages.</span></span>
<span data-ttu-id="f8f89-160">Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="f8f89-160">You can set the optional [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) property to control how your message's text content is rendered.</span></span>

<span data-ttu-id="f8f89-161">Ausführliche Informationen dazu, wie Microsoft Teams Textformatierungen in Microsoft Teams unterstützt, finden Sie unter [Textformatierung in bot-Nachrichten](~/resources/bot-v3/bots-text-formats.md).</span><span class="sxs-lookup"><span data-stu-id="f8f89-161">For detailed information on how Teams supports text formatting in teams see [Text formatting in bot messages](~/resources/bot-v3/bots-text-formats.md).</span></span>

<span data-ttu-id="f8f89-162">Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).</span><span class="sxs-lookup"><span data-stu-id="f8f89-162">For information on formatting cards in messages, see [Card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

## <a name="picture-messages"></a><span data-ttu-id="f8f89-163">Bildnachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-163">Picture messages</span></span>

<span data-ttu-id="f8f89-164">Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet.</span><span class="sxs-lookup"><span data-stu-id="f8f89-164">Pictures are sent by adding attachments to a message.</span></span> <span data-ttu-id="f8f89-165">Weitere Informationen zu Anlagen finden Sie in der [bot-Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span><span class="sxs-lookup"><span data-stu-id="f8f89-165">You can find more information on attachments in the [Bot Framework documentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).</span></span>

<span data-ttu-id="f8f89-166">Bilder können im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f8f89-166">Pictures can be at most 1024×1024 and 1 MB in PNG, JPEG, or GIF format; animated GIF is not supported.</span></span>

<span data-ttu-id="f8f89-167">Es wird empfohlen, die Höhe und Breite jedes Bilds mithilfe von XML anzugeben.</span><span class="sxs-lookup"><span data-stu-id="f8f89-167">We recommend that you specify the height and width of each image by using XML.</span></span> <span data-ttu-id="f8f89-168">Wenn Sie den Abschlag verwenden, beträgt die Bildgröße standardmäßig 256 × 256.</span><span class="sxs-lookup"><span data-stu-id="f8f89-168">If you use Markdown, the image size defaults to 256×256.</span></span> <span data-ttu-id="f8f89-169">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f8f89-169">For example:</span></span>

* <span data-ttu-id="f8f89-170">Verwenden`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span><span class="sxs-lookup"><span data-stu-id="f8f89-170">Use `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`</span></span>
* <span data-ttu-id="f8f89-171">Nicht verwenden`![Duck on a rock](http://aka.ms/Fo983c)`</span><span class="sxs-lookup"><span data-stu-id="f8f89-171">Don't use `![Duck on a rock](http://aka.ms/Fo983c)`</span></span>

## <a name="receiving-messages"></a><span data-ttu-id="f8f89-172">Empfangen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-172">Receiving messages</span></span>

<span data-ttu-id="f8f89-173">Je nachdem, welche Bereiche deklariert werden, kann Ihr bot Nachrichten in den folgenden Kontexten empfangen:</span><span class="sxs-lookup"><span data-stu-id="f8f89-173">Depending on which scopes are declared, your bot can receive messages in the following contexts:</span></span>

* <span data-ttu-id="f8f89-174">**persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem bot interagieren, indem Sie einfach den hinzugefügten bot im Chatverlauf auswählen oder den Namen oder die APP-ID in das Feld an: in einem neuen Chat eingeben.</span><span class="sxs-lookup"><span data-stu-id="f8f89-174">**personal chat** Users can interact in a private conversation with a bot by simply selecting the added bot in the chat history, or typing its name or app ID in the To: box on a new chat.</span></span>
* <span data-ttu-id="f8f89-175">**Kanäle** Ein Bot kann ("@_botname_") in einem Kanal erwähnt werden, wenn er dem Team hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f8f89-175">**Channels** A bot can be mentioned ("@_botname_") in a channel if it has been added to the team.</span></span> <span data-ttu-id="f8f89-176">Beachten Sie, dass zusätzliche Antworten auf einen bot in einem Kanal den bot erwähnen müssen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-176">Note that additional replies to a bot in a channel require mentioning the bot.</span></span> <span data-ttu-id="f8f89-177">Er antwortet nicht auf Antworten, wenn er nicht erwähnt wird.</span><span class="sxs-lookup"><span data-stu-id="f8f89-177">It will not respond to replies where it is not mentioned.</span></span>

<span data-ttu-id="f8f89-178">Bei eingehenden Nachrichten erhält Ihr bot ein [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) Objekt vom Typ `messageType: message` .</span><span class="sxs-lookup"><span data-stu-id="f8f89-178">For incoming messages, your bot receives an [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) object of type `messageType: message`.</span></span> <span data-ttu-id="f8f89-179">Obwohl das `Activity` Objekt andere Arten von Informationen enthalten kann, wie [Kanal Aktualisierungen](~/resources/bot-v3/bots-notifications.md#channel-updates) , die an Ihren bot gesendet werden, `message` stellt der Typ die Kommunikation zwischen bot und Benutzer dar.</span><span class="sxs-lookup"><span data-stu-id="f8f89-179">Although the `Activity` object can contain other types of information, like [channel updates](~/resources/bot-v3/bots-notifications.md#channel-updates) sent to your bot, the `message` type represents communication between bot and user.</span></span>

<span data-ttu-id="f8f89-180">Ihr bot erhält eine Nutzlast, die die Benutzernachricht sowie `Text` andere Informationen über den Benutzer, die Quelle der Nachricht und die Informationen zu Teams enthält.</span><span class="sxs-lookup"><span data-stu-id="f8f89-180">Your bot receives a payload that contains the user message `Text` as well as other information about the user, the source of the message, and Teams information.</span></span> <span data-ttu-id="f8f89-181">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="f8f89-181">Of note:</span></span>

* <span data-ttu-id="f8f89-182">`timestamp`Das Datum und die Uhrzeit der Nachricht in koordinierter Weltzeit (Coordinated Universal Time, UTC)</span><span class="sxs-lookup"><span data-stu-id="f8f89-182">`timestamp` The date and time of the message in Coordinated Universal Time (UTC)</span></span>
* <span data-ttu-id="f8f89-183">`localTimestamp`Das Datum und die Uhrzeit der Nachricht in der Zeitzone des Absenders.</span><span class="sxs-lookup"><span data-stu-id="f8f89-183">`localTimestamp` The date and time of the message in the time zone of the sender</span></span>
* <span data-ttu-id="f8f89-184">`channelId`Immer "msteams".</span><span class="sxs-lookup"><span data-stu-id="f8f89-184">`channelId` Always "msteams".</span></span> <span data-ttu-id="f8f89-185">Dies bezieht sich auf einen bot-Framework-Kanal und nicht auf einen Teams-Kanal.</span><span class="sxs-lookup"><span data-stu-id="f8f89-185">This refers to a bot framework channel, not a teams channel.</span></span>
* <span data-ttu-id="f8f89-186">`from.id`Eine eindeutige und verschlüsselte ID für diesen Benutzer für Ihren bot; geeignet als Schlüssel, wenn Ihre APP Benutzerdaten speichern muss.</span><span class="sxs-lookup"><span data-stu-id="f8f89-186">`from.id` A unique and encrypted ID for that user for your bot; suitable as a key if your app needs to store user data.</span></span> <span data-ttu-id="f8f89-187">Es ist für Ihren bot eindeutig und kann nicht direkt außerhalb ihrer bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-187">It is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user</span></span>
* <span data-ttu-id="f8f89-188">`channelData.tenant.id`Die Mandanten-ID für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="f8f89-188">`channelData.tenant.id` The tenant ID for the user.</span></span>

> [!NOTE]
> <span data-ttu-id="f8f89-189">`from.id`ist für Ihren bot eindeutig und kann nicht direkt außerhalb ihrer bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-189">`from.id` is unique for your bot and cannot be directly used outside your bot instance in any meaningful way to identify that user.</span></span>

## <a name="combining-channel-and-private-interactions-with-your-bot"></a><span data-ttu-id="f8f89-190">Kombinieren von Kanal-und privaten Interaktionen mit Ihrem bot</span><span class="sxs-lookup"><span data-stu-id="f8f89-190">Combining channel and private interactions with your bot</span></span>

<span data-ttu-id="f8f89-191">Bei der Interaktion in einem Kanal sollte Ihr bot intelligent sein, bestimmte Unterhaltungen mit einem Benutzer offline zu führen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-191">When interacting in a channel, your bot should be smart about taking certain conversations offline with a user.</span></span> <span data-ttu-id="f8f89-192">Nehmen wir beispielsweise an, dass ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, wie etwa die Planung mit einer Gruppe von Teammitgliedern.</span><span class="sxs-lookup"><span data-stu-id="f8f89-192">For instance, suppose a user is trying to coordinate a complex task, such as scheduling with a set of team members.</span></span> <span data-ttu-id="f8f89-193">Anstatt die gesamte Sequenz von Interaktionen für den Kanal sichtbar zu machen, sollten Sie eine persönliche Chatnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-193">Rather than have the entire sequence of interactions visible to the channel, consider sending a personal chat message to the user.</span></span> <span data-ttu-id="f8f89-194">Ihr bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen und Kanal Unterhaltungen zu wechseln, ohne den Zustand zu verlieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-194">Your bot should be able to easily transition the user between personal and channel conversations without losing state.</span></span>

> [!NOTE]
><span data-ttu-id="f8f89-195">Vergessen Sie nicht, den Kanal zu aktualisieren, wenn die Interaktion abgeschlossen ist, um die anderen Teammitglieder zu benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-195">Don’t forget to update the channel when the interaction is complete to notify the other team members.</span></span>

## <a name="full-inbound-schema-example"></a><span data-ttu-id="f8f89-196">Beispiel für ein vollständiges eingehendes Schema</span><span class="sxs-lookup"><span data-stu-id="f8f89-196">Full inbound schema example</span></span>

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
> <span data-ttu-id="f8f89-197">Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-197">The text field for inbound messages sometimes contains mentions.</span></span> <span data-ttu-id="f8f89-198">Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-198">Be sure to properly check and strip those.</span></span> <span data-ttu-id="f8f89-199">Weitere Informationen finden Sie unter [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).</span><span class="sxs-lookup"><span data-stu-id="f8f89-199">For more information, see [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).</span></span>

## <a name="teams-channel-data"></a><span data-ttu-id="f8f89-200">Teams-Kanaldaten</span><span class="sxs-lookup"><span data-stu-id="f8f89-200">Teams channel data</span></span>

<span data-ttu-id="f8f89-201">Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team-und Kanal-IDs.</span><span class="sxs-lookup"><span data-stu-id="f8f89-201">The `channelData` object contains Teams-specific information and is the definitive source for team and channel IDs.</span></span> <span data-ttu-id="f8f89-202">Sie sollten diese IDs Zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-202">You should cache and use these ids as keys for local storage.</span></span>

<span data-ttu-id="f8f89-203">Das `channelData` Objekt wird nicht in Nachrichten in persönlichen Unterhaltungen eingeschlossen, da diese außerhalb eines Kanals stattfinden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-203">The `channelData` object is not included in messages in personal conversations since these take place outside of any channel.</span></span>

<span data-ttu-id="f8f89-204">Ein typisches channelData-Objekt in einer an Ihren bot gesendeten Aktivität enthält die folgenden Informationen:</span><span class="sxs-lookup"><span data-stu-id="f8f89-204">A typical channelData object in an activity sent to your bot contains the following information:</span></span>

* <span data-ttu-id="f8f89-205">`eventType`Teams-Ereignistyp; nur in Fällen von [Kanal Änderungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates) übergeben</span><span class="sxs-lookup"><span data-stu-id="f8f89-205">`eventType` Teams event type; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates)</span></span>
* <span data-ttu-id="f8f89-206">`tenant.id`Azure Active Directory-Mandanten-ID; in allen Kontexten übergeben</span><span class="sxs-lookup"><span data-stu-id="f8f89-206">`tenant.id` Azure Active Directory tenant ID; passed in all contexts</span></span>
* <span data-ttu-id="f8f89-207">`team`Wird nur in Kanal Kontexten übergeben, nicht im persönlichen Chat.</span><span class="sxs-lookup"><span data-stu-id="f8f89-207">`team` Passed only in channel contexts, not in personal chat.</span></span>
  * <span data-ttu-id="f8f89-208">`id`GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="f8f89-208">`id` GUID for the channel</span></span>
  * <span data-ttu-id="f8f89-209">`name`Name des Teams; nur in Fällen von [Team Umbenennungs Ereignissen](~/resources/bot-v3/bots-notifications.md#team-name-updates) übergeben</span><span class="sxs-lookup"><span data-stu-id="f8f89-209">`name` Name of the team; passed only in cases of [team rename events](~/resources/bot-v3/bots-notifications.md#team-name-updates)</span></span>
* <span data-ttu-id="f8f89-210">`channel`Wird nur in Kanal Kontexten übergeben, wenn der bot erwähnt wird, oder für Ereignisse in Kanälen in Microsoft Teams, in denen der bot hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="f8f89-210">`channel` Passed only in channel contexts when the bot is mentioned or for events in channels in teams where the bot has been added</span></span>
  * <span data-ttu-id="f8f89-211">`id`GUID für den Kanal</span><span class="sxs-lookup"><span data-stu-id="f8f89-211">`id` GUID for the channel</span></span>
  * <span data-ttu-id="f8f89-212">`name`Kanal Name; nur in Fällen von [Kanal Änderungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates)übergeben.</span><span class="sxs-lookup"><span data-stu-id="f8f89-212">`name` Channel name; passed only in cases of [channel modification events](~/resources/bot-v3/bots-notifications.md#channel-updates).</span></span>
* <span data-ttu-id="f8f89-213">`channelData.teamsTeamId`Veraltet.</span><span class="sxs-lookup"><span data-stu-id="f8f89-213">`channelData.teamsTeamId` Deprecated.</span></span> <span data-ttu-id="f8f89-214">Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="f8f89-214">This property is included only for backwards compatibility.</span></span>
* <span data-ttu-id="f8f89-215">`channelData.teamsChannelId`Veraltet.</span><span class="sxs-lookup"><span data-stu-id="f8f89-215">`channelData.teamsChannelId` Deprecated.</span></span> <span data-ttu-id="f8f89-216">Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.</span><span class="sxs-lookup"><span data-stu-id="f8f89-216">This property is included only for backwards compatibility.</span></span>

### <a name="example-channeldata-object-channelcreated-event"></a><span data-ttu-id="f8f89-217">Beispiel für ein channelData-Objekt (channelCreated-Ereignis)</span><span class="sxs-lookup"><span data-stu-id="f8f89-217">Example channelData object (channelCreated event)</span></span>

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

### <a name="net-example"></a><span data-ttu-id="f8f89-218">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="f8f89-218">.NET example</span></span>

<span data-ttu-id="f8f89-219">Das NuGet-Paket " [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) " stellt ein spezielles `TeamsChannelData` Objekt bereit, das Eigenschaften für den Zugriff auf Teams-spezifische Informationen verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="f8f89-219">The [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package provides a specialized `TeamsChannelData` object, which exposes properties to access Teams-specific information.</span></span>

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a><span data-ttu-id="f8f89-220">Senden von Antworten an Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-220">Sending replies to messages</span></span>

<span data-ttu-id="f8f89-221">Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) .net oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) Node.js auf.</span><span class="sxs-lookup"><span data-stu-id="f8f89-221">To reply to an existing message, call [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) in .NET or [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) in Node.js.</span></span> <span data-ttu-id="f8f89-222">Das Robot Builder SDK verarbeitet alle Details.</span><span class="sxs-lookup"><span data-stu-id="f8f89-222">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="f8f89-223">Wenn Sie sich für die Verwendung der Rest-API entscheiden, können Sie auch den [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) Endpunkt aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-223">If you choose to use the REST API, you can also call the [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) endpoint.</span></span>

<span data-ttu-id="f8f89-224">Der Nachrichteninhalt selbst kann einfachen Text oder einige der bereitgestellten [Karten-und Karten Aktionen](~/task-modules-and-cards/cards/cards-actions.md)für bot-Framework enthalten.</span><span class="sxs-lookup"><span data-stu-id="f8f89-224">The message content itself can contain simple text or some of the Bot Framework supplied [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="f8f89-225">Beachten Sie, dass Sie in Ihrem ausgehenden Schema immer das gleiche verwenden sollten, das `serviceUrl` Sie erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="f8f89-225">Please note that in your outbound schema you should always use the same `serviceUrl` as the one you received.</span></span> <span data-ttu-id="f8f89-226">Beachten Sie, dass der Wert `serviceUrl` tendenziell stabil ist, sich jedoch ändern kann.</span><span class="sxs-lookup"><span data-stu-id="f8f89-226">Be aware that the value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="f8f89-227">Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von überprüfen `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="f8f89-227">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

## <a name="updating-messages"></a><span data-ttu-id="f8f89-228">Aktualisieren von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-228">Updating messages</span></span>

<span data-ttu-id="f8f89-229">Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten Inline nach dem Senden dynamisch aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-229">Rather than have your messages be static snapshots of data, your bot can dynamically update messages inline after sending them.</span></span> <span data-ttu-id="f8f89-230">Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-230">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="f8f89-231">Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-231">The new message need not match the original in type.</span></span> <span data-ttu-id="f8f89-232">Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.</span><span class="sxs-lookup"><span data-stu-id="f8f89-232">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

> [!NOTE]
> <span data-ttu-id="f8f89-233">Sie können nur Inhalte aktualisieren, die in Einzelanlagen Nachrichten und Karussell Layouts gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-233">You can update only content sent in single-attachment messages and carousel layouts.</span></span> <span data-ttu-id="f8f89-234">Das Veröffentlichen von Aktualisierungen an Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f8f89-234">Posting updates to messages with multiple attachments in list layout is not supported.</span></span>

### <a name="rest-api"></a><span data-ttu-id="f8f89-235">REST-API</span><span class="sxs-lookup"><span data-stu-id="f8f89-235">REST API</span></span>

<span data-ttu-id="f8f89-236">Um eine Nachrichten Aktualisierung auszugeben, führen Sie einfach eine PUT-Anforderung für den `/v3/conversations/<conversationId>/activities/<activityId>/` Endpunkt mithilfe einer bestimmten Aktivitäts-ID aus.</span><span class="sxs-lookup"><span data-stu-id="f8f89-236">To issue a message update, simply perform a PUT request against the `/v3/conversations/<conversationId>/activities/<activityId>/` endpoint using a given activity ID.</span></span> <span data-ttu-id="f8f89-237">Um dieses Szenario abzuschließen, sollten Sie die vom ursprünglichen Post-Aufruf zurückgegebene Aktivitäts-ID Zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="f8f89-237">To complete this scenario, you should cache the activity ID returned by the original POST call.</span></span>

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a><span data-ttu-id="f8f89-238">.NET-Beispiel</span><span class="sxs-lookup"><span data-stu-id="f8f89-238">.NET example</span></span>

<span data-ttu-id="f8f89-239">Sie können die `UpdateActivityAsync` -Methode im bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-239">You can use the `UpdateActivityAsync` method in the Bot Builder SDK to update an existing message.</span></span>

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

### <a name="nodejs-example"></a><span data-ttu-id="f8f89-240">Node.js Beispiel</span><span class="sxs-lookup"><span data-stu-id="f8f89-240">Node.js example</span></span>

<span data-ttu-id="f8f89-241">Sie können die `session.connector.update` -Methode im bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f8f89-241">You can use the `session.connector.update` method in the Bot Builder SDK to update an existing message.</span></span>

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

## <a name="starting-a-conversation-proactive-messaging"></a><span data-ttu-id="f8f89-242">Starten einer Unterhaltung (proaktives Messaging)</span><span class="sxs-lookup"><span data-stu-id="f8f89-242">Starting a conversation (proactive messaging)</span></span>

<span data-ttu-id="f8f89-243">Sie können ein persönliches Gespräch mit einem Benutzer erstellen oder eine neue Antwort Kette in einem Kanal für Ihr Team bot starten.</span><span class="sxs-lookup"><span data-stu-id="f8f89-243">You can create a personal conversation with a user or start a new reply chain in a channel for your team bot.</span></span> <span data-ttu-id="f8f89-244">Auf diese Weise können Sie Ihre Benutzer oder Benutzer Nachrichten, ohne dass Sie zuerst Kontakt mit Ihrem bot initiieren müssen.</span><span class="sxs-lookup"><span data-stu-id="f8f89-244">This lets you to message your user or users without having them first initiate contact with your bot.</span></span> <span data-ttu-id="f8f89-245">Weitere Informationen hierzu finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="f8f89-245">For more information, see the following topics:</span></span>

<span data-ttu-id="f8f89-246">Weitere allgemeine Informationen zu Unterhaltungen, die von Bots gestartet wurden, finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .</span><span class="sxs-lookup"><span data-stu-id="f8f89-246">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more general information on conversations started by bots.</span></span>

## <a name="deleting-messages"></a><span data-ttu-id="f8f89-247">Löschen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="f8f89-247">Deleting messages</span></span>

<span data-ttu-id="f8f89-248">Nachrichten können mithilfe der Connectors [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) -Methode im [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted)gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="f8f89-248">Messages can be deleted using the connectors [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) method in the [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted).</span></span>

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
