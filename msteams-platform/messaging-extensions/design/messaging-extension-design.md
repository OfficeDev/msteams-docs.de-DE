---
title: Entwerfen Ihrer Messagingerweiterung
description: Erfahren Sie, wie Sie eine Microsoft Teams-Messagingerweiterung entwerfen und das Microsoft Teams UI Kit erhalten.
keywords: Bewährte Methode für Teams-Entwurfsrichtlinien zur Referenz von Messagingerweiterungen
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: 747b48e3aeb803f91cfb8d4412c98cb6d52c1fd1
ms.sourcegitcommit: f6e4a303828224a702138753a8e5e27c8a094c82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2021
ms.locfileid: "51176977"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="f42da-104">Entwerfen Ihrer Microsoft Teams-Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="f42da-105">Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="f42da-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="f42da-106">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="f42da-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="f42da-107">Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="f42da-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="f42da-108">Im Microsoft Teams UI Kit finden Sie umfassende Entwurfsrichtlinien für Messagingerweiterungen, einschließlich Elementen, die Sie bei Bedarf packen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="f42da-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f42da-109">Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="f42da-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="f42da-110">Hinzufügen einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-110">Add a messaging extension</span></span>

<span data-ttu-id="f42da-111">Sie können eine Messagingerweiterung in den folgenden Teams-Kontexten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="f42da-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="f42da-112">Aus dem Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="f42da-112">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="f42da-113">In einem Kanal, Chat oder einer Besprechung (vor, während und nach) in der Nähe des Verfassenfelds.</span><span class="sxs-lookup"><span data-stu-id="f42da-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="f42da-114">Es ist erwähnenswert, wenn Sie eine Messagingerweiterung an einem dieser Orte hinzufügen, nur Sie können sie in diesem Kontext verwenden.</span><span class="sxs-lookup"><span data-stu-id="f42da-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="f42da-115">Das folgende Beispiel zeigt, wie Sie eine Messagingerweiterung in einem Kanal hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f42da-115">The following example shows how you add a messaging extension in a channel.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung in der Nähe des Verfassenfelds in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="f42da-117">Einrichten einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-117">Set up a messaging extension</span></span>

<span data-ttu-id="f42da-118">Die Authentifizierung ist nicht zwingend erforderlich, aber wenn Ihre App so etwas wie ein Ticketverfolgungstool ist, müssen Sie sich möglicherweise anmelden, um die Messagingerweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f42da-118">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="f42da-119">Aus Gründen der Konsistenz in teams-Apps können Sie den Anmeldebildschirm nicht anpassen.</span><span class="sxs-lookup"><span data-stu-id="f42da-119">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="f42da-120">Wenn Sie die einmalige Anmeldung (Single Sign-On, SSO)-Authentifizierung verwenden, werden Benutzer automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="f42da-120">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Beispiel zeigt den Setupbildschirm der Messagingerweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="f42da-122">Arten von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="f42da-122">Types of messaging extensions</span></span>

<span data-ttu-id="f42da-123">Messagingerweiterungen können Suchbefehle, Aktionsbefehle oder beides enthalten.</span><span class="sxs-lookup"><span data-stu-id="f42da-123">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="f42da-124">Ihre Befehle hängen von den Features Ihrer App ab und davon, wie diese in Teams passen.</span><span class="sxs-lookup"><span data-stu-id="f42da-124">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="f42da-125">Suchbefehle</span><span class="sxs-lookup"><span data-stu-id="f42da-125">Search commands</span></span>

<span data-ttu-id="f42da-126">Mithilfe von Suchbefehlen können Benutzer Ihre Messagingerweiterung verwenden, um schnell externe Inhalte zu finden und in eine Nachricht zu einfügen.</span><span class="sxs-lookup"><span data-stu-id="f42da-126">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="f42da-127">Suchbefehle werden häufig im Verfassenfeld verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="f42da-127">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="f42da-128">Sie können beispielsweise eine Diskussion starten oder einer Diskussion hinzufügen, indem Sie einen Teil des Inhalts freigeben – ohne Teams jemals zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="f42da-128">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Beispiel zeigt eine suchbasierte Messagingerweiterung, die über das Verfassenfeld gestartet wird." border="false":::

#### <a name="compose-box-layout-options"></a><span data-ttu-id="f42da-130">Layoutoptionen für Verfassen von Schachteln</span><span class="sxs-lookup"><span data-stu-id="f42da-130">Compose box layout options</span></span>

<span data-ttu-id="f42da-131">Sie haben einige Optionen zum Anzeigen von Suchergebnissen der Messagingerweiterung, einschließlich [Listen- und Rasteransichten.](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests)</span><span class="sxs-lookup"><span data-stu-id="f42da-131">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse für Messagingerweiterungen." border="false":::

### <a name="action-commands"></a><span data-ttu-id="f42da-133">Aktionsbefehle</span><span class="sxs-lookup"><span data-stu-id="f42da-133">Action commands</span></span>

<span data-ttu-id="f42da-134">Mit Aktionsbefehlen können Benutzer Aktionen auslösen und Anforderungen in externen Diensten in Teams verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f42da-134">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="f42da-135">Wenn Ihre App beispielsweise Bestellungen verfolgt, kann ein Benutzer eine neue Bestellung erstellen, indem er den Inhalt der Nachricht eines Kollegen direkt in seinem Chat verwendet.</span><span class="sxs-lookup"><span data-stu-id="f42da-135">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="f42da-136">Für aktionsbasierte Messagingerweiterungen müssen Benutzer häufig ein Formular oder eine andere Art von Konfiguration innerhalb eines modalen Formulars abschließen.</span><span class="sxs-lookup"><span data-stu-id="f42da-136">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="f42da-137">Sie können diese Erfahrungen mit [Aufgabenmodulen erstellen.](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)</span><span class="sxs-lookup"><span data-stu-id="f42da-137">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="f42da-138">Öffnen einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-138">Open a messaging extension</span></span>

<span data-ttu-id="f42da-139">Das Verfassenfeld und Nachrichten/Beiträge sind die primären Kontexte, in denen Personen Messagingerweiterungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="f42da-139">The compose box and messages/posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="f42da-140">Aus dem Verfassenfeld</span><span class="sxs-lookup"><span data-stu-id="f42da-140">From the compose box</span></span>

<span data-ttu-id="f42da-141">Nach dem Hinzufügen können Benutzer Ihre Messagingerweiterung öffnen, indem sie ihr App-Symbol unterhalb des Verfassenfelds auswählen.</span><span class="sxs-lookup"><span data-stu-id="f42da-141">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="f42da-142">In diesem Beispiel verfügt die Erweiterung über Such- und Aktionsbefehle.</span><span class="sxs-lookup"><span data-stu-id="f42da-142">In this example, the extension has search and action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung aus dem Verfassenfeld öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="f42da-144">Aus einer Chatnachricht oder einem Kanalbeitrag</span><span class="sxs-lookup"><span data-stu-id="f42da-144">From a chat message or channel post</span></span>

Nach dem Hinzufügen können Benutzer das Symbol **Mehr** in der Chatnachricht oder dem Kanalbeitrag auswählen, um die :::image type="icon" source="../../assets/icons/teams-client-more.png"::: Aktionsbefehle Ihrer Erweiterung zu finden. <span data-ttu-id="f42da-146">Ihre Erweiterung kann unter **Weitere Aktionen basierend auf der** Verwendung aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f42da-146">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="f42da-147">Unterstützung für weitere Aktionen aus einer Chatnachricht oder einem Kanalbeitrag ist auf der mobilen Microsoft Teams-Plattform nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f42da-147">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="f42da-148">Chatnachricht</span><span class="sxs-lookup"><span data-stu-id="f42da-148">Chat message</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a><span data-ttu-id="f42da-150">Kanalbeitrag</span><span class="sxs-lookup"><span data-stu-id="f42da-150">Channel post</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung über einen Kanalbeitrag öffnen." border="false":::

## <a name="use-a-messaging-extension"></a><span data-ttu-id="f42da-152">Verwenden einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-152">Use a messaging extension</span></span>

<span data-ttu-id="f42da-153">In den folgenden Szenarien wird die primäre Verwendung von Messagingerweiterungen für Personen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f42da-153">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="f42da-154">Einfügen von Inhalten in eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="f42da-154">Insert content into a message</span></span>

<span data-ttu-id="f42da-155">**1. Wählen Sie eine Messagingerweiterung aus.**</span><span class="sxs-lookup"><span data-stu-id="f42da-155">**1. Select a messaging extension**.</span></span> <span data-ttu-id="f42da-156">Benutzer können im Verfassenfeld nach den Inhalten suchen, die sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="f42da-156">Users can search for the content they want to share from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Beispiel zeigt einen Benutzer, der nach Inhalt sucht, der aus dem Verfassenfeld eingefügt werden soll." border="false":::

<span data-ttu-id="f42da-158">**2. Einfügen von Inhalten**.</span><span class="sxs-lookup"><span data-stu-id="f42da-158">**2. Insert content**.</span></span> <span data-ttu-id="f42da-159">Nachdem sie veröffentlicht wurden, können andere Personen den Inhalt beantworten oder auswählen, um weitere Informationen in Ihrer App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f42da-159">Once posted, others can reply or select the content to see more information in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Beispiel zeigt einen Benutzer, der Inhalte in einer Kanal unterhaltung postet." border="false":::

### <a name="take-action-on-a-message"></a><span data-ttu-id="f42da-161">Ergreifen von Aktionen für eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="f42da-161">Take action on a message</span></span>

<span data-ttu-id="f42da-162">**1. Wählen Sie eine Messagingerweiterung aus.**</span><span class="sxs-lookup"><span data-stu-id="f42da-162">**1. Select a messaging extension**.</span></span> <span data-ttu-id="f42da-163">Ihre App kann einen oder mehrere Aktionsbefehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="f42da-163">Your app can include one or more action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Beispiel zeigt einen Benutzer, der einen Befehl für die Messagingerweiterungsaktion aus wählt." border="false":::

<span data-ttu-id="f42da-165">**2. Führen Sie die Aktion aus.**</span><span class="sxs-lookup"><span data-stu-id="f42da-165">**2. Complete the action**.</span></span> <span data-ttu-id="f42da-166">Ihre App kann alle von der Nachrichtenaktion gesendeten Inhalte oder Daten empfangen und verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f42da-166">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="f42da-167">Dies ermöglicht Benutzern, in ihrer Unterhaltung zu bleiben und sich im folgenden Beispiel keine Gedanken über die direkte Eingabe von Informationen in Ihrer App zu machen.</span><span class="sxs-lookup"><span data-stu-id="f42da-167">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel zeigt einen Benutzer, der nach Inhalt sucht, der aus dem Verfassenfeld eingefügt werden soll." border="false":::

### <a name="preview-links"></a><span data-ttu-id="f42da-169">Vorschaulinks</span><span class="sxs-lookup"><span data-stu-id="f42da-169">Preview links</span></span>

<span data-ttu-id="f42da-170">Mit Messagingerweiterungen können Sie auch rich links from a recognized URL in eine Nachricht einfügen (diese Funktion wird als [Link unfurling bezeichnet.)](../../messaging-extensions/how-to/link-unfurling.md)</span><span class="sxs-lookup"><span data-stu-id="f42da-170">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="f42da-171">**1. Fügen Sie einen erkannten Link** in das Verfassenfeld ein.</span><span class="sxs-lookup"><span data-stu-id="f42da-171">**1. Paste a recognized link** in the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Ein Beispiel zeigt einen Benutzer, der einen Link in das Kompostfeld einklinkt." border="false":::

<span data-ttu-id="f42da-173">**2. Einfügen von Inhalten**.</span><span class="sxs-lookup"><span data-stu-id="f42da-173">**2. Insert content**.</span></span> <span data-ttu-id="f42da-174">Wenn Ihre App die URL im Verfassenfeld erkennt, wird der Link als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bietet.</span><span class="sxs-lookup"><span data-stu-id="f42da-174">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="f42da-175">(Weitere Informationen finden Sie unter [Entwurfsrichtlinien für](../../task-modules-and-cards/cards/design-effective-cards.md) adaptive Karten.)</span><span class="sxs-lookup"><span data-stu-id="f42da-175">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Beispiel zeigt, wie die URL, da sie von Ihrer App erkannt wird, einige umfangreiche Inhalte im Verfassenfeld enthält." border="false":::

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="f42da-177">Verwalten einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="f42da-177">Manage a messaging extension</span></span>

<span data-ttu-id="f42da-178">Durch klicken mit der rechten Maustaste auf Ihr Symbol können Benutzer Ihre Messagingerweiterung anheften, entfernen oder konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f42da-178">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="f42da-179">Anatomie</span><span class="sxs-lookup"><span data-stu-id="f42da-179">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="f42da-180">Messagingerweiterung im Verfassenfeld</span><span class="sxs-lookup"><span data-stu-id="f42da-180">Messaging extension in the compose box</span></span>

<span data-ttu-id="f42da-181">Das folgende Beispiel ist eine Messagingerweiterung, die über das Verfassenfeld geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="f42da-181">The following example is a messaging extension opened from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung der Anatomie der Benutzeroberfläche einer Messagingerweiterung im Verfassenfeld." border="false":::

|<span data-ttu-id="f42da-183">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f42da-183">Counter</span></span>|<span data-ttu-id="f42da-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f42da-184">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f42da-185">1</span><span class="sxs-lookup"><span data-stu-id="f42da-185">1</span></span>|<span data-ttu-id="f42da-186">**App-Logo:** Farbsymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="f42da-186">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="f42da-187">2</span><span class="sxs-lookup"><span data-stu-id="f42da-187">2</span></span>|<span data-ttu-id="f42da-188">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="f42da-188">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="f42da-189">3</span><span class="sxs-lookup"><span data-stu-id="f42da-189">3</span></span>|<span data-ttu-id="f42da-190">**Menüsymbol für Aktionsbefehle (optional):** Öffnet eine Liste der Aktionsbefehle für Ihre Messagingerweiterung (sofern vorhanden).</span><span class="sxs-lookup"><span data-stu-id="f42da-190">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="f42da-191">4 </span><span class="sxs-lookup"><span data-stu-id="f42da-191">4</span></span>|<span data-ttu-id="f42da-192">**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="f42da-192">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="f42da-193">5 </span><span class="sxs-lookup"><span data-stu-id="f42da-193">5</span></span>|<span data-ttu-id="f42da-194">**Registerkartenmenü (optional):** Stellt mehrere Inhaltskategorien zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="f42da-194">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="f42da-195">6 </span><span class="sxs-lookup"><span data-stu-id="f42da-195">6</span></span>|<span data-ttu-id="f42da-196">**Menü "Aktionsbefehle" (optional):** Zeigt eine Liste der Aktionsbefehle an (wenn Sie einen angeben).</span><span class="sxs-lookup"><span data-stu-id="f42da-196">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="f42da-197">7 </span><span class="sxs-lookup"><span data-stu-id="f42da-197">7</span></span>|<span data-ttu-id="f42da-198">**App-Inhalt**: In erster Linie zum Anzeigen von Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="f42da-198">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="f42da-199">Im folgenden Beispiel wird das Listenlayout verwendet (rasterlayout ist eine weitere Option).</span><span class="sxs-lookup"><span data-stu-id="f42da-199">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="f42da-200">8 </span><span class="sxs-lookup"><span data-stu-id="f42da-200">8</span></span>|<span data-ttu-id="f42da-201">**App-Logo:** Gliederungssymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="f42da-201">**App logo**: Outline icon of your app logo.</span></span>|

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="f42da-202">Menü "Verwaltung von Nachrichtenerweiterungen"</span><span class="sxs-lookup"><span data-stu-id="f42da-202">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung der Benutzeroberflächenanatomie eines Menüs zur Verwaltung von Messagingerweiterungen." border="false":::

|<span data-ttu-id="f42da-204">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="f42da-204">Counter</span></span>|<span data-ttu-id="f42da-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f42da-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f42da-206">1</span><span class="sxs-lookup"><span data-stu-id="f42da-206">1</span></span>|<span data-ttu-id="f42da-207">**Unpin**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="f42da-207">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="f42da-208">2</span><span class="sxs-lookup"><span data-stu-id="f42da-208">2</span></span>|<span data-ttu-id="f42da-209">**Remove**: Entfernt die Messagingerweiterung aus dem Kanal, Chat oder der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="f42da-209">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="f42da-210">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="f42da-210">Best practices</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="f42da-211">Setup und allgemeine Verwendung</span><span class="sxs-lookup"><span data-stu-id="f42da-211">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="f42da-213">Do: Integration in einmaliges Anmelden</span><span class="sxs-lookup"><span data-stu-id="f42da-213">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="f42da-214">SSO erleichtert, schneller und sicherer den Anmeldevorgang.</span><span class="sxs-lookup"><span data-stu-id="f42da-214">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="f42da-215">Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messagingerweiterung zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f42da-215">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="f42da-217">Don't: Take users away from the conversation</span><span class="sxs-lookup"><span data-stu-id="f42da-217">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="f42da-218">Messagingerweiterungen sind Verknüpfungen, die den Kontextwechsel reduzieren sollen.</span><span class="sxs-lookup"><span data-stu-id="f42da-218">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="f42da-219">Ihre Erweiterung sollte z. B. Benutzer nicht an eine Webseite außerhalb von Teams weiterverdingen.</span><span class="sxs-lookup"><span data-stu-id="f42da-219">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="f42da-220">Do: Highlight your messaging extension</span><span class="sxs-lookup"><span data-stu-id="f42da-220">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="f42da-221">Messagingerweiterungen sind nicht immer einfach zu finden.</span><span class="sxs-lookup"><span data-stu-id="f42da-221">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="f42da-222">Fügen Sie Screenshots dazu hinzu, wie Sie sie auf der Seite mit den App-Details verwenden.</span><span class="sxs-lookup"><span data-stu-id="f42da-222">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="f42da-223">Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation zur Messagingerweiterung in eine Bot-Willkommenstour einfüllen.</span><span class="sxs-lookup"><span data-stu-id="f42da-223">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="f42da-224">Templating</span><span class="sxs-lookup"><span data-stu-id="f42da-224">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="f42da-226">Do: Lassen Sie Teams einen Teil der Entwurfsarbeit nach Möglichkeit behandeln</span><span class="sxs-lookup"><span data-stu-id="f42da-226">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="f42da-227">Wenn es für Ihre Verwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messagingerweiterung erstellen.</span><span class="sxs-lookup"><span data-stu-id="f42da-227">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="f42da-228">Teams rendert diese Arten von Erweiterungen mit integriertem Theming und Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="f42da-228">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="f42da-230">Don't: Embed your entire app in a task module</span><span class="sxs-lookup"><span data-stu-id="f42da-230">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="f42da-231">Wenn ihre Messagingerweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul einfach und zeigen Sie nur die Komponenten an, die zum Ausführen der Aktion erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f42da-231">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="f42da-232">Designs</span><span class="sxs-lookup"><span data-stu-id="f42da-232">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="f42da-234">Do: Nutzen von Teams-Farbtoken</span><span class="sxs-lookup"><span data-stu-id="f42da-234">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="f42da-235">Jedes Teams-Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="f42da-235">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="f42da-236">Verwenden Sie Farbtoken <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">(Fluent UI)</a> in Ihrem Entwurf, um Designänderungen automatisch zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f42da-236">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="f42da-238">Don't: Hartcodefarbwerte</span><span class="sxs-lookup"><span data-stu-id="f42da-238">Don't: Hard code color values</span></span>

<span data-ttu-id="f42da-239">Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und brauchen mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="f42da-239">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="f42da-240">Aktionen</span><span class="sxs-lookup"><span data-stu-id="f42da-240">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="f42da-242">Do: Fügen Sie Aktionsbefehle ein, die im Kontext sinnvoll sind</span><span class="sxs-lookup"><span data-stu-id="f42da-242">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="f42da-243">Nachrichtenaktionen sollten sich darauf beziehen, was ein Benutzer anschaut.</span><span class="sxs-lookup"><span data-stu-id="f42da-243">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="f42da-244">Stellen Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mithilfe des Texts in einem Beitrag einer Person zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="f42da-244">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für eine bewährte Methode für eine Messagingerweiterung." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="f42da-246">Don't: Include actions commands that aren't contextual</span><span class="sxs-lookup"><span data-stu-id="f42da-246">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="f42da-247">Eine Nachrichtenaktion zum **Anzeigen Des Dashboards** scheint wahrscheinlich nicht mit den meisten Unterhaltungen verbunden zu sein.</span><span class="sxs-lookup"><span data-stu-id="f42da-247">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="f42da-248">Suchen</span><span class="sxs-lookup"><span data-stu-id="f42da-248">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="f42da-249">Do: Anzeigen von Suchergebnissen während der Eingabe</span><span class="sxs-lookup"><span data-stu-id="f42da-249">Do: Show search results while typing</span></span>

<span data-ttu-id="f42da-250">Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer eingeben.</span><span class="sxs-lookup"><span data-stu-id="f42da-250">Provide suggested search results while users type.</span></span> <span data-ttu-id="f42da-251">Möglicherweise finden sie die benötigten Inhalte schneller mit minimaler Zeichenmenge.</span><span class="sxs-lookup"><span data-stu-id="f42da-251">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="f42da-252">Don't: Benutzer zum Senden einer Abfrage benötigen</span><span class="sxs-lookup"><span data-stu-id="f42da-252">Don't: Require users to submit a query</span></span>

<span data-ttu-id="f42da-253">Sie können benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre App zu senden.</span><span class="sxs-lookup"><span data-stu-id="f42da-253">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="f42da-254">Während dies im App-Dienste-Dienst möglicherweise einfacher ist, sind die Personen möglicherweise verwirrt, dass bei der Eingabe keine Echtzeitsuchergebnisse angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f42da-254">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="f42da-255">Do: Berücksichtigen von Zero-Term-Abfragen</span><span class="sxs-lookup"><span data-stu-id="f42da-255">Do: Consider zero-term queries</span></span>

<span data-ttu-id="f42da-256">Bevor ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angezeigt hat.</span><span class="sxs-lookup"><span data-stu-id="f42da-256">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="f42da-257">Es ist möglich, dass sie diese Inhalte in ihre Unterhaltung einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="f42da-257">It's possible that they want to insert that content into their conversation.</span></span>

## <a name="validate-your-design"></a><span data-ttu-id="f42da-258">Überprüfen Des Entwurfs</span><span class="sxs-lookup"><span data-stu-id="f42da-258">Validate your design</span></span>

<span data-ttu-id="f42da-259">Wenn Sie planen, Ihre App in AppSource zu veröffentlichen, sollten Sie die Entwurfsprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="f42da-259">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f42da-260">Überprüfen der Richtlinien für die Entwurfsüberprüfung</span><span class="sxs-lookup"><span data-stu-id="f42da-260">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
