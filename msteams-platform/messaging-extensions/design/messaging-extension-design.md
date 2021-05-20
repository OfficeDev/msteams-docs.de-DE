---
title: Entwerfen Ihrer Messagingerweiterung
description: Erfahren Sie, wie Sie eine Teams Messaging-Erweiterung entwerfen und das Microsoft Teams UI Kit abrufen.
keywords: Teams entwerfen Richtlinien referenzieren Messaging-Erweiterungen Tipps best Practice
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ed1f0f2eb2ce8d429a8a780bd2c4c4eb421d6d54
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566215"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="ef869-104">Entwerfen ihrer Microsoft Teams Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="ef869-105">Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln auf eine Nachricht, ohne von der Unterhaltung weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="ef869-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="ef869-106">Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="ef869-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="ef869-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="ef869-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="ef869-108">Umfassende Richtlinien für den Entwurf von Messagingerweiterungen, einschließlich Elementen, die Sie bei Bedarf aussuchen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="ef869-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef869-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="ef869-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="ef869-110">Hinzufügen einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-110">Add a messaging extension</span></span>

<span data-ttu-id="ef869-111">Sie können eine Messagingerweiterung in den folgenden Teams Kontexten hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="ef869-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="ef869-112">Aus dem Teams Store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="ef869-112">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="ef869-113">In einem Kanal, Chat oder Meeting (vorher, während und nach) in der Nähe des Verfassensfeldes.</span><span class="sxs-lookup"><span data-stu-id="ef869-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="ef869-114">Es ist erwähnenswert, wenn Sie eine Messaging-Erweiterung an einem dieser Orte hinzufügen, nur Sie können es in diesem Kontext verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef869-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="ef869-115">Das folgende Beispiel zeigt, wie Sie eine Messagingerweiterung in einem Kanal hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="ef869-115">The following example shows how you add a messaging extension in a channel:</span></span>

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Ein Beispiel zeigt, wie Sie eine Messagingerweiterung in der Nähe des Verfassensfeldes in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="ef869-117">Einrichten einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-117">Set up a messaging extension</span></span>

<span data-ttu-id="ef869-118">Die Authentifizierung ist nicht obligatorisch, aber wenn Ihre App so etwas wie ein Ticketverfolgungstool ist, müssen sich möglicherweise Personen anmelden, um die Messagingerweiterung verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="ef869-118">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="ef869-119">Aus Gründen der Konsistenz in Teams Apps können Sie den Anmeldebildschirm nicht anpassen.</span><span class="sxs-lookup"><span data-stu-id="ef869-119">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="ef869-120">Wenn Sie die SSO-Authentifizierung (Single Sign-On) verwenden, werden Benutzer automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="ef869-120">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm für die Messagingerweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="ef869-122">Arten von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="ef869-122">Types of messaging extensions</span></span>

<span data-ttu-id="ef869-123">Messagingerweiterungen können Suchbefehle, Aktionsbefehle oder beides haben.</span><span class="sxs-lookup"><span data-stu-id="ef869-123">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="ef869-124">Ihre Befehle hängen von den Funktionen Ihrer App ab und davon, wie diese in Teams Anwendungsfälle passen.</span><span class="sxs-lookup"><span data-stu-id="ef869-124">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="ef869-125">Suchbefehle</span><span class="sxs-lookup"><span data-stu-id="ef869-125">Search commands</span></span>

<span data-ttu-id="ef869-126">Mit Suchbefehlen können Benutzer Ihre Messaging-Erweiterung verwenden, um externe Inhalte schnell zu finden und in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="ef869-126">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="ef869-127">Suchbefehle werden häufig im Feld Verfassen zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="ef869-127">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="ef869-128">Sie können z. B. eine Diskussion starten oder hinzufügen, indem Sie einen Inhalt freigeben, ohne jemals Teams zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="ef869-128">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messagingerweiterung, die aus dem Verfassenfeld gestartet wurde." border="false":::

#### <a name="compose-box-layout-options"></a><span data-ttu-id="ef869-130">Layoutoptionen des Felds verfassen</span><span class="sxs-lookup"><span data-stu-id="ef869-130">Compose box layout options</span></span>

<span data-ttu-id="ef869-131">Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messagingerweiterungen, einschließlich [Listen- und Rasteransichten](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span><span class="sxs-lookup"><span data-stu-id="ef869-131">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse für Messagingerweiterungen." border="false":::

### <a name="action-commands"></a><span data-ttu-id="ef869-133">Aktionsbefehle</span><span class="sxs-lookup"><span data-stu-id="ef869-133">Action commands</span></span>

<span data-ttu-id="ef869-134">Aktionsbefehle ermöglichen es Benutzern, Aktionen auszulösen und Anforderungen in externen Diensten innerhalb Teams zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ef869-134">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="ef869-135">Wenn Ihre App beispielsweise Bestellungen nachverfolgt, kann ein Benutzer eine neue Bestellung mithilfe des Inhalts der Nachricht eines Kollegen direkt in seinem Chat erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef869-135">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="ef869-136">Aktionsbasierte Messagingerweiterungen erfordern häufig, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines Modals ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="ef869-136">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="ef869-137">Sie können diese Erfahrungen mit [Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef869-137">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="ef869-138">Öffnen einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-138">Open a messaging extension</span></span>

<span data-ttu-id="ef869-139">Das Verfassen-Feld und Nachrichten oder Beiträge sind die primären Kontexte, in denen Benutzer Messagingerweiterungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef869-139">The compose box and messages or posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="ef869-140">Aus der Verfassenbox</span><span class="sxs-lookup"><span data-stu-id="ef869-140">From the compose box</span></span>

<span data-ttu-id="ef869-141">Nach dem Zusatz können Benutzer Ihre Messagingerweiterung öffnen, indem sie Ihr App-Symbol unter dem Verfassen-Feld auswählen.</span><span class="sxs-lookup"><span data-stu-id="ef869-141">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="ef869-142">In diesem Beispiel verfügt die Erweiterung über Such- und Aktionsbefehle:</span><span class="sxs-lookup"><span data-stu-id="ef869-142">In this example, the extension has search and action commands:</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messagingerweiterung aus dem Verfassen-Feld öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="ef869-144">Von einer Chat-Nachricht oder einem Kanalbeitrag</span><span class="sxs-lookup"><span data-stu-id="ef869-144">From a chat message or channel post</span></span>

Nach dem Zusatz können Benutzer das Symbol **Mehr** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chat-Nachricht oder im Kanalbeitrag auswählen, um die Aktionsbefehle Ihrer Erweiterung zu finden. <span data-ttu-id="ef869-146">Ihre Erweiterung kann unter **Weitere Aktionen** basierend auf der Nutzung aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ef869-146">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="ef869-147">Unterstützung für weitere Aktionen von einer Chat-Nachricht oder einem Kanalbeitrag ist auf Microsoft Teams mobilen Plattform nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ef869-147">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="ef869-148">Chatnachricht</span><span class="sxs-lookup"><span data-stu-id="ef869-148">Chat message</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Ein Beispiel zeigt, wie sie eine Messagingerweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a><span data-ttu-id="ef869-150">Channel-Post</span><span class="sxs-lookup"><span data-stu-id="ef869-150">Channel post</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Ein Beispiel zeigt, wie sie eine Messagingerweiterung über einen Kanalbeitrag öffnen." border="false":::

## <a name="use-a-messaging-extension"></a><span data-ttu-id="ef869-152">Verwenden einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-152">Use a messaging extension</span></span>

<span data-ttu-id="ef869-153">Die folgenden Szenarien zeigen die primäre Verwendung von Messagingerweiterungen.</span><span class="sxs-lookup"><span data-stu-id="ef869-153">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="ef869-154">Einfügen von Inhalten in eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="ef869-154">Insert content into a message</span></span>

<span data-ttu-id="ef869-155">**1. Wählen Sie eine Messaging-Erweiterung**.</span><span class="sxs-lookup"><span data-stu-id="ef869-155">**1. Select a messaging extension**.</span></span> <span data-ttu-id="ef869-156">Benutzer können im Verfassen-Feld nach dem Inhalt suchen, den sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="ef869-156">Users can search for the content they want to share from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der nach Inhalten sucht, die aus dem Verfassenfeld eingefügt werden sollen." border="false":::

<span data-ttu-id="ef869-158">**2. Fügen Sie Inhalt** ein.</span><span class="sxs-lookup"><span data-stu-id="ef869-158">**2. Insert content**.</span></span> <span data-ttu-id="ef869-159">Nach der Veröffentlichung können andere Personen antworten oder den Inhalt auswählen, um weitere Informationen in Ihrer App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ef869-159">Once posted, others can reply or select the content to see more information in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Ein Beispiel zeigt einen Benutzer, der Inhalte in einer Kanalunterhaltung postet." border="false":::

### <a name="take-action-on-a-message"></a><span data-ttu-id="ef869-161">Maßnahmen für eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="ef869-161">Take action on a message</span></span>

<span data-ttu-id="ef869-162">**1. Wählen Sie eine Messaging-Erweiterung**.</span><span class="sxs-lookup"><span data-stu-id="ef869-162">**1. Select a messaging extension**.</span></span> <span data-ttu-id="ef869-163">Ihre App kann einen oder mehrere Aktionsbefehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="ef869-163">Your app can include one or more action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Aktionsbefehl für die Messagingerweiterung auswählt." border="false":::

<span data-ttu-id="ef869-165">**2. Schließen Sie die Aktion ab.**</span><span class="sxs-lookup"><span data-stu-id="ef869-165">**2. Complete the action**.</span></span> <span data-ttu-id="ef869-166">Ihre App kann alle Inhalte oder Daten empfangen und verarbeiten, die von der Nachrichtenaktion gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ef869-166">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="ef869-167">Auf diese Weise können Benutzer in ihrer Unterhaltung bleiben und sich im folgenden Beispiel keine Gedanken über die direkte Eingabe von Informationen in Ihrer App machen.</span><span class="sxs-lookup"><span data-stu-id="ef869-167">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel, wie Sie Maßnahmen für eine Nachricht ergreifen." border="false":::

### <a name="preview-links"></a><span data-ttu-id="ef869-169">Vorschaulinks</span><span class="sxs-lookup"><span data-stu-id="ef869-169">Preview links</span></span>

<span data-ttu-id="ef869-170">Messagingerweiterungen ermöglichen es Ihnen auch, Rich Links von einer erkannten URL in eine Nachricht einzufügen (diese Funktion wird als [Link-Entfurling](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet.)</span><span class="sxs-lookup"><span data-stu-id="ef869-170">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="ef869-171">**1. Fügen Sie einen erkannten Link** in das Verfassen-Feld ein.</span><span class="sxs-lookup"><span data-stu-id="ef869-171">**1. Paste a recognized link** in the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Link in das Kompostfeld einfügt." border="false":::

<span data-ttu-id="ef869-173">**2. Fügen Sie Inhalt** ein.</span><span class="sxs-lookup"><span data-stu-id="ef869-173">**2. Insert content**.</span></span> <span data-ttu-id="ef869-174">Wenn Ihre App die URL im Verfassen-Feld erkennt, wird der Link als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bietet.</span><span class="sxs-lookup"><span data-stu-id="ef869-174">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="ef869-175">(Weitere Informationen finden Sie unter [Designrichtlinien für Adaptive Karten.)](../../task-modules-and-cards/cards/design-effective-cards.md)</span><span class="sxs-lookup"><span data-stu-id="ef869-175">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL, da sie von Ihrer App erkannt wird, einige umfangreiche Inhalte in das Verfassen-Feld enthält." border="false":::

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="ef869-177">Verwalten einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-177">Manage a messaging extension</span></span>

<span data-ttu-id="ef869-178">Wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken, können Benutzer Ihre Messagingerweiterung anheften, entfernen oder konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ef869-178">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="ef869-179">Anatomie</span><span class="sxs-lookup"><span data-stu-id="ef869-179">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="ef869-180">Messagingerweiterung im Verfassenfeld</span><span class="sxs-lookup"><span data-stu-id="ef869-180">Messaging extension in the compose box</span></span>

<span data-ttu-id="ef869-181">Das folgende Beispiel ist eine Messagingerweiterung, die aus dem Verfassen-Feld geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="ef869-181">The following example is a messaging extension opened from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung, die die Ui-Anatomie einer Messagingerweiterung im Verfassen-Feld zeigt." border="false":::

|<span data-ttu-id="ef869-183">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ef869-183">Counter</span></span>|<span data-ttu-id="ef869-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ef869-184">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ef869-185">1</span><span class="sxs-lookup"><span data-stu-id="ef869-185">1</span></span>|<span data-ttu-id="ef869-186">**App-Logo**: Farbsymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="ef869-186">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="ef869-187">2</span><span class="sxs-lookup"><span data-stu-id="ef869-187">2</span></span>|<span data-ttu-id="ef869-188">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="ef869-188">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="ef869-189">3</span><span class="sxs-lookup"><span data-stu-id="ef869-189">3</span></span>|<span data-ttu-id="ef869-190">**Aktionsbefehls-Menüsymbol (optional):** Öffnet eine Liste von Aktionsbefehlen für Ihre Messagingerweiterung (falls vorhanden).</span><span class="sxs-lookup"><span data-stu-id="ef869-190">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="ef869-191">4 </span><span class="sxs-lookup"><span data-stu-id="ef869-191">4</span></span>|<span data-ttu-id="ef869-192">**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="ef869-192">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="ef869-193">5 </span><span class="sxs-lookup"><span data-stu-id="ef869-193">5</span></span>|<span data-ttu-id="ef869-194">**Tab-Menü (optional):** Bietet mehrere Inhaltskategorien.</span><span class="sxs-lookup"><span data-stu-id="ef869-194">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="ef869-195">6 </span><span class="sxs-lookup"><span data-stu-id="ef869-195">6</span></span>|<span data-ttu-id="ef869-196">**Aktionsbefehlsmenü (optional)**: Zeigt eine Liste der Aktionsbefehle an (falls Sie irgendwelche angeben).</span><span class="sxs-lookup"><span data-stu-id="ef869-196">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="ef869-197">7 </span><span class="sxs-lookup"><span data-stu-id="ef869-197">7</span></span>|<span data-ttu-id="ef869-198">**App-Inhalt**: In erster Linie zum Anzeigen von Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="ef869-198">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="ef869-199">Das Beispiel hier ist die Verwendung des Listenlayouts (Rasterlayout ist eine andere Option).</span><span class="sxs-lookup"><span data-stu-id="ef869-199">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="ef869-200">8 </span><span class="sxs-lookup"><span data-stu-id="ef869-200">8</span></span>|<span data-ttu-id="ef869-201">**App-Logo**: Gliederungssymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="ef869-201">**App logo**: Outline icon of your app logo.</span></span>|

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="ef869-202">Messagingerweiterungsverwaltungsmenü</span><span class="sxs-lookup"><span data-stu-id="ef869-202">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung, die die Ui-Anatomie eines Messagingerweiterungsverwaltungsmenüs zeigt." border="false":::

|<span data-ttu-id="ef869-204">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="ef869-204">Counter</span></span>|<span data-ttu-id="ef869-205">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ef869-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="ef869-206">1</span><span class="sxs-lookup"><span data-stu-id="ef869-206">1</span></span>|<span data-ttu-id="ef869-207">**Unpin**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="ef869-207">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="ef869-208">2</span><span class="sxs-lookup"><span data-stu-id="ef869-208">2</span></span>|<span data-ttu-id="ef869-209">**Entfernen**: Entfernt die Messaging-Erweiterung aus dem Kanal, Chat oder Besprechung.</span><span class="sxs-lookup"><span data-stu-id="ef869-209">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="ef869-210">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="ef869-210">Best practices</span></span>

<span data-ttu-id="ef869-211">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef869-211">Use these recommendations to create a quality app experience.</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="ef869-212">Setup und allgemeine Verwendung</span><span class="sxs-lookup"><span data-stu-id="ef869-212">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für Einrichtung und allgemeine Verwendung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="ef869-214">Do: Integration mit Single-Sign on</span><span class="sxs-lookup"><span data-stu-id="ef869-214">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="ef869-215">SSO erleichtert, schneller und sicherer den Anmeldevorgang.</span><span class="sxs-lookup"><span data-stu-id="ef869-215">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="ef869-216">Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich nicht erneut anmelden, um auf die Messagingerweiterung zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="ef869-216">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit Single-Sign On." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="ef869-218">Nicht: Benutzer aus der Unterhaltung mitnehmen</span><span class="sxs-lookup"><span data-stu-id="ef869-218">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="ef869-219">Messagingerweiterungen sind Verknüpfungen, die die Kontextumschaltung reduzieren sollen.</span><span class="sxs-lookup"><span data-stu-id="ef869-219">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="ef869-220">Ihre Erweiterung sollte benutzernicht z. B. zu einer Webseite außerhalb Teams.</span><span class="sxs-lookup"><span data-stu-id="ef869-220">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="ef869-221">Tun: Markieren Sie Ihre Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="ef869-221">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="ef869-222">Messagingerweiterungen sind nicht immer leicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="ef869-222">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="ef869-223">Fügen Sie Screenshots zur Verwendung in Ihrer App-Detailseite ein.</span><span class="sxs-lookup"><span data-stu-id="ef869-223">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="ef869-224">Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation für messaging-Erweiterungen in eine Bot-Willkommenstour einschließen.</span><span class="sxs-lookup"><span data-stu-id="ef869-224">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="ef869-225">Templating</span><span class="sxs-lookup"><span data-stu-id="ef869-225">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für die Vorlagenerstellung." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="ef869-227">Tun: Lassen Sie Teams einige der Entwurfsarbeiten nach Möglichkeit erledigen</span><span class="sxs-lookup"><span data-stu-id="ef869-227">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="ef869-228">Wenn dies für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messagingerweiterung erstellen.</span><span class="sxs-lookup"><span data-stu-id="ef869-228">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="ef869-229">Teams rendert diese Arten von Erweiterungen mit integrierter Thesierung und Zugänglichkeit.</span><span class="sxs-lookup"><span data-stu-id="ef869-229">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Handhabung von Konstruktionsarbeiten." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="ef869-231">Nicht: Einbetten Der gesamten App in ein Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="ef869-231">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="ef869-232">Wenn Ihre Messagingerweiterung Aktionsbefehle erfordert, halten Sie das Taskmodul einfach und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="ef869-232">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="ef869-233">Designs</span><span class="sxs-lookup"><span data-stu-id="ef869-233">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für die Themen." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="ef869-235">Tun: Nutzen Sie Teams Farbtoken</span><span class="sxs-lookup"><span data-stu-id="ef869-235">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="ef869-236">Jedes Teams-Thema hat sein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="ef869-236">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="ef869-237">Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.</span><span class="sxs-lookup"><span data-stu-id="ef869-237">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="ef869-239">Nicht: Harte Code-Farbwerte</span><span class="sxs-lookup"><span data-stu-id="ef869-239">Don't: Hard code color values</span></span>

<span data-ttu-id="ef869-240">Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.</span><span class="sxs-lookup"><span data-stu-id="ef869-240">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="ef869-241">Aktionen</span><span class="sxs-lookup"><span data-stu-id="ef869-241">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="ef869-243">Tun: Einschließen von Aktionsbefehlen, die im Kontext sinnvoll sind</span><span class="sxs-lookup"><span data-stu-id="ef869-243">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="ef869-244">Nachrichtenaktionen sollten sich auf das beziehen, was ein Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="ef869-244">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="ef869-245">Stellen Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mithilfe des Texts im Beitrag einer Person bereit.</span><span class="sxs-lookup"><span data-stu-id="ef869-245">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="ef869-247">Nicht: Einschließen von Aktionsbefehlen, die nicht kontextbezogen sind</span><span class="sxs-lookup"><span data-stu-id="ef869-247">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="ef869-248">Eine Nachrichtenaktion zum **Anzeigen Ihres Dashboards** scheint wahrscheinlich von den meisten Unterhaltungen getrennt zu sein.</span><span class="sxs-lookup"><span data-stu-id="ef869-248">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="ef869-249">Sucht</span><span class="sxs-lookup"><span data-stu-id="ef869-249">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="ef869-250">Tun: Anzeigen von Suchergebnissen während der Eingabe</span><span class="sxs-lookup"><span data-stu-id="ef869-250">Do: Show search results while typing</span></span>

<span data-ttu-id="ef869-251">Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer eingeben.</span><span class="sxs-lookup"><span data-stu-id="ef869-251">Provide suggested search results while users type.</span></span> <span data-ttu-id="ef869-252">Sie können den Inhalt, den sie benötigen, schneller mit minimaler Anzahl von Zeichen finden.</span><span class="sxs-lookup"><span data-stu-id="ef869-252">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="ef869-253">Nicht: Benutzer müssen eine Abfrage senden</span><span class="sxs-lookup"><span data-stu-id="ef869-253">Don't: Require users to submit a query</span></span>

<span data-ttu-id="ef869-254">Sie können Benutzer dazu veranlassen, eine Taste zu drücken oder eine Schaltfläche auszuwählen, um Abfragen an Ihre App zu senden.</span><span class="sxs-lookup"><span data-stu-id="ef869-254">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="ef869-255">Auch wenn dies bei Ihrem App-Dienst einfacher sein kann, können die Personen verwirrt sein, dass sie beim Eingeben keine Echtzeit-Suchergebnisse sehen.</span><span class="sxs-lookup"><span data-stu-id="ef869-255">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="ef869-256">Tun: Betrachten Sie Null-Term-Abfragen</span><span class="sxs-lookup"><span data-stu-id="ef869-256">Do: Consider zero-term queries</span></span>

<span data-ttu-id="ef869-257">Wenn ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angezeigt hat.</span><span class="sxs-lookup"><span data-stu-id="ef869-257">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="ef869-258">Es ist möglich, dass sie diesen Inhalt in ihre Unterhaltung einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="ef869-258">It's possible that they want to insert that content into their conversation.</span></span>
