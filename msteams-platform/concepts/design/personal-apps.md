---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie eine persönliche Microsoft Teams-App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 8302f3768034014ef5a446effeee0603afe4a5f4
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020758"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="aae2a-103">Entwerfen Ihrer persönlichen App für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="aae2a-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="aae2a-104">Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein.</span><span class="sxs-lookup"><span data-stu-id="aae2a-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="aae2a-105">Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, andere Mal bietet sie dem Benutzer eine Vogelperspektive über alles, was ihnen selbst ist, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="aae2a-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that's theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="aae2a-106">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Personen persönliche Apps in Teams hinzufügen, verwenden und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="aae2a-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="aae2a-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="aae2a-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="aae2a-108">Im Microsoft Teams UI Kit finden Sie umfassende Richtlinien für das Design persönlicher Apps, einschließlich Elemente, die Sie bei Bedarf packen und ändern können.</span><span class="sxs-lookup"><span data-stu-id="aae2a-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="aae2a-109">Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="aae2a-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aae2a-110">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="aae2a-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="aae2a-111">Hinzufügen einer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="aae2a-111">Add a personal app</span></span>

<span data-ttu-id="aae2a-112">Sie können eine persönliche App aus dem Teams Store (AppSource)  oder dem App-Flyout hinzufügen, indem Sie auf der linken Seite von Teams das Symbol Mehr auswählen (im folgenden Beispiel gezeigt).</span><span class="sxs-lookup"><span data-stu-id="aae2a-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="aae2a-114">Verwenden einer persönlichen App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="aae2a-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="aae2a-115">Mit einem privaten Arbeitsbereich können Sie App-Inhalte anzeigen, die für Sie an einem zentralen Ort von Bedeutung sind, ohne Teams zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="aae2a-116">(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen Registerkartenfunktion.)*](../../build-your-first-app/build-personal-tab.md)</span><span class="sxs-lookup"><span data-stu-id="aae2a-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="aae2a-117">Anatomie: Persönliche App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="aae2a-117">Anatomy: Personal app (private workspace)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="aae2a-119">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aae2a-119">Counter</span></span>|<span data-ttu-id="aae2a-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aae2a-120">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aae2a-121">A</span><span class="sxs-lookup"><span data-stu-id="aae2a-121">A</span></span>|<span data-ttu-id="aae2a-122">**App-Attributierung:** Ihr App-Logo und -Name.</span><span class="sxs-lookup"><span data-stu-id="aae2a-122">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="aae2a-123">B</span><span class="sxs-lookup"><span data-stu-id="aae2a-123">B</span></span>|<span data-ttu-id="aae2a-124">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="aae2a-124">**Tabs**: Provides navigation for your personal app.</span></span> <span data-ttu-id="aae2a-125">Fügen Sie z. B. eine **Registerkarte Informationen** oder **Hilfe** ein.</span><span class="sxs-lookup"><span data-stu-id="aae2a-125">For example, include an **About** or **Help** tab.</span></span>|
|<span data-ttu-id="aae2a-126">C</span><span class="sxs-lookup"><span data-stu-id="aae2a-126">C</span></span>|<span data-ttu-id="aae2a-127">**Popupansicht:** Pusht Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.</span><span class="sxs-lookup"><span data-stu-id="aae2a-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="aae2a-128">D</span><span class="sxs-lookup"><span data-stu-id="aae2a-128">D</span></span>|<span data-ttu-id="aae2a-129">**Weitere Menü**: Enthält zusätzliche App-Informationen und -Optionen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-129">**More menu**: Includes additional app information and options.</span></span> <span data-ttu-id="aae2a-130">(Alternativ können Sie Einstellungen **als** Registerkarte festlegen.)</span><span class="sxs-lookup"><span data-stu-id="aae2a-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="aae2a-132">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aae2a-132">Counter</span></span>|<span data-ttu-id="aae2a-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aae2a-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aae2a-134">A</span><span class="sxs-lookup"><span data-stu-id="aae2a-134">A</span></span>|<span data-ttu-id="aae2a-135">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="aae2a-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="aae2a-136">1</span><span class="sxs-lookup"><span data-stu-id="aae2a-136">1</span></span>|<span data-ttu-id="aae2a-137">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="aae2a-137">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="aae2a-138">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="aae2a-138">Designing with UI templates</span></span>

<span data-ttu-id="aae2a-139">Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Ihre persönliche Registerkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="aae2a-139">Use one of the following Teams UI templates to help design your personal tab:</span></span>

* <span data-ttu-id="aae2a-140">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-140">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="aae2a-141">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="aae2a-141">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="aae2a-142">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="aae2a-142">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="aae2a-143">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="aae2a-143">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="aae2a-144">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="aae2a-144">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="aae2a-145">[Linkes](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Navigationsmenü: Die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="aae2a-145">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="aae2a-146">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="aae2a-146">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="aae2a-147">Verwenden einer persönlichen App (Bot)</span><span class="sxs-lookup"><span data-stu-id="aae2a-147">Use a personal app (bot)</span></span>

<span data-ttu-id="aae2a-148">Persönliche Apps können einen Bot für Einzelunterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf Ihrer Artboard veröffentlicht).</span><span class="sxs-lookup"><span data-stu-id="aae2a-148">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="aae2a-149">Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="aae2a-149">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="aae2a-150">Anatomie: Persönliche App (Bot)</span><span class="sxs-lookup"><span data-stu-id="aae2a-150">Anatomy: Personal app (bot)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|<span data-ttu-id="aae2a-152">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="aae2a-152">Counter</span></span>|<span data-ttu-id="aae2a-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="aae2a-153">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="aae2a-154">A</span><span class="sxs-lookup"><span data-stu-id="aae2a-154">A</span></span>|<span data-ttu-id="aae2a-155">**Registerkarte "Bot":** Fügen Sie beispielsweise eine Registerkarte **Chat** ein, um auf Botunterhaltungen und -benachrichtigungen zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-155">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="aae2a-156">B</span><span class="sxs-lookup"><span data-stu-id="aae2a-156">B</span></span>|<span data-ttu-id="aae2a-157">**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).</span><span class="sxs-lookup"><span data-stu-id="aae2a-157">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="aae2a-158">C</span><span class="sxs-lookup"><span data-stu-id="aae2a-158">C</span></span>|<span data-ttu-id="aae2a-159">**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.</span><span class="sxs-lookup"><span data-stu-id="aae2a-159">**Compose box**: Input field for sending messages to the bot.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="aae2a-160">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="aae2a-160">Best practices</span></span>

### <a name="tab-priority"></a><span data-ttu-id="aae2a-161">Registerkartenpriorität</span><span class="sxs-lookup"><span data-stu-id="aae2a-161">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="aae2a-162">Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte</span><span class="sxs-lookup"><span data-stu-id="aae2a-162">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="aae2a-163">Bei einer reaktionsschnellen Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aae2a-163">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche Apps." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="aae2a-165">Don't: Lead with secondary content or metadata</span><span class="sxs-lookup"><span data-stu-id="aae2a-165">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="aae2a-166">Wie bei einer standardmäßigen Web-App sollte die Registerkartennavigation in einer Reihenfolge ausgeführt werden, die die primären Features Ihrer App sinnvoll macht.</span><span class="sxs-lookup"><span data-stu-id="aae2a-166">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel für eine bewährte Methode für eine persönliche App." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="aae2a-168">Registerkartenhierarchie</span><span class="sxs-lookup"><span data-stu-id="aae2a-168">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="aae2a-169">Do: Registerkarten sollten die gleiche Hierarchie haben und wichtige App-Seiten darstellen</span><span class="sxs-lookup"><span data-stu-id="aae2a-169">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="aae2a-170">Ihre Registerkarten sollten die primären Features und Inhalte Ihrer App kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="aae2a-170">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="aae2a-171">Bei einer reaktionsschnellen Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aae2a-171">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt bewährte Vorgehensweisen für persönliche Apps." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="aae2a-173">Don't: Include different levels of hierarchy</span><span class="sxs-lookup"><span data-stu-id="aae2a-173">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="aae2a-174">Ihre Inhalte sollten in einer logischen Reihenfolge ausgeführt werden, die Benutzern dabei hilft, den Inhalt sinnvoll zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-174">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="aae2a-175">Wenn Sie über zwei Registerkarten verfügen, die eng miteinander verbunden sind, sollten Sie sie in einer Registerkarte kombinieren.</span><span class="sxs-lookup"><span data-stu-id="aae2a-175">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche Apps an." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="aae2a-177">Erste Ausführung</span><span class="sxs-lookup"><span data-stu-id="aae2a-177">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="aae2a-178">Do: Include a first-run experience</span><span class="sxs-lookup"><span data-stu-id="aae2a-178">Do: Include a first-run experience</span></span>

<span data-ttu-id="aae2a-179">Bei der ersten Verwendung einer persönlichen App sollte mindestens ein Willkommensbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="aae2a-179">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="aae2a-180">Beschreiben Sie für Bots, was Ihr Bot tun kann, und stellen Sie schnelle Aktionen wie z. B. eine Anmeldeschaltfläche zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="aae2a-180">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Abbildung zeigt eine bewährte Methode für persönliche Apps." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Illustration einer bewährten Methode für eine persönliche App." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="aae2a-183">Don't: Start with a blank screen</span><span class="sxs-lookup"><span data-stu-id="aae2a-183">Don't: Start with a blank screen</span></span>

<span data-ttu-id="aae2a-184">Benutzer sind möglicherweise verwirrt, wenn beim ersten Ausführen Ihrer App nichts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="aae2a-184">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Abbildung zeigt eine bewährte Methode für persönliche Apps an." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="aae2a-186">Personalisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="aae2a-186">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="aae2a-187">Do: Aggregieren von für einen Benutzer relevanten App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="aae2a-187">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="aae2a-188">Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen persönlichen Bot handele, zeigen Sie Inhalte an, die sich nur auf die Aktivitäten eines Benutzers in Ihrer App bezogen haben.</span><span class="sxs-lookup"><span data-stu-id="aae2a-188">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel bietet eine bewährte Methode für persönliche Apps." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Das Beispiel zeigt eine bewährte Methode für persönliche Apps." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="aae2a-191">Don't: Unrelated or overly broad content anzeigen</span><span class="sxs-lookup"><span data-stu-id="aae2a-191">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="aae2a-192">Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu der ein Benutzer nicht gehört.</span><span class="sxs-lookup"><span data-stu-id="aae2a-192">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="aae2a-193">Persönliche Botinhalte sollten sich auf die Person konzentrieren, nicht auf eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="aae2a-193">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Offengelegt ist ein Beispiel für eine bewährte Methode für persönliche Apps." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche Apps." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="aae2a-196">Komplexe App-Features</span><span class="sxs-lookup"><span data-stu-id="aae2a-196">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="aae2a-197">Do: Benutzern den Zugriff auf komplexe Features in einem Browser erlauben</span><span class="sxs-lookup"><span data-stu-id="aae2a-197">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="aae2a-198">Ihre App sollte sich auf die Kernaufgaben in Teams konzentrieren, Sie können jedoch weiterhin die vollständige, eigenständige App in einem Browser anzeigen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-198">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt bewährte Vorgehensweisen für persönliche Apps." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="aae2a-200">Don't: Include your entire app</span><span class="sxs-lookup"><span data-stu-id="aae2a-200">Don’t: Include your entire app</span></span>

<span data-ttu-id="aae2a-201">Wenn Sie Ihre App nicht speziell für Teams erstellt haben, verfügen Sie wahrscheinlich über Features, die in einem Tool für die Zusammenarbeit keinen Sinn machen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-201">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Illustration bietet bewährte Vorgehensweisen für persönliche Apps." border="false":::

## <a name="manage-a-personal-tab"></a><span data-ttu-id="aae2a-203">Verwalten einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="aae2a-203">Manage a personal tab</span></span>

<span data-ttu-id="aae2a-204">Auf der linken Seite von Teams können Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen anheften, entfernen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="aae2a-204">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen App." border="false":::

## <a name="learn-more"></a><span data-ttu-id="aae2a-206">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aae2a-206">Learn more</span></span>

<span data-ttu-id="aae2a-207">Diese anderen Entwurfsrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="aae2a-207">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="aae2a-208">Entwerfen Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="aae2a-208">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="aae2a-209">Entwerfen eines Bots</span><span class="sxs-lookup"><span data-stu-id="aae2a-209">Designing you bot</span></span>](../../bots/design/bots.md)

## <a name="validate-your-design"></a><span data-ttu-id="aae2a-210">Validieren Ihres Designs</span><span class="sxs-lookup"><span data-stu-id="aae2a-210">Validate your design</span></span>

<span data-ttu-id="aae2a-211">Wenn Sie Ihre App in AppSource veröffentlichen möchten, sollten Sie die Entwurfsprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="aae2a-211">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aae2a-212">Überprüfen der Richtlinien zur Designvalidierung</span><span class="sxs-lookup"><span data-stu-id="aae2a-212">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
