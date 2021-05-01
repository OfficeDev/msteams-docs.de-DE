---
title: Entwerfen Ihres Bots
description: Erfahren Sie, wie Sie einen Teams-Bot entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: d2967abdc6c0055eca8c94ed4e4a7fdf1bdba322
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101695"
---
# <a name="designing-your-microsoft-teams-bot"></a><span data-ttu-id="be8c5-103">Entwerfen Ihres Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="be8c5-103">Designing your Microsoft Teams bot</span></span>

<span data-ttu-id="be8c5-104">Bots sind Unterhaltungs-Apps, die bestimmte Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-104">Bots are conversational apps that perform a specific set of tasks.</span></span> <span data-ttu-id="be8c5-105">Basierend auf dem <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a> kommunizieren Bots mit Benutzern, beantworten ihre Fragen und benachrichtigen sie proaktiv über Änderungen und andere Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="be8c5-105">Based on the <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, bots communicate with users, respond to their questions, and proactively notify them about changes and other events.</span></span> <span data-ttu-id="be8c5-106">Sie sind eine tolle Möglichkeit zur Kontaktaufnahme.</span><span class="sxs-lookup"><span data-stu-id="be8c5-106">They're a great way to reach out.</span></span>

<span data-ttu-id="be8c5-107">Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Bots in Teams hinzufügen, verwenden und verwalten können, um Ihr App-Design zu steuern.</span><span class="sxs-lookup"><span data-stu-id="be8c5-107">To guide your app design, the following information describes and illustrates how people can add, use, and manage bots in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="be8c5-108">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="be8c5-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="be8c5-109">Umfassendere Richtlinien für das Bot-Design, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.</span><span class="sxs-lookup"><span data-stu-id="be8c5-109">You can find more comprehensive bot design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be8c5-110">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="be8c5-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a><span data-ttu-id="be8c5-111">Einen Bot hinzufügen</span><span class="sxs-lookup"><span data-stu-id="be8c5-111">Add a bot</span></span>

<span data-ttu-id="be8c5-112">Bots sind in Chats, Kanälen und persönlichen Apps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="be8c5-112">Bots are available in chats, channels, and personal apps.</span></span> <span data-ttu-id="be8c5-113">Sie können einen Bot auf eine der folgenden Arten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="be8c5-113">You can add a bot one of the following ways:</span></span>

* <span data-ttu-id="be8c5-114">Aus dem Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="be8c5-114">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="be8c5-115">Verwenden des App-Flyouts durch Auswahl des Symbols **Mehr** auf der linken Seite von Teams.</span><span class="sxs-lookup"><span data-stu-id="be8c5-115">Using the app flyout by selecting the **More** icon on the left side of Teams.</span></span>
* <span data-ttu-id="be8c5-116">Mit einer @Erwähnung im neuen Chat- oder Erstellungsfeld (das folgende Beispiel zeigt, wie Sie dies in einem Gruppenchat tun können).</span><span class="sxs-lookup"><span data-stu-id="be8c5-116">With an @mention in the new chat or compose box (the following example shows how you can do this in a group chat).</span></span>

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Beispiel: So fügen Sie einen Bot in einem Gruppenchat mit einer @Erwähnung hinzu." border="false":::

## <a name="introduce-a-bot"></a><span data-ttu-id="be8c5-118">Einführen eines Bots</span><span class="sxs-lookup"><span data-stu-id="be8c5-118">Introduce a bot</span></span>

<span data-ttu-id="be8c5-119">Es ist wichtig, dass sich Ihr Bot vorstellt und beschreibt, was er kann.</span><span class="sxs-lookup"><span data-stu-id="be8c5-119">It’s critical that your bot introduces itself and describes what it can do.</span></span> <span data-ttu-id="be8c5-120">Dieser anfängliche Austausch hilft Personen zu verstehen, was sie mit dem Bot tun sollen, seine Beschränkungen herauszufinden und sich vor allem mit ihm vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-120">This initial exchange helps people understand what to do with the bot, find out its limitations and, most importantly, get comfortable interacting with it.</span></span>

### <a name="welcome-message-in-a-one-on-one-chat"></a><span data-ttu-id="be8c5-121">Willkommensnachricht in einem 1:1-Chat</span><span class="sxs-lookup"><span data-stu-id="be8c5-121">Welcome message in a one-on-one chat</span></span>

<span data-ttu-id="be8c5-122">In persönlichen Kontexten geben Willkommensnachrichten den Ton Ihres Bots an.</span><span class="sxs-lookup"><span data-stu-id="be8c5-122">In personal contexts, welcome messages set your bot's tone.</span></span> <span data-ttu-id="be8c5-123">Die Nachricht enthält eine Begrüßung, was der Bot tun kann, und einige Vorschläge für die Interaktion (z. B. "Stellen Sie mir eine Frage zu...").</span><span class="sxs-lookup"><span data-stu-id="be8c5-123">The message includes a greeting, what the bot can do, and some suggestions for how to interact (for example, “Try asking me about …”).</span></span> <span data-ttu-id="be8c5-124">Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-124">If possible, these suggestions should return stored responses without having to sign in.</span></span>

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einer persönlichen App." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a><span data-ttu-id="be8c5-126">Einführungen in Gruppenchats und Kanäle</span><span class="sxs-lookup"><span data-stu-id="be8c5-126">Introductions in group chats and channels</span></span>

<span data-ttu-id="be8c5-127">Die Einführung Ihres Bots sollte sich in Gruppenchats und -kanälen geringfügig von einem persönlichen Kontext (wie einer persönlichen App) unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="be8c5-127">Your bot's introduction should be slightly different in group chats and channels compared to a personal context (like a personal app).</span></span> <span data-ttu-id="be8c5-128">Wenn Sie in der realen Welt einen Raum voller Personen betreten haben, würden Sie sich vorstellen, anstatt alle zu begrüßen, die bereits dort sind.</span><span class="sxs-lookup"><span data-stu-id="be8c5-128">In real life, if you entered a room full of people; you’d introduce yourself instead of welcoming everyone who’s already there.</span></span> <span data-ttu-id="be8c5-129">Lassen Sie dieses Denken in Ihr Bot-Design einfließen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-129">Carry that thinking into your bot design.</span></span>

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einem kollaborativen Kontext." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a><span data-ttu-id="be8c5-131">Bot-Authentifizierung mit Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="be8c5-131">Bot authentication with single sign-on</span></span>

<span data-ttu-id="be8c5-132">Wenn eine Person einem Bot eine Nachricht sendet, muss möglicherweise eine Anmeldung erforderlich sein, um alle Funktionen zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-132">When a person messages a bot, sign in may be required use all its features.</span></span> <span data-ttu-id="be8c5-133">Sie können den Authentifizierungsprozess mithilfe von Single Sign-On (SSO) vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-133">You can simplify the authentication process using single sign-on (SSO).</span></span>

<span data-ttu-id="be8c5-134">Vergessen Sie nicht: Im Bot-Befehlsmenü (**Was kann ich tun?**) müssen Sie auch einen Befehl zum Abmelden eingeben.</span><span class="sxs-lookup"><span data-stu-id="be8c5-134">Don’t forget: In the bot command menu (**What can I do?**), you must also provide a command to sign out.</span></span>

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Beispiel zeigt einen Bot mit einer Anmeldeschaltfläche." border="false":::

### <a name="tours"></a><span data-ttu-id="be8c5-136">Touren</span><span class="sxs-lookup"><span data-stu-id="be8c5-136">Tours</span></span>

<span data-ttu-id="be8c5-137">Sie können eine Tour mit Begrüßungsnachrichten einfügen und wenn der Bot auf so etwas wie einen Hilfebefehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="be8c5-137">You can include a tour with welcome messages and if the bot responds to something like a “help” command.</span></span> <span data-ttu-id="be8c5-138">Eine Tour ist der effektivste Weg, um zu beschreiben, was Ihr Bot tun kann.</span><span class="sxs-lookup"><span data-stu-id="be8c5-138">A tour is the most effective way to describe what your bot can do.</span></span> <span data-ttu-id="be8c5-139">Falls zutreffend, eignen sie sich auch hervorragend zur Beschreibung der anderen Features Ihrer App (z. B. durch Screenshots Ihrer Messaging-Erweiterung).</span><span class="sxs-lookup"><span data-stu-id="be8c5-139">If applicable, they’re also great for describing your app’s other features (for example, include screenshots of your messaging extension).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be8c5-140">Touren sollten zugänglich sein, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-140">Tours should be accessible without having to sign in.</span></span>

#### <a name="one-on-one-chats"></a><span data-ttu-id="be8c5-141">1:1-Chats</span><span class="sxs-lookup"><span data-stu-id="be8c5-141">One-on-one chats</span></span>

<span data-ttu-id="be8c5-142">In einer persönlichen App bietet ein Karussell einen effektiven Überblick über Ihren Bot und alle anderen Features Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="be8c5-142">In a personal app, a carousel can provide an effective overview of your bot and any other features of your app.</span></span> <span data-ttu-id="be8c5-143">Das Verwenden von Schaltflächen, mit denen Benutzer Bot-Befehle ausprobieren können, wird empfohlen (z. B. **Erstellen einer Aufgabe**).</span><span class="sxs-lookup"><span data-stu-id="be8c5-143">Including buttons the let users try bot commands is encouraged (for example, **Create a task**).</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Beispiel zeigt eine Bot-Tour in einem 1:1-Chat." border="false":::

#### <a name="channels-and-group-chats"></a><span data-ttu-id="be8c5-145">Kanäle und Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="be8c5-145">Channels and group chats</span></span>

<span data-ttu-id="be8c5-146">In Kanälen und Gruppenchats sollte eine Tour in einem Modal (auch als [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) bezeichnet) geöffnet werden, damit laufende Gespräche nicht unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="be8c5-146">In channels and group chats, a tour should open in a modal (also known as a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) so it doesn’t interrupt ongoing conversations.</span></span> <span data-ttu-id="be8c5-147">Dies gibt Ihnen auch die Möglichkeit, rollenbasierte Ansichten für Ihre Tour zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-147">This also gives you the option to implement role-based views for your tour.</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Beispiel zeigt eine Bot-Tour in einem Kanal." border="false":::

## <a name="chat-with-a-bot"></a><span data-ttu-id="be8c5-149">Chatten mit einem Bot</span><span class="sxs-lookup"><span data-stu-id="be8c5-149">Chat with a bot</span></span>

<span data-ttu-id="be8c5-150">Bots werden direkt in das Messaging-Framework des Teams integriert.</span><span class="sxs-lookup"><span data-stu-id="be8c5-150">Bots integrate directly into Team’s messaging framework.</span></span> <span data-ttu-id="be8c5-151">Benutzer können mit einem Bot chatten, um ihre Fragen zu beantworten, oder Befehle eingeben, damit der Bot eine enge oder bestimmte Gruppe von Aufgaben ausführt.</span><span class="sxs-lookup"><span data-stu-id="be8c5-151">Users can chat with a bot to get their questions answered or type commands to have the bot perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="be8c5-152">Bots können Benutzer proaktiv per Chat über Änderungen oder Aktualisierungen Ihrer App informieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-152">Bots can proactively notify users about changes or updates to your app via chat.</span></span>

### <a name="chat-with-a-bot-in-different-contexts"></a><span data-ttu-id="be8c5-153">Chatten mit einem Bot in verschiedenen Kontexten</span><span class="sxs-lookup"><span data-stu-id="be8c5-153">Chat with a bot in different contexts</span></span>

<span data-ttu-id="be8c5-154">Sie können Bots in den folgenden Kontexten verwenden:</span><span class="sxs-lookup"><span data-stu-id="be8c5-154">You can use bots in the following contexts:</span></span>

* <span data-ttu-id="be8c5-155">**Persönliche Apps**: In einer persönlichen App verfügt ein Bot über eine eigene Chat-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="be8c5-155">**Personal apps**: In a personal app, a bot has a dedicated chat tab.</span></span>
* <span data-ttu-id="be8c5-156">**1:1-Chat**: Ein Benutzer kann eine private Unterhaltung mit einem Bot initiieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-156">**One-on-one chat**: A user can initiate a private conversation with a bot.</span></span> <span data-ttu-id="be8c5-157">Es ist die gleiche Erfahrung wie bei der Verwendung eines Bots in einer persönlichen App.</span><span class="sxs-lookup"><span data-stu-id="be8c5-157">It's the same experience as using a bot in a personal app.</span></span>
* <span data-ttu-id="be8c5-158">**Gruppenchat**: Benutzer können mit einem Bot in einem Gruppenchat interagieren, indem sie den Bot @erwähnen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-158">**Group chat**: People can interact with a bot in a group chat by @mentioning the bot.</span></span>
* <span data-ttu-id="be8c5-159">**Kanal**: Benutzer können mit einem Bot in einem Kanal interagieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-159">**Channel**: People can interact with a bot in a channel.</span></span> <span data-ttu-id="be8c5-160">indem sie den Bot-Namen im Erstellungsfeld @erwähnen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-160">by @mentioning the bot name in the compose box.</span></span> <span data-ttu-id="be8c5-161">Denken Sie daran, dass der Bot in diesem Zusammenhang dem gesamten Team zur Verfügung steht, nicht nur dem Kanal.</span><span class="sxs-lookup"><span data-stu-id="be8c5-161">Remember, in this context, the bot is available to the entire team, not just the channel.</span></span>

### <a name="anatomy"></a><span data-ttu-id="be8c5-162">Anatomie</span><span class="sxs-lookup"><span data-stu-id="be8c5-162">Anatomy</span></span>

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Bots." border="false":::

|<span data-ttu-id="be8c5-164">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="be8c5-164">Counter</span></span>|<span data-ttu-id="be8c5-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be8c5-165">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="be8c5-166">1</span><span class="sxs-lookup"><span data-stu-id="be8c5-166">1</span></span>|<span data-ttu-id="be8c5-167">**App-Name und -Symbol**</span><span class="sxs-lookup"><span data-stu-id="be8c5-167">**App name and icon**</span></span>|
|<span data-ttu-id="be8c5-168">2</span><span class="sxs-lookup"><span data-stu-id="be8c5-168">2</span></span>|<span data-ttu-id="be8c5-169">**Chat-Registerkarte**: Öffnet den Bereich für Gespräche mit Ihrem Bot (gilt nur für persönliche Apps).</span><span class="sxs-lookup"><span data-stu-id="be8c5-169">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="be8c5-170">3</span><span class="sxs-lookup"><span data-stu-id="be8c5-170">3</span></span>|<span data-ttu-id="be8c5-171">**Benutzerdefinierte Registerkarten**: Öffnet weitere Inhalte zu Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="be8c5-171">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="be8c5-172">4 </span><span class="sxs-lookup"><span data-stu-id="be8c5-172">4</span></span>|<span data-ttu-id="be8c5-173">**Info-Registerkarte**: Zeigt grundlegende Informationen zu Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="be8c5-173">**About tab**: Displays basic information about your app.</span></span>|
|<span data-ttu-id="be8c5-174">5 </span><span class="sxs-lookup"><span data-stu-id="be8c5-174">5</span></span>|<span data-ttu-id="be8c5-175">**Chat-Blase**: Bot-Unterhaltungen verwenden das Team-Messaging-Framework.</span><span class="sxs-lookup"><span data-stu-id="be8c5-175">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="be8c5-176">6 </span><span class="sxs-lookup"><span data-stu-id="be8c5-176">6</span></span>|<span data-ttu-id="be8c5-177">**Adaptive Karte**: Wenn die Antworten Ihres Bots adaptive Karten enthalten, nimmt die Karte die gesamte Breite der Chat-Blase ein.</span><span class="sxs-lookup"><span data-stu-id="be8c5-177">**Adaptive Card**: If your bot’s responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|
|<span data-ttu-id="be8c5-178">7 </span><span class="sxs-lookup"><span data-stu-id="be8c5-178">7</span></span>|<span data-ttu-id="be8c5-179">**Befehlsmenü**: Zeigt die von Ihnen definierten Standardbefehle Ihres Bots an.</span><span class="sxs-lookup"><span data-stu-id="be8c5-179">**Command menu**: Displays your bot's standard commands (defined by you).</span></span>

### <a name="command-menu"></a><span data-ttu-id="be8c5-180">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="be8c5-180">Command menu</span></span>

<span data-ttu-id="be8c5-181">Das Befehlsmenü enthält eine Liste von Wörtern oder Begriffen, auf die Ihr Bot immer reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="be8c5-181">The command menu provides a list of words or phrases you want your bot to always respond to.</span></span> <span data-ttu-id="be8c5-182">Das Befehlsmenü wird über dem Verfassungsfeld angezeigt, wenn sich jemand mit einem Bot unterhält.</span><span class="sxs-lookup"><span data-stu-id="be8c5-182">The command menu displays above the compose box when someone is conversing with a bot.</span></span> <span data-ttu-id="be8c5-183">Wenn ein Befehl ausgewählt ist, wird er in eine Nachricht eingefügt.</span><span class="sxs-lookup"><span data-stu-id="be8c5-183">When a command is selected, it gets inserted into a message.</span></span>

<span data-ttu-id="be8c5-184">Die Liste der Befehle sollte kurz sein.</span><span class="sxs-lookup"><span data-stu-id="be8c5-184">The list of commands should be brief.</span></span> <span data-ttu-id="be8c5-185">Das Menü soll nur die wichtigsten Features Ihres Bots hervorheben.</span><span class="sxs-lookup"><span data-stu-id="be8c5-185">The menu is only meant to highlight your bot’s primary features.</span></span> <span data-ttu-id="be8c5-186">Halten Sie auch Befehle präzise.</span><span class="sxs-lookup"><span data-stu-id="be8c5-186">Keep commands concise, too.</span></span> <span data-ttu-id="be8c5-187">Erstellen Sie beispielsweise einen Befehl namens **Hilfe** anstelle von **Können Sie mir bitte helfen?**.</span><span class="sxs-lookup"><span data-stu-id="be8c5-187">For example, create a command called **Help** instead of **Can you please help me**?</span></span>
<span data-ttu-id="be8c5-188">Das Befehlsmenü muss unabhängig vom Unterhaltungsstatus immer verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="be8c5-188">The command menu must always be available regardless of the state of the conversation.</span></span>

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Beispiel zeigt das Befehlsmenü eines Bots." border="false":::

## <a name="understand-what-people-are-saying"></a><span data-ttu-id="be8c5-190">Verstehen, was Personen sagen</span><span class="sxs-lookup"><span data-stu-id="be8c5-190">Understand what people are saying</span></span>

<span data-ttu-id="be8c5-191">Verwenden Sie einen Thesaurus und arbeiten Sie mit Personen mit möglichst vielen unterschiedlichen Hintergründen, um unterschiedliche Interpretationen von Standardabfragen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-191">Use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of standard queries.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Hallo&quot; interpretieren könnte." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Hilfe&quot; interpretieren könnte." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Danke&quot; interpretieren könnte." border="false":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a><span data-ttu-id="be8c5-195">Extrahieren von Absichten und Daten aus Nachrichten</span><span class="sxs-lookup"><span data-stu-id="be8c5-195">Extract intent and data from messages</span></span>

<span data-ttu-id="be8c5-196">Entwerfen Sie Ihren Bot so, dass er Absichten erkennt, die erfassen, was jemand von einem Bot als Antwort auf eine Nachricht oder eine Anfrage erwartet.</span><span class="sxs-lookup"><span data-stu-id="be8c5-196">Design your bot to recognize intent, which captures what someone wants from a bot in response to a message or query.</span></span> <span data-ttu-id="be8c5-197">Intent klassifiziert eine Nachricht oder Abfrage als eine einzelne Aktion mit einem oder mehreren Datenobjekten, die von der Aktion betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="be8c5-197">Intent classifies a message or query as a single action with one or more data objects that are affected by the action.</span></span> 

<span data-ttu-id="be8c5-198">Die folgenden Beispiele beschreiben die Benutzerabsicht und die Daten in Nachrichten, die an Bots gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="be8c5-198">The following examples outline the user intent and data in messages sent to bots.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="Beispiel im Satz &quot;Flug nach Seattle buchen&quot;, Benutzerabsicht ist &quot;Flug buchen&quot; und Daten sind &quot;Seattle&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="Beispiel im Satz &quot;Wann öffnet das Geschäft?&quot; , die Benutzerabsicht lautet &quot;Wann&quot; und die Daten sind &quot;öffnet&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Beispiel im Satz &quot;Besprechung planen mit Bob vom Vertrieb um 13:00 Uhr&quot;. Die Benutzerabsicht lautet &quot;Besprechung planen&quot; und die Daten lauten &quot;13:00 Uhr&quot; und &quot;Bob vom Vertrieb&quot;." border="false":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a><span data-ttu-id="be8c5-202">Analysieren und Verbessern</span><span class="sxs-lookup"><span data-stu-id="be8c5-202">Analyze and improve</span></span>

<span data-ttu-id="be8c5-203">Erfahren Sie, was Benutzer sagen, wenn Sie mit Ihrem Bot chatten.</span><span class="sxs-lookup"><span data-stu-id="be8c5-203">Learn what users say when chatting with your bot.</span></span> <span data-ttu-id="be8c5-204">Dies ist ein fortlaufender, iterativer Prozess, da Ihre Benutzerbasis an verschiedenen Standorten und in verschiedenen Organisationen wächst.</span><span class="sxs-lookup"><span data-stu-id="be8c5-204">This will be an ongoing, iterative process as your user base grows in different locations and orgs.</span></span> <span data-ttu-id="be8c5-205">Sie können die Spracherkennung und Absichtszuordnung Ihres Bots mit Microsoft Language Understanding (LUIS) optimieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-205">You can tune your bot's language recognition and intent mapping with Microsoft Language Understanding (LUIS).</span></span>

* <span data-ttu-id="be8c5-206">[Grundlegendes zu LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Erfahren Sie, wie LUIS AI verwendet, um Ihren App-Daten ein Verständnis von natürlicher Sprache (NLU) zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="be8c5-206">[Understanding LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Find out how LUIS uses AI to provide natural language understanding (NLU) to your app data.</span></span>
* <span data-ttu-id="be8c5-207">[Integration in LUIS](https://www.luis.ai/): Fügen Sie Ihrem Bot Funktionen in natürlicher Sprache hinzu, ohne den komplexen Prozess der Erstellung von Modellen für maschinelles Lernen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-207">[Integrating with LUIS](https://www.luis.ai/): Add natural language capabilities to your bot without the complex process of creating machine learning models.</span></span>

## <a name="use-cases"></a><span data-ttu-id="be8c5-208">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="be8c5-208">Use cases</span></span>

### <a name="simple-queries"></a><span data-ttu-id="be8c5-209">Einfache Abfragen</span><span class="sxs-lookup"><span data-stu-id="be8c5-209">Simple queries</span></span>

<span data-ttu-id="be8c5-210">Bots bieten eine genaue Übereinstimmung mit einer Abfrage oder einer Gruppe verwandter Übereinstimmungen, um die Begriffsklärung zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="be8c5-210">Bots can deliver an exact match to a query or a group of related matches to help with disambiguation.</span></span> <span data-ttu-id="be8c5-211">Gruppieren Sie den Inhalt für verwandte Übereinstimmungen mithilfe einer Listenkarte.</span><span class="sxs-lookup"><span data-stu-id="be8c5-211">For related matches, group the content using a list card.</span></span>

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrageinteraktion mit einem Bot." border="false":::

### <a name="multi-turn-interactions"></a><span data-ttu-id="be8c5-213">Mehrfach-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="be8c5-213">Multi-turn interactions</span></span>

<span data-ttu-id="be8c5-214">Während Ihr Bot vollständige Anfragen und Fragen unterstützen kann, sollte er auch in der Lage sein, Interaktionen mit mehreren Runden zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="be8c5-214">While your bot can support complete requests and questions, it should also be able to handle multi-turn interactions.</span></span> <span data-ttu-id="be8c5-215">Das Vorhersehen möglicher nächster Schritte erleichtert es den Mitarbeitern erheblich, einen vollständigen Aufgabenablauf durchzuführen (anstatt von ihnen zu erwarten, dass sie eine umfassende Anfrage erstellen).</span><span class="sxs-lookup"><span data-stu-id="be8c5-215">Anticipating possible next steps makes it much easier for people to a complete task flow (rather than expecting them to craft a comprehensive request).</span></span>

<span data-ttu-id="be8c5-216">Im folgenden Beispiel antwortet der Bot auf jede Nachricht mit Optionen für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="be8c5-216">In the following example, the bot responds to each message with options for what might want to do next.</span></span>

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Beispiel zeigt eine Mehrfach-Interaktion mit einem Bot." border="false":::

### <a name="reach-out-to-users"></a><span data-ttu-id="be8c5-218">Benutzer erreichen</span><span class="sxs-lookup"><span data-stu-id="be8c5-218">Reach out to users</span></span>

<span data-ttu-id="be8c5-219">Mit proaktiven Nachrichten kann sich Ihr Bot wie ein Digest verhalten, der mit einer bestimmten Häufigkeit Benachrichtigungen sendet, die für eine Person, einen Gruppenchat oder einen Kanal relevant sind.</span><span class="sxs-lookup"><span data-stu-id="be8c5-219">With proactive messaging, your bot can act like a digest that sends notifications relevant to an individual, group chat, or channel at a specific frequency.</span></span> <span data-ttu-id="be8c5-220">Ein Bot kann eine Nachricht senden, wenn sich etwas in einem Dokument geändert hat oder ein Arbeitselement geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="be8c5-220">A bot may send a message when something has changed in a document or a work item is closed.</span></span>

<span data-ttu-id="be8c5-221">Im folgenden Beispiel erhält ein Benutzer eine Popup-Benachrichtigung, dass ein Bot sie in einem anderen Kanal benachrichtigt hat.</span><span class="sxs-lookup"><span data-stu-id="be8c5-221">In the following example, a user gets a toast notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Das Beispiel zeigt ein Popup eines Bots, der einen Benutzer proaktiv von einem anderen Kanal aus benachrichtigt." border="false":::

<span data-ttu-id="be8c5-223">Nun kann der Benutzer in diesem Kanal seine Nachricht des Bots lesen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-223">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Beispiel: Benutzer betrachtet die proaktive Nachricht des Bots." border="false":::

### <a name="use-tabs-with-bots"></a><span data-ttu-id="be8c5-225">Verwenden von Registerkarten mit Bots</span><span class="sxs-lookup"><span data-stu-id="be8c5-225">Use tabs with bots</span></span>

<span data-ttu-id="be8c5-226">Eine Registerkarte kann die Verwendung Ihres Bots vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-226">A tab can make your bot easier to use.</span></span> <span data-ttu-id="be8c5-227">Wenn Ihr Bot beispielsweise Arbeitselemente erstellen kann, ist es hilfreich, alle diese Elemente an einer zentralen Stelle in einer Registerkarte anzuzeigen. Weitere Informationen zum [Entwerfen von Registerkarten](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="be8c5-227">For example, if your bot can create work items, it would be nice to show all those items in a central location inside a tab. See more about [designing tabs](../../tabs/design/tabs.md).</span></span>

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte beim Organisieren von Bot-Inhalten helfen kann." border="false":::

## <a name="manage-a-bot"></a><span data-ttu-id="be8c5-229">Verwalten eines Bots</span><span class="sxs-lookup"><span data-stu-id="be8c5-229">Manage a bot</span></span>

<span data-ttu-id="be8c5-230">Benutzer sollten in der Lage sein, die Einstellungen eines Bots zu ändern.</span><span class="sxs-lookup"><span data-stu-id="be8c5-230">Users should be able to change a bot's settings.</span></span> <span data-ttu-id="be8c5-231">Sie können diese Funktionalität mit Bot-Befehlen bereitstellen, aber es ist normalerweise effizienter, alle Einstellungen in ein [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) aufzunehmen (wie im folgenden Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="be8c5-231">You can provide this functionality with bot commands, but it's usually more efficient to include all settings in a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (as shown in the following example).</span></span>

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Beispiel zeigt ein Aufgabenmodul zum Konfigurieren der Einstellungen eines Bots." border="false":::

## <a name="best-practices"></a><span data-ttu-id="be8c5-233">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="be8c5-233">Best practices</span></span>

<span data-ttu-id="be8c5-234">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-234">Use these recommendations to create a quality app experience.</span></span>

### <a name="content"></a><span data-ttu-id="be8c5-235">Inhalt</span><span class="sxs-lookup"><span data-stu-id="be8c5-235">Content</span></span>

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Beispiel für eine bewährte Methode eines Bots zum Einrichten einer eindeutigen Persona." border="false":::

#### <a name="do-establish-a-clear-persona"></a><span data-ttu-id="be8c5-237">Do: Erstellen einer eindeutigen Persona</span><span class="sxs-lookup"><span data-stu-id="be8c5-237">Do: Establish a clear persona</span></span>

<span data-ttu-id="be8c5-238">Ist der Ton Ihres Bots freundlich und leicht, "nur die Fakten" oder super ungewöhnlich?</span><span class="sxs-lookup"><span data-stu-id="be8c5-238">Is your bot's tone friendly and light, “just the facts”, or super quirky?</span></span> <span data-ttu-id="be8c5-239">Wie soll er in verschiedenen Szenarien reagieren?</span><span class="sxs-lookup"><span data-stu-id="be8c5-239">How should it respond in different scenarios?</span></span> <span data-ttu-id="be8c5-240">Das Planen und Dokumentieren der Persona Ihres Bots erleichtert das Schreiben von Antworten, die natürlich und zusammenhängend erscheinen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-240">Planning and documenting your bot's persona makes it easier to write responses that seem natural and cohesive.</span></span>

<span data-ttu-id="be8c5-241">Weitere Informationen zum Schreiben für Bots finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span><span class="sxs-lookup"><span data-stu-id="be8c5-241">See more about writing for bots in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Beispiel, das zeigt, was Ihr Bot tun kann." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a><span data-ttu-id="be8c5-243">Do: Vermitteln Sie eindeutig, was Ihr Bot alles kann.</span><span class="sxs-lookup"><span data-stu-id="be8c5-243">Do: Clearly convey what your bot can do</span></span>

<span data-ttu-id="be8c5-244">Willkommensnachrichten und Touren helfen den Benutzern zu verstehen, was sie mit Ihrem Bot tun können.</span><span class="sxs-lookup"><span data-stu-id="be8c5-244">Welcome messages and tours help people understand what they can do with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Beispiel, das zeigt, dass die Funktionen Ihres Bots nicht verhüllt werden sollen." border="false":::

#### <a name="dont-obscure-your-bots-features"></a><span data-ttu-id="be8c5-246">Don‘t: Verschleiern der Features Ihres Bots</span><span class="sxs-lookup"><span data-stu-id="be8c5-246">Don't: Obscure your bot's features</span></span>

<span data-ttu-id="be8c5-247">Der erste Eindruck zählt.</span><span class="sxs-lookup"><span data-stu-id="be8c5-247">First impressions matter.</span></span> <span data-ttu-id="be8c5-248">Personen sind wahrscheinlich verwirrt oder misstrauisch, wenn ihnen eine unscheinbare Anmeldenachricht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="be8c5-248">People will likely be confused or suspicious when presented with a nondescript sign-in message.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Beispiel, in dem Ihr Bot keine Fragen erkennt." border="false":::

#### <a name="do-recognize-non-questions"></a><span data-ttu-id="be8c5-250">Do: Nicht-Fragen erkennen</span><span class="sxs-lookup"><span data-stu-id="be8c5-250">Do: Recognize non-questions</span></span>

<span data-ttu-id="be8c5-251">Ihr Bot sollte in der Lage sein, auf Nachrichten wie "Hallo", "Hilfe" und "Danke" zu antworten und gleichzeitig häufige Rechtschreibfehler und Umgangssprachen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-251">Your bot should be able to respond to messages like "Hi", "Help", and "Thanks" while also accounting for common misspellings and colloquialisms.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Beispiel, in dem Sie ungeschickte Antworten auf einfache Botnachrichten vermeiden sollten." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a><span data-ttu-id="be8c5-253">Don‘t: Keine Gelegenheit verpassen, die Freude schenkt</span><span class="sxs-lookup"><span data-stu-id="be8c5-253">Don't: Miss out on opportunities to delight</span></span>

<span data-ttu-id="be8c5-254">Einige Personen erwarten, dass Gespräche auf natürliche Weise ablaufen, so wie mit einer realen Person.</span><span class="sxs-lookup"><span data-stu-id="be8c5-254">Some people expect conversations to flow naturally like they would with a real person.</span></span> <span data-ttu-id="be8c5-255">Vermeiden Sie ungeschickte Antworten auf einfache Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="be8c5-255">Try to avoid clumsy responses to simple messages.</span></span>

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a><span data-ttu-id="be8c5-256">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="be8c5-256">Troubleshooting</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Ein Beispiel für Bots sollte Benutzern dabei helfen, die Verwendung von Bots zu verstehen." border="false":::

#### <a name="do-provide-help"></a><span data-ttu-id="be8c5-258">Do: Hilfe anbieten</span><span class="sxs-lookup"><span data-stu-id="be8c5-258">Do: Provide help</span></span>

<span data-ttu-id="be8c5-259">Wenn Ihr Bot eine Anfrage nicht erfüllen kann, bieten Sie einem Benutzer Möglichkeiten, sich über die Interaktion mit Ihrem Bot zu informieren.</span><span class="sxs-lookup"><span data-stu-id="be8c5-259">If your bot can’t satisfy a request, provide ways for a user to educate themselves about interacting with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Beispiel, in dem Der Bot benutzer nicht litzen sollte." border="false":::

#### <a name="dont-leave-users-stranded"></a><span data-ttu-id="be8c5-261">Don‘t: Lassen Sie Benutzer nicht hängen</span><span class="sxs-lookup"><span data-stu-id="be8c5-261">Don't: Leave users stranded</span></span>

<span data-ttu-id="be8c5-262">Benutzer werden Ihren Bot schnell verlassen, wenn er keine Probleme beheben kann.</span><span class="sxs-lookup"><span data-stu-id="be8c5-262">People will quickly abandon your bot if they can’t troubleshoot issues.</span></span>

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a><span data-ttu-id="be8c5-263">Komplexe Interaktionen</span><span class="sxs-lookup"><span data-stu-id="be8c5-263">Complex interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Beispiel, in dem Sie Aufgabenmodule oder Registerkarten mit Ihrem Bot für komplexe Interaktionen verwenden können." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a><span data-ttu-id="be8c5-265">Do: Verwenden Sie Aufgabenmodule oder Registerkarten</span><span class="sxs-lookup"><span data-stu-id="be8c5-265">Do: Use task modules or tabs</span></span>

<span data-ttu-id="be8c5-266">Wenn Ihr Bot eine Antwort liefert, die einige weitere Schritte erfordert, können Sie eine Verknüpfung zu einem Aufgabenmodul oder einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-266">If your bot provides an answer that requires a few more steps, you can link to a task module or tab to complete the task or flow.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Ihr Bot Interaktionen mit mehreren Drehungen vermeiden sollte." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a><span data-ttu-id="be8c5-268">Don‘t: Machen Sie Mehrfach-Interaktionen nicht langweilig</span><span class="sxs-lookup"><span data-stu-id="be8c5-268">Don't: Make multi-turn interactions tedious</span></span>

<span data-ttu-id="be8c5-269">Eine umfassende Unterhaltung zum Abschließen einer einzelnen Aufgabe ist langsam und übermäßig komplex.</span><span class="sxs-lookup"><span data-stu-id="be8c5-269">An extensive conversation to complete a single task is slow and overly complex.</span></span> <span data-ttu-id="be8c5-270">Außerdem muss der Entwickler Statusänderungen berücksichtigen (z. B. das Zeitlimit der Unterhaltung oder das Senden einer Nachricht zum Abbrechen).</span><span class="sxs-lookup"><span data-stu-id="be8c5-270">It also requires the developer to account for state changes (such as the conversation timing out or you sending a “Cancel” message).</span></span>

   :::column-end:::
:::row-end:::

### <a name="privacy"></a><span data-ttu-id="be8c5-271">Datenschutz</span><span class="sxs-lookup"><span data-stu-id="be8c5-271">Privacy</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Beispiel, in dem gezeigt wird, wie Bots nur private Informationen in einem persönlichen Kontext anzeigen sollten." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a><span data-ttu-id="be8c5-273">Do: Zeigen Sie vertrauliche Informationen nur in einem persönlichen Kontext an</span><span class="sxs-lookup"><span data-stu-id="be8c5-273">Do: Only show sensitive info in a personal context</span></span>

<span data-ttu-id="be8c5-274">Wenn sich Ihr Bot in einem Gruppenchat oder -kanal befindet, empfehlen wir, Benutzer an einen privaten Ort (z. B. ein Aufgabenmodul, eine Registerkarte oder einen Browser) zu leiten, um vertrauliche Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="be8c5-274">If your bot is in a group chat or channel, we recommend directing users to a private location (such as a task module, tab, or browser) to view sensitive information.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Bots keine vertraulichen Informationen für eine Gruppe oder Personen anzeigen sollten." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a><span data-ttu-id="be8c5-276">Don‘t: Einige Inhalte sollten nicht für alle einsehbar sein</span><span class="sxs-lookup"><span data-stu-id="be8c5-276">Don't: Some content isn’t meant to be seen by everyone</span></span>

<span data-ttu-id="be8c5-277">Ihr Bot sollte keine vertraulichen Informationen an Personen in einer Gruppe weitergeben.</span><span class="sxs-lookup"><span data-stu-id="be8c5-277">Your bot shouldn’t reveal sensitive information to a group of people.</span></span>

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="be8c5-278">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="be8c5-278">See also</span></span>

<span data-ttu-id="be8c5-279">Diese weiteren Richtlinien könnten bei Ihrem Bot-Design hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="be8c5-279">These other guidelines may help with your bot design:</span></span>

* [<span data-ttu-id="be8c5-280">Entwerfen Ihrer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="be8c5-280">Designing your personal app</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="be8c5-281">Entwerfen Adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="be8c5-281">Designing Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)
* [<span data-ttu-id="be8c5-282">Entwerfen von Aufgabenmodulen</span><span class="sxs-lookup"><span data-stu-id="be8c5-282">Designing task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
