---
title: Entwerfen Ihres Bots
description: Erfahren Sie, wie Sie einen Teams-Bot entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 98e36bf55e61ef59261959021409d9e60d8542f5
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630082"
---
# <a name="designing-your-microsoft-teams-bot"></a><span data-ttu-id="30276-103">Entwerfen Ihres Microsoft Teams-Bots</span><span class="sxs-lookup"><span data-stu-id="30276-103">Designing your Microsoft Teams bot</span></span>

<span data-ttu-id="30276-104">Bots sind Unterhaltungs-Apps, die bestimmte Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="30276-104">Bots are conversational apps that perform a specific set of tasks.</span></span> <span data-ttu-id="30276-105">Basierend auf dem <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a> kommunizieren Bots mit Benutzern, beantworten ihre Fragen und benachrichtigen sie proaktiv über Änderungen und andere Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="30276-105">Based on the <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a>, bots communicate with users, respond to their questions, and proactively notify them about changes and other events.</span></span> <span data-ttu-id="30276-106">Sie sind eine tolle Möglichkeit zur Kontaktaufnahme.</span><span class="sxs-lookup"><span data-stu-id="30276-106">They're a great way to reach out.</span></span>

<span data-ttu-id="30276-107">Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Bots in Teams hinzufügen, verwenden und verwalten können, um Ihr App-Design zu steuern.</span><span class="sxs-lookup"><span data-stu-id="30276-107">To guide your app design, the following information describes and illustrates how people can add, use, and manage bots in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="30276-108">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="30276-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="30276-109">Umfassendere Richtlinien für das Bot-Design, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.</span><span class="sxs-lookup"><span data-stu-id="30276-109">You can find more comprehensive bot design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="30276-110">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="30276-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a><span data-ttu-id="30276-111">Einen Bot hinzufügen</span><span class="sxs-lookup"><span data-stu-id="30276-111">Add a bot</span></span>

<span data-ttu-id="30276-112">Bots sind in Chats, Kanälen und persönlichen Apps verfügbar.</span><span class="sxs-lookup"><span data-stu-id="30276-112">Bots are available in chats, channels, and personal apps.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-113">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-113">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="30276-114">Benutzer können einen Bot auf folgende Weise hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="30276-114">Users can add a bot one of the following ways:</span></span>

* <span data-ttu-id="30276-115">Aus dem Teams speichern.</span><span class="sxs-lookup"><span data-stu-id="30276-115">From the Teams store.</span></span>
* <span data-ttu-id="30276-116">Verwenden des App-Flyouts durch Auswahl des Symbols **Mehr** auf der linken Seite von Teams.</span><span class="sxs-lookup"><span data-stu-id="30276-116">Using the app flyout by selecting the **More** icon on the left side of Teams.</span></span>
* <span data-ttu-id="30276-117">Mit einer @Erwähnung im neuen Chat- oder Erstellungsfeld (das folgende Beispiel zeigt, wie Sie dies in einem Gruppenchat tun können).</span><span class="sxs-lookup"><span data-stu-id="30276-117">With an @mention in the new chat or compose box (the following example shows how you can do this in a group chat).</span></span>

    :::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Beispiel: So fügen Sie einen Bot in einem Gruppenchat mit einer @Erwähnung hinzu." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-119">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-119">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="30276-120">Benutzer können auf Bots zugreifen, die auf dem Desktop mit einer @mention.</span><span class="sxs-lookup"><span data-stu-id="30276-120">Users can access bots that were added on desktop with an @mention.</span></span>

:::image type="content" source="../../assets/images/bots/mobile-access-bot-chat-at-mention.png" alt-text="Im Beispiel wird gezeigt, wie Sie in einem Gruppenchat mithilfe einer App auf einen mobilen Bot @mention." border="false":::

---

## <a name="introduce-a-bot"></a><span data-ttu-id="30276-122">Einführen eines Bots</span><span class="sxs-lookup"><span data-stu-id="30276-122">Introduce a bot</span></span>

<span data-ttu-id="30276-123">Es ist wichtig, dass sich Ihr Bot vorstellt und beschreibt, was er kann.</span><span class="sxs-lookup"><span data-stu-id="30276-123">It’s critical that your bot introduces itself and describes what it can do.</span></span> <span data-ttu-id="30276-124">Dieser anfängliche Austausch hilft Personen zu verstehen, was sie mit dem Bot tun sollen, seine Beschränkungen herauszufinden und sich vor allem mit ihm vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="30276-124">This initial exchange helps people understand what to do with the bot, find out its limitations and, most importantly, get comfortable interacting with it.</span></span>

### <a name="welcome-message-in-a-one-on-one-chat"></a><span data-ttu-id="30276-125">Willkommensnachricht in einem 1:1-Chat</span><span class="sxs-lookup"><span data-stu-id="30276-125">Welcome message in a one-on-one chat</span></span>

<span data-ttu-id="30276-126">In persönlichen Kontexten geben Willkommensnachrichten den Ton Ihres Bots an.</span><span class="sxs-lookup"><span data-stu-id="30276-126">In personal contexts, welcome messages set your bot's tone.</span></span> <span data-ttu-id="30276-127">Die Nachricht enthält eine Begrüßung, was der Bot tun kann, und einige Vorschläge für die Interaktion.</span><span class="sxs-lookup"><span data-stu-id="30276-127">The message includes a greeting, what the bot can do, and some suggestions for how to interact.</span></span> <span data-ttu-id="30276-128">Beispiel: "Versuchen Sie, mich nach ..." zu fragen.</span><span class="sxs-lookup"><span data-stu-id="30276-128">For example, “Try asking me about …”.</span></span> <span data-ttu-id="30276-129">Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="30276-129">If possible, these suggestions should return stored responses without having to sign in.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-130">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-130">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einer persönlichen App." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-132">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-132">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-personal-welcome.png" alt-text="Beispiel zeigt eine Boteinführung in einer persönlichen App auf Mobilgeräten." border="false":::

---

### <a name="welcome-message-in-channels-and-group-chats"></a><span data-ttu-id="30276-134">Willkommensnachricht in Kanälen und Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="30276-134">Welcome message in channels and group chats</span></span>

<span data-ttu-id="30276-135">Die Einführung Ihres Bots sollte sich in Kanälen und Gruppenchats im Vergleich zu einem persönlichen Raum (z. B. einer persönlichen App) geringfügig unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="30276-135">Your bot's introduction should be slightly different in channels and group chats compared to a personal space (like a personal app).</span></span> <span data-ttu-id="30276-136">Wenn Sie in der realen Welt einen Raum voller Personen betreten haben, würden Sie sich vorstellen, anstatt alle zu begrüßen, die bereits dort sind.</span><span class="sxs-lookup"><span data-stu-id="30276-136">In real life, if you entered a room full of people; you’d introduce yourself instead of welcoming everyone who’s already there.</span></span> <span data-ttu-id="30276-137">Lassen Sie dieses Denken in Ihr Bot-Design einfließen.</span><span class="sxs-lookup"><span data-stu-id="30276-137">Carry that thinking into your bot design.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-138">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-138">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einem kollaborativen Kontext." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-140">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-140">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-group-welcome.png" alt-text="Beispiel zeigt eine Boteinführung in einem kontextbezogenen Kontext auf Mobilgeräten." border="false":::

---

### <a name="bot-authentication-with-single-sign-on"></a><span data-ttu-id="30276-142">Bot-Authentifizierung mit Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="30276-142">Bot authentication with single sign-on</span></span>

<span data-ttu-id="30276-143">Wenn eine Person einem Bot eine Nachricht sendet, muss möglicherweise eine Anmeldung erforderlich sein, um alle Funktionen zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="30276-143">When a person messages a bot, sign in may be required use all its features.</span></span> <span data-ttu-id="30276-144">Sie können den Authentifizierungsprozess mithilfe von Single Sign-On (SSO) vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="30276-144">You can simplify the authentication process using single sign-on (SSO).</span></span>

<span data-ttu-id="30276-145">Vergessen Sie nicht: Im Bot-Befehlsmenü (**Was kann ich tun?**) müssen Sie auch einen Befehl zum Abmelden eingeben.</span><span class="sxs-lookup"><span data-stu-id="30276-145">Don’t forget: In the bot command menu (**What can I do?**), you must also provide a command to sign out.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-146">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-146">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Beispiel zeigt einen Bot mit einer Anmeldeschaltfläche." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-148">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-148">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-sso-example.png" alt-text="Beispiel zeigt einen Bot mit einer Anmeldeschaltfläche auf Mobilgeräten." border="false":::

---

### <a name="tours"></a><span data-ttu-id="30276-150">Touren</span><span class="sxs-lookup"><span data-stu-id="30276-150">Tours</span></span>

<span data-ttu-id="30276-151">Sie können eine Tour mit Begrüßungsnachrichten einfügen und wenn der Bot auf so etwas wie einen Hilfebefehl reagiert.</span><span class="sxs-lookup"><span data-stu-id="30276-151">You can include a tour with welcome messages and if the bot responds to something like a “help” command.</span></span> <span data-ttu-id="30276-152">Eine Tour ist der effektivste Weg, um zu beschreiben, was Ihr Bot tun kann.</span><span class="sxs-lookup"><span data-stu-id="30276-152">A tour is the most effective way to describe what your bot can do.</span></span> <span data-ttu-id="30276-153">Falls zutreffend, n nen sie auch für die Beschreibung der anderen Features Ihrer App geeignet sein.</span><span class="sxs-lookup"><span data-stu-id="30276-153">If applicable, they’re also great for describing your app’s other features.</span></span> <span data-ttu-id="30276-154">Fügen Sie z. B. Screenshots ihrer Messagingerweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="30276-154">For example, include screenshots of your messaging extension.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30276-155">Touren sollten zugänglich sein, ohne sich anmelden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="30276-155">Tours should be accessible without having to sign in.</span></span>

#### <a name="one-on-one-chats"></a><span data-ttu-id="30276-156">1:1-Chats</span><span class="sxs-lookup"><span data-stu-id="30276-156">One-on-one chats</span></span>

<span data-ttu-id="30276-157">In einer persönlichen App bietet ein Karussell einen effektiven Überblick über Ihren Bot und alle anderen Features Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="30276-157">In a personal app, a carousel can provide an effective overview of your bot and any other features of your app.</span></span> <span data-ttu-id="30276-158">Das Verwenden von Schaltflächen, mit denen Benutzer Botbefehle ausprobieren können, wird empfohlen.</span><span class="sxs-lookup"><span data-stu-id="30276-158">Including buttons the let users try bot commands is encouraged.</span></span> <span data-ttu-id="30276-159">Beispiel: **Erstellen einer Aufgabe**.</span><span class="sxs-lookup"><span data-stu-id="30276-159">For example, **Create a task**.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-160">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-160">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Beispiel zeigt eine Bot-Tour in einem 1:1-Chat." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-162">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-162">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-personal.png" alt-text="Beispiel zeigt eine Bot-Tour in einem 1:1-Chat auf Mobilgeräten." border="false":::

---

#### <a name="channels-and-group-chats"></a><span data-ttu-id="30276-164">Kanäle und Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="30276-164">Channels and group chats</span></span>

<span data-ttu-id="30276-165">In Kanälen und Gruppenchats sollte eine Tour in einem Modal (auch als [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) bezeichnet) geöffnet werden, damit laufende Gespräche nicht unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="30276-165">In channels and group chats, a tour should open in a modal (also known as a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) so it doesn’t interrupt ongoing conversations.</span></span> <span data-ttu-id="30276-166">Dies gibt Ihnen auch die Möglichkeit, rollenbasierte Ansichten für Ihre Tour zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="30276-166">This also gives you the option to implement role-based views for your tour.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-167">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-167">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Beispiel zeigt eine Bot-Tour in einem Kanal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-169">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-169">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-channel.png" alt-text="Beispiel zeigt eine Bot-Tour in einem Kanal auf Mobilgeräten." border="false":::

---

## <a name="chat-with-a-bot"></a><span data-ttu-id="30276-171">Chatten mit einem Bot</span><span class="sxs-lookup"><span data-stu-id="30276-171">Chat with a bot</span></span>

<span data-ttu-id="30276-172">Bots werden direkt in das Messaging-Framework des Teams integriert.</span><span class="sxs-lookup"><span data-stu-id="30276-172">Bots integrate directly into Team’s messaging framework.</span></span> <span data-ttu-id="30276-173">Benutzer können mit einem Bot chatten, um ihre Fragen zu beantworten, oder Befehle eingeben, damit der Bot eine enge oder bestimmte Gruppe von Aufgaben ausführt.</span><span class="sxs-lookup"><span data-stu-id="30276-173">Users can chat with a bot to get their questions answered or type commands to have the bot perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="30276-174">Bots können Benutzer proaktiv per Chat über Änderungen oder Aktualisierungen Ihrer App informieren.</span><span class="sxs-lookup"><span data-stu-id="30276-174">Bots can proactively notify users about changes or updates to your app via chat.</span></span>

### <a name="chat-with-a-bot-in-different-contexts"></a><span data-ttu-id="30276-175">Chatten mit einem Bot in verschiedenen Kontexten</span><span class="sxs-lookup"><span data-stu-id="30276-175">Chat with a bot in different contexts</span></span>

<span data-ttu-id="30276-176">Sie können Bots in den folgenden Kontexten verwenden:</span><span class="sxs-lookup"><span data-stu-id="30276-176">You can use bots in the following contexts:</span></span>

* <span data-ttu-id="30276-177">**Persönliche Apps**: In einer persönlichen App verfügt ein Bot über eine eigene Chat-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="30276-177">**Personal apps**: In a personal app, a bot has a dedicated chat tab.</span></span>
* <span data-ttu-id="30276-178">**1:1-Chat**: Ein Benutzer kann eine private Unterhaltung mit einem Bot initiieren.</span><span class="sxs-lookup"><span data-stu-id="30276-178">**One-on-one chat**: A user can initiate a private conversation with a bot.</span></span> <span data-ttu-id="30276-179">Es ist die gleiche Erfahrung wie bei der Verwendung eines Bots in einer persönlichen App.</span><span class="sxs-lookup"><span data-stu-id="30276-179">It's the same experience as using a bot in a personal app.</span></span>
* <span data-ttu-id="30276-180">**Gruppenchat**: Benutzer können mit einem Bot in einem Gruppenchat interagieren, indem sie den Bot @erwähnen.</span><span class="sxs-lookup"><span data-stu-id="30276-180">**Group chat**: People can interact with a bot in a group chat by @mentioning the bot.</span></span>
* <span data-ttu-id="30276-181">**Kanal**: Benutzer können mit einem Bot in einem Kanal interagieren.</span><span class="sxs-lookup"><span data-stu-id="30276-181">**Channel**: People can interact with a bot in a channel.</span></span> <span data-ttu-id="30276-182">indem sie den Bot-Namen im Erstellungsfeld @erwähnen.</span><span class="sxs-lookup"><span data-stu-id="30276-182">by @mentioning the bot name in the compose box.</span></span> <span data-ttu-id="30276-183">Denken Sie daran, dass der Bot in diesem Zusammenhang dem gesamten Team zur Verfügung steht, nicht nur dem Kanal.</span><span class="sxs-lookup"><span data-stu-id="30276-183">Remember, in this context, the bot is available to the entire team, not just the channel.</span></span>

### <a name="anatomy"></a><span data-ttu-id="30276-184">Anatomie</span><span class="sxs-lookup"><span data-stu-id="30276-184">Anatomy</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-185">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-185">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Bots." border="false":::

|<span data-ttu-id="30276-187">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="30276-187">Counter</span></span>|<span data-ttu-id="30276-188">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="30276-188">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="30276-189">1</span><span class="sxs-lookup"><span data-stu-id="30276-189">1</span></span>|<span data-ttu-id="30276-190">**App-Name und -Symbol**</span><span class="sxs-lookup"><span data-stu-id="30276-190">**App name and icon**</span></span>|
|<span data-ttu-id="30276-191">2</span><span class="sxs-lookup"><span data-stu-id="30276-191">2</span></span>|<span data-ttu-id="30276-192">**Chat-Registerkarte**: Öffnet den Bereich für Gespräche mit Ihrem Bot (gilt nur für persönliche Apps).</span><span class="sxs-lookup"><span data-stu-id="30276-192">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="30276-193">3</span><span class="sxs-lookup"><span data-stu-id="30276-193">3</span></span>|<span data-ttu-id="30276-194">**Benutzerdefinierte Registerkarten**: Öffnet weitere Inhalte zu Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="30276-194">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="30276-195">4 </span><span class="sxs-lookup"><span data-stu-id="30276-195">4</span></span>|<span data-ttu-id="30276-196">**Info-Registerkarte**: Zeigt grundlegende Informationen zu Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="30276-196">**About tab**: Displays basic information about your app.</span></span>|
|<span data-ttu-id="30276-197">5 </span><span class="sxs-lookup"><span data-stu-id="30276-197">5</span></span>|<span data-ttu-id="30276-198">**Chat-Blase**: Bot-Unterhaltungen verwenden das Team-Messaging-Framework.</span><span class="sxs-lookup"><span data-stu-id="30276-198">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="30276-199">6 </span><span class="sxs-lookup"><span data-stu-id="30276-199">6</span></span>|<span data-ttu-id="30276-200">**Adaptive Karte:** Wenn die Antworten Ihres Bots adaptive Karten enthalten, übernimmt die Karte die volle Breite der Chatblase.</span><span class="sxs-lookup"><span data-stu-id="30276-200">**Adaptive Card**: If your bot's responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|
|<span data-ttu-id="30276-201">7 </span><span class="sxs-lookup"><span data-stu-id="30276-201">7</span></span>|<span data-ttu-id="30276-202">**Befehlsmenü**: Zeigt die von Ihnen definierten Standardbefehle Ihres Bots an.</span><span class="sxs-lookup"><span data-stu-id="30276-202">**Command menu**: Displays your bot's standard commands (defined by you).</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="30276-203">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-203">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines mobilen Bots." border="false":::

|<span data-ttu-id="30276-205">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="30276-205">Counter</span></span>|<span data-ttu-id="30276-206">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="30276-206">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="30276-207">1</span><span class="sxs-lookup"><span data-stu-id="30276-207">1</span></span>|<span data-ttu-id="30276-208">**App-Name und -Symbol**</span><span class="sxs-lookup"><span data-stu-id="30276-208">**App name and icon**</span></span>|
|<span data-ttu-id="30276-209">2</span><span class="sxs-lookup"><span data-stu-id="30276-209">2</span></span>|<span data-ttu-id="30276-210">**Chat-Registerkarte**: Öffnet den Bereich für Gespräche mit Ihrem Bot (gilt nur für persönliche Apps).</span><span class="sxs-lookup"><span data-stu-id="30276-210">**Chat tab**: Opens the space to talk with your bot (applicable only to personal apps).</span></span>|
|<span data-ttu-id="30276-211">3</span><span class="sxs-lookup"><span data-stu-id="30276-211">3</span></span>|<span data-ttu-id="30276-212">**Benutzerdefinierte Registerkarten**: Öffnet weitere Inhalte zu Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="30276-212">**Custom tabs**: Opens other content related to your app.</span></span>|
|<span data-ttu-id="30276-213">4 </span><span class="sxs-lookup"><span data-stu-id="30276-213">4</span></span>|<span data-ttu-id="30276-214">**Chat-Blase**: Bot-Unterhaltungen verwenden das Team-Messaging-Framework.</span><span class="sxs-lookup"><span data-stu-id="30276-214">**Chat bubble**: Bot conversations use the Teams messaging framework.</span></span>|
|<span data-ttu-id="30276-215">5 </span><span class="sxs-lookup"><span data-stu-id="30276-215">5</span></span>|<span data-ttu-id="30276-216">**Adaptive Karte:** Wenn die Antworten Ihres Bots adaptive Karten enthalten, übernimmt die Karte die volle Breite der Chatblase.</span><span class="sxs-lookup"><span data-stu-id="30276-216">**Adaptive Card**: If your bot's responses include Adaptive Cards, the card takes up the full width of the chat bubble.</span></span>|

---

### <a name="command-menu"></a><span data-ttu-id="30276-217">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="30276-217">Command menu</span></span>

<span data-ttu-id="30276-218">Das Befehlsmenü enthält eine Liste von Wörtern oder Begriffen, auf die Ihr Bot immer reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="30276-218">The command menu provides a list of words or phrases you want your bot to always respond to.</span></span> <span data-ttu-id="30276-219">Das Befehlsmenü wird über dem Verfassungsfeld angezeigt, wenn sich jemand mit einem Bot unterhält.</span><span class="sxs-lookup"><span data-stu-id="30276-219">The command menu displays above the compose box when someone is conversing with a bot.</span></span> <span data-ttu-id="30276-220">Wenn ein Befehl ausgewählt ist, wird er in eine Nachricht eingefügt.</span><span class="sxs-lookup"><span data-stu-id="30276-220">When a command is selected, it gets inserted into a message.</span></span>

<span data-ttu-id="30276-221">Die Liste der Befehle sollte kurz sein.</span><span class="sxs-lookup"><span data-stu-id="30276-221">The list of commands should be brief.</span></span> <span data-ttu-id="30276-222">Das Menü soll nur die wichtigsten Features Ihres Bots hervorheben.</span><span class="sxs-lookup"><span data-stu-id="30276-222">The menu is only meant to highlight your bot’s primary features.</span></span> <span data-ttu-id="30276-223">Halten Sie auch Befehle präzise.</span><span class="sxs-lookup"><span data-stu-id="30276-223">Keep commands concise, too.</span></span> <span data-ttu-id="30276-224">Erstellen Sie beispielsweise einen Befehl namens **Hilfe** anstelle von **Können Sie mir bitte helfen?**.</span><span class="sxs-lookup"><span data-stu-id="30276-224">For example, create a command called **Help** instead of **Can you please help me**?</span></span>
<span data-ttu-id="30276-225">Das Befehlsmenü muss unabhängig vom Unterhaltungsstatus immer verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="30276-225">The command menu must always be available regardless of the state of the conversation.</span></span>

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Beispiel zeigt das Befehlsmenü eines Bots." border="false":::

## <a name="understand-what-people-are-saying"></a><span data-ttu-id="30276-227">Verstehen, was Personen sagen</span><span class="sxs-lookup"><span data-stu-id="30276-227">Understand what people are saying</span></span>

<span data-ttu-id="30276-228">Verwenden Sie einen Thesaurus und arbeiten Sie mit Personen mit möglichst vielen unterschiedlichen Hintergründen, um unterschiedliche Interpretationen von Standardabfragen zu generieren.</span><span class="sxs-lookup"><span data-stu-id="30276-228">Use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of standard queries.</span></span>

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

### <a name="extract-intent-and-data-from-messages"></a><span data-ttu-id="30276-232">Extrahieren von Absichten und Daten aus Nachrichten</span><span class="sxs-lookup"><span data-stu-id="30276-232">Extract intent and data from messages</span></span>

<span data-ttu-id="30276-233">Entwerfen Sie Ihren Bot so, dass er Absichten erkennt, die erfassen, was jemand von einem Bot als Antwort auf eine Nachricht oder eine Anfrage erwartet.</span><span class="sxs-lookup"><span data-stu-id="30276-233">Design your bot to recognize intent, which captures what someone wants from a bot in response to a message or query.</span></span> <span data-ttu-id="30276-234">Intent klassifiziert eine Nachricht oder Abfrage als eine einzelne Aktion mit einem oder mehreren Datenobjekten, die von der Aktion betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="30276-234">Intent classifies a message or query as a single action with one or more data objects that are affected by the action.</span></span> 

<span data-ttu-id="30276-235">In den folgenden Beispielen werden die Benutzerabsichten und Daten in Nachrichten, die an Bots gesendet werden, erläutert:</span><span class="sxs-lookup"><span data-stu-id="30276-235">The following examples outline the user intent and data in messages sent to bots:</span></span>

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

### <a name="analyze-and-improve"></a><span data-ttu-id="30276-239">Analysieren und Verbessern</span><span class="sxs-lookup"><span data-stu-id="30276-239">Analyze and improve</span></span>

<span data-ttu-id="30276-240">Erfahren Sie, was Benutzer sagen, wenn Sie mit Ihrem Bot chatten.</span><span class="sxs-lookup"><span data-stu-id="30276-240">Learn what users say when chatting with your bot.</span></span> <span data-ttu-id="30276-241">Dies ist ein fortlaufender, iterativer Prozess, da Ihre Benutzerbasis an verschiedenen Standorten und in verschiedenen Organisationen wächst.</span><span class="sxs-lookup"><span data-stu-id="30276-241">This will be an ongoing, iterative process as your user base grows in different locations and orgs.</span></span> <span data-ttu-id="30276-242">Sie können die Spracherkennung und Absichtszuordnung Ihres Bots mit Microsoft Language Understanding (LUIS) optimieren.</span><span class="sxs-lookup"><span data-stu-id="30276-242">You can tune your bot's language recognition and intent mapping with Microsoft Language Understanding (LUIS).</span></span>

* <span data-ttu-id="30276-243">[Grundlegendes zu LUIS](/azure/cognitive-services/luis/artificial-intelligence): Erfahren Sie, wie LUIS AI verwendet, um Ihren App-Daten ein Verständnis von natürlicher Sprache (NLU) zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="30276-243">[Understanding LUIS](/azure/cognitive-services/luis/artificial-intelligence): Find out how LUIS uses AI to provide natural language understanding (NLU) to your app data.</span></span>
* <span data-ttu-id="30276-244">[Integration in LUIS](https://www.luis.ai/): Fügen Sie Ihrem Bot Funktionen in natürlicher Sprache hinzu, ohne den komplexen Prozess der Erstellung von Modellen für maschinelles Lernen.</span><span class="sxs-lookup"><span data-stu-id="30276-244">[Integrating with LUIS](https://www.luis.ai/): Add natural language capabilities to your bot without the complex process of creating machine learning models.</span></span>

## <a name="use-cases"></a><span data-ttu-id="30276-245">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="30276-245">Use cases</span></span>

### <a name="simple-queries"></a><span data-ttu-id="30276-246">Einfache Abfragen</span><span class="sxs-lookup"><span data-stu-id="30276-246">Simple queries</span></span>

<span data-ttu-id="30276-247">Bots bieten eine genaue Übereinstimmung mit einer Abfrage oder einer Gruppe verwandter Übereinstimmungen, um die Begriffsklärung zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="30276-247">Bots can deliver an exact match to a query or a group of related matches to help with disambiguation.</span></span> <span data-ttu-id="30276-248">Gruppieren Sie den Inhalt für verwandte Übereinstimmungen mithilfe einer Listenkarte.</span><span class="sxs-lookup"><span data-stu-id="30276-248">For related matches, group the content using a list card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-249">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-249">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrageinteraktion mit einem Bot." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-251">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-251">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrageinteraktion mit einem Bot auf Mobilgeräten." border="false":::

---

### <a name="multi-turn-interactions"></a><span data-ttu-id="30276-253">Mehrfach-Interaktionen</span><span class="sxs-lookup"><span data-stu-id="30276-253">Multi-turn interactions</span></span>

<span data-ttu-id="30276-254">Während Ihr Bot vollständige Anfragen und Fragen unterstützen kann, sollte er auch in der Lage sein, Interaktionen mit mehreren Runden zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="30276-254">While your bot can support complete requests and questions, it should also be able to handle multi-turn interactions.</span></span> <span data-ttu-id="30276-255">Das Vorhersehen möglicher nächster Schritte erleichtert es den Mitarbeitern erheblich, einen vollständigen Aufgabenablauf durchzuführen (anstatt von ihnen zu erwarten, dass sie eine umfassende Anfrage erstellen).</span><span class="sxs-lookup"><span data-stu-id="30276-255">Anticipating possible next steps makes it much easier for people to a complete task flow (rather than expecting them to craft a comprehensive request).</span></span>

<span data-ttu-id="30276-256">In den folgenden Beispielen antwortet der Bot auf jede Nachricht mit Optionen für die nächsten Schritte.</span><span class="sxs-lookup"><span data-stu-id="30276-256">In the following examples, the bot responds to each message with options for what might want to do next.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-257">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-257">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Beispiel zeigt eine Mehrfach-Interaktion mit einem Bot." border="false":::


# <a name="mobile"></a>[<span data-ttu-id="30276-259">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-259">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-multi-turn.png" alt-text="Beispiel zeigt eine Multi-Turn-Interaktion mit einem Bot auf Mobilgeräten." border="false":::


---

### <a name="reach-out-to-users"></a><span data-ttu-id="30276-261">Benutzer erreichen</span><span class="sxs-lookup"><span data-stu-id="30276-261">Reach out to users</span></span>

<span data-ttu-id="30276-262">Mit proaktiven Nachrichten kann sich Ihr Bot wie ein Digest verhalten, der mit einer bestimmten Häufigkeit Benachrichtigungen sendet, die für eine Person, einen Gruppenchat oder einen Kanal relevant sind.</span><span class="sxs-lookup"><span data-stu-id="30276-262">With proactive messaging, your bot can act like a digest that sends notifications relevant to an individual, group chat, or channel at a specific frequency.</span></span> <span data-ttu-id="30276-263">Ein Bot kann eine Nachricht senden, wenn sich etwas in einem Dokument geändert hat oder ein Arbeitselement geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="30276-263">A bot may send a message when something has changed in a document or a work item is closed.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-264">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-264">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="30276-265">Im folgenden Beispiel ruft der Benutzer eine Popupbenachrichtigung ab, dass ein Bot sie in einem anderen Kanal benachrichtigt hat.</span><span class="sxs-lookup"><span data-stu-id="30276-265">In the following example, the user gets a toast notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Das Beispiel zeigt ein Popup eines Bots, der einen Benutzer proaktiv von einem anderen Kanal aus benachrichtigt." border="false":::

<span data-ttu-id="30276-267">Nun kann der Benutzer in diesem Kanal seine Nachricht des Bots lesen.</span><span class="sxs-lookup"><span data-stu-id="30276-267">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Beispiel: Benutzer betrachtet die proaktive Nachricht des Bots." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-269">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-269">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="30276-270">Im folgenden Beispiel ruft der Benutzer eine Benachrichtigung ab, dass ein Bot sie in einem anderen Kanal benachrichtigt hat.</span><span class="sxs-lookup"><span data-stu-id="30276-270">In the following example, the user gets a notification that a bot messaged them in another channel.</span></span>

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message-toast.png" alt-text="Beispiel zeigt ein Popup eines Bots, das einen Benutzer proaktiv von einem anderen Kanal auf Mobilgeräten mit Nachrichten ansastet." border="false":::

<span data-ttu-id="30276-272">Nun kann der Benutzer in diesem Kanal seine Nachricht des Bots lesen.</span><span class="sxs-lookup"><span data-stu-id="30276-272">Now in that channel, the user can read their message from the bot.</span></span>

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message.png" alt-text="Beispiel zeigt den Benutzer, der die proaktive Nachricht des Bots auf Mobilgeräten betrachtet." border="false":::

---

### <a name="use-tabs-with-bots"></a><span data-ttu-id="30276-274">Verwenden von Registerkarten mit Bots</span><span class="sxs-lookup"><span data-stu-id="30276-274">Use tabs with bots</span></span>

<span data-ttu-id="30276-275">In persönlichen Apps kann eine Registerkarte ergänzen, was Ihr Bot tun kann.</span><span class="sxs-lookup"><span data-stu-id="30276-275">In personal apps, a tab can complement what your bot can do.</span></span> <span data-ttu-id="30276-276">Wenn Ihr Bot beispielsweise Arbeitselemente erstellen kann, ist es hilfreich, alle diese Elemente an einer zentralen Stelle in einer Registerkarte anzuzeigen. Weitere Informationen zum [Entwerfen von Registerkarten](../../tabs/design/tabs.md).</span><span class="sxs-lookup"><span data-stu-id="30276-276">For example, if your bot can create work items, it would be nice to show all those items in a central location inside a tab. See more about [designing tabs](../../tabs/design/tabs.md).</span></span>

# <a name="desktop"></a>[<span data-ttu-id="30276-277">Desktop</span><span class="sxs-lookup"><span data-stu-id="30276-277">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte beim Organisieren von Bot-Inhalten helfen kann." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="30276-279">Mobil</span><span class="sxs-lookup"><span data-stu-id="30276-279">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/bots/mobile-bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte beim Organisieren von Botinhalten auf Mobilgeräten helfen kann." border="false":::

---

## <a name="manage-a-bot"></a><span data-ttu-id="30276-281">Verwalten eines Bots</span><span class="sxs-lookup"><span data-stu-id="30276-281">Manage a bot</span></span>

<span data-ttu-id="30276-282">Benutzer sollten in der Lage sein, die Einstellungen eines Bots zu ändern.</span><span class="sxs-lookup"><span data-stu-id="30276-282">Users should be able to change a bot's settings.</span></span> <span data-ttu-id="30276-283">Sie können diese Funktionalität mit Bot-Befehlen bereitstellen, aber es ist normalerweise effizienter, alle Einstellungen in ein [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) aufzunehmen (wie im folgenden Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="30276-283">You can provide this functionality with bot commands, but it's usually more efficient to include all settings in a [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) (as shown in the following example).</span></span>

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Beispiel zeigt ein Aufgabenmodul zum Konfigurieren der Einstellungen eines Bots." border="false":::

## <a name="best-practices"></a><span data-ttu-id="30276-285">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="30276-285">Best practices</span></span>

<span data-ttu-id="30276-286">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="30276-286">Use these recommendations to create a quality app experience.</span></span>

### <a name="content"></a><span data-ttu-id="30276-287">Inhalt</span><span class="sxs-lookup"><span data-stu-id="30276-287">Content</span></span>

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Beispiel für eine bewährte Methode eines Bots zum Einrichten einer eindeutigen Persona." border="false":::

#### <a name="do-establish-a-clear-persona"></a><span data-ttu-id="30276-289">Do: Erstellen einer eindeutigen Persona</span><span class="sxs-lookup"><span data-stu-id="30276-289">Do: Establish a clear persona</span></span>

<span data-ttu-id="30276-290">Ist der Ton Ihres Bots freundlich und leicht, "nur die Fakten" oder super ungewöhnlich?</span><span class="sxs-lookup"><span data-stu-id="30276-290">Is your bot's tone friendly and light, “just the facts”, or super quirky?</span></span> <span data-ttu-id="30276-291">Wie soll er in verschiedenen Szenarien reagieren?</span><span class="sxs-lookup"><span data-stu-id="30276-291">How should it respond in different scenarios?</span></span> <span data-ttu-id="30276-292">Das Planen und Dokumentieren der Persona Ihres Bots erleichtert das Schreiben von Antworten, die natürlich und zusammenhängend erscheinen.</span><span class="sxs-lookup"><span data-stu-id="30276-292">Planning and documenting your bot's persona makes it easier to write responses that seem natural and cohesive.</span></span>

<span data-ttu-id="30276-293">Weitere Informationen zum Schreiben für Bots finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span><span class="sxs-lookup"><span data-stu-id="30276-293">See more about writing for bots in the <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a></span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Beispiel, das zeigt, was Ihr Bot tun kann." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a><span data-ttu-id="30276-295">Do: Vermitteln Sie eindeutig, was Ihr Bot alles kann.</span><span class="sxs-lookup"><span data-stu-id="30276-295">Do: Clearly convey what your bot can do</span></span>

<span data-ttu-id="30276-296">Willkommensnachrichten und Touren helfen den Benutzern zu verstehen, was sie mit Ihrem Bot tun können.</span><span class="sxs-lookup"><span data-stu-id="30276-296">Welcome messages and tours help people understand what they can do with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Beispiel, das zeigt, dass die Funktionen Ihres Bots nicht verhüllt werden sollen." border="false":::

#### <a name="dont-obscure-your-bots-features"></a><span data-ttu-id="30276-298">Don‘t: Verschleiern der Features Ihres Bots</span><span class="sxs-lookup"><span data-stu-id="30276-298">Don't: Obscure your bot's features</span></span>

<span data-ttu-id="30276-299">Der erste Eindruck zählt.</span><span class="sxs-lookup"><span data-stu-id="30276-299">First impressions matter.</span></span> <span data-ttu-id="30276-300">Personen sind wahrscheinlich verwirrt oder misstrauisch, wenn ihnen eine unscheinbare Anmeldenachricht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="30276-300">People will likely be confused or suspicious when presented with a nondescript sign-in message.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Beispiel, in dem Ihr Bot keine Fragen erkennt." border="false":::

#### <a name="do-recognize-non-questions"></a><span data-ttu-id="30276-302">Do: Nicht-Fragen erkennen</span><span class="sxs-lookup"><span data-stu-id="30276-302">Do: Recognize non-questions</span></span>

<span data-ttu-id="30276-303">Ihr Bot sollte in der Lage sein, auf Nachrichten wie "Hallo", "Hilfe" und "Danke" zu antworten und gleichzeitig häufige Rechtschreibfehler und Umgangssprachen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="30276-303">Your bot should be able to respond to messages like "Hi", "Help", and "Thanks" while also accounting for common misspellings and colloquialisms.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Beispiel, in dem Sie ungeschickte Antworten auf einfache Botnachrichten vermeiden sollten." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a><span data-ttu-id="30276-305">Don‘t: Keine Gelegenheit verpassen, die Freude schenkt</span><span class="sxs-lookup"><span data-stu-id="30276-305">Don't: Miss out on opportunities to delight</span></span>

<span data-ttu-id="30276-306">Einige Personen erwarten, dass Gespräche auf natürliche Weise ablaufen, so wie mit einer realen Person.</span><span class="sxs-lookup"><span data-stu-id="30276-306">Some people expect conversations to flow naturally like they would with a real person.</span></span> <span data-ttu-id="30276-307">Vermeiden Sie ungeschickte Antworten auf einfache Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="30276-307">Try to avoid clumsy responses to simple messages.</span></span>

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a><span data-ttu-id="30276-308">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="30276-308">Troubleshooting</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Ein Beispiel für Bots sollte Benutzern dabei helfen, die Verwendung von Bots zu verstehen." border="false":::

#### <a name="do-provide-help"></a><span data-ttu-id="30276-310">Do: Hilfe anbieten</span><span class="sxs-lookup"><span data-stu-id="30276-310">Do: Provide help</span></span>

<span data-ttu-id="30276-311">Wenn Ihr Bot eine Anfrage nicht erfüllen kann, bieten Sie einem Benutzer Möglichkeiten, sich über die Interaktion mit Ihrem Bot zu informieren.</span><span class="sxs-lookup"><span data-stu-id="30276-311">If your bot can’t satisfy a request, provide ways for a user to educate themselves about interacting with your bot.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Beispiel, in dem Der Bot benutzer nicht litzen sollte." border="false":::

#### <a name="dont-leave-users-stranded"></a><span data-ttu-id="30276-313">Don‘t: Lassen Sie Benutzer nicht hängen</span><span class="sxs-lookup"><span data-stu-id="30276-313">Don't: Leave users stranded</span></span>

<span data-ttu-id="30276-314">Benutzer werden Ihren Bot schnell verlassen, wenn er keine Probleme beheben kann.</span><span class="sxs-lookup"><span data-stu-id="30276-314">People will quickly abandon your bot if they can’t troubleshoot issues.</span></span>

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a><span data-ttu-id="30276-315">Komplexe Interaktionen</span><span class="sxs-lookup"><span data-stu-id="30276-315">Complex interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Beispiel, in dem Sie Aufgabenmodule oder Registerkarten mit Ihrem Bot für komplexe Interaktionen verwenden können." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a><span data-ttu-id="30276-317">Do: Verwenden Sie Aufgabenmodule oder Registerkarten</span><span class="sxs-lookup"><span data-stu-id="30276-317">Do: Use task modules or tabs</span></span>

<span data-ttu-id="30276-318">Wenn Ihr Bot eine Antwort liefert, die einige weitere Schritte erfordert, können Sie eine Verknüpfung zu einem Aufgabenmodul oder einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="30276-318">If your bot provides an answer that requires a few more steps, you can link to a task module or tab to complete the task or flow.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Ihr Bot Interaktionen mit mehreren Drehungen vermeiden sollte." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a><span data-ttu-id="30276-320">Don‘t: Machen Sie Mehrfach-Interaktionen nicht langweilig</span><span class="sxs-lookup"><span data-stu-id="30276-320">Don't: Make multi-turn interactions tedious</span></span>

<span data-ttu-id="30276-321">Eine umfassende Unterhaltung zum Abschließen einer einzelnen Aufgabe ist langsam und übermäßig komplex.</span><span class="sxs-lookup"><span data-stu-id="30276-321">An extensive conversation to complete a single task is slow and overly complex.</span></span> <span data-ttu-id="30276-322">Außerdem muss der Entwickler Statusänderungen berücksichtigen (z. B. das Zeitlimit der Unterhaltung oder das Senden einer Nachricht zum Abbrechen).</span><span class="sxs-lookup"><span data-stu-id="30276-322">It also requires the developer to account for state changes (such as the conversation timing out or you sending a “Cancel” message).</span></span>

   :::column-end:::
:::row-end:::

### <a name="privacy"></a><span data-ttu-id="30276-323">Datenschutz</span><span class="sxs-lookup"><span data-stu-id="30276-323">Privacy</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Beispiel, in dem gezeigt wird, wie Bots nur private Informationen in einem persönlichen Kontext anzeigen sollten." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a><span data-ttu-id="30276-325">Do: Zeigen Sie vertrauliche Informationen nur in einem persönlichen Kontext an</span><span class="sxs-lookup"><span data-stu-id="30276-325">Do: Only show sensitive info in a personal context</span></span>

<span data-ttu-id="30276-326">Wenn sich Ihr Bot in einem Gruppenchat oder -kanal befindet, empfehlen wir, Benutzer an einen privaten Ort (z. B. ein Aufgabenmodul, eine Registerkarte oder einen Browser) zu leiten, um vertrauliche Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="30276-326">If your bot is in a group chat or channel, we recommend directing users to a private location (such as a task module, tab, or browser) to view sensitive information.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Bots keine vertraulichen Informationen für eine Gruppe oder Personen anzeigen sollten." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a><span data-ttu-id="30276-328">Don‘t: Einige Inhalte sollten nicht für alle einsehbar sein</span><span class="sxs-lookup"><span data-stu-id="30276-328">Don't: Some content isn’t meant to be seen by everyone</span></span>

<span data-ttu-id="30276-329">Ihr Bot sollte keine vertraulichen Informationen an Personen in einer Gruppe weitergeben.</span><span class="sxs-lookup"><span data-stu-id="30276-329">Your bot shouldn’t reveal sensitive information to a group of people.</span></span>

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="30276-330">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="30276-330">See also</span></span>

<span data-ttu-id="30276-331">Diese weiteren Richtlinien könnten bei Ihrem Bot-Design hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="30276-331">These other guidelines may help with your bot design:</span></span>

* [<span data-ttu-id="30276-332">Entwerfen Ihrer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="30276-332">Designing your personal app</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="30276-333">Entwerfen Adaptiver Karten</span><span class="sxs-lookup"><span data-stu-id="30276-333">Designing Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)
* [<span data-ttu-id="30276-334">Entwerfen von Aufgabenmodulen</span><span class="sxs-lookup"><span data-stu-id="30276-334">Designing task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
