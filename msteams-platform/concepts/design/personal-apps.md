---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie Teams persönliche App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: b3f08c39a7900b80fb46d167fae8d9e8bdbcc574
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101555"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="7227b-103">Entwerfen Ihrer persönlichen App für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7227b-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="7227b-104">Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein.</span><span class="sxs-lookup"><span data-stu-id="7227b-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="7227b-105">Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, andere Mal bietet sie dem Benutzer eine Vogelperspektive über alles, was ihnen selbst ist, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="7227b-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that's theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="7227b-106">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Personen persönliche Apps hinzufügen, verwenden und verwalten Teams.</span><span class="sxs-lookup"><span data-stu-id="7227b-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="7227b-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="7227b-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="7227b-108">Umfassende Richtlinien für das Design persönlicher Apps, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="7227b-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="7227b-109">Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="7227b-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7227b-110">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="7227b-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="7227b-111">Hinzufügen einer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="7227b-111">Add a personal app</span></span>

<span data-ttu-id="7227b-112">Sie können eine persönliche App aus dem Teams Store (AppSource) oder  dem App-Flyout hinzufügen, indem Sie auf der linken Seite von Teams das Symbol Mehr auswählen (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="7227b-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="7227b-114">Verwenden einer persönlichen App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="7227b-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="7227b-115">Mit einem privaten Arbeitsbereich können Sie App-Inhalte anzeigen, die für Sie an einem zentralen Ort von Bedeutung sind, ohne Teams.</span><span class="sxs-lookup"><span data-stu-id="7227b-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="7227b-116">(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen Registerkartenfunktion.)*](../../build-your-first-app/build-personal-tab.md)</span><span class="sxs-lookup"><span data-stu-id="7227b-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="7227b-117">Anatomie: Persönliche App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="7227b-117">Anatomy: Personal app (private workspace)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="7227b-119">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="7227b-119">Counter</span></span>|<span data-ttu-id="7227b-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7227b-120">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="7227b-121">A</span><span class="sxs-lookup"><span data-stu-id="7227b-121">A</span></span>|<span data-ttu-id="7227b-122">**App-Attributierung:** Ihr App-Logo und -Name.</span><span class="sxs-lookup"><span data-stu-id="7227b-122">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="7227b-123">B</span><span class="sxs-lookup"><span data-stu-id="7227b-123">B</span></span>|<span data-ttu-id="7227b-124">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="7227b-124">**Tabs**: Provides navigation for your personal app.</span></span> <span data-ttu-id="7227b-125">Fügen Sie z. B. eine **Registerkarte Informationen** oder **Hilfe** ein.</span><span class="sxs-lookup"><span data-stu-id="7227b-125">For example, include an **About** or **Help** tab.</span></span>|
|<span data-ttu-id="7227b-126">C</span><span class="sxs-lookup"><span data-stu-id="7227b-126">C</span></span>|<span data-ttu-id="7227b-127">**Popupansicht:** Pusht Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.</span><span class="sxs-lookup"><span data-stu-id="7227b-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="7227b-128">D</span><span class="sxs-lookup"><span data-stu-id="7227b-128">D</span></span>|<span data-ttu-id="7227b-129">**Weitere Menü**: Enthält zusätzliche App-Informationen und -Optionen.</span><span class="sxs-lookup"><span data-stu-id="7227b-129">**More menu**: Includes additional app information and options.</span></span> <span data-ttu-id="7227b-130">(Alternativ können Sie **Einstellungen** Registerkarte erstellen.)</span><span class="sxs-lookup"><span data-stu-id="7227b-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="7227b-132">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="7227b-132">Counter</span></span>|<span data-ttu-id="7227b-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7227b-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="7227b-134">A</span><span class="sxs-lookup"><span data-stu-id="7227b-134">A</span></span>|<span data-ttu-id="7227b-135">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="7227b-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="7227b-136">1</span><span class="sxs-lookup"><span data-stu-id="7227b-136">1</span></span>|<span data-ttu-id="7227b-137">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="7227b-137">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="7227b-138">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="7227b-138">Designing with UI templates</span></span>

<span data-ttu-id="7227b-139">Verwenden Sie eine der folgenden Teams, um Ihre persönliche Registerkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="7227b-139">Use one of the following Teams UI templates to help design your personal tab:</span></span>

* <span data-ttu-id="7227b-140">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="7227b-140">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="7227b-141">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7227b-141">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="7227b-142">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="7227b-142">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="7227b-143">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="7227b-143">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="7227b-144">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="7227b-144">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="7227b-145">[Linkes](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Navigationsmenü: Die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="7227b-145">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="7227b-146">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="7227b-146">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="7227b-147">Verwenden einer persönlichen App (Bot)</span><span class="sxs-lookup"><span data-stu-id="7227b-147">Use a personal app (bot)</span></span>

<span data-ttu-id="7227b-148">Persönliche Apps können einen Bot für Einzelunterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf Ihrer Artboard veröffentlicht).</span><span class="sxs-lookup"><span data-stu-id="7227b-148">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="7227b-149">Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7227b-149">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="7227b-150">Anatomie: Persönliche App (Bot)</span><span class="sxs-lookup"><span data-stu-id="7227b-150">Anatomy: Personal app (bot)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|<span data-ttu-id="7227b-152">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="7227b-152">Counter</span></span>|<span data-ttu-id="7227b-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7227b-153">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="7227b-154">A</span><span class="sxs-lookup"><span data-stu-id="7227b-154">A</span></span>|<span data-ttu-id="7227b-155">**Registerkarte "Bot":** Fügen Sie beispielsweise eine Registerkarte **Chat** ein, um auf Botunterhaltungen und -benachrichtigungen zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7227b-155">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="7227b-156">B</span><span class="sxs-lookup"><span data-stu-id="7227b-156">B</span></span>|<span data-ttu-id="7227b-157">**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).</span><span class="sxs-lookup"><span data-stu-id="7227b-157">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="7227b-158">C</span><span class="sxs-lookup"><span data-stu-id="7227b-158">C</span></span>|<span data-ttu-id="7227b-159">**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.</span><span class="sxs-lookup"><span data-stu-id="7227b-159">**Compose box**: Input field for sending messages to the bot.</span></span>|

## <a name="manage-a-personal-tab"></a><span data-ttu-id="7227b-160">Verwalten einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7227b-160">Manage a personal tab</span></span>

<span data-ttu-id="7227b-161">Auf der linken Seite Teams Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen anheften, entfernen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="7227b-161">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen App." border="false":::

## <a name="best-practices"></a><span data-ttu-id="7227b-163">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="7227b-163">Best practices</span></span>

<span data-ttu-id="7227b-164">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7227b-164">Use these recommendations to create a quality app experience.</span></span>

### <a name="tab-priority"></a><span data-ttu-id="7227b-165">Registerkartenpriorität</span><span class="sxs-lookup"><span data-stu-id="7227b-165">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="7227b-166">Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7227b-166">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="7227b-167">Bei einer reaktionsschnellen Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7227b-167">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine persönliche App, in der die relevantesten Inhalte auf der ersten Registerkarte angezeigt werden." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="7227b-169">Don't: Lead with secondary content or metadata</span><span class="sxs-lookup"><span data-stu-id="7227b-169">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="7227b-170">Wie bei einer standardmäßigen Web-App sollte die Registerkartennavigation in einer Reihenfolge ausgeführt werden, die die primären Features Ihrer App sinnvoll macht.</span><span class="sxs-lookup"><span data-stu-id="7227b-170">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine persönliche App, die mit sekundären Inhalten oder Metadaten führt." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="7227b-172">Registerkartenhierarchie</span><span class="sxs-lookup"><span data-stu-id="7227b-172">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="7227b-173">Do: Registerkarten sollten die gleiche Hierarchie haben und wichtige App-Seiten darstellen</span><span class="sxs-lookup"><span data-stu-id="7227b-173">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="7227b-174">Ihre Registerkarten sollten die primären Features und Inhalte Ihrer App kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="7227b-174">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="7227b-175">Bei einer reaktionsschnellen Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7227b-175">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine persönliche App mit Registerkarten gleicher Hierarchie." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="7227b-177">Don't: Include different levels of hierarchy</span><span class="sxs-lookup"><span data-stu-id="7227b-177">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="7227b-178">Ihre Inhalte sollten in einer logischen Reihenfolge ausgeführt werden, die Benutzern dabei hilft, den Inhalt sinnvoll zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="7227b-178">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="7227b-179">Wenn Sie über zwei Registerkarten verfügen, die eng miteinander verbunden sind, sollten Sie sie in einer Registerkarte kombinieren.</span><span class="sxs-lookup"><span data-stu-id="7227b-179">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine persönliche App mit unterschiedlichen Hierarchieebenen." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="7227b-181">Erste Ausführung</span><span class="sxs-lookup"><span data-stu-id="7227b-181">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="7227b-182">Do: Include a first-run experience</span><span class="sxs-lookup"><span data-stu-id="7227b-182">Do: Include a first-run experience</span></span>

<span data-ttu-id="7227b-183">Bei der ersten Verwendung einer persönlichen App sollte mindestens ein Willkommensbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7227b-183">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="7227b-184">Beschreiben Sie für Bots, was Ihr Bot tun kann, und stellen Sie schnelle Aktionen wie z. B. eine Anmeldeschaltfläche zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="7227b-184">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Beispiel zeigt, was während einer persönlichen App beim ersten Ausführen zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Ein weiteres Beispiel zeigt, was während einer persönlichen App-Erstlauferfahrung zu tun ist." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="7227b-187">Don't: Start with a blank screen</span><span class="sxs-lookup"><span data-stu-id="7227b-187">Don't: Start with a blank screen</span></span>

<span data-ttu-id="7227b-188">Benutzer sind möglicherweise verwirrt, wenn beim ersten Ausführen Ihrer App nichts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7227b-188">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Beispiel zeigt, was während der ersten Ausführung einer persönlichen App nicht zu tun ist." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="7227b-190">Personalisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="7227b-190">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="7227b-191">Do: Aggregieren von für einen Benutzer relevanten App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="7227b-191">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="7227b-192">Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen persönlichen Bot handele, zeigen Sie Inhalte an, die sich nur auf die Aktivitäten eines Benutzers in Ihrer App bezogen haben.</span><span class="sxs-lookup"><span data-stu-id="7227b-192">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Ein weiteres Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="7227b-195">Don't: Unrelated or overly broad content anzeigen</span><span class="sxs-lookup"><span data-stu-id="7227b-195">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="7227b-196">Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu der ein Benutzer nicht gehört.</span><span class="sxs-lookup"><span data-stu-id="7227b-196">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="7227b-197">Persönliche Botinhalte sollten sich auf die Person konzentrieren, nicht auf eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="7227b-197">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Ein weiteres Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="7227b-200">Komplexe App-Features</span><span class="sxs-lookup"><span data-stu-id="7227b-200">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="7227b-201">Do: Benutzern den Zugriff auf komplexe Features in einem Browser erlauben</span><span class="sxs-lookup"><span data-stu-id="7227b-201">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="7227b-202">Ihre App sollte sich auf Kernaufgaben in Teams konzentrieren, Sie können jedoch weiterhin die vollständige, eigenständige App in einem Browser anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7227b-202">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt, wie Komplexe App-Features mit einer persönlichen App verwendet werden." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="7227b-204">Don't: Include your entire app</span><span class="sxs-lookup"><span data-stu-id="7227b-204">Don’t: Include your entire app</span></span>

<span data-ttu-id="7227b-205">Wenn Sie Ihre App nicht speziell für Teams erstellt haben, verfügen Sie wahrscheinlich über Features, die in einem Tool für die Zusammenarbeit keinen Sinn machen.</span><span class="sxs-lookup"><span data-stu-id="7227b-205">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Beispiel zeigt, wie komplexe App-Features nicht mit einer persönlichen App zu verarbeiten sind." border="false":::

## <a name="see-also"></a><span data-ttu-id="7227b-207">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7227b-207">See also</span></span>

<span data-ttu-id="7227b-208">Diese anderen Entwurfsrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="7227b-208">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="7227b-209">Entwerfen Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7227b-209">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="7227b-210">Entwerfen eines Bots</span><span class="sxs-lookup"><span data-stu-id="7227b-210">Designing you bot</span></span>](../../bots/design/bots.md)
