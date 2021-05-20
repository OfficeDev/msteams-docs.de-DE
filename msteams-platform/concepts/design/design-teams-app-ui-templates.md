---
title: Entwerfen Ihrer App mit UI-Vorlagen
author: heath-hamilton
description: Entwerfen Sie Ihre App schneller mit standardisierten UI-Komponenten, Layouts und Mustern, die häufig in Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 0cd5c6c4525e340f9aa53a78749211783880225a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566019"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="a47fa-103">Entwerfen Ihrer Microsoft Teams-App mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="a47fa-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="a47fa-104">Entwerfen Sie Ihre Microsoft Teams App schneller mit UI-Vorlagen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="a47fa-105">Die Vorlagen sind eine Sammlung von fluent UI-basierten Komponenten, die über gängige Teams Anwendungsfälle hinweg funktionieren, sodass Sie mehr Zeit haben, um die beste Erfahrung für Ihre Benutzer herauszufinden.</span><span class="sxs-lookup"><span data-stu-id="a47fa-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="a47fa-106">Erste Schritte mit Tools und Beispielen</span><span class="sxs-lookup"><span data-stu-id="a47fa-106">Getting started with tools and samples</span></span>

<span data-ttu-id="a47fa-107">Die folgenden Ressourcen können Ihnen beim Entwerfen und Entwickeln Ihrer App mithilfe von UI-Vorlagen helfen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="a47fa-108">Microsoft Teams-UI-Kit</span><span class="sxs-lookup"><span data-stu-id="a47fa-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="a47fa-109">Holen Sie sich UI-Vorlagen für Ihr App-Design aus dem Microsoft Teams UI Kit, das auch umfangreiche Informationen zu Nutzung, Anatomie, Zugänglichkeit und bewährten Methoden enthält.</span><span class="sxs-lookup"><span data-stu-id="a47fa-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a47fa-110">Holen Sie sich das UI-Kit (Figma)</span><span class="sxs-lookup"><span data-stu-id="a47fa-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="a47fa-111">Microsoft Teams UI-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="a47fa-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="a47fa-112">Zeigen Sie einzelne Teams UI-Vorlagen und zugehörigeKomponenten in Ihrem Browser an und testen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="a47fa-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a47fa-113">Testen Sie die UI-Bibliothek (Spielplatz)</span><span class="sxs-lookup"><span data-stu-id="a47fa-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="a47fa-114">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="a47fa-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a47fa-115">Abrufen der UI-Bibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a47fa-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="a47fa-116">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="a47fa-116">Sample app</span></span>

<span data-ttu-id="a47fa-117">Installieren Sie eine Beispiel-App, um zu sehen, wie UI-Vorlagen in Teams Kontexten aussehen und sich verhalten.</span><span class="sxs-lookup"><span data-stu-id="a47fa-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a47fa-118">Abrufen der Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a47fa-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a><span data-ttu-id="a47fa-119">Liste</span><span class="sxs-lookup"><span data-stu-id="a47fa-119">List</span></span>

<span data-ttu-id="a47fa-120">Sie können eine Liste verwenden, um verwandte Elemente in einem scannbaren Format anzuzeigen und Benutzern die Möglichkeit zu geben, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-120">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Das Beispiel zeigt eine Listen-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-122">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-122">Top use cases</span></span>

* <span data-ttu-id="a47fa-123">Anzeigevon Daten</span><span class="sxs-lookup"><span data-stu-id="a47fa-123">Display data</span></span>
* <span data-ttu-id="a47fa-124">Kontextbezogene Aktionen für App-Inhalte</span><span class="sxs-lookup"><span data-stu-id="a47fa-124">Contextual actions on app content</span></span>

## <a name="dashboard"></a><span data-ttu-id="a47fa-125">Dashboard</span><span class="sxs-lookup"><span data-stu-id="a47fa-125">Dashboard</span></span>

<span data-ttu-id="a47fa-126">Ein Dashboard zeigt verschiedene Inhaltstypen an einem zentralen Ort an (Teams persönliche App oder Registerkarte).</span><span class="sxs-lookup"><span data-stu-id="a47fa-126">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="a47fa-127">Benutzer sollten in der Lage sein, zumindest einen Teil dessen, was sie auf einem Dashboard sehen, anzupassen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-127">Users should be able to customize at least some of what they see on a dashboard.</span></span>

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Das Beispiel zeigt eine Dashboard-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-129">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-129">Top use cases</span></span>

* <span data-ttu-id="a47fa-130">Analysieren von Daten</span><span class="sxs-lookup"><span data-stu-id="a47fa-130">Analyze data</span></span>
* <span data-ttu-id="a47fa-131">Berichtsmetriken</span><span class="sxs-lookup"><span data-stu-id="a47fa-131">Report metrics</span></span>
* <span data-ttu-id="a47fa-132">Organisieren verschiedener Informationen an einem Ort</span><span class="sxs-lookup"><span data-stu-id="a47fa-132">Organize different information in one place</span></span>

## <a name="form"></a><span data-ttu-id="a47fa-133">Formular</span><span class="sxs-lookup"><span data-stu-id="a47fa-133">Form</span></span>

<span data-ttu-id="a47fa-134">Formulare werden verwendet, um Benutzereingaben auf strukturierte Weise zu sammeln, zu validieren und zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="a47fa-134">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="a47fa-135">Eine klare Beschriftung und logische Gruppierungen von Eingabefeldern sind für eine gute Benutzererfahrung von entscheidender Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="a47fa-135">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Das Beispiel zeigt eine Formular-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-137">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-137">Top use cases</span></span>

* <span data-ttu-id="a47fa-138">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a47fa-138">Sign in</span></span>
* <span data-ttu-id="a47fa-139">Benutzerprofile</span><span class="sxs-lookup"><span data-stu-id="a47fa-139">User profiles</span></span>
* <span data-ttu-id="a47fa-140">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="a47fa-140">Settings</span></span>
* <span data-ttu-id="a47fa-141">Benutzereingabesammlung</span><span class="sxs-lookup"><span data-stu-id="a47fa-141">User input collection</span></span>

## <a name="sign-in"></a><span data-ttu-id="a47fa-142">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a47fa-142">Sign in</span></span>

<span data-ttu-id="a47fa-143">Sie können App-Anmeldeflüsse für verschiedene Teams Kontexte und Identitätsanbieter entwerfen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-143">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="a47fa-144">Das folgende Beispiel enthält Single Sign-On (SSO), das wir für die einfachste Authentifizierungempfehlen empfehlen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-144">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Ein Beispiel zeigt eine Anmeldevorlage in der Ui-Vorlage." border="false":::

### <a name="top-use-case"></a><span data-ttu-id="a47fa-146">Top-Anwendungsfall</span><span class="sxs-lookup"><span data-stu-id="a47fa-146">Top use case</span></span>

* <span data-ttu-id="a47fa-147">Authentifizieren von Benutzern</span><span class="sxs-lookup"><span data-stu-id="a47fa-147">Authenticate users</span></span>

## <a name="task-board"></a><span data-ttu-id="a47fa-148">Aufgabentafel</span><span class="sxs-lookup"><span data-stu-id="a47fa-148">Task board</span></span>

<span data-ttu-id="a47fa-149">Eine Aufgabentafel, manchmal auch Kanban-Board oder Schwimmbahnen genannt, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitsaufgaben oder Tickets zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-149">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="a47fa-150">Es kann auch verwendet werden, um jede Art von Inhalt in Kategorien zu sortieren.</span><span class="sxs-lookup"><span data-stu-id="a47fa-150">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="a47fa-151">Sie können die Karten zwischen Spalten bearbeiten und verschieben.</span><span class="sxs-lookup"><span data-stu-id="a47fa-151">You can edit and move the cards between columns.</span></span>

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Das Beispiel zeigt eine Benutzeroberflächenvorlage für Aufgabenplatinen." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-153">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-153">Top use cases</span></span>

* <span data-ttu-id="a47fa-154">Project Verwaltung: Zuweisen von Aufgaben und Nachverfolgungsstatus.</span><span class="sxs-lookup"><span data-stu-id="a47fa-154">Project management: Assigning tasks and tracking status.</span></span>
* <span data-ttu-id="a47fa-155">Brainstorming: Hinzufügen von Ideen in verschiedenen Kategorien.</span><span class="sxs-lookup"><span data-stu-id="a47fa-155">Brainstorming: Adding ideas in different categories.</span></span>
* <span data-ttu-id="a47fa-156">Sortierübungen: Organisieren jeder Art von Informationen in Eimer.</span><span class="sxs-lookup"><span data-stu-id="a47fa-156">Sorting exercises: Organizing any kind of information into buckets.</span></span>

## <a name="data-visualization"></a><span data-ttu-id="a47fa-157">Datenvisualisierung</span><span class="sxs-lookup"><span data-stu-id="a47fa-157">Data visualization</span></span>

<span data-ttu-id="a47fa-158">Sie können verschiedene Kartengrößen (einzeln, doppelt und vollständig) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="a47fa-158">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="a47fa-159">Die Karten werden skaliert, um an das Spaltenlayout anzupassen und Leerzeichen auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-159">The cards scale to fit the column layout and fill in blank spaces.</span></span>

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Ein Beispiel zeigt eine UI-Vorlage für die Datenvisualisierung." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-161">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-161">Top use cases</span></span>

* <span data-ttu-id="a47fa-162">Anzeigen komplexer Informationen</span><span class="sxs-lookup"><span data-stu-id="a47fa-162">Display complex information</span></span>
* <span data-ttu-id="a47fa-163">Erstellen eines Dashboards</span><span class="sxs-lookup"><span data-stu-id="a47fa-163">Create a dashboard</span></span>

## <a name="wizard"></a><span data-ttu-id="a47fa-164">Assistent</span><span class="sxs-lookup"><span data-stu-id="a47fa-164">Wizard</span></span>

<span data-ttu-id="a47fa-165">Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe (z. B. einen Einrichtungsprozess) abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-165">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Das Beispiel zeigt eine Vorlagenvorlage für die Benutzeroberflächenvorlage des Assistenten." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-167">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-167">Top use cases</span></span>

* <span data-ttu-id="a47fa-168">Setup</span><span class="sxs-lookup"><span data-stu-id="a47fa-168">Setup</span></span>
* <span data-ttu-id="a47fa-169">Onboarding</span><span class="sxs-lookup"><span data-stu-id="a47fa-169">Onboarding</span></span>
* <span data-ttu-id="a47fa-170">Erfahrungen im ersten Lauf</span><span class="sxs-lookup"><span data-stu-id="a47fa-170">First-run experiences</span></span>

## <a name="empty-state"></a><span data-ttu-id="a47fa-171">Leerer Zustand</span><span class="sxs-lookup"><span data-stu-id="a47fa-171">Empty state</span></span>

<span data-ttu-id="a47fa-172">Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.</span><span class="sxs-lookup"><span data-stu-id="a47fa-172">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="a47fa-173">Es ist sehr flexibel – passen Sie es an, um eine, einige oder alle Komponenten im folgenden Entwurf zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a47fa-173">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Das Beispiel zeigt eine leere Status-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-175">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-175">Top use cases</span></span>

* <span data-ttu-id="a47fa-176">Anmelden</span><span class="sxs-lookup"><span data-stu-id="a47fa-176">Sign in</span></span>
* <span data-ttu-id="a47fa-177">Begrüßungsbotschaften und Erstrundenerfahrungen</span><span class="sxs-lookup"><span data-stu-id="a47fa-177">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="a47fa-178">Erfolgsbotschaften</span><span class="sxs-lookup"><span data-stu-id="a47fa-178">Success messages</span></span>
* <span data-ttu-id="a47fa-179">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="a47fa-179">Error messages</span></span>

## <a name="notification-bar"></a><span data-ttu-id="a47fa-180">Benachrichtigungsleiste</span><span class="sxs-lookup"><span data-stu-id="a47fa-180">Notification bar</span></span>

<span data-ttu-id="a47fa-181">Eine Benachrichtigungsleiste ist ein dedizierter Bereich zum Anzeigen einer kurzen, wichtigen Nachricht, für die der Benutzer keine sofortigen Maßnahmen ergreifen muss.</span><span class="sxs-lookup"><span data-stu-id="a47fa-181">A notification bar is a dedicated area for displaying a brief, important messages that do not require the user to take immediate action.</span></span> <span data-ttu-id="a47fa-182">Bestimmte Hintergrundfarben und Symbole sind bestimmten Nachrichtentypen zugeordnet (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="a47fa-182">Specific background colors and icons are associated with specific types of messages (see below).</span></span>

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Das Beispiel zeigt Benachrichtigungsleistenvorlagen." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-184">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-184">Top use cases</span></span>

* <span data-ttu-id="a47fa-185">Kritische Meldungen, Fehler und Warnungen</span><span class="sxs-lookup"><span data-stu-id="a47fa-185">Critical messages, errors, and warnings</span></span>
* <span data-ttu-id="a47fa-186">Erfolgsbotschaften</span><span class="sxs-lookup"><span data-stu-id="a47fa-186">Success messages</span></span>
* <span data-ttu-id="a47fa-187">Informations- oder Werbebotschaften</span><span class="sxs-lookup"><span data-stu-id="a47fa-187">Informational or promotional messages</span></span>

## <a name="left-nav"></a><span data-ttu-id="a47fa-188">Linkes Navi</span><span class="sxs-lookup"><span data-stu-id="a47fa-188">Left nav</span></span>

<span data-ttu-id="a47fa-189">Verwenden Sie das linke Navi, um mehrere Seiten in Ihrem Teams Registerkarte zu durchsuchen. Im folgenden Beispiel befindet sich das linke Navi zwischen der Kanalliste und dem Tabinhalt.</span><span class="sxs-lookup"><span data-stu-id="a47fa-189">Use the left nav to browse multiple pages within your Teams tab. In the following example, the left nav is between the channel list and tab content.</span></span>

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Das Beispiel zeigt eine linke Navigationsvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-191">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-191">Top use cases</span></span>

* <span data-ttu-id="a47fa-192">Durchsuchen Sie mehrere Seiten auf einer Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="a47fa-192">Browse multiple pages within a Teams tab.</span></span>
* <span data-ttu-id="a47fa-193">Unterteilen Sie komplexe Apps in mehrere Seiten.</span><span class="sxs-lookup"><span data-stu-id="a47fa-193">Break down complex apps into multiple pages.</span></span>

## <a name="breadcrumb"></a><span data-ttu-id="a47fa-194">Breadcrumb</span><span class="sxs-lookup"><span data-stu-id="a47fa-194">Breadcrumb</span></span>

<span data-ttu-id="a47fa-195">Breadcrumbs sind eine Navigationshilfe, die die Hierarchie Ihrer App vermittelt.</span><span class="sxs-lookup"><span data-stu-id="a47fa-195">Breadcrumbs are a navigational aid that convey your app’s hierarchy.</span></span> <span data-ttu-id="a47fa-196">Sie helfen Benutzern zu verstehen, wie die angezeigte Seite in die Gesamterfahrung passt und ermöglichen mit einem Klick Zugriff auf höhere Ebenen in dieser Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="a47fa-196">They help users understand how the page they’re viewing fits into the overall experience and afford one-click access to higher levels in that hierarchy.</span></span>

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Ein Beispiel zeigt eine Breadcrumb-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-198">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-198">Top use cases</span></span>

* <span data-ttu-id="a47fa-199">Kommunizieren der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="a47fa-199">Communicate hierarchy</span></span>
* <span data-ttu-id="a47fa-200">Navigation</span><span class="sxs-lookup"><span data-stu-id="a47fa-200">Navigation</span></span>

## <a name="toolbar"></a><span data-ttu-id="a47fa-201">Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="a47fa-201">Toolbar</span></span>

<span data-ttu-id="a47fa-202">Eine Symbolleiste ist ein Container zum Gruppieren eines Satzes von Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-202">A toolbar is a container for grouping a set of controls.</span></span>

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Das Beispiel zeigt eine Symbolleistenvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-204">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-204">Top use cases</span></span>

* <span data-ttu-id="a47fa-205">Kontextbezogene Aktionen für App-Inhalte</span><span class="sxs-lookup"><span data-stu-id="a47fa-205">Contextual actions on app content</span></span>
* <span data-ttu-id="a47fa-206">Kontextfilter und Suchen</span><span class="sxs-lookup"><span data-stu-id="a47fa-206">Contextual filter and find</span></span>
* <span data-ttu-id="a47fa-207">Navigation und Breadcrumbs</span><span class="sxs-lookup"><span data-stu-id="a47fa-207">Navigation and breadcrumbs</span></span>

## <a name="stage"></a><span data-ttu-id="a47fa-208">Stufe</span><span class="sxs-lookup"><span data-stu-id="a47fa-208">Stage</span></span>

<span data-ttu-id="a47fa-209">Stage bietet Benutzern die Möglichkeit, eine Entität (z. B. ein Bild, eine Datei oder eine Website) in Teams zu öffnen, anstatt sie in einer anderen App oder einem anderen Browser zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a47fa-209">Stage offers a way for users to open an entity—like an image, file, or website—in Teams instead of opening it in another app or browser.</span></span> <span data-ttu-id="a47fa-210">Der primäre Anwendungsfall der Bühne ist die Anzeige; die Oberfläche sollte nicht für komplexe Wechselwirkungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a47fa-210">The primary use case of stage is viewing; the surface should not be used for complex interactions.</span></span>

<span data-ttu-id="a47fa-211">(Implementierungshinweis: Erstellen Sie Ihre Bühne mit einem großen [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span><span class="sxs-lookup"><span data-stu-id="a47fa-211">(Implementation note: Build your stage using a large [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span></span>

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Das Beispiel zeigt eine Bühnenvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="a47fa-213">Top-Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="a47fa-213">Top use cases</span></span>

* <span data-ttu-id="a47fa-214">Öffnen Sie eine Entität in Teams anstelle einer anderen App oder eines anderen Browsers.</span><span class="sxs-lookup"><span data-stu-id="a47fa-214">Open an entity in Teams instead of another app or browser.</span></span>
* <span data-ttu-id="a47fa-215">Spotlight-Medien oder andere Inhalte.</span><span class="sxs-lookup"><span data-stu-id="a47fa-215">Spotlight media or other content.</span></span>
