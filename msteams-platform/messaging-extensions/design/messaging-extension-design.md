---
title: Entwerfen Sie Ihre Messaging-Erweiterung
description: Erfahren Sie, wie Sie eine Teams-Messaging-Erweiterung entwerfen und das Microsoft Teams-UI-Kit erhalten.
keywords: Richtlinien für Teams-Entwurfsreferenzen für Messaging-Erweiterungs-Tips – Bewährte Methode
author: heath-hamilton
localization_priority: Priority
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: f4d1ba1e6e0b71b37e2b7b2d2a32fb729822ba1c
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037670"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="aa321-104">Entwerfen Sie Ihre Microsoft Teams-Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="aa321-105">Messagingerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne von der Konversation weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="aa321-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="aa321-106">Um Ihr App-Design zu steuern, beschreiben und veranschaulichen die folgenden Informationen, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="aa321-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="aa321-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="aa321-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="aa321-108">Umfassende Richtlinien für den Entwurf von Messaging-Erweiterungen, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.</span><span class="sxs-lookup"><span data-stu-id="aa321-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa321-109">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="aa321-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="aa321-110">Hinzufügen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-110">Add a messaging extension</span></span>

<span data-ttu-id="aa321-111">In den folgenden Teams-Kontexten können eine Messaging-Erweiterung hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="aa321-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="aa321-112">Aus dem Teams-Store.</span><span class="sxs-lookup"><span data-stu-id="aa321-112">From the Teams store.</span></span>
* <span data-ttu-id="aa321-113">In einem Kanal, Chat oder einer Besprechung (vor, während und nachher) in der Nähe des "Verfassen"-Felds.</span><span class="sxs-lookup"><span data-stu-id="aa321-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="aa321-114">Beachten Sie, dass wenn Sie eine Messaging-Erweiterung an einer dieser Stellen hinzufügen, nur Sie sie in diesem Kontext verwenden können.</span><span class="sxs-lookup"><span data-stu-id="aa321-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="aa321-115">Das folgende Beispiel zeigt, wie Sie eine Messaging-Erweiterung in einem Kanal hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="aa321-115">The following example shows how you add a messaging extension in a channel:</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-116">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Das Beispiel zeigt, wie eine Messaging-Erweiterung in der Nähe des &quot;Verfassen&quot;-Felds in einem Kanal hinzugefügt wird." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-118">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-118">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="Das Beispiel zeigt, wie eine Messaging-Erweiterung in der Nähe des &quot;Verfassen&quot;-Felds in einem Kanal auf Mobilgeräten hinzugefügt wird." border="false":::

---

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="aa321-120">Einrichten einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-120">Set up a messaging extension</span></span>

<span data-ttu-id="aa321-121">Die Authentifizierung ist nicht obligatorisch, aber wenn Ihre App zum Beispiel eine Art Ticketverfolgungstool ist, müssen Sie sich Benutzer möglicherweise anmelden, um die Messaging-Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa321-121">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="aa321-122">Aus Gründen der Konsistenz zwischen Teams-Apps können Sie den Anmeldebildschirm nicht anpassen.</span><span class="sxs-lookup"><span data-stu-id="aa321-122">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="aa321-123">Wenn Sie die Authentifizierung mit einmaligem Anmelden (Single Sign-On, SSO) verwenden, werden Benutzer automatisch angemeldet.</span><span class="sxs-lookup"><span data-stu-id="aa321-123">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-124">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm der Messaging-Erweiterung mit einer Anmeldeschaltfläche." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-126">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-126">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm der Messaging-Erweiterung mit einer Anmeldeschaltfläche auf Mobilgeräten." border="false":::

---

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="aa321-128">Typen von Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="aa321-128">Types of messaging extensions</span></span>

<span data-ttu-id="aa321-129">Messaging-Erweiterungen können Suchbefehle, Aktionsbefehle oder beides aufweisen.</span><span class="sxs-lookup"><span data-stu-id="aa321-129">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="aa321-130">Ihre Befehle hängen von den Features Ihrer App und davon ab, wie diese in Teams-Anwendungsfälle passen.</span><span class="sxs-lookup"><span data-stu-id="aa321-130">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="aa321-131">Suchbefehle</span><span class="sxs-lookup"><span data-stu-id="aa321-131">Search commands</span></span>

<span data-ttu-id="aa321-132">Mit Suchbefehlen können Benutzer Ihre Messaging-Erweiterung dazu nutzen, schnell externe Inhalte zu finden und in eine Nachricht einzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa321-132">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="aa321-133">Suchbefehle werden häufig im "Verfassen"-Feld zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="aa321-133">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="aa321-134">Sie können z. B. eine Diskussion beginnen oder etwas zu einer Diskussion hinzufügen, indem Sie einen Teil des Inhalts teilen – ohne Teams verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="aa321-134">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-135">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-135">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messaging-Erweiterung, die über das &quot;Verfassen&quot;-Feld gestartet wurde." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-137">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-137">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messaging-Erweiterung, die über das &quot;Verfassen&quot;-Feld auf mobilen Geräten gestartet wurde." border="false":::

---

#### <a name="compose-box-layout-options"></a><span data-ttu-id="aa321-139">Layoutoptionen für das "Verfassen"-Feld </span><span class="sxs-lookup"><span data-stu-id="aa321-139">Compose box layout options</span></span>

<span data-ttu-id="aa321-140">Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messaging-Erweiterung, einschließlich [Listen- und Rasteransichten](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span><span class="sxs-lookup"><span data-stu-id="aa321-140">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse von Messaging-Erweiterung." border="false":::

### <a name="action-commands"></a><span data-ttu-id="aa321-142">Aktionsbefehle</span><span class="sxs-lookup"><span data-stu-id="aa321-142">Action commands</span></span>

<span data-ttu-id="aa321-143">Aktionsbefehle ermöglichen es Personen, Aktionen auszulösen und Anforderungen in externen Diensten in Teams zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="aa321-143">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="aa321-144">Wenn Ihre App beispielsweise Bestellungen nachverfolgt, kann ein Benutzer eine neue Bestellung erstellen, indem er den Inhalt der Nachricht eines Kollegen direkt in seinem Chat verwendet.</span><span class="sxs-lookup"><span data-stu-id="aa321-144">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="aa321-145">Aktionsbasierte Messaging-Erweiterungen erfordern häufig, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines Modals ausfüllen müssen.</span><span class="sxs-lookup"><span data-stu-id="aa321-145">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="aa321-146">Sie können diese Erfahrungen mit [Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa321-146">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="aa321-147">Öffnen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-147">Open a messaging extension</span></span>

<span data-ttu-id="aa321-148">Das "Verfassen"-Feld und Nachrichten oder Beiträge sind die primären Kontexte, in denen Benutzer Messaging-Erweiterungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa321-148">The compose box and messages or posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="aa321-149">Über das "Verfassen"-Feld</span><span class="sxs-lookup"><span data-stu-id="aa321-149">From the compose box</span></span>

<span data-ttu-id="aa321-150">Nach dem Hinzufügen können Benutzer Ihre Messaging-Erweiterung öffnen, indem sie ihr App-Symbol unter dem "Verfassen"-Feld auswählen.</span><span class="sxs-lookup"><span data-stu-id="aa321-150">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="aa321-151">In diesen Beispielen verfügt die Erweiterung über Such- und Aktionsbefehle.</span><span class="sxs-lookup"><span data-stu-id="aa321-151">In these examples, the extension has search and action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung über das &quot;Verfassen&quot;-Feld öffnen." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-154">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung über das &quot;Verfassen&quot;-Feld auf Mobilgeräten öffnen." border="false":::

---

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="aa321-156">Aus einer Chatnachricht oder einem Kanalbeitrag</span><span class="sxs-lookup"><span data-stu-id="aa321-156">From a chat message or channel post</span></span>

Nach dem Hinzufügen können Benutzer das Symbol **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chatnachricht oder im Kanalbeitrag auswählen, um die Aktionsbefehle Ihrer Erweiterung zu finden. <span data-ttu-id="aa321-158">Ihre Erweiterung wird möglicherweise basierend auf der Nutzung unter **Weitere Aktionen** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="aa321-158">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="aa321-159">Unterstützung für weitere Aktionen aus einer Chatnachricht oder einem Kanalbeitrag ist auf der mobilen Microsoft Teams-Plattform nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="aa321-159">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="aa321-160">Chatnachricht</span><span class="sxs-lookup"><span data-stu-id="aa321-160">Chat message</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-161">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-161">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung aus einer Chatnachricht öffnen." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-163">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-163">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-chat-post.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung aus einem Chatbeitrag auf mobilen Geräten öffnen." border="false":::

---
':::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
':::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
---

## <a name="use-a-messaging-extension"></a><span data-ttu-id="aa321-165">Verwenden einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-165">Use a messaging extension</span></span>

<span data-ttu-id="aa321-166">In den folgenden Szenarien wird veranschaulicht, wie Benutzer Messaging-Erweiterungen in erster Linie verwenden.</span><span class="sxs-lookup"><span data-stu-id="aa321-166">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="aa321-167">Einfügen von Inhalt in eine Nachricht</span><span class="sxs-lookup"><span data-stu-id="aa321-167">Insert content into a message</span></span>

<span data-ttu-id="aa321-168">**1. Wählen Sie eine Messaging-Erweiterung aus**.</span><span class="sxs-lookup"><span data-stu-id="aa321-168">**1. Select a messaging extension**.</span></span> <span data-ttu-id="aa321-169">Benutzer können über das "Verfassen"-Feld nach dem Inhalt suchen, den sie freigeben möchten.</span><span class="sxs-lookup"><span data-stu-id="aa321-169">Users can search for the content they want to share from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der nach Inhalten sucht, die aus dem &quot;Verfassen&quot;-Feld eingefügt werden sollen." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-172">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der auf einem Mobilgerät über das &quot;Verfassen&quot;-Feld nach Inhalten sucht, die eingefügt werden sollen." border="false":::

---

<span data-ttu-id="aa321-174">**2. Inhalt einfügen**.</span><span class="sxs-lookup"><span data-stu-id="aa321-174">**2. Insert content**.</span></span> <span data-ttu-id="aa321-175">Nach der Veröffentlichung können andere Personen auf den Inhalt antworten oder diesen auswählen, um weitere Informationen in Ihrer App anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="aa321-175">Once posted, others can reply or select the content to see more information in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-176">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-176">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer Inhalte in einer Kanalunterhaltung postet." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-178">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-178">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät Inhalte in einer Kanalunterhaltung postet." border="false":::

---

### <a name="take-action-on-a-message"></a><span data-ttu-id="aa321-180">Aktionen für eine Nachricht ausführen</span><span class="sxs-lookup"><span data-stu-id="aa321-180">Take action on a message</span></span>

<span data-ttu-id="aa321-181">**1. Wählen Sie eine Messaging-Erweiterung aus**.</span><span class="sxs-lookup"><span data-stu-id="aa321-181">**1. Select a messaging extension**.</span></span> <span data-ttu-id="aa321-182">Ihre App kann einen oder mehrere Aktionsbefehle enthalten.</span><span class="sxs-lookup"><span data-stu-id="aa321-182">Your app can include one or more action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-183">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-183">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Aktionsbefehl für die Messaging-Erweiterung auswählt." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-185">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-185">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät einen Aktionsbefehl für die Messaging-Erweiterung auswählt." border="false":::

---

<span data-ttu-id="aa321-187">**2. Führen Sie die Aktion aus**.</span><span class="sxs-lookup"><span data-stu-id="aa321-187">**2. Complete the action**.</span></span> <span data-ttu-id="aa321-188">Ihre App kann alle Inhalte oder Daten empfangen und verarbeiten, die von der Nachrichtenaktion gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="aa321-188">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="aa321-189">Dadurch können Benutzer in ihrer Unterhaltung bleiben und sich keine Gedanken über die direkte Eingabe von Informationen in Ihrer App machen, wie im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="aa321-189">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-190">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-190">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel für das Ausführen von Aktionen für eine Nachricht." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-192">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-192">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-complete-action-command.png" alt-text="Beispiel für das Ausführen von Aktionen für eine Nachricht auf einem Mobilgerät." border="false":::

---

### <a name="preview-links"></a><span data-ttu-id="aa321-194">Vorschaulinks</span><span class="sxs-lookup"><span data-stu-id="aa321-194">Preview links</span></span>

<span data-ttu-id="aa321-195">Messaging-Erweiterungen ermöglichen es Ihnen auch, Rich-Links aus einer erkannten URL in eine Nachricht einzufügen. (Diese Funktion wird als[Entfalten von Links](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="aa321-195">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="aa321-196">**1. Fügen Sie einen erkannten Link** in das "Verfassen"-Feld ein.</span><span class="sxs-lookup"><span data-stu-id="aa321-196">**1. Paste a recognized link** in the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-197">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-197">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Link in das &quot;Verfassen&quot;-Feld eingibt." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-199">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-199">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät einen Link in das &quot;Verfassen&quot;-Feld eingibt." border="false":::

---

<span data-ttu-id="aa321-201">**2. Inhalt einfügen**.</span><span class="sxs-lookup"><span data-stu-id="aa321-201">**2. Insert content**.</span></span> <span data-ttu-id="aa321-202">Wenn Ihre App die URL im "Verfassen"-Feld erkennt, rendert sie den Link als Karte, die eine inhaltsreiche Vorschau des Webinhalts bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="aa321-202">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="aa321-203">(Weitere Informationen finden Sie unter [Entwurfsrichtlinien für Adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md).)</span><span class="sxs-lookup"><span data-stu-id="aa321-203">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-204">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-204">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="aa321-206">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-206">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL auf einem Mobilgerät umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird." border="false":::

---

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="aa321-208">Verwalten einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-208">Manage a messaging extension</span></span>

<span data-ttu-id="aa321-209">Benutzer können Ihre Messaging-Erweiterung anheften, entfernen oder konfigurieren, wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken.</span><span class="sxs-lookup"><span data-stu-id="aa321-209">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="aa321-210">Anatomie</span><span class="sxs-lookup"><span data-stu-id="aa321-210">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="aa321-211">Messaging-Erweiterung im "Verfassen"-Feld</span><span class="sxs-lookup"><span data-stu-id="aa321-211">Messaging extension in the compose box</span></span>

<span data-ttu-id="aa321-212">Das folgende Beispiel ist eine Messaging-Erweiterung, die über das "Verfassen"-Feld geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="aa321-212">The following example is a messaging extension opened from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="aa321-213">Desktop</span><span class="sxs-lookup"><span data-stu-id="aa321-213">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung zeigt die UI-Anatomie einer Messaging-Erweiterung im Feld &quot;Verfassen&quot;." border="false":::

|<span data-ttu-id="aa321-215">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aa321-215">Counter</span></span>|<span data-ttu-id="aa321-216">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aa321-216">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aa321-217">1</span><span class="sxs-lookup"><span data-stu-id="aa321-217">1</span></span>|<span data-ttu-id="aa321-218">**App-Logo**: Farbsymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="aa321-218">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="aa321-219">2</span><span class="sxs-lookup"><span data-stu-id="aa321-219">2</span></span>|<span data-ttu-id="aa321-220">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="aa321-220">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="aa321-221">3</span><span class="sxs-lookup"><span data-stu-id="aa321-221">3</span></span>|<span data-ttu-id="aa321-222">**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Messaging-Erweiterung (sofern vorhanden).</span><span class="sxs-lookup"><span data-stu-id="aa321-222">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="aa321-223">4</span><span class="sxs-lookup"><span data-stu-id="aa321-223">4</span></span>|<span data-ttu-id="aa321-224">**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="aa321-224">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="aa321-225">5</span><span class="sxs-lookup"><span data-stu-id="aa321-225">5</span></span>|<span data-ttu-id="aa321-226">**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.</span><span class="sxs-lookup"><span data-stu-id="aa321-226">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="aa321-227">6</span><span class="sxs-lookup"><span data-stu-id="aa321-227">6</span></span>|<span data-ttu-id="aa321-228">**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).</span><span class="sxs-lookup"><span data-stu-id="aa321-228">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="aa321-229">7</span><span class="sxs-lookup"><span data-stu-id="aa321-229">7</span></span>|<span data-ttu-id="aa321-230">**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="aa321-230">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="aa321-231">Im folgenden Beispiel wird das Listenlayout verwendet (Rasterlayout ist eine weitere Option).</span><span class="sxs-lookup"><span data-stu-id="aa321-231">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="aa321-232">8</span><span class="sxs-lookup"><span data-stu-id="aa321-232">8</span></span>|<span data-ttu-id="aa321-233">**App-Logo**: Gliederungssymbol Ihres App-Logos.</span><span class="sxs-lookup"><span data-stu-id="aa321-233">**App logo**: Outline icon of your app logo.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="aa321-234">Mobil</span><span class="sxs-lookup"><span data-stu-id="aa321-234">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Abbildung zeigt die UI-Anatomie einer Messaging-Erweiterung im Feld &quot;Verfassen&quot;auf einem Mobilgerät." border="false":::

|<span data-ttu-id="aa321-236">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aa321-236">Counter</span></span>|<span data-ttu-id="aa321-237">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aa321-237">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aa321-238">1</span><span class="sxs-lookup"><span data-stu-id="aa321-238">1</span></span>|<span data-ttu-id="aa321-239">**App-Name**: Vollständiger Name Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="aa321-239">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="aa321-240">2</span><span class="sxs-lookup"><span data-stu-id="aa321-240">2</span></span>|<span data-ttu-id="aa321-241">**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Messaging-Erweiterung (sofern vorhanden).</span><span class="sxs-lookup"><span data-stu-id="aa321-241">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="aa321-242">3</span><span class="sxs-lookup"><span data-stu-id="aa321-242">3</span></span>|<span data-ttu-id="aa321-243">**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="aa321-243">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="aa321-244">4</span><span class="sxs-lookup"><span data-stu-id="aa321-244">4</span></span>|<span data-ttu-id="aa321-245">**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.</span><span class="sxs-lookup"><span data-stu-id="aa321-245">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="aa321-246">5</span><span class="sxs-lookup"><span data-stu-id="aa321-246">5</span></span>|<span data-ttu-id="aa321-247">**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).</span><span class="sxs-lookup"><span data-stu-id="aa321-247">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="aa321-248">6</span><span class="sxs-lookup"><span data-stu-id="aa321-248">6</span></span>|<span data-ttu-id="aa321-249">**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="aa321-249">**App content**: Primarily to display search results.</span></span>|

---

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="aa321-250">Menü "Verwalten der Messaging-Erweiterung"</span><span class="sxs-lookup"><span data-stu-id="aa321-250">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung zeigt die UI-Anatomie eines &quot;Verwalten der Messaging-Erweiterung&quot;-Menüs." border="false":::

|<span data-ttu-id="aa321-252">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aa321-252">Counter</span></span>|<span data-ttu-id="aa321-253">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aa321-253">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aa321-254">1</span><span class="sxs-lookup"><span data-stu-id="aa321-254">1</span></span>|<span data-ttu-id="aa321-255">**Lösen sie**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.</span><span class="sxs-lookup"><span data-stu-id="aa321-255">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="aa321-256">2</span><span class="sxs-lookup"><span data-stu-id="aa321-256">2</span></span>|<span data-ttu-id="aa321-257">**Entfernen**: Entfernt die Messaging-Erweiterung aus dem Kanal, Chat oder der Besprechung.</span><span class="sxs-lookup"><span data-stu-id="aa321-257">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="aa321-258">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="aa321-258">Best practices</span></span>

<span data-ttu-id="aa321-259">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa321-259">Use these recommendations to create a quality app experience.</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="aa321-260">Setup und allgemeine Nutzung</span><span class="sxs-lookup"><span data-stu-id="aa321-260">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für Setup und allgemeine Nutzung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="aa321-262">Was Sie tun sollten: Integration mit einmaligem Anmelden</span><span class="sxs-lookup"><span data-stu-id="aa321-262">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="aa321-263">Einmaliges Anmelden vereinfacht, beschleunigt und schützt den Anmeldevorgang.</span><span class="sxs-lookup"><span data-stu-id="aa321-263">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="aa321-264">Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messaging-Erweiterung zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="aa321-264">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit einmaligem Anmelden." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="aa321-266">Was Sie nicht tun sollten: Benutzer aus der Unterhaltung entfernen</span><span class="sxs-lookup"><span data-stu-id="aa321-266">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="aa321-267">Messaging-Erweiterungen sind Tastenkombinationen, die den Kontextwechsel reduzieren sollen.</span><span class="sxs-lookup"><span data-stu-id="aa321-267">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="aa321-268">Ihre Erweiterung sollte Benutzer beispielsweise nicht zu einer Webseite außerhalb von Teams weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="aa321-268">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="aa321-269">Was Sie tun sollten: Hervorheben Ihrer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="aa321-269">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="aa321-270">Messaging-Erweiterungen sind nicht immer leicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="aa321-270">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="aa321-271">Fügen Sie Screenshots zur Verwendungsweise auf der Detailseite Ihrer App ein.</span><span class="sxs-lookup"><span data-stu-id="aa321-271">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="aa321-272">Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation zur Messaging-Erweiterung in eine Bot-Willkommenstour aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="aa321-272">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="aa321-273">Vorlagen</span><span class="sxs-lookup"><span data-stu-id="aa321-273">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für Vorlagen." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="aa321-275">Was Sie tun sollten: Lassen Sie Teams nach Möglichkeit einen Teil der Entwurfsarbeit erledigen</span><span class="sxs-lookup"><span data-stu-id="aa321-275">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="aa321-276">Wenn es für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messaging-Erweiterung erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa321-276">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="aa321-277">Teams rendert diese Arten von Erweiterungen mit integriertem Design und Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="aa321-277">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Verarbeitung von Entwurfsarbeiten." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="aa321-279">Was Sie nicht tun sollten: Einbetten der gesamten App in ein Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="aa321-279">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="aa321-280">Wenn Ihre Messaging-Erweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul schlicht, und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="aa321-280">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="aa321-281">Design</span><span class="sxs-lookup"><span data-stu-id="aa321-281">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für Design." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="aa321-283">Was Sie tun sollten: Teams-Farbtoken nutzen</span><span class="sxs-lookup"><span data-stu-id="aa321-283">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="aa321-284">Jedes Teams-Design verfügt über ein eigenes Farbschema.</span><span class="sxs-lookup"><span data-stu-id="aa321-284">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="aa321-285">Um Designänderungen automatisch zu verarbeiten, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.</span><span class="sxs-lookup"><span data-stu-id="aa321-285">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="aa321-287">Was Sie nicht tun sollten: Hartcodieren von Farbwerten</span><span class="sxs-lookup"><span data-stu-id="aa321-287">Don't: Hard code color values</span></span>

<span data-ttu-id="aa321-288">Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit für die Verwaltung.</span><span class="sxs-lookup"><span data-stu-id="aa321-288">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="aa321-289">Aktionen</span><span class="sxs-lookup"><span data-stu-id="aa321-289">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="aa321-291">Was Sie tun sollten: Aktionsbefehle einschließen, die im Kontext sinnvoll sind</span><span class="sxs-lookup"><span data-stu-id="aa321-291">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="aa321-292">Nachrichtenaktionen sollten sich auf das beziehen, was ein Benutzer sieht.</span><span class="sxs-lookup"><span data-stu-id="aa321-292">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="aa321-293">Geben Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder Arbeitselements mithilfe des Texts in einem Beitrag einer Person an.</span><span class="sxs-lookup"><span data-stu-id="aa321-293">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="aa321-295">Was Sie nicht tun sollten: Aktionsbefehle einschließen, die nicht kontextbezogen sind</span><span class="sxs-lookup"><span data-stu-id="aa321-295">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="aa321-296">Eine Nachrichtenaktion zum **Anzeigen Ihres Dashboards** scheint wahrscheinlich von den meisten Unterhaltungen getrennt zu sein.</span><span class="sxs-lookup"><span data-stu-id="aa321-296">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="aa321-297">Suchvorgänge</span><span class="sxs-lookup"><span data-stu-id="aa321-297">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="aa321-298">Was Sie tun sollten: Suchergebnisse während der Eingabe anzeigen</span><span class="sxs-lookup"><span data-stu-id="aa321-298">Do: Show search results while typing</span></span>

<span data-ttu-id="aa321-299">Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="aa321-299">Provide suggested search results while users type.</span></span> <span data-ttu-id="aa321-300">Möglicherweise finden sie so den benötigten Inhalt schneller mit einer minimalen Anzahl von Zeichen.</span><span class="sxs-lookup"><span data-stu-id="aa321-300">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="aa321-301">Was Sie nicht tun sollten: Benutzer müssen eine Abfrage übermitteln</span><span class="sxs-lookup"><span data-stu-id="aa321-301">Don't: Require users to submit a query</span></span>

<span data-ttu-id="aa321-302">Sie können festlegen, dass Benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre App zu senden.</span><span class="sxs-lookup"><span data-stu-id="aa321-302">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="aa321-303">Obwohl dies für Ihren App-Services-Dienst einfacher sein kann, sind Benutzer möglicherweise verwirrt, dass sie während der Texteingabe keine Echtzeitsuchergebnisse sehen.</span><span class="sxs-lookup"><span data-stu-id="aa321-303">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="aa321-304">Was Sie tun sollten: Erwägen Sie Nullausdrucksabfragen</span><span class="sxs-lookup"><span data-stu-id="aa321-304">Do: Consider zero-term queries</span></span>

<span data-ttu-id="aa321-305">Bevor ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angesehen hat.</span><span class="sxs-lookup"><span data-stu-id="aa321-305">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="aa321-306">Es ist möglich, dass sie diesen Inhalt in ihre Unterhaltung einfügen möchten.</span><span class="sxs-lookup"><span data-stu-id="aa321-306">It's possible that they want to insert that content into their conversation.</span></span>
