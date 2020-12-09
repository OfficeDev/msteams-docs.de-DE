---
title: Entwerfen Ihrer Messaging Erweiterung
description: Erfahren Sie, wie Sie eine Teams-Messaging Erweiterung entwerfen und das Microsoft Teams UI Kit erhalten.
keywords: Design Guidelines für Teams Referenz Tipps für Messaging-Erweiterungen bewährte Methode
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ad628bdaa46058aed4acdcea1a224c7ebfe40f89
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604853"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="73ea9-104">Entwerfen Ihrer Microsoft Teams-Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="73ea9-105">Messaging-Erweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne von der Unterhaltung Weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="73ea9-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>

<span data-ttu-id="73ea9-106">Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Personen Messaging Erweiterungen in Microsoft Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="73ea9-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="73ea9-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="73ea9-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="73ea9-108">Umfassende Entwurfsrichtlinien für Messaging-Erweiterungen, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="73ea9-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73ea9-109">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="73ea9-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="73ea9-110">Hinzufügen einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-110">Add a messaging extension</span></span>

<span data-ttu-id="73ea9-111">Sie können eine Messaging Erweiterung in den folgenden Microsoft Teams-Kontexten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="73ea9-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="73ea9-112">Aus dem Microsoft Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="73ea9-112">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="73ea9-113">In einem Kanal, Chat oder einer Besprechung (vor, während und nach) in der Nähe des Felds zum Verfassen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="73ea9-114">Es ist erwähnenswert, wenn Sie eine Messaging Erweiterung an einer dieser Orte hinzufügen, nur Sie können Sie in diesem Kontext verwenden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="73ea9-115">Im folgenden Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung in einem Kanal hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-115">The following example shows how you add a messaging extension in a channel.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung neben dem Feld Verfassen in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="73ea9-117">Einrichten einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-117">Set up a messaging extension</span></span>

<span data-ttu-id="73ea9-118">Die Authentifizierung ist nicht zwingend erforderlich, aber wenn Ihre APP so etwas wie ein Ticket verfolgungstool ist, müssen sich möglicherweise Benutzer anmelden, um die Messaging Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-118">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="73ea9-119">Für Konsistenz in Microsoft Teams-Apps können Sie den Anmeldebildschirm nicht anpassen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-119">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="73ea9-120">Wenn Sie die SSO-Authentifizierung (Single Sign-on, einmaliges Anmelden) verwenden, werden Benutzer automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="73ea9-120">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Beispiel zeigt den Setupbildschirm für die Messaging Erweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="73ea9-122">Typen von Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="73ea9-122">Types of messaging extensions</span></span>

<span data-ttu-id="73ea9-123">Messaging Erweiterungen können Suchbefehle, Aktionsbefehle oder beides haben.</span><span class="sxs-lookup"><span data-stu-id="73ea9-123">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="73ea9-124">Ihre Befehle hängen von den Funktionen Ihrer APP ab und davon, wie diese in Microsoft Teams-Anwendungsfällen angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-124">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="73ea9-125">Suchbefehle</span><span class="sxs-lookup"><span data-stu-id="73ea9-125">Search commands</span></span>

<span data-ttu-id="73ea9-126">Mit Suchbefehlen können Benutzer Ihre Messaging Erweiterung verwenden, um schnell externe Inhalte zu finden und in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-126">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="73ea9-127">Suchbefehle werden häufig im Feld Verfassen zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="73ea9-127">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="73ea9-128">Sie können beispielsweise eine Diskussion starten oder hinzufügen, indem Sie einen Teil des Inhalts freigeben, ohne Teams jemals verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-128">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Beispiel zeigt eine suchbasierte Messaging Erweiterung, die im Feld erstellen gestartet wurde." border="false":::

#### <a name="compose-box-layout-options"></a><span data-ttu-id="73ea9-130">Optionen für das Erstellen von Feldlayouts</span><span class="sxs-lookup"><span data-stu-id="73ea9-130">Compose box layout options</span></span>

<span data-ttu-id="73ea9-131">Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messaging Erweiterungen, einschließlich [Listen-und rasteransichten](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span><span class="sxs-lookup"><span data-stu-id="73ea9-131">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Illustrationen mit Layout-Optionen für Suchergebnisse der Messaging-Erweiterung." border="false":::

### <a name="action-commands"></a><span data-ttu-id="73ea9-133">Aktionsbefehle</span><span class="sxs-lookup"><span data-stu-id="73ea9-133">Action commands</span></span>

<span data-ttu-id="73ea9-134">Aktionsbefehle ermöglichen Benutzern das Auslösen von Aktionen und Verarbeiten von Anforderungen in externen Diensten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="73ea9-134">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="73ea9-135">Wenn Ihre APP beispielsweise Bestellungen aufspürt, könnte ein Benutzer eine neue Bestellung mit dem Inhalt der Nachricht eines Kollegen von rechts in seinem Chat erstellen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-135">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="73ea9-136">Bei Aktionen basierenden Messaging Erweiterungen ist es häufig erforderlich, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines modalen Formulars ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-136">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="73ea9-137">Sie können diese Erfahrungen mit [Aufgaben Modulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-137">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="73ea9-138">Öffnen einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-138">Open a messaging extension</span></span>

<span data-ttu-id="73ea9-139">Das Feld "Verfassen" und "Nachrichten/Beiträge" sind die primären Kontexte, in denen Personen Messaging Erweiterungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-139">The compose box and messages/posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="73ea9-140">Aus dem Feld Verfassen</span><span class="sxs-lookup"><span data-stu-id="73ea9-140">From the compose box</span></span>

<span data-ttu-id="73ea9-141">Sobald die Benutzer hinzugefügt wurden, können Sie Ihre Messaging Erweiterung öffnen, indem Sie das App-Symbol unter dem Feld Verfassen auswählen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-141">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="73ea9-142">In diesem Beispiel verfügt die Erweiterung über Such-und Aktionsbefehle.</span><span class="sxs-lookup"><span data-stu-id="73ea9-142">In this example, the extension has search and action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung aus dem Feld Verfassen öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="73ea9-144">Aus einer Chatnachricht oder einem Kanal Beitrag</span><span class="sxs-lookup"><span data-stu-id="73ea9-144">From a chat message or channel post</span></span>

Nachdem die Benutzer hinzugefügt wurden **More** , können Sie :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chatnachricht oder im Kanal Beitrag das Symbol "More" auswählen, um die Aktionsbefehle ihrer Erweiterung zu finden. <span data-ttu-id="73ea9-146">Ihre Erweiterung wird möglicherweise unter **Weitere Aktionen** basierend auf der Verwendung aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="73ea9-146">Your extension may be listed under **More actions** based on usage.</span></span>

#### <a name="chat-message"></a><span data-ttu-id="73ea9-147">Chatnachricht</span><span class="sxs-lookup"><span data-stu-id="73ea9-147">Chat message</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Beispiel zeigt, wie Sie eine Messaging Erweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a><span data-ttu-id="73ea9-149">Kanal Beitrag</span><span class="sxs-lookup"><span data-stu-id="73ea9-149">Channel post</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung von einem Kanal Beitrag aus öffnen." border="false":::

## <a name="use-a-messaging-extension"></a><span data-ttu-id="73ea9-151">Verwenden einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-151">Use a messaging extension</span></span>

<span data-ttu-id="73ea9-152">In den folgenden Szenarien werden die primären Methoden für die Verwendung von Messaging Erweiterungen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="73ea9-152">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="73ea9-153">Einfügen von Inhalt in eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="73ea9-153">Insert content into a message</span></span>

<span data-ttu-id="73ea9-154">**1. Wählen Sie eine Messaging Erweiterung aus**.</span><span class="sxs-lookup"><span data-stu-id="73ea9-154">**1. Select a messaging extension**.</span></span> <span data-ttu-id="73ea9-155">Benutzer können im Feld Verfassen nach dem Inhalt suchen, den Sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-155">Users can search for the content they want to share from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Beispiel: ein Benutzer, der nach einzufügenden Inhalten sucht, wird aus dem Feld Verfassen angezeigt." border="false":::

<span data-ttu-id="73ea9-157">**2. Einfügen von Inhalten**.</span><span class="sxs-lookup"><span data-stu-id="73ea9-157">**2. Insert content**.</span></span> <span data-ttu-id="73ea9-158">Nach der Veröffentlichung können andere Personen Antworten oder den Inhalt auswählen, um weitere Informationen in Ihrer APP anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-158">Once posted, others can reply or select the content to see more information in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Beispiel zeigt einen Benutzer, der Inhalte in einer Kanal Unterhaltung veröffentlicht." border="false":::

### <a name="take-action-on-a-message"></a><span data-ttu-id="73ea9-160">Aktion für eine Nachricht ausführen</span><span class="sxs-lookup"><span data-stu-id="73ea9-160">Take action on a message</span></span>

<span data-ttu-id="73ea9-161">**1. Wählen Sie eine Messaging Erweiterung aus**.</span><span class="sxs-lookup"><span data-stu-id="73ea9-161">**1. Select a messaging extension**.</span></span> <span data-ttu-id="73ea9-162">Ihre APP kann einen oder mehrere Aktionsbefehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-162">Your app can include one or more action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Beispiel zeigt einen Benutzer, der einen Aktionsbefehl für die Messaging Erweiterung auswählt." border="false":::

<span data-ttu-id="73ea9-164">**2. führen Sie die Aktion** aus.</span><span class="sxs-lookup"><span data-stu-id="73ea9-164">**2. Complete the action**.</span></span> <span data-ttu-id="73ea9-165">Ihre APP kann alle Inhalte oder Daten, die von der Nachrichtenaktion gesendet werden, empfangen und verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-165">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="73ea9-166">Auf diese Weise können Benutzer in Ihrer Unterhaltung bleiben, und im folgenden Beispiel wird keine direkte Eingabe von Informationen in Ihre APP befürchtet.</span><span class="sxs-lookup"><span data-stu-id="73ea9-166">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel: ein Benutzer, der nach einzufügenden Inhalten sucht, wird aus dem Feld Verfassen angezeigt." border="false":::

### <a name="preview-links"></a><span data-ttu-id="73ea9-168">Vorschau Links</span><span class="sxs-lookup"><span data-stu-id="73ea9-168">Preview links</span></span>

<span data-ttu-id="73ea9-169">Mithilfe von Messaging Erweiterungen können Sie auch Rich-Links von einer erkannten URL in eine Nachricht einfügen (diese Funktion wird als [Verknüpfungs Entfaltung](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="73ea9-169">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="73ea9-170">**1. Fügen Sie einen erkannten Link** in das Feld Verfassen ein.</span><span class="sxs-lookup"><span data-stu-id="73ea9-170">**1. Paste a recognized link** in the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Beispiel zeigt ein Benutzer, der einen Link in das Feld Kompost einfügt." border="false":::

<span data-ttu-id="73ea9-172">**2. Einfügen von Inhalten**.</span><span class="sxs-lookup"><span data-stu-id="73ea9-172">**2. Insert content**.</span></span> <span data-ttu-id="73ea9-173">Wenn Ihre APP die URL im Feld Verfassen erkennt, wird die Verknüpfung als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="73ea9-173">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="73ea9-174">(Weitere Informationen finden Sie unter [Adaptive Cards Design Guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) .)</span><span class="sxs-lookup"><span data-stu-id="73ea9-174">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Beispiel zeigt, wie die URL, da Sie von Ihrer APP erkannt wird, einen umfangreichen Inhalt im Feld Verfassen enthält." border="false":::

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="73ea9-176">Verwalten einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-176">Manage a messaging extension</span></span>

<span data-ttu-id="73ea9-177">Wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken, können Benutzer Ihre Messaging Erweiterung anheften, entfernen oder konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="73ea9-177">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="73ea9-178">Anatomie</span><span class="sxs-lookup"><span data-stu-id="73ea9-178">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="73ea9-179">Messaging Erweiterung im Feld Verfassen</span><span class="sxs-lookup"><span data-stu-id="73ea9-179">Messaging extension in the compose box</span></span>

<span data-ttu-id="73ea9-180">Das folgende Beispiel ist eine im Feld Verfassen geöffnete Messaging Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="73ea9-180">The following example is a messaging extension opened from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Illustration, die die Benutzeroberflächen Anatomie einer Messaging Erweiterung im Feld Verfassen zeigt." border="false":::

|<span data-ttu-id="73ea9-182">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="73ea9-182">Counter</span></span>|<span data-ttu-id="73ea9-183">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73ea9-183">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="73ea9-184">1</span><span class="sxs-lookup"><span data-stu-id="73ea9-184">1</span></span>|<span data-ttu-id="73ea9-185">**App-Logo**: Farbsymbol des App-Logos.</span><span class="sxs-lookup"><span data-stu-id="73ea9-185">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="73ea9-186">2 </span><span class="sxs-lookup"><span data-stu-id="73ea9-186">2</span></span>|<span data-ttu-id="73ea9-187">**App-Name**: vollständiger Name Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="73ea9-187">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="73ea9-188">3 </span><span class="sxs-lookup"><span data-stu-id="73ea9-188">3</span></span>|<span data-ttu-id="73ea9-189">**Menüsymbol für Aktionsbefehle (optional)**: öffnet eine Liste mit Aktions Befehlen für Ihre Messaging Erweiterung (wenn Sie eine beliebige Option angeben).</span><span class="sxs-lookup"><span data-stu-id="73ea9-189">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="73ea9-190">4 </span><span class="sxs-lookup"><span data-stu-id="73ea9-190">4</span></span>|<span data-ttu-id="73ea9-191">**Suchfeld**: ermöglicht Benutzern das Auffinden von App-Inhalten, die Sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-191">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="73ea9-192">5 </span><span class="sxs-lookup"><span data-stu-id="73ea9-192">5</span></span>|<span data-ttu-id="73ea9-193">**Tab-Menü (optional)**: bietet mehrere Inhaltskategorien.</span><span class="sxs-lookup"><span data-stu-id="73ea9-193">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="73ea9-194">6 </span><span class="sxs-lookup"><span data-stu-id="73ea9-194">6</span></span>|<span data-ttu-id="73ea9-195">**Menü "Aktionsbefehle" (optional)**: zeigt eine Liste der Aktionsbefehle an (sofern angegeben).</span><span class="sxs-lookup"><span data-stu-id="73ea9-195">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="73ea9-196">7 </span><span class="sxs-lookup"><span data-stu-id="73ea9-196">7</span></span>|<span data-ttu-id="73ea9-197">**App-Inhalt**: in erster Linie zum Anzeigen von Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-197">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="73ea9-198">Im Beispiel wird das Listenlayout verwendet (das Rasterlayout ist eine weitere Option).</span><span class="sxs-lookup"><span data-stu-id="73ea9-198">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="73ea9-199">8 </span><span class="sxs-lookup"><span data-stu-id="73ea9-199">8</span></span>|<span data-ttu-id="73ea9-200">**App-Logo**: Gliederungssymbol des App-Logos.</span><span class="sxs-lookup"><span data-stu-id="73ea9-200">**App logo**: Outline icon of your app logo.</span></span>|

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="73ea9-201">Menü "Messaging-Erweiterungsverwaltung"</span><span class="sxs-lookup"><span data-stu-id="73ea9-201">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung der UI-Anatomie eines Messaging-Erweiterungs Verwaltungsmenüs." border="false":::

|<span data-ttu-id="73ea9-203">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="73ea9-203">Counter</span></span>|<span data-ttu-id="73ea9-204">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="73ea9-204">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="73ea9-205">1</span><span class="sxs-lookup"><span data-stu-id="73ea9-205">1</span></span>|<span data-ttu-id="73ea9-206">**Unpin**: verfügbar, wenn der Benutzer Ihre APP angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="73ea9-206">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="73ea9-207">2 </span><span class="sxs-lookup"><span data-stu-id="73ea9-207">2</span></span>|<span data-ttu-id="73ea9-208">**Remove**: entfernt die Messaging Erweiterung aus dem Kanal, dem Chat oder der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="73ea9-208">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="73ea9-209">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="73ea9-209">Best practices</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="73ea9-210">Setup und allgemeine Verwendung</span><span class="sxs-lookup"><span data-stu-id="73ea9-210">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="73ea9-212">Do: integrieren in einmaliges Anmelden</span><span class="sxs-lookup"><span data-stu-id="73ea9-212">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="73ea9-213">Mit SSO wird der Anmeldeprozess einfacher, schneller und sicherer.</span><span class="sxs-lookup"><span data-stu-id="73ea9-213">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="73ea9-214">Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messaging Erweiterung zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-214">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="73ea9-216">Nicht: Benutzer von der Unterhaltung entfernen</span><span class="sxs-lookup"><span data-stu-id="73ea9-216">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="73ea9-217">Bei Messaging Erweiterungen handelt es sich um Verknüpfungen, die den Kontextwechsel reduzieren sollen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-217">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="73ea9-218">Ihre Erweiterung sollte beispielsweise keine Benutzer zu einer Webseite außerhalb von Teams weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-218">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="73ea9-219">Do: Markieren Sie Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="73ea9-219">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="73ea9-220">Messaging Erweiterungen sind nicht immer leicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-220">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="73ea9-221">Fügen Sie Screenshots zur Verwendung in Ihrer APP-Detailseite hinzu.</span><span class="sxs-lookup"><span data-stu-id="73ea9-221">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="73ea9-222">Wenn Ihre APP auch einen bot enthält, können Sie die Hilfedokumentation zur Messaging Erweiterung in eine bot-Willkommens Tour einbeziehen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-222">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="73ea9-223">Vorlagen hinzu</span><span class="sxs-lookup"><span data-stu-id="73ea9-223">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="73ea9-225">Do: Teams können einen Teil des Entwurfs bearbeiten, wenn möglich</span><span class="sxs-lookup"><span data-stu-id="73ea9-225">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="73ea9-226">Wenn es für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messaging Erweiterung erstellen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-226">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="73ea9-227">Microsoft Teams rendert diese Erweiterungstypen mit integrierter Gestaltung und Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="73ea9-227">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="73ea9-229">Nicht: bettet die gesamte app in ein Aufgabenmodul ein.</span><span class="sxs-lookup"><span data-stu-id="73ea9-229">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="73ea9-230">Wenn Ihre Messaging-Erweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul einfach, und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="73ea9-230">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="73ea9-231">Designs</span><span class="sxs-lookup"><span data-stu-id="73ea9-231">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="73ea9-233">Do: nutzen Sie die Vorteile von Microsoft Teams-Farb Token</span><span class="sxs-lookup"><span data-stu-id="73ea9-233">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="73ea9-234">Jedes Microsoft Teams-Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="73ea9-234">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="73ea9-235">Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a> in Ihrem Design.</span><span class="sxs-lookup"><span data-stu-id="73ea9-235">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="73ea9-237">Nicht: Farb Werte mit festem Code</span><span class="sxs-lookup"><span data-stu-id="73ea9-237">Don't: Hard code color values</span></span>

<span data-ttu-id="73ea9-238">Wenn Sie keine Microsoft Teams-Farb Token verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit zum Verwalten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-238">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="73ea9-239">Aktionen</span><span class="sxs-lookup"><span data-stu-id="73ea9-239">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="73ea9-241">Do: Aktionsbefehle einschließen, die im Kontext sinnvoll sind</span><span class="sxs-lookup"><span data-stu-id="73ea9-241">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="73ea9-242">Nachrichten Aktionen sollten sich auf das beziehen, was ein Benutzer sucht.</span><span class="sxs-lookup"><span data-stu-id="73ea9-242">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="73ea9-243">Stellen Sie beispielsweise Benutzern eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mit dem Text im Beitrag eines anderen Benutzers bereit.</span><span class="sxs-lookup"><span data-stu-id="73ea9-243">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="73ea9-245">Nicht: Aktionsbefehle einbeziehen, die nicht kontextbezogen sind</span><span class="sxs-lookup"><span data-stu-id="73ea9-245">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="73ea9-246">Eine Nachrichtenaktion zum **Anzeigen des Dashboards** würde wahrscheinlich von den meisten Unterhaltungen getrennt erscheinen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-246">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="73ea9-247">Sucht</span><span class="sxs-lookup"><span data-stu-id="73ea9-247">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="73ea9-248">Do: Suchergebnisse bei der Eingabe anzeigen</span><span class="sxs-lookup"><span data-stu-id="73ea9-248">Do: Show search results while typing</span></span>

<span data-ttu-id="73ea9-249">Stellen Sie vorgeschlagene Suchergebnisse bereit, während Benutzer eingeben.</span><span class="sxs-lookup"><span data-stu-id="73ea9-249">Provide suggested search results while users type.</span></span> <span data-ttu-id="73ea9-250">Sie finden möglicherweise den benötigten Inhalt schneller bei minimaler Anzahl von Zeichen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-250">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="73ea9-251">Nicht: Benutzer müssen eine Abfrage senden</span><span class="sxs-lookup"><span data-stu-id="73ea9-251">Don't: Require users to submit a query</span></span>

<span data-ttu-id="73ea9-252">Sie können festlegen, dass Benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre APP zu senden.</span><span class="sxs-lookup"><span data-stu-id="73ea9-252">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="73ea9-253">Dies ist zwar für Ihren app-Dienste-Dienst möglicherweise einfacher, aber die Benutzer werden möglicherweise verwechselt, dass Sie beim eingeben keine Echtzeitsuchergebnisse sehen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-253">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="73ea9-254">Do: in Frage stellen von NULL-Term-Abfragen</span><span class="sxs-lookup"><span data-stu-id="73ea9-254">Do: Consider zero-term queries</span></span>

<span data-ttu-id="73ea9-255">Wenn ein Benutzer beispielsweise eine beliebige Person in das Suchfeld schreibt, zeigen Sie an, was diese zuletzt in ihrer App angezeigt haben.</span><span class="sxs-lookup"><span data-stu-id="73ea9-255">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="73ea9-256">Es ist möglich, dass Sie diese Inhalte in Ihre Unterhaltung einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="73ea9-256">It's possible that they want to insert that content into their conversation.</span></span>

## <a name="validate-your-design"></a><span data-ttu-id="73ea9-257">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="73ea9-257">Validate your design</span></span>

<span data-ttu-id="73ea9-258">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="73ea9-258">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73ea9-259">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="73ea9-259">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
