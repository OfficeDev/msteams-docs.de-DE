---
title: Entwerfen Ihres bot
description: Hier erfahren Sie, wie Sie einen Teams-bot entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d1a7470f4986de22ecca7071823b620cb0234abb
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605427"
---
# <a name="designing-your-microsoft-teams-bot"></a><span data-ttu-id="d43d6-103">Entwerfen Ihres Microsoft Teams-bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-103">Designing your Microsoft Teams bot</span></span>

<span data-ttu-id="d43d6-104">Bots sind Unterhaltungs-apps, die eine bestimmte Gruppe von Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-104">Bots are conversational apps that perform a specific set of tasks.</span></span> <span data-ttu-id="d43d6-105">Basierend auf dem <a href="https://dev.botframework.com/" target="_blank">Microsoft-bot-Framework</a>kommunizieren Bots mit Benutzern, Antworten auf Ihre Fragen und informieren Sie proaktiv über Änderungen und andere Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="d43d6-105">Based on the <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, bots communicate with users, respond to their questions, and proactively notify them about changes and other events.</span></span> <span data-ttu-id="d43d6-106">Sie sind eine großartige Möglichkeit, um Sie zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-106">They're a great way to reach out.</span></span>

<span data-ttu-id="d43d6-107">Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Bots in Microsoft Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="d43d6-107">To guide your app design, the following information describes and illustrates how people can add, use, and manage bots in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="d43d6-108">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="d43d6-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="d43d6-109">Ausführlichere bot-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="d43d6-109">You can find more comprehensive bot design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d43d6-110">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="d43d6-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a><span data-ttu-id="d43d6-111">Hinzufügen eines bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-111">Add a bot</span></span>

<span data-ttu-id="d43d6-112">Bots stehen in Chats, Kanälen und persönlichen Apps zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="d43d6-112">Bots are available in chats, channels, and personal apps.</span></span> <span data-ttu-id="d43d6-113">Sie können einen bot einer der folgenden Möglichkeiten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="d43d6-113">You can add a bot one of the following ways:</span></span>

* <span data-ttu-id="d43d6-114">Aus dem Microsoft Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="d43d6-114">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="d43d6-115">Verwenden des App-Flyouts, indem Sie das Symbol **Weitere** auf der linken Seite von Teams auswählen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-115">Using the app flyout by selecting the **More** icon on the left side of Teams.</span></span>
* <span data-ttu-id="d43d6-116">Mit einem @mention im Feld Neuer Chat oder verfassen (im folgenden Beispiel wird gezeigt, wie Sie dies in einem Gruppenchat tun können).</span><span class="sxs-lookup"><span data-stu-id="d43d6-116">With an @mention in the new chat or compose box (the following example shows how you can do this in a group chat).</span></span>

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Beispiel zeigt, wie ein bot in einem Gruppenchat mithilfe eines @mention hinzugefügt wird." border="false":::

## <a name="introduce-a-bot"></a><span data-ttu-id="d43d6-118">Einführung eines bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-118">Introduce a bot</span></span>

<span data-ttu-id="d43d6-119">Es ist wichtig, dass sich Ihr bot selbst vorstellt und beschreibt, was er tun kann.</span><span class="sxs-lookup"><span data-stu-id="d43d6-119">It’s critical that your bot introduces itself and describes what it can do.</span></span> <span data-ttu-id="d43d6-120">Diese anfängliche Exchange hilft den Benutzern zu verstehen, was mit dem bot zu tun ist, um seine Einschränkungen herauszufinden und, was am wichtigsten ist, eine bequeme Interaktion mit ihm zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d43d6-120">This initial exchange helps people understand what to do with the bot, find out its limitations and, most importantly, get comfortable interacting with it.</span></span>

### <a name="welcome-message-in-a-one-on-one-chat"></a><span data-ttu-id="d43d6-121">Willkommensnachricht in einem Einzelchat</span><span class="sxs-lookup"><span data-stu-id="d43d6-121">Welcome message in a one-on-one chat</span></span>

<span data-ttu-id="d43d6-122">In persönlichen Kontexten legen Begrüßungsnachrichten den Ton Ihres bot fest.</span><span class="sxs-lookup"><span data-stu-id="d43d6-122">In personal contexts, welcome messages set your bot's tone.</span></span> <span data-ttu-id="d43d6-123">Die Nachricht enthält eine Begrüßung, was der bot tun kann, und einige Vorschläge für die Interaktion (beispielsweise "versuchen Sie, mich zu Fragen...").</span><span class="sxs-lookup"><span data-stu-id="d43d6-123">The message includes a greeting, what the bot can do, and some suggestions for how to interact (for example, “Try asking me about …”).</span></span> <span data-ttu-id="d43d6-124">Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben, ohne sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-124">If possible, these suggestions should return stored responses without having to sign in.</span></span>

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Beispiel zeigt eine bot-Einführung in einer persönlichen app." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a><span data-ttu-id="d43d6-126">Einführungen in Gruppenchats und-Kanälen</span><span class="sxs-lookup"><span data-stu-id="d43d6-126">Introductions in group chats and channels</span></span>

<span data-ttu-id="d43d6-127">Die Einführung Ihres bot sollte in Gruppenchats und Kanälen im Vergleich zu einem persönlichen Kontext (wie einer persönlichen APP) geringfügig unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="d43d6-127">Your bot's introduction should be slightly little different in group chats and channels compared to a personal context (like a personal app).</span></span> <span data-ttu-id="d43d6-128">Im wirklichen Leben, wenn Sie einen Raum voller Personen betraten; Sie würden sich vorstellen, anstatt alle Personen, die bereits dort sind, zu begrüßen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-128">In real life, if you entered a room full of people; you’d introduce yourself instead of welcoming everyone who’s already there.</span></span> <span data-ttu-id="d43d6-129">Tragen Sie dieses Denken in Ihr bot-Design.</span><span class="sxs-lookup"><span data-stu-id="d43d6-129">Carry that thinking into your bot design.</span></span>

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Beispiel zeigt eine bot-Einführung in einen kollaborativen Kontext." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a><span data-ttu-id="d43d6-131">Bot-Authentifizierung mit einmaligem Anmelden</span><span class="sxs-lookup"><span data-stu-id="d43d6-131">Bot authentication with single sign-on</span></span>

<span data-ttu-id="d43d6-132">Wenn eine Person einen bot Nachrichten kann, müssen Sie unter Umständen alle ihre Funktionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-132">When a person messages a bot, sign in may be required use all its features.</span></span> <span data-ttu-id="d43d6-133">Sie können den Authentifizierungsprozess mithilfe von einmaligem Anmelden (Single Sign-on, SSO) vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-133">You can simplify the authentication process using single sign-on (SSO).</span></span>

<span data-ttu-id="d43d6-134">Vergessen Sie nicht: im bot-Befehlsmenü (**Was kann ich tun?**) müssen Sie auch einen Befehl zur Abmeldung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-134">Don’t forget: In the bot command menu (**What can I do?**), you must also provide a command to sign out.</span></span>

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Beispiel zeigt einen bot mit einer Anmeldeschaltfläche." border="false":::

### <a name="tours"></a><span data-ttu-id="d43d6-136">Touren</span><span class="sxs-lookup"><span data-stu-id="d43d6-136">Tours</span></span>

<span data-ttu-id="d43d6-137">Sie können eine Tour mit Begrüßungsnachrichten einschließen, und wenn der bot auf etwas wie einen "Help"-Befehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="d43d6-137">You can include a tour with welcome messages and if the bot responds to something like a “help” command.</span></span> <span data-ttu-id="d43d6-138">Eine Tour ist die effektivste Möglichkeit, um zu beschreiben, was Ihr bot tun kann.</span><span class="sxs-lookup"><span data-stu-id="d43d6-138">A tour is the most effective way to describe what your bot can do.</span></span> <span data-ttu-id="d43d6-139">Wenn zutreffend, eignen Sie sich auch hervorragend für die Beschreibung der anderen Features Ihrer APP (beispielsweise Screenshots Ihrer Messaging Erweiterung).</span><span class="sxs-lookup"><span data-stu-id="d43d6-139">If applicable, they’re also great for describing your app’s other features (for example, include screenshots of your messaging extension).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d43d6-140">Auf Touren sollte zugegriffen werden, ohne dass Sie sich anmelden müssen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-140">Tours should be accessible without having to sign in.</span></span>

#### <a name="one-on-one-chats"></a><span data-ttu-id="d43d6-141">Eins-zu-eins-Chats</span><span class="sxs-lookup"><span data-stu-id="d43d6-141">One-on-one chats</span></span>

<span data-ttu-id="d43d6-142">In einer persönlichen App kann ein Karussell einen effektiven Überblick über Ihren bot und andere Features Ihrer APP bieten.</span><span class="sxs-lookup"><span data-stu-id="d43d6-142">In a personal app, a carousel can provide an effective overview of your bot and any other features of your app.</span></span> <span data-ttu-id="d43d6-143">Einschließlich Schaltflächen die Benutzer können bot-Befehle versuchen, wird empfohlen (beispielsweise **Erstellen einer Aufgabe**).</span><span class="sxs-lookup"><span data-stu-id="d43d6-143">Including buttons the let users try bot commands is encouraged (for example, **Create a task**).</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Beispiel zeigt eine bot-Tour in einem Einzelchat." border="false":::

#### <a name="channels-and-group-chats"></a><span data-ttu-id="d43d6-145">Kanäle und Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="d43d6-145">Channels and group chats</span></span>

<span data-ttu-id="d43d6-146">In Kanälen und Gruppenchats sollte ein Rundgang in einem modalen (auch als [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) bezeichnet) geöffnet werden, damit keine laufenden Unterhaltungen unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-146">In channels and group chats, a tour should open in a modal (also known as a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) so it doesn’t interrupt ongoing conversations.</span></span> <span data-ttu-id="d43d6-147">Dadurch erhalten Sie auch die Möglichkeit, rollenbasierte Ansichten für Ihre Tour zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-147">This also gives you the option to implement role-based views for your tour.</span></span>

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Beispiel zeigt eine bot-Tour in einem Kanal." border="false":::

## <a name="chat-with-a-bot"></a><span data-ttu-id="d43d6-149">Chat mit einem bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-149">Chat with a bot</span></span>

<span data-ttu-id="d43d6-150">Bots können direkt in das Messaging Framework von Teams integriert werden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-150">Bots integrate directly into Team’s messaging framework.</span></span> <span data-ttu-id="d43d6-151">Benutzer können mit einem bot chatten, um Ihre Fragen zu beantworten, oder Befehle eingeben, damit der bot einen engen oder bestimmten Aufgabensatz ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="d43d6-151">Users can chat with a bot to get their questions answered or type commands to have the bot perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="d43d6-152">Bots können Benutzer proaktiv über Änderungen oder Aktualisierungen Ihrer APP per Chat informieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-152">Bots can proactively notify users about changes or updates to your app via chat.</span></span>

### <a name="chat-with-a-bot-in-different-contexts"></a><span data-ttu-id="d43d6-153">Chatten mit einem bot in unterschiedlichen Kontexten</span><span class="sxs-lookup"><span data-stu-id="d43d6-153">Chat with a bot in different contexts</span></span>

<span data-ttu-id="d43d6-154">Sie können Bots in den folgenden Kontexten verwenden:</span><span class="sxs-lookup"><span data-stu-id="d43d6-154">You can use bots in the following contexts:</span></span>

* <span data-ttu-id="d43d6-155">**Persönliche apps**: in einer persönlichen App verfügt ein bot über eine dedizierte Chat-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="d43d6-155">**Personal apps**: In a personal app, a bot has a dedicated chat tab.</span></span>
* <span data-ttu-id="d43d6-156">**Eins-zu-eins-Chat**: ein Benutzer kann eine private Unterhaltung mit einem bot initiieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-156">**One-on-one chat**: A user can initiate a private conversation with a bot.</span></span> <span data-ttu-id="d43d6-157">Es ist die gleiche Erfahrung wie die Verwendung eines bot in einer persönlichen app.</span><span class="sxs-lookup"><span data-stu-id="d43d6-157">It's the same experience as using a bot in a personal app.</span></span>
* <span data-ttu-id="d43d6-158">**Gruppenchat**: Personen können mit einem bot in einem Gruppenchat interagieren, indem Sie den bot @mentioning.</span><span class="sxs-lookup"><span data-stu-id="d43d6-158">**Group chat**: People can interact with a bot in a group chat by @mentioning the bot.</span></span>
* <span data-ttu-id="d43d6-159">**Kanal**: Personen können mit einem bot in einem Kanal interagieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-159">**Channel**: People can interact with a bot in a channel.</span></span> <span data-ttu-id="d43d6-160">durch @mentioning des Namens des bot im Feld Verfassen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-160">by @mentioning the bot name in the compose box.</span></span> <span data-ttu-id="d43d6-161">Denken Sie daran, dass der bot in diesem Zusammenhang für das gesamte Team und nicht nur für den Kanal verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="d43d6-161">Remember, in this context, the bot is available to the entire team, not just the channel.</span></span>

### <a name="anatomy"></a><span data-ttu-id="d43d6-162">Anatomie</span><span class="sxs-lookup"><span data-stu-id="d43d6-162">Anatomy</span></span>

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines bot." border="false":::

|<span data-ttu-id="d43d6-164">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="d43d6-164">Counter</span></span>|<span data-ttu-id="d43d6-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d43d6-165">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="d43d6-166">1</span><span class="sxs-lookup"><span data-stu-id="d43d6-166">1</span></span>|<span data-ttu-id="d43d6-167">**App-Name und Symbol**</span><span class="sxs-lookup"><span data-stu-id="d43d6-167">**App name and icon**</span></span>|
|<span data-ttu-id="d43d6-168">2 </span><span class="sxs-lookup"><span data-stu-id="d43d6-168">2</span></span>|<span data-ttu-id="d43d6-169">**Registerkarte Chat**: öffnet den Raum für Gespräche mit Ihrem bot (gilt nur für persönliche Apps).</span><span class="sxs-lookup"><span data-stu-id="d43d6-169">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="d43d6-170">3 </span><span class="sxs-lookup"><span data-stu-id="d43d6-170">3</span></span>|<span data-ttu-id="d43d6-171">**Benutzerdefinierte Registerkarten**: öffnet andere Inhalte im Zusammenhang mit Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="d43d6-171">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="d43d6-172">4 </span><span class="sxs-lookup"><span data-stu-id="d43d6-172">4</span></span>|<span data-ttu-id="d43d6-173">Informationen **zur Registerkarte**: zeigt grundlegende Informationen zu Ihrer APP an.</span><span class="sxs-lookup"><span data-stu-id="d43d6-173">**About tab**: Displays basic information about your app.</span></span>|
|<span data-ttu-id="d43d6-174">5 </span><span class="sxs-lookup"><span data-stu-id="d43d6-174">5</span></span>|<span data-ttu-id="d43d6-175">**Chat Blase**: bot-Unterhaltungen verwenden das Teams-Messaging Framework.</span><span class="sxs-lookup"><span data-stu-id="d43d6-175">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="d43d6-176">6 </span><span class="sxs-lookup"><span data-stu-id="d43d6-176">6</span></span>|<span data-ttu-id="d43d6-177">**Adaptive Karte**: Wenn die Antworten Ihres bot Adaptive Karten enthalten, nimmt die Karte die gesamte Breite der Chat Blase an.</span><span class="sxs-lookup"><span data-stu-id="d43d6-177">**Adaptive Card**: If your bot’s responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|
|<span data-ttu-id="d43d6-178">7 </span><span class="sxs-lookup"><span data-stu-id="d43d6-178">7</span></span>|<span data-ttu-id="d43d6-179">**Befehlsmenü**: zeigt die Standardbefehle Ihres bot an (definiert von Ihnen).</span><span class="sxs-lookup"><span data-stu-id="d43d6-179">**Command menu**: Displays your bot's standard commands (defined by you).</span></span>

### <a name="command-menu"></a><span data-ttu-id="d43d6-180">Befehlsmenü</span><span class="sxs-lookup"><span data-stu-id="d43d6-180">Command menu</span></span>

<span data-ttu-id="d43d6-181">Das Befehlsmenü enthält eine Liste von Wörtern oder Ausdrücken, auf die ihr bot immer antworten soll.</span><span class="sxs-lookup"><span data-stu-id="d43d6-181">The command menu provides a list of words or phrases you want your bot to always respond to.</span></span> <span data-ttu-id="d43d6-182">Das Befehlsmenü wird über dem Feld Verfassen angezeigt, wenn jemand mit einem bot in Gespräch kommt.</span><span class="sxs-lookup"><span data-stu-id="d43d6-182">The command menu displays above the compose box when someone is conversing with a bot.</span></span> <span data-ttu-id="d43d6-183">Wenn ein Befehl ausgewählt wird, wird er in eine Nachricht eingefügt.</span><span class="sxs-lookup"><span data-stu-id="d43d6-183">When a command is selected, it gets inserted into a message.</span></span>

<span data-ttu-id="d43d6-184">Die Liste der Befehle sollte kurz sein.</span><span class="sxs-lookup"><span data-stu-id="d43d6-184">The list of commands should be brief.</span></span> <span data-ttu-id="d43d6-185">Das Menü ist nur dazu gedacht, die primären Funktionen Ihres bot hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="d43d6-185">The menu is only meant to highlight your bot’s primary features.</span></span> <span data-ttu-id="d43d6-186">Halten Sie die Befehle auch prägnant.</span><span class="sxs-lookup"><span data-stu-id="d43d6-186">Keep commands concise, too.</span></span> <span data-ttu-id="d43d6-187">Erstellen Sie beispielsweise einen Befehl namens " **Help** " anstelle von **können Sie mir bitte helfen**?</span><span class="sxs-lookup"><span data-stu-id="d43d6-187">For example, create a command called **Help** instead of **Can you please help me**?</span></span>
<span data-ttu-id="d43d6-188">Das Befehlsmenü muss unabhängig vom Status der Unterhaltung immer verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="d43d6-188">The command menu must always be available regardless of the state of the conversation.</span></span>

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Beispiel zeigt das Befehlsmenü eines bot." border="false":::

## <a name="understand-what-people-are-saying"></a><span data-ttu-id="d43d6-190">Verstehen, was die Leute sagen</span><span class="sxs-lookup"><span data-stu-id="d43d6-190">Understand what people are saying</span></span>

<span data-ttu-id="d43d6-191">Verwenden Sie einen Thesaurus, und rufen Sie Personen aus so vielen verschiedenen Hintergründen ab, die Sie bei der Generierung unterschiedlicher Interpretationen von Standardabfragen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-191">Use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of standard queries.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Illustration, die zeigt, wie ein bot möglicherweise &quot;Hello&quot; interpretiert." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Illustration, die zeigt, wie ein bot die &quot;Hilfe&quot; interpretieren kann." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Illustration, die zeigt, wie ein bot vielleicht &quot;Danke&quot; interpretiert." border="false":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a><span data-ttu-id="d43d6-195">Extrahieren von Absichtserklärungen und Daten aus Nachrichten</span><span class="sxs-lookup"><span data-stu-id="d43d6-195">Extract intent and data from messages</span></span>

<span data-ttu-id="d43d6-196">Entwerfen Sie Ihren bot, um Absichtserklärungen zu erkennen, wodurch erfasst wird, was jemand von einem bot als Reaktion auf eine Nachricht oder Abfrage wünscht.</span><span class="sxs-lookup"><span data-stu-id="d43d6-196">Design your bot to recognize intent, which captures what someone wants from a bot in response to a message or query.</span></span> <span data-ttu-id="d43d6-197">Intent klassifiziert eine Nachricht oder Abfrage als einzelne Aktion mit einem oder mehreren Datenobjekten, die von der Aktion betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="d43d6-197">Intent classifies a message or query as a single action with one or more data objects that are affected by the action.</span></span> 

<span data-ttu-id="d43d6-198">In den folgenden Beispielen werden die Benutzerabsicht und die Daten in Nachrichten, die an Bots gesendet werden, umrissen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-198">The following examples outline the user intent and data in messages sent to bots.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="Beispiel im Satz &quot;Buchen eines Flugs nach Seattle&quot; zeigt die Benutzerabsicht &quot;Flug buchen&quot; und die Daten sind &quot;Seattle&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="Beispiel im Satz &quot;Wenn der Speicher geöffnet wird&quot; ist die Benutzerabsicht &quot;When&quot; und die Daten sind &quot;Open&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Beispiel im Satz &quot;Planen einer Besprechung am 13.00 Uhr mit Bob in der Verteilung&quot; angezeigt wird, ist die Benutzerabsicht &quot;Besprechung planen&quot; und die Daten sind &quot;13.00&quot; und &quot;Bob in Distribution&quot;." border="false":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a><span data-ttu-id="d43d6-202">Analysieren und verbessern</span><span class="sxs-lookup"><span data-stu-id="d43d6-202">Analyze and improve</span></span>

<span data-ttu-id="d43d6-203">Erfahren Sie, was Benutzer sagen, wenn Sie mit Ihrem bot chatten.</span><span class="sxs-lookup"><span data-stu-id="d43d6-203">Learn what users say when chatting with your bot.</span></span> <span data-ttu-id="d43d6-204">Dies wird ein fortlaufender, iterativer Prozess, wenn Ihre Benutzerbasis an unterschiedlichen Standorten und Organisationen wächst.</span><span class="sxs-lookup"><span data-stu-id="d43d6-204">This will be an ongoing, iterative process as your user base grows in different locations and orgs.</span></span> <span data-ttu-id="d43d6-205">Sie können die Spracherkennung und die Absicht-Zuordnung Ihres bot mit Microsoft Language Understanding (Luis) optimieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-205">You can tune your bot's language recognition and intent mapping with Microsoft Language Understanding (LUIS).</span></span>

* <span data-ttu-id="d43d6-206">[Understanding Luis](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): erfahren Sie, wie Luis AI verwendet, um Ihre APP-Daten mit natürlichen Sprachkenntnissen (NLU) zu versorgen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-206">[Understanding LUIS](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): Find out how LUIS uses AI to provide natural language understanding (NLU) to your app data.</span></span>
* <span data-ttu-id="d43d6-207">[Integration mit Luis](https://www.luis.ai/): Fügen Sie Ihrem bot natürliche Sprachfunktionen hinzu, ohne dass ein komplexer Prozess zum Erstellen von maschinellen Lernmodellen vorliegt.</span><span class="sxs-lookup"><span data-stu-id="d43d6-207">[Integrating with LUIS](https://www.luis.ai/): Add natural language capabilities to your bot without the complex process of creating machine learning models.</span></span>

## <a name="use-cases"></a><span data-ttu-id="d43d6-208">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="d43d6-208">Use cases</span></span>

### <a name="simple-queries"></a><span data-ttu-id="d43d6-209">Einfache Abfragen</span><span class="sxs-lookup"><span data-stu-id="d43d6-209">Simple queries</span></span>

<span data-ttu-id="d43d6-210">Bots können eine exakte Übereinstimmung mit einer Abfrage oder einer Gruppe verwandter Übereinstimmungen zur Unterstützung der Begriffsklärung liefern.</span><span class="sxs-lookup"><span data-stu-id="d43d6-210">Bots can deliver an exact match to a query or a group of related matches to help with disambiguation.</span></span> <span data-ttu-id="d43d6-211">Gruppieren Sie bei Verwandten Übereinstimmungen den Inhalt mithilfe einer Listen Karte.</span><span class="sxs-lookup"><span data-stu-id="d43d6-211">For related matches, group the content using a list card.</span></span>

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrage Interaktion mit einem bot." border="false":::

### <a name="multi-turn-interactions"></a><span data-ttu-id="d43d6-213">Multi-Turn-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="d43d6-213">Multi-turn interactions</span></span>

<span data-ttu-id="d43d6-214">Während Ihr bot vollständige Anfragen und Fragen unterstützenkann, sollte er auch Multi-Turn-Interaktionen verarbeiten können.</span><span class="sxs-lookup"><span data-stu-id="d43d6-214">While your bot can support complete requests and questions, it should also be able to handle multi-turn interactions.</span></span> <span data-ttu-id="d43d6-215">Die Vorwegnahme möglicher nächster Schritte macht es für Personen viel einfacher, einen vollständigen Aufgabenfluss zu planen (statt zu erwarten, dass Sie eine umfassende Anforderung fertig stellen).</span><span class="sxs-lookup"><span data-stu-id="d43d6-215">Anticipating possible next steps makes it much easier for people to a complete task flow (rather than expecting them to craft a comprehensive request).</span></span>

<span data-ttu-id="d43d6-216">Im folgenden Beispiel reagiert der bot auf jede Nachricht mit Optionen für das, was als nächstes möglicherweise gewünscht wird.</span><span class="sxs-lookup"><span data-stu-id="d43d6-216">In the following example, the bot responds to each message with options for what might want to do next.</span></span>

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Beispiel zeigt eine Multi-Turn-Interaktion mit einem bot." border="false":::

### <a name="reach-out-to-users"></a><span data-ttu-id="d43d6-218">Erreichen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="d43d6-218">Reach out to users</span></span>

<span data-ttu-id="d43d6-219">Mit proaktivem Messaging kann Ihr bot wie ein Digest fungieren, der Benachrichtigungen für eine Person, einen Gruppenchat oder einen Kanal mit einer bestimmten Frequenz sendet.</span><span class="sxs-lookup"><span data-stu-id="d43d6-219">With proactive messaging, your bot can act like a digest that sends notifications relevant to an individual, group chat, or channel at a specific frequency.</span></span> <span data-ttu-id="d43d6-220">Ein Bot kann eine Nachricht senden, wenn sich etwas in einem Dokument geändert hat oder wenn ein Arbeitselement geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d43d6-220">A bot may send a message when something has changed in a document or a work item is closed.</span></span>

<span data-ttu-id="d43d6-221">Im folgenden Beispiel erhält ein Benutzer eine Popupbenachrichtigung, die von einem bot in einem anderen Kanal gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d43d6-221">In the following example, a user gets a toast notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Beispiel zeigt einen Toast eines bot-proaktiven Messaging eines Benutzers aus einem anderen Kanal." border="false":::

<span data-ttu-id="d43d6-223">Der Benutzer kann nun in diesem Kanal seine Nachricht vom bot lesen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-223">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Das Beispiel zeigt, wie der Benutzer die proaktive Nachricht des bot sucht." border="false":::

### <a name="use-tabs-with-bots"></a><span data-ttu-id="d43d6-225">Verwenden von Tabs mit Bots</span><span class="sxs-lookup"><span data-stu-id="d43d6-225">Use tabs with bots</span></span>

<span data-ttu-id="d43d6-226">Eine Registerkarte kann Ihren bot einfacher zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-226">A tab can make your bot easier to use.</span></span> <span data-ttu-id="d43d6-227">Wenn Ihr bot beispielsweise Arbeitsaufgaben erstellen kann, wäre es schön, alle diese Elemente an einer zentralen Stelle in einer Registerkarte anzuzeigen. Weitere Informationen finden Sie unter [Entwerfen von Registerkarten](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="d43d6-227">For example, if your bot can create work items, it would be nice to show all those items in a central location inside a tab. See more about [designing tabs](../../tabs/design/tabs.md).</span></span>

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte helfen kann, bot-Inhalte zu organisieren." border="false":::

## <a name="manage-a-bot"></a><span data-ttu-id="d43d6-229">Verwalten eines bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-229">Manage a bot</span></span>

<span data-ttu-id="d43d6-230">Benutzer sollten in der Lage sein, die Einstellungen eines bot zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d43d6-230">Users should be able to change a bot's settings.</span></span> <span data-ttu-id="d43d6-231">Sie können diese Funktionalität mit bot-Befehlen bereitstellen, es ist jedoch in der Regel effizienter, alle Einstellungen in einem [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) einzuschließen (wie im folgenden Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="d43d6-231">You can provide this functionality with bot commands, but it's usually more efficient to include all settings in a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (as shown in the following example).</span></span>

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Beispiel zeigt ein Aufgabenmodul zum Konfigurieren der Einstellungen eines bot." border="false":::

## <a name="best-practices"></a><span data-ttu-id="d43d6-233">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="d43d6-233">Best practices</span></span>

### <a name="content"></a><span data-ttu-id="d43d6-234">Inhalt</span><span class="sxs-lookup"><span data-stu-id="d43d6-234">Content</span></span>

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-establish-a-clear-persona"></a><span data-ttu-id="d43d6-236">Do: Erstellen einer eindeutigen Rolle</span><span class="sxs-lookup"><span data-stu-id="d43d6-236">Do: Establish a clear persona</span></span>

<span data-ttu-id="d43d6-237">Ist Ihr bot Ton freundlich und leicht, "nur die Fakten" oder Super schrullig?</span><span class="sxs-lookup"><span data-stu-id="d43d6-237">Is your bot's tone friendly and light, “just the facts”, or super quirky?</span></span> <span data-ttu-id="d43d6-238">Wie sollte Sie in unterschiedlichen Szenarien reagieren?</span><span class="sxs-lookup"><span data-stu-id="d43d6-238">How should it respond in different scenarios?</span></span> <span data-ttu-id="d43d6-239">Das Planen und Dokumentieren der Persona Ihres bot erleichtert das Schreiben von Antworten, die natürlich und zusammenhängend wirken.</span><span class="sxs-lookup"><span data-stu-id="d43d6-239">Planning and documenting your bot's persona makes it easier to write responses that seem natural and cohesive.</span></span>

<span data-ttu-id="d43d6-240">Weitere Informationen zum Schreiben von Bots finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span><span class="sxs-lookup"><span data-stu-id="d43d6-240">See more about writing for bots in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a><span data-ttu-id="d43d6-242">Do: deutlich vermitteln, was Ihr bot tun kann</span><span class="sxs-lookup"><span data-stu-id="d43d6-242">Do: Clearly convey what your bot can do</span></span>

<span data-ttu-id="d43d6-243">Begrüßungsnachrichten und-Touren helfen Benutzern zu verstehen, was Sie mit Ihrem bot tun können.</span><span class="sxs-lookup"><span data-stu-id="d43d6-243">Welcome messages and tours help people understand what they can do with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-obscure-your-bots-features"></a><span data-ttu-id="d43d6-245">Nicht: verdecken der Funktionen Ihres bot</span><span class="sxs-lookup"><span data-stu-id="d43d6-245">Don't: Obscure your bot's features</span></span>

<span data-ttu-id="d43d6-246">Erste Eindrücke sind wichtig.</span><span class="sxs-lookup"><span data-stu-id="d43d6-246">First impressions matter.</span></span> <span data-ttu-id="d43d6-247">Personen werden wahrscheinlich verwirrt oder misstrauisch, wenn Sie mit einer unscheinbaren Anmeldenachricht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-247">People will likely be confused or suspicious when presented with a nondescript sign-in message.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-recognize-non-questions"></a><span data-ttu-id="d43d6-249">Do: Erkennen von nicht-Fragen</span><span class="sxs-lookup"><span data-stu-id="d43d6-249">Do: Recognize non-questions</span></span>

<span data-ttu-id="d43d6-250">Ihr bot sollte in der Lage sein, auf Nachrichten wie "Hi", "Help" und "Thanks" zu Antworten und gleichzeitig häufige Rechtschreibfehler und Colloquialisms zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-250">Your bot should be able to respond to messages like "Hi", "Help", and "Thanks" while also accounting for common misspellings and colloquialisms.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a><span data-ttu-id="d43d6-252">Nicht: Gelegenheiten zur Freude verpassen</span><span class="sxs-lookup"><span data-stu-id="d43d6-252">Don't: Miss out on opportunities to delight</span></span>

<span data-ttu-id="d43d6-253">Einige Leute erwarten, dass Unterhaltungen natürlich wie bei einer realen Person fließen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-253">Some people expect conversations to flow naturally like they would with a real person.</span></span> <span data-ttu-id="d43d6-254">Versuchen Sie, ungeschickte Antworten auf einfache Nachrichten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d43d6-254">Try to avoid clumsy responses to simple messages.</span></span>

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a><span data-ttu-id="d43d6-255">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="d43d6-255">Troubleshooting</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-provide-help"></a><span data-ttu-id="d43d6-257">Do: Hilfe bereitstellen</span><span class="sxs-lookup"><span data-stu-id="d43d6-257">Do: Provide help</span></span>

<span data-ttu-id="d43d6-258">Wenn Ihr bot eine Anforderung nicht erfüllen kann, bieten Sie Möglichkeiten für einen Benutzer, sich über die Interaktion mit Ihrem bot zu informieren.</span><span class="sxs-lookup"><span data-stu-id="d43d6-258">If your bot can’t satisfy a request, provide ways for a user to educate themselves about interacting with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-leave-users-stranded"></a><span data-ttu-id="d43d6-260">Nicht: lassen Sie die Benutzer gestrandet</span><span class="sxs-lookup"><span data-stu-id="d43d6-260">Don't: Leave users stranded</span></span>

<span data-ttu-id="d43d6-261">Personen werden Ihren bot schnell verlassen, wenn Sie Probleme nicht beheben können.</span><span class="sxs-lookup"><span data-stu-id="d43d6-261">People will quickly abandon your bot if they can’t troubleshoot issues.</span></span>

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a><span data-ttu-id="d43d6-262">Komplexe Interaktionen</span><span class="sxs-lookup"><span data-stu-id="d43d6-262">Complex interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a><span data-ttu-id="d43d6-264">Do: Verwenden von Aufgaben Modulen oder Registerkarten</span><span class="sxs-lookup"><span data-stu-id="d43d6-264">Do: Use task modules or tabs</span></span>

<span data-ttu-id="d43d6-265">Wenn Ihr bot eine Antwort enthält, die ein paar weitere Schritte erfordert, können Sie einen Link zu einem Aufgabenmodul oder einer RegisterkarteErstellen, um den Vorgang oder den Ablauf abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-265">If your bot provides an answer that requires a few more steps, you can link to a task module or tab to complete the task or flow.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a><span data-ttu-id="d43d6-267">Nicht: machen Sie Multi-Turn-Interaktionen langweilig</span><span class="sxs-lookup"><span data-stu-id="d43d6-267">Don't: Make multi-turn interactions tedious</span></span>

<span data-ttu-id="d43d6-268">Eine umfassende Unterhaltung zum Ausführen einer einzelnen Aufgabe ist langsam und übermäßig Komplex.</span><span class="sxs-lookup"><span data-stu-id="d43d6-268">An extensive conversation to complete a single task is slow and overly complex.</span></span> <span data-ttu-id="d43d6-269">Außerdem muss der Entwicklerstatus Änderungen berücksichtigen (beispielsweise das Timeout bei der Unterhaltung oder das Senden einer "Cancel"-Nachricht).</span><span class="sxs-lookup"><span data-stu-id="d43d6-269">It also requires the developer to account for state changes (such as the conversation timing out or you sending a “Cancel” message).</span></span>

   :::column-end:::
:::row-end:::

### <a name="privacy"></a><span data-ttu-id="d43d6-270">Datenschutz</span><span class="sxs-lookup"><span data-stu-id="d43d6-270">Privacy</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a><span data-ttu-id="d43d6-272">Do: nur vertrauliche Informationen in einem persönlichen Kontext anzeigen</span><span class="sxs-lookup"><span data-stu-id="d43d6-272">Do: Only show sensitive info in a personal context</span></span>

<span data-ttu-id="d43d6-273">Wenn sich Ihr bot in einem Gruppenchat oder-Kanal befindet, empfehlen wir, Benutzer zu einem privaten Speicherort (wie einem Aufgabenmodul, einer Registerkarte oder einem Browser) zu leiten, um vertrauliche Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-273">If your bot is in a group chat or channel, we recommend directing users to a private location (such as a task module, tab, or browser) to view sensitive information.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a><span data-ttu-id="d43d6-275">Nicht: einige Inhalte werden nicht für alle sichtbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-275">Don't: Some content isn’t meant to be seen by everyone</span></span>

<span data-ttu-id="d43d6-276">Ihr bot sollte keine vertraulichen Informationen für eine Gruppe von Personen offen legen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-276">Your bot shouldn’t reveal sensitive information to a group of people.</span></span>

   :::column-end:::
:::row-end:::

## <a name="learn-more"></a><span data-ttu-id="d43d6-277">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="d43d6-277">Learn more</span></span>

<span data-ttu-id="d43d6-278">Diese anderen Richtlinien können bei Ihrem bot-Design hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="d43d6-278">These other guidelines may help with your bot design:</span></span>

* [<span data-ttu-id="d43d6-279">Entwerfen Ihrer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="d43d6-279">Designing your personal app</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="d43d6-280">Entwerfen adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="d43d6-280">Designing Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)
* [<span data-ttu-id="d43d6-281">Entwerfen von Aufgaben Modulen</span><span class="sxs-lookup"><span data-stu-id="d43d6-281">Designing task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="validate-your-design"></a><span data-ttu-id="d43d6-282">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="d43d6-282">Validate your design</span></span>

<span data-ttu-id="d43d6-283">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="d43d6-283">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d43d6-284">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="d43d6-284">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
