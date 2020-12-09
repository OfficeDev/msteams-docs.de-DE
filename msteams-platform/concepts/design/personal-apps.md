---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie eine persönliche Teams-App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 971071be9f345815f5461646d7970efdf05fd5c4
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604990"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="3d2db-103">Entwerfen Ihrer persönlichen App für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3d2db-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="3d2db-104">Eine persönliche App kann ein bot, ein privater Arbeitsbereich oder beides sein.</span><span class="sxs-lookup"><span data-stu-id="3d2db-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="3d2db-105">Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, ein anderes Mal bietet es dem Benutzer eine Vogelperspektive auf alles, was Ihnen gehört, wenn die APP als Registerkarte in mehreren Kanälen konfiguriert wurde.</span><span class="sxs-lookup"><span data-stu-id="3d2db-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that’s theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="3d2db-106">Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie personenbezogene apps in Microsoft Teams hinzugefügt, verwendet und verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="3d2db-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="3d2db-107">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="3d2db-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="3d2db-108">Umfassende persönliche App-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="3d2db-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="3d2db-109">Das UI Kit enthält auch wichtige Themen wie Barrierefreiheit und Anpassungsfähigkeit, die hier nicht behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="3d2db-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d2db-110">Abrufen des Microsoft Teams UI Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="3d2db-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="3d2db-111">Hinzufügen einer persönlichen App</span><span class="sxs-lookup"><span data-stu-id="3d2db-111">Add a personal app</span></span>

<span data-ttu-id="3d2db-112">Sie können eine persönliche App aus dem teamstore (AppSource) oder dem App-Flyout hinzufügen, indem Sie das Symbol **Weitere** auf der linken Seite von Teams auswählen (siehe folgendes Beispiel).</span><span class="sxs-lookup"><span data-stu-id="3d2db-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="3d2db-114">Verwenden einer persönlichen app (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="3d2db-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="3d2db-115">Mit einem privaten Arbeitsbereich können Sie für Sie bedeutsame App-Inhalte an einem zentralen Ort anzeigen, ohne Teams zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="3d2db-116">(Implementierungs Hinweis: der private Arbeitsbereich basiert auf der [*persönlichen Registerkarten*](../../build-your-first-app/build-personal-tab.md) Funktion.)</span><span class="sxs-lookup"><span data-stu-id="3d2db-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="3d2db-117">Anatomie: persönliche app (privater Arbeitsbereich)</span><span class="sxs-lookup"><span data-stu-id="3d2db-117">Anatomy: Personal app (private workspace)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponenten Anatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="3d2db-119">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="3d2db-119">Counter</span></span>|<span data-ttu-id="3d2db-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3d2db-120">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3d2db-121">A</span><span class="sxs-lookup"><span data-stu-id="3d2db-121">A</span></span>|<span data-ttu-id="3d2db-122">**App-Attribution**: Ihr App-Logo und Name.</span><span class="sxs-lookup"><span data-stu-id="3d2db-122">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="3d2db-123">B</span><span class="sxs-lookup"><span data-stu-id="3d2db-123">B</span></span>|<span data-ttu-id="3d2db-124">**Tabs**: bietet Navigation für Ihre persönliche app.</span><span class="sxs-lookup"><span data-stu-id="3d2db-124">**Tabs**: Provides navigation for your personal app.</span></span> <span data-ttu-id="3d2db-125">Fügen Sie beispielsweise eine Registerkarte **Info** oder **Help** hinzu.</span><span class="sxs-lookup"><span data-stu-id="3d2db-125">For example, include an **About** or **Help** tab.</span></span>|
|<span data-ttu-id="3d2db-126">C</span><span class="sxs-lookup"><span data-stu-id="3d2db-126">C</span></span>|<span data-ttu-id="3d2db-127">**Popout-Ansicht**: verschiebt Ihre APP-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.</span><span class="sxs-lookup"><span data-stu-id="3d2db-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="3d2db-128">D</span><span class="sxs-lookup"><span data-stu-id="3d2db-128">D</span></span>|<span data-ttu-id="3d2db-129">**Weiteres Menü**: enthält zusätzliche APP-Informationen und-Optionen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-129">**More menu**: Includes additional app information and options.</span></span> <span data-ttu-id="3d2db-130">(Sie können **Einstellungen** auch als Registerkarte festlegen.)</span><span class="sxs-lookup"><span data-stu-id="3d2db-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte." border="false":::

|<span data-ttu-id="3d2db-132">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="3d2db-132">Counter</span></span>|<span data-ttu-id="3d2db-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3d2db-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3d2db-134">A</span><span class="sxs-lookup"><span data-stu-id="3d2db-134">A</span></span>|<span data-ttu-id="3d2db-135">**Tabs**: bietet Navigation für Ihre persönliche app.</span><span class="sxs-lookup"><span data-stu-id="3d2db-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="3d2db-136">1 </span><span class="sxs-lookup"><span data-stu-id="3d2db-136">1</span></span>|<span data-ttu-id="3d2db-137">**iframe**: zeigt den App-Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="3d2db-137">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="3d2db-138">Entwerfen mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="3d2db-138">Designing with UI templates</span></span>

<span data-ttu-id="3d2db-139">Verwenden Sie eine der folgenden Microsoft Teams-Benutzeroberflächenvorlagen, um die Gestaltung Ihrer persönlichen Registerkarte zu unterstützen:</span><span class="sxs-lookup"><span data-stu-id="3d2db-139">Use one of the following Teams UI templates to help design your personal tab:</span></span>

* <span data-ttu-id="3d2db-140">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.</span><span class="sxs-lookup"><span data-stu-id="3d2db-140">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="3d2db-141">[Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3d2db-141">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="3d2db-142">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.</span><span class="sxs-lookup"><span data-stu-id="3d2db-142">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="3d2db-143">[Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.</span><span class="sxs-lookup"><span data-stu-id="3d2db-143">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="3d2db-144">[Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="3d2db-144">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="3d2db-145">[Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert.</span><span class="sxs-lookup"><span data-stu-id="3d2db-145">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="3d2db-146">Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.</span><span class="sxs-lookup"><span data-stu-id="3d2db-146">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="3d2db-147">Verwenden einer persönlichen app (bot)</span><span class="sxs-lookup"><span data-stu-id="3d2db-147">Use a personal app (bot)</span></span>

<span data-ttu-id="3d2db-148">Persönliche Apps können einen bot für Einzelgespräche und private Benachrichtigungen umfassen (beispielsweise, wenn ein Kollege einen Kommentar auf Ihrer Zeichenfläche veröffentlicht).</span><span class="sxs-lookup"><span data-stu-id="3d2db-148">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="3d2db-149">Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3d2db-149">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="3d2db-150">Anatomie: persönliche app (bot)</span><span class="sxs-lookup"><span data-stu-id="3d2db-150">Anatomy: Personal app (bot)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie des persönlichen bot-Komponenten." border="false":::

|<span data-ttu-id="3d2db-152">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="3d2db-152">Counter</span></span>|<span data-ttu-id="3d2db-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3d2db-153">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3d2db-154">A</span><span class="sxs-lookup"><span data-stu-id="3d2db-154">A</span></span>|<span data-ttu-id="3d2db-155">**Bot-Registerkarte**: Fügen Sie beispielsweise eine Registerkarte **Chat** hinzu, um auf bot-Unterhaltungen und-Benachrichtigungen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-155">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="3d2db-156">B</span><span class="sxs-lookup"><span data-stu-id="3d2db-156">B</span></span>|<span data-ttu-id="3d2db-157">**Bot-Nachricht**: Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (beispielsweise eine Adaptive Karte).</span><span class="sxs-lookup"><span data-stu-id="3d2db-157">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="3d2db-158">C</span><span class="sxs-lookup"><span data-stu-id="3d2db-158">C</span></span>|<span data-ttu-id="3d2db-159">**Feld "Verfassen"**: Eingabefeld zum Senden von Nachrichten an den bot.</span><span class="sxs-lookup"><span data-stu-id="3d2db-159">**Compose box**: Input field for sending messages to the bot.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="3d2db-160">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="3d2db-160">Best practices</span></span>

### <a name="tab-priority"></a><span data-ttu-id="3d2db-161">Tab-Priorität</span><span class="sxs-lookup"><span data-stu-id="3d2db-161">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="3d2db-162">Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte</span><span class="sxs-lookup"><span data-stu-id="3d2db-162">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="3d2db-163">Bei angepasster Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3d2db-163">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="3d2db-165">Nicht: Lead mit sekundärem Inhalt oder Metadaten</span><span class="sxs-lookup"><span data-stu-id="3d2db-165">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="3d2db-166">Wie bei einer standardmäßigen Webanwendung sollte die Tab-Navigation in einer Reihenfolge fortgeschritten sein, die den Sinn der primären Features Ihrer APP erleichtert.</span><span class="sxs-lookup"><span data-stu-id="3d2db-166">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="3d2db-168">Tab-Hierarchie</span><span class="sxs-lookup"><span data-stu-id="3d2db-168">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="3d2db-169">Do: Registerkarten sollten der gleichen Hierarchie entsprechen und wichtige App-Seiten darstellen</span><span class="sxs-lookup"><span data-stu-id="3d2db-169">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="3d2db-170">Ihre Registerkarten sollten die primären Features und Inhalte Ihrer APP kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="3d2db-170">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="3d2db-171">Durch die reaktionsschnelle Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3d2db-171">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="3d2db-173">Nicht: unterschiedliche Hierarchieebenen einbeziehen</span><span class="sxs-lookup"><span data-stu-id="3d2db-173">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="3d2db-174">Ihre Inhalte sollten in einer logischen Reihenfolge weiterentwickelt werden, die es Benutzern ermöglicht, diese zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-174">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="3d2db-175">Wenn Sie zwei Registerkarten haben, die eng miteinander verbunden sind, sollten Sie diese in einer Registerkarte kombinieren.</span><span class="sxs-lookup"><span data-stu-id="3d2db-175">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="3d2db-177">Erste Ausführung</span><span class="sxs-lookup"><span data-stu-id="3d2db-177">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="3d2db-178">Do: Einschließen einer ersten Ausführung</span><span class="sxs-lookup"><span data-stu-id="3d2db-178">Do: Include a first-run experience</span></span>

<span data-ttu-id="3d2db-179">Es sollte mindestens einen Willkommensbildschirm geben, wenn Sie das erste Mal eine persönliche App verwenden.</span><span class="sxs-lookup"><span data-stu-id="3d2db-179">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="3d2db-180">Beschreiben Sie für Bots, was Ihr bot tun kann, und geben Sie schnell Aktionen an, beispielsweise eine Anmeldeschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="3d2db-180">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="3d2db-183">Nicht: mit einem leeren Bildschirm beginnen</span><span class="sxs-lookup"><span data-stu-id="3d2db-183">Don't: Start with a blank screen</span></span>

<span data-ttu-id="3d2db-184">Benutzer können verwechselt werden, wenn nichts angezeigt wird, wenn Sie Ihre APP zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-184">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="3d2db-186">Personalisierter Inhalt</span><span class="sxs-lookup"><span data-stu-id="3d2db-186">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="3d2db-187">Do: aggregierter App-Inhalt, der für einen Benutzer relevant ist</span><span class="sxs-lookup"><span data-stu-id="3d2db-187">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="3d2db-188">Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen bot handelt, werden Inhalte angezeigt, die sich nur auf die Aktivität eines Benutzers in Ihrer APP beziehen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-188">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="3d2db-191">Nicht: Anzeigen von nicht verwandten oder übermäßig großen Inhalten</span><span class="sxs-lookup"><span data-stu-id="3d2db-191">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="3d2db-192">Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu denen ein Benutzer nicht gehört.</span><span class="sxs-lookup"><span data-stu-id="3d2db-192">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="3d2db-193">Der persönliche bot-Inhalt sollte sich auf das Individuum konzentrieren – nicht auf eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="3d2db-193">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="3d2db-196">Komplexe App-Features</span><span class="sxs-lookup"><span data-stu-id="3d2db-196">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="3d2db-197">Do: Benutzern den Zugriff auf komplexe Features in einem Browser ermöglichen</span><span class="sxs-lookup"><span data-stu-id="3d2db-197">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="3d2db-198">Ihre APP sollte sich auf Kernaufgaben in Microsoft Teams konzentrieren, aber Sie können die vollständige eigenständige app in einem Browser anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-198">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="3d2db-200">Nicht: einschließen der gesamten App</span><span class="sxs-lookup"><span data-stu-id="3d2db-200">Don’t: Include your entire app</span></span>

<span data-ttu-id="3d2db-201">Wenn Sie Ihre APP nicht speziell für Teams erstellt haben, haben Sie wahrscheinlich Features, die in einem Tool für die Zusammenarbeit keinen Sinn ergeben.</span><span class="sxs-lookup"><span data-stu-id="3d2db-201">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für persönliche app." border="false":::

## <a name="manage-a-personal-tab"></a><span data-ttu-id="3d2db-203">Verwalten einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="3d2db-203">Manage a personal tab</span></span>

<span data-ttu-id="3d2db-204">Auf der linken Seite der Teams können Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen zu fixieren, zu entfernen und zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3d2db-204">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen app." border="false":::

## <a name="learn-more"></a><span data-ttu-id="3d2db-206">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="3d2db-206">Learn more</span></span>

<span data-ttu-id="3d2db-207">Diese anderen Entwurfsrichtlinien können abhängig vom Umfang ihrer persönlichen App hilfreich sein:</span><span class="sxs-lookup"><span data-stu-id="3d2db-207">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="3d2db-208">Entwerfen der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="3d2db-208">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="3d2db-209">Entwerfen von Ihnen bot</span><span class="sxs-lookup"><span data-stu-id="3d2db-209">Designing you bot</span></span>](../../bots/design/bots.md)

## <a name="validate-your-design"></a><span data-ttu-id="3d2db-210">Überprüfen des Designs</span><span class="sxs-lookup"><span data-stu-id="3d2db-210">Validate your design</span></span>

<span data-ttu-id="3d2db-211">Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.</span><span class="sxs-lookup"><span data-stu-id="3d2db-211">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3d2db-212">Überprüfen der Entwurfs Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="3d2db-212">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
