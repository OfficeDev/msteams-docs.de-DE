---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie Teams persönliche App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 83fad746d71dd196f6efa6526f5c6c28ceac9e20
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644892"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="718c0-103">Entwerfen Ihrer persönlichen App für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="718c0-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="718c0-104">Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein.</span><span class="sxs-lookup"><span data-stu-id="718c0-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="718c0-105">Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, andere Mal bietet sie dem Benutzer eine Vogelperspektive über alles, was ihnen selbst ist, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="718c0-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that's theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="718c0-106">Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Personen persönliche Apps hinzufügen, verwenden und verwalten Teams.</span><span class="sxs-lookup"><span data-stu-id="718c0-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="718c0-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="718c0-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="718c0-108">Umfassende Richtlinien für das Design persönlicher Apps, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="718c0-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="718c0-109">Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="718c0-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="718c0-110">Holen Sie sich das Microsoft Teams-UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="718c0-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="718c0-111">Hinzufügen einer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="718c0-111">Add a personal app</span></span>

<span data-ttu-id="718c0-112">Sie können eine persönliche App aus dem Teams Store (AppSource) oder  dem App-Flyout hinzufügen, indem Sie auf der linken Seite von Teams das Symbol Mehr auswählen (siehe das folgende Beispiel).</span><span class="sxs-lookup"><span data-stu-id="718c0-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="718c0-114">Verwenden einer persönlichen App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="718c0-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="718c0-115">Mit einem privaten Arbeitsbereich können Sie App-Inhalte anzeigen, die für Sie an einem zentralen Ort von Bedeutung sind, ohne Teams.</span><span class="sxs-lookup"><span data-stu-id="718c0-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="718c0-116">(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen Registerkartenfunktion.)*](../../build-your-first-app/build-personal-tab.md)</span><span class="sxs-lookup"><span data-stu-id="718c0-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="718c0-117">Anatomie: Persönliche App (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="718c0-117">Anatomy: Personal app (private workspace)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="718c0-118">Desktop</span><span class="sxs-lookup"><span data-stu-id="718c0-118">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="718c0-120">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-120">Counter</span></span>|<span data-ttu-id="718c0-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-121">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-122">A</span><span class="sxs-lookup"><span data-stu-id="718c0-122">A</span></span>|<span data-ttu-id="718c0-123">**App-Attributierung:** Ihr App-Logo und -Name.</span><span class="sxs-lookup"><span data-stu-id="718c0-123">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="718c0-124">B</span><span class="sxs-lookup"><span data-stu-id="718c0-124">B</span></span>|<span data-ttu-id="718c0-125">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="718c0-125">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="718c0-126">C</span><span class="sxs-lookup"><span data-stu-id="718c0-126">C</span></span>|<span data-ttu-id="718c0-127">**Popupansicht:** Pusht Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.</span><span class="sxs-lookup"><span data-stu-id="718c0-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="718c0-128">D</span><span class="sxs-lookup"><span data-stu-id="718c0-128">D</span></span>|<span data-ttu-id="718c0-129">**Weitere Menü**: Enthält zusätzliche App-Optionen und Informationen.</span><span class="sxs-lookup"><span data-stu-id="718c0-129">**More menu**: Includes additional app options and information.</span></span> <span data-ttu-id="718c0-130">(Alternativ können Sie **Einstellungen** Registerkarte erstellen.)</span><span class="sxs-lookup"><span data-stu-id="718c0-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="718c0-132">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-132">Counter</span></span>|<span data-ttu-id="718c0-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-134">A</span><span class="sxs-lookup"><span data-stu-id="718c0-134">A</span></span>|<span data-ttu-id="718c0-135">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="718c0-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="718c0-136">1</span><span class="sxs-lookup"><span data-stu-id="718c0-136">1</span></span>|<span data-ttu-id="718c0-137">**iframe**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="718c0-137">**iframe**: Displays your app content.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="718c0-138">Mobil</span><span class="sxs-lookup"><span data-stu-id="718c0-138">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="718c0-140">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-140">Counter</span></span>|<span data-ttu-id="718c0-141">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-141">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-142">A</span><span class="sxs-lookup"><span data-stu-id="718c0-142">A</span></span>|<span data-ttu-id="718c0-143">**App-Attribution:** Ihr App-Name.</span><span class="sxs-lookup"><span data-stu-id="718c0-143">**App attribution**: Your app name.</span></span>|
|<span data-ttu-id="718c0-144">B</span><span class="sxs-lookup"><span data-stu-id="718c0-144">B</span></span>|<span data-ttu-id="718c0-145">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="718c0-145">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="718c0-146">C</span><span class="sxs-lookup"><span data-stu-id="718c0-146">C</span></span>|<span data-ttu-id="718c0-147">**Weitere Menü**: Enthält zusätzliche App-Optionen und Informationen.</span><span class="sxs-lookup"><span data-stu-id="718c0-147">**More menu**: Includes additional app options and information.</span></span>|
|<span data-ttu-id="718c0-148">D</span><span class="sxs-lookup"><span data-stu-id="718c0-148">D</span></span>|<span data-ttu-id="718c0-149">**Primäre Navigation:** Stellt navigation zu Ihrer App andere Hauptfunktionen Teams zur Seite.</span><span class="sxs-lookup"><span data-stu-id="718c0-149">**Primary navigation**: Provides navigation to your app other main Teams features.</span></span>|

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="718c0-151">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-151">Counter</span></span>|<span data-ttu-id="718c0-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-153">A</span><span class="sxs-lookup"><span data-stu-id="718c0-153">A</span></span>|<span data-ttu-id="718c0-154">**Registerkarten**: Bietet Navigation für Ihre persönliche App.</span><span class="sxs-lookup"><span data-stu-id="718c0-154">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="718c0-155">1</span><span class="sxs-lookup"><span data-stu-id="718c0-155">1</span></span>|<span data-ttu-id="718c0-156">**webview**: Zeigt Ihre App-Inhalte an.</span><span class="sxs-lookup"><span data-stu-id="718c0-156">**webview**: Displays your app content.</span></span>|

---

### <a name="designing-with-ui-templates-and-advanced-components"></a><span data-ttu-id="718c0-157">Entwerfen mit Benutzeroberflächenvorlagen und erweiterten Komponenten</span><span class="sxs-lookup"><span data-stu-id="718c0-157">Designing with UI templates and advanced components</span></span>

<span data-ttu-id="718c0-158">Verwenden Sie eine der folgenden Teams und Komponenten, um Ihre persönliche Registerkarte zu entwerfen:</span><span class="sxs-lookup"><span data-stu-id="718c0-158">Use one of the following Teams templates and components to help design your personal tab:</span></span>

* <span data-ttu-id="718c0-159">[Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="718c0-159">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="718c0-160">[Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="718c0-160">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="718c0-161">[Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="718c0-161">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="718c0-162">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.</span><span class="sxs-lookup"><span data-stu-id="718c0-162">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="718c0-163">[Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="718c0-163">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="718c0-164">[Linkes](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Navigationsmenü: Die linke Navigationskomponente kann hilfreich sein, wenn Ihre persönliche App eine gewisse Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="718c0-164">[Left nav](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your personal app requires some navigation.</span></span> <span data-ttu-id="718c0-165">Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="718c0-165">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="718c0-166">Verwenden einer persönlichen App (Bot)</span><span class="sxs-lookup"><span data-stu-id="718c0-166">Use a personal app (bot)</span></span>

<span data-ttu-id="718c0-167">Persönliche Apps können einen Bot für Einzelunterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf Ihrer Artboard veröffentlicht).</span><span class="sxs-lookup"><span data-stu-id="718c0-167">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="718c0-168">Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="718c0-168">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="718c0-169">Anatomie: Persönliche App (Bot)</span><span class="sxs-lookup"><span data-stu-id="718c0-169">Anatomy: Personal app (bot)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="718c0-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="718c0-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|<span data-ttu-id="718c0-172">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-172">Counter</span></span>|<span data-ttu-id="718c0-173">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-173">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-174">A</span><span class="sxs-lookup"><span data-stu-id="718c0-174">A</span></span>|<span data-ttu-id="718c0-175">**Registerkarte "Bot":** Fügen Sie beispielsweise eine Registerkarte **Chat** ein, um auf Botunterhaltungen und -benachrichtigungen zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="718c0-175">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="718c0-176">B</span><span class="sxs-lookup"><span data-stu-id="718c0-176">B</span></span>|<span data-ttu-id="718c0-177">**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).</span><span class="sxs-lookup"><span data-stu-id="718c0-177">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="718c0-178">C</span><span class="sxs-lookup"><span data-stu-id="718c0-178">C</span></span>|<span data-ttu-id="718c0-179">**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.</span><span class="sxs-lookup"><span data-stu-id="718c0-179">**Compose box**: Input field for sending messages to the bot.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="718c0-180">Mobil</span><span class="sxs-lookup"><span data-stu-id="718c0-180">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|<span data-ttu-id="718c0-182">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="718c0-182">Counter</span></span>|<span data-ttu-id="718c0-183">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="718c0-183">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="718c0-184">A</span><span class="sxs-lookup"><span data-stu-id="718c0-184">A</span></span>|<span data-ttu-id="718c0-185">**Bot-Einstiegspunkt:** Einstiegspunkt für Benutzer, um auf das Botfeature in Ihrer persönlichen App zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="718c0-185">**Bot entry point**: Entry point for users to access the bot feature in your personal app.</span></span>|
|<span data-ttu-id="718c0-186">B</span><span class="sxs-lookup"><span data-stu-id="718c0-186">B</span></span>|<span data-ttu-id="718c0-187">**Schaltfläche "Zurück":** Führt Benutzer zurück zum privaten Arbeitsbereich.</span><span class="sxs-lookup"><span data-stu-id="718c0-187">**Back button**: Takes users back to the private workspace.</span></span>|
|<span data-ttu-id="718c0-188">C</span><span class="sxs-lookup"><span data-stu-id="718c0-188">C</span></span>|<span data-ttu-id="718c0-189">**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).</span><span class="sxs-lookup"><span data-stu-id="718c0-189">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="718c0-190">D</span><span class="sxs-lookup"><span data-stu-id="718c0-190">D</span></span>|<span data-ttu-id="718c0-191">**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.</span><span class="sxs-lookup"><span data-stu-id="718c0-191">**Compose box**: Input field for sending messages to the bot.</span></span>|

---

## <a name="manage-a-personal-tab"></a><span data-ttu-id="718c0-192">Verwalten einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="718c0-192">Manage a personal tab</span></span>

<span data-ttu-id="718c0-193">Auf der linken Seite Teams Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen anheften, entfernen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="718c0-193">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen App." border="false":::

## <a name="best-practices"></a><span data-ttu-id="718c0-195">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="718c0-195">Best practices</span></span>

<span data-ttu-id="718c0-196">Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="718c0-196">Use these recommendations to create a quality app experience.</span></span>

### <a name="tab-priority"></a><span data-ttu-id="718c0-197">Registerkartenpriorität</span><span class="sxs-lookup"><span data-stu-id="718c0-197">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="718c0-198">Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte</span><span class="sxs-lookup"><span data-stu-id="718c0-198">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="718c0-199">Bei einer reaktionsschnellen Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="718c0-199">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine persönliche App, in der die relevantesten Inhalte auf der ersten Registerkarte angezeigt werden." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="718c0-201">Don't: Lead with secondary content or metadata</span><span class="sxs-lookup"><span data-stu-id="718c0-201">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="718c0-202">Wie bei einer standardmäßigen Web-App sollte die Registerkartennavigation in einer Reihenfolge ausgeführt werden, die die primären Features Ihrer App sinnvoll macht.</span><span class="sxs-lookup"><span data-stu-id="718c0-202">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine persönliche App, die mit sekundären Inhalten oder Metadaten führt." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="718c0-204">Registerkartenhierarchie</span><span class="sxs-lookup"><span data-stu-id="718c0-204">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="718c0-205">Do: Registerkarten sollten die gleiche Hierarchie haben und wichtige App-Seiten darstellen</span><span class="sxs-lookup"><span data-stu-id="718c0-205">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="718c0-206">Ihre Registerkarten sollten die primären Features und Inhalte Ihrer App kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="718c0-206">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="718c0-207">Bei einer reaktionsschnellen Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="718c0-207">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine persönliche App mit Registerkarten gleicher Hierarchie." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="718c0-209">Don't: Include different levels of hierarchy</span><span class="sxs-lookup"><span data-stu-id="718c0-209">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="718c0-210">Ihre Inhalte sollten in einer logischen Reihenfolge ausgeführt werden, die Benutzern dabei hilft, den Inhalt sinnvoll zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="718c0-210">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="718c0-211">Wenn Sie über zwei Registerkarten verfügen, die eng miteinander verbunden sind, sollten Sie sie in einer Registerkarte kombinieren.</span><span class="sxs-lookup"><span data-stu-id="718c0-211">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine persönliche App mit unterschiedlichen Hierarchieebenen." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="718c0-213">Erste Ausführung</span><span class="sxs-lookup"><span data-stu-id="718c0-213">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="718c0-214">Do: Include a first-run experience</span><span class="sxs-lookup"><span data-stu-id="718c0-214">Do: Include a first-run experience</span></span>

<span data-ttu-id="718c0-215">Bei der ersten Verwendung einer persönlichen App sollte mindestens ein Willkommensbildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="718c0-215">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="718c0-216">Beschreiben Sie für Bots, was Ihr Bot tun kann, und stellen Sie schnelle Aktionen wie z. B. eine Anmeldeschaltfläche zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="718c0-216">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Beispiel zeigt, was während einer persönlichen App beim ersten Ausführen zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Ein weiteres Beispiel zeigt, was während einer persönlichen App-Erstlauferfahrung zu tun ist." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="718c0-219">Don't: Start with a blank screen</span><span class="sxs-lookup"><span data-stu-id="718c0-219">Don't: Start with a blank screen</span></span>

<span data-ttu-id="718c0-220">Benutzer sind möglicherweise verwirrt, wenn beim ersten Ausführen Ihrer App nichts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="718c0-220">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Beispiel zeigt, was während der ersten Ausführung einer persönlichen App nicht zu tun ist." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="718c0-222">Personalisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="718c0-222">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="718c0-223">Do: Aggregieren von für einen Benutzer relevanten App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="718c0-223">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="718c0-224">Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen persönlichen Bot handele, zeigen Sie Inhalte an, die sich nur auf die Aktivitäten eines Benutzers in Ihrer App bezogen haben.</span><span class="sxs-lookup"><span data-stu-id="718c0-224">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Ein weiteres Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="718c0-227">Don't: Unrelated or overly broad content anzeigen</span><span class="sxs-lookup"><span data-stu-id="718c0-227">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="718c0-228">Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu der ein Benutzer nicht gehört.</span><span class="sxs-lookup"><span data-stu-id="718c0-228">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="718c0-229">Persönliche Botinhalte sollten sich auf die Person konzentrieren, nicht auf eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="718c0-229">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Ein weiteres Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="718c0-232">Komplexe App-Features</span><span class="sxs-lookup"><span data-stu-id="718c0-232">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="718c0-233">Do: Benutzern den Zugriff auf komplexe Features in einem Browser erlauben</span><span class="sxs-lookup"><span data-stu-id="718c0-233">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="718c0-234">Ihre App sollte sich auf Kernaufgaben in Teams konzentrieren, Sie können jedoch weiterhin die vollständige, eigenständige App in einem Browser anzeigen.</span><span class="sxs-lookup"><span data-stu-id="718c0-234">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt, wie Komplexe App-Features mit einer persönlichen App verwendet werden." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="718c0-236">Don't: Include your entire app</span><span class="sxs-lookup"><span data-stu-id="718c0-236">Don’t: Include your entire app</span></span>

<span data-ttu-id="718c0-237">Wenn Sie Ihre App nicht speziell für Teams erstellt haben, verfügen Sie wahrscheinlich über Features, die in einem Tool für die Zusammenarbeit keinen Sinn machen.</span><span class="sxs-lookup"><span data-stu-id="718c0-237">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Beispiel zeigt, wie komplexe App-Features nicht mit einer persönlichen App zu verarbeiten sind." border="false":::

## <a name="see-also"></a><span data-ttu-id="718c0-239">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="718c0-239">See also</span></span>

<span data-ttu-id="718c0-240">Diese anderen Entwurfsrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="718c0-240">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="718c0-241">Entwerfen Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="718c0-241">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="718c0-242">Entwerfen eines Bots</span><span class="sxs-lookup"><span data-stu-id="718c0-242">Designing you bot</span></span>](../../bots/design/bots.md)
