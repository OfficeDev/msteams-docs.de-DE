---
title: Entwerfen Ihrer App mit Benutzeroberflächenvorlagen
author: heath-hamilton
description: Entwerfen Sie Ihre App schneller mit standardisierten Benutzeroberflächenkomponenten, Layouts und Mustern, die in Microsoft Teams häufig verwendet werden.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: b4d244bbf78ac85042d5caf8ec84afe42e79b3c7
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911926"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="dcefc-103">Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="dcefc-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="dcefc-104">Entwerfen Sie Ihre Microsoft Teams-App schneller mit Benutzeroberflächenvorlagen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="dcefc-105">Die Vorlagen sind eine Sammlung von Fluent-UI-basierten Komponenten, die in gängigen Teams-Verwendungsfällen funktionieren, um Ihnen mehr Zeit zu geben, um die beste Erfahrung für Ihre Benutzer zu finden.</span><span class="sxs-lookup"><span data-stu-id="dcefc-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="dcefc-106">Erste Schritte mit Tools und Beispielen</span><span class="sxs-lookup"><span data-stu-id="dcefc-106">Getting started with tools and samples</span></span>

<span data-ttu-id="dcefc-107">Die folgenden Ressourcen können Sie beim Entwerfen und Entwickeln Ihrer App mithilfe von Benutzeroberflächenvorlagen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="dcefc-108">Microsoft Teams UI Kit</span><span class="sxs-lookup"><span data-stu-id="dcefc-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="dcefc-109">Greifen Sie ui templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span><span class="sxs-lookup"><span data-stu-id="dcefc-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcefc-110">Benutzeroberflächenkit (Bissma)</span><span class="sxs-lookup"><span data-stu-id="dcefc-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="dcefc-111">Microsoft Teams UI Library</span><span class="sxs-lookup"><span data-stu-id="dcefc-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="dcefc-112">Anzeigen und Testen einzelner Benutzeroberflächenvorlagen und zugehöriger Komponenten von Teams in Ihrem Browser.</span><span class="sxs-lookup"><span data-stu-id="dcefc-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcefc-113">Probieren Sie die Benutzeroberflächenbibliothek (Playground) aus.</span><span class="sxs-lookup"><span data-stu-id="dcefc-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="dcefc-114">Importieren Sie diese Vorlagen und zugehörigen Komponenten direkt in Ihr Teams-App-Projekt.</span><span class="sxs-lookup"><span data-stu-id="dcefc-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcefc-115">Abrufen der Benutzeroberflächenbibliothek (GitHub)</span><span class="sxs-lookup"><span data-stu-id="dcefc-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="dcefc-116">Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="dcefc-116">Sample app</span></span>

<span data-ttu-id="dcefc-117">Installieren Sie eine Beispiel-App, um zu sehen, wie Benutzeroberflächenvorlagen im Kontext von Teams aussehen und sich verhalten.</span><span class="sxs-lookup"><span data-stu-id="dcefc-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcefc-118">Abrufen der Beispiel-App (GitHub)</span><span class="sxs-lookup"><span data-stu-id="dcefc-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a><span data-ttu-id="dcefc-119">List</span><span class="sxs-lookup"><span data-stu-id="dcefc-119">List</span></span>

<span data-ttu-id="dcefc-120">Sie können eine Liste verwenden, um verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-120">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Beispiel zeigt eine Listenbenutzeroberflächenvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-122">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-122">Top use cases</span></span>

* <span data-ttu-id="dcefc-123">Anzeigen von Daten</span><span class="sxs-lookup"><span data-stu-id="dcefc-123">Display data</span></span>
* <span data-ttu-id="dcefc-124">Kontextbezogene Aktionen zu App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="dcefc-124">Contextual actions on app content</span></span>

## <a name="dashboard"></a><span data-ttu-id="dcefc-125">Dashboard</span><span class="sxs-lookup"><span data-stu-id="dcefc-125">Dashboard</span></span>

<span data-ttu-id="dcefc-126">Ein Dashboard zeigt verschiedene Arten von Inhalten an einem zentralen Ort an (persönliche Teams-App oder Registerkarte).</span><span class="sxs-lookup"><span data-stu-id="dcefc-126">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="dcefc-127">Benutzer sollten in der Lage sein, zumindest einige der auf einem Dashboard angezeigten Funktionen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-127">Users should be able to customize at least some of what they see on a dashboard.</span></span>

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Beispiel zeigt eine Dashboard-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-129">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-129">Top use cases</span></span>

* <span data-ttu-id="dcefc-130">Analysieren von Daten</span><span class="sxs-lookup"><span data-stu-id="dcefc-130">Analyze data</span></span>
* <span data-ttu-id="dcefc-131">Berichtsmetriken</span><span class="sxs-lookup"><span data-stu-id="dcefc-131">Report metrics</span></span>
* <span data-ttu-id="dcefc-132">Organisieren unterschiedlicher Informationen an einem Ort</span><span class="sxs-lookup"><span data-stu-id="dcefc-132">Organize different information in one place</span></span>

## <a name="form"></a><span data-ttu-id="dcefc-133">Formular</span><span class="sxs-lookup"><span data-stu-id="dcefc-133">Form</span></span>

<span data-ttu-id="dcefc-134">Formulare werden verwendet, um Benutzereingaben auf strukturierte Weise zu sammeln, zu überprüfen und zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="dcefc-134">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="dcefc-135">Klare Bezeichnungen und logische Gruppierungen von Eingabefeldern sind für eine gute Benutzererfahrung entscheidend.</span><span class="sxs-lookup"><span data-stu-id="dcefc-135">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Beispiel zeigt eine Formular-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-137">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-137">Top use cases</span></span>

* <span data-ttu-id="dcefc-138">Anmelden</span><span class="sxs-lookup"><span data-stu-id="dcefc-138">Sign in</span></span>
* <span data-ttu-id="dcefc-139">Benutzerprofile</span><span class="sxs-lookup"><span data-stu-id="dcefc-139">User profiles</span></span>
* <span data-ttu-id="dcefc-140">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="dcefc-140">Settings</span></span>
* <span data-ttu-id="dcefc-141">Benutzereingabesammlung</span><span class="sxs-lookup"><span data-stu-id="dcefc-141">User input collection</span></span>

## <a name="sign-in"></a><span data-ttu-id="dcefc-142">Anmelden</span><span class="sxs-lookup"><span data-stu-id="dcefc-142">Sign in</span></span>

<span data-ttu-id="dcefc-143">Sie können App-Anmeldeabläufe für verschiedene Kontexte und Identitätsanbieter von Teams entwerfen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-143">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="dcefc-144">Das folgende Beispiel enthält einmaliges Anmelden (Single Sign-On, SSO), was für die einfachste Authentifizierungserfahrung empfohlen wird.</span><span class="sxs-lookup"><span data-stu-id="dcefc-144">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Beispiel zeigt eine Vorlage für die Anmeldung der Benutzeroberfläche." border="false":::

### <a name="top-use-case"></a><span data-ttu-id="dcefc-146">Der am besten zu verwendende Fall</span><span class="sxs-lookup"><span data-stu-id="dcefc-146">Top use case</span></span>

* <span data-ttu-id="dcefc-147">Authentifizieren von Benutzern</span><span class="sxs-lookup"><span data-stu-id="dcefc-147">Authenticate users</span></span>

## <a name="task-board"></a><span data-ttu-id="dcefc-148">Task Board</span><span class="sxs-lookup"><span data-stu-id="dcefc-148">Task board</span></span>

<span data-ttu-id="dcefc-149">Ein Task Board, manchmal auch als Kanban Board oder Rettungsweg bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitsaufgaben oder Tickets nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="dcefc-149">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="dcefc-150">Es kann auch verwendet werden, um jeden Inhaltstyp in Kategorien zu sortieren.</span><span class="sxs-lookup"><span data-stu-id="dcefc-150">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="dcefc-151">Sie können die Karten bearbeiten und zwischen Spalten verschieben.</span><span class="sxs-lookup"><span data-stu-id="dcefc-151">You can edit and move the cards between columns.</span></span>

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Beispiel zeigt eine Task Board-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-153">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-153">Top use cases</span></span>

* <span data-ttu-id="dcefc-154">Projektmanagement</span><span class="sxs-lookup"><span data-stu-id="dcefc-154">Project management.</span></span> <span data-ttu-id="dcefc-155">Zuweisen von Aufgaben und Nachverfolgungsstatus</span><span class="sxs-lookup"><span data-stu-id="dcefc-155">Assigning tasks and tracking status</span></span>
* <span data-ttu-id="dcefc-156">Brainstorming.</span><span class="sxs-lookup"><span data-stu-id="dcefc-156">Brainstorming.</span></span> <span data-ttu-id="dcefc-157">Hinzufügen von Ideen in verschiedenen Kategorien</span><span class="sxs-lookup"><span data-stu-id="dcefc-157">Adding ideas in different categories</span></span>
* <span data-ttu-id="dcefc-158">Sortierübungen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-158">Sorting exercises.</span></span> <span data-ttu-id="dcefc-159">Organisieren aller Arten von Informationen in Buckets</span><span class="sxs-lookup"><span data-stu-id="dcefc-159">Organizing any kind of information into buckets</span></span>

## <a name="data-visualization"></a><span data-ttu-id="dcefc-160">Datenvisualisierung</span><span class="sxs-lookup"><span data-stu-id="dcefc-160">Data visualization</span></span>

<span data-ttu-id="dcefc-161">Sie können verschiedene Kartengrößen (einzel, doppelt und vollständig) verwenden, um Datenvisualisierungen auf derselben Seite zu stapeln und zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="dcefc-161">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="dcefc-162">Die Karten passen sich an das Spaltenlayout an und füllen Leerzeichen aus.</span><span class="sxs-lookup"><span data-stu-id="dcefc-162">The cards scale to fit the column layout and fill in blank spaces.</span></span>

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Beispiel zeigt eine Benutzeroberflächenvorlage für die Datenvisualisierung." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-164">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-164">Top use cases</span></span>

* <span data-ttu-id="dcefc-165">Anzeigen komplexer Informationen</span><span class="sxs-lookup"><span data-stu-id="dcefc-165">Display complex information</span></span>
* <span data-ttu-id="dcefc-166">Erstellen eines Dashboards</span><span class="sxs-lookup"><span data-stu-id="dcefc-166">Create a dashboard</span></span>

## <a name="wizard"></a><span data-ttu-id="dcefc-167">Assistent</span><span class="sxs-lookup"><span data-stu-id="dcefc-167">Wizard</span></span>

<span data-ttu-id="dcefc-168">Ein Assistent führt einen Benutzer durch mehrere Bildschirme, um eine Aufgabe auszuführen (z. B. einen Einrichtungsprozess).</span><span class="sxs-lookup"><span data-stu-id="dcefc-168">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Beispiel zeigt eine Assistenten-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-170">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-170">Top use cases</span></span>

* <span data-ttu-id="dcefc-171">Setup</span><span class="sxs-lookup"><span data-stu-id="dcefc-171">Setup</span></span>
* <span data-ttu-id="dcefc-172">Onboarding</span><span class="sxs-lookup"><span data-stu-id="dcefc-172">Onboarding</span></span>
* <span data-ttu-id="dcefc-173">Erfahrungen bei der ersten Ausführung</span><span class="sxs-lookup"><span data-stu-id="dcefc-173">First-run experiences</span></span>

## <a name="empty-state"></a><span data-ttu-id="dcefc-174">Leerer Zustand</span><span class="sxs-lookup"><span data-stu-id="dcefc-174">Empty state</span></span>

<span data-ttu-id="dcefc-175">Die Vorlage "Leerer Zustand" kann für viele Szenarien verwendet werden, z. B. anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="dcefc-175">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="dcefc-176">Es ist äußerst flexibel – passen Sie es an, um eine, einige oder alle Komponenten im folgenden Design zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="dcefc-176">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Beispiel zeigt eine leere Zustands-UI-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-178">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-178">Top use cases</span></span>

* <span data-ttu-id="dcefc-179">Anmelden</span><span class="sxs-lookup"><span data-stu-id="dcefc-179">Sign in</span></span>
* <span data-ttu-id="dcefc-180">Willkommensnachrichten und Erfahrungen bei der ersten Ausführung</span><span class="sxs-lookup"><span data-stu-id="dcefc-180">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="dcefc-181">Erfolgsmeldungen</span><span class="sxs-lookup"><span data-stu-id="dcefc-181">Success messages</span></span>
* <span data-ttu-id="dcefc-182">Fehlermeldungen</span><span class="sxs-lookup"><span data-stu-id="dcefc-182">Error messages</span></span>

## <a name="notification-bar"></a><span data-ttu-id="dcefc-183">Benachrichtigungsleiste</span><span class="sxs-lookup"><span data-stu-id="dcefc-183">Notification bar</span></span>

<span data-ttu-id="dcefc-184">Eine Benachrichtigungsleiste ist ein dedizierter Bereich zum Anzeigen kurzer, wichtiger Meldungen, für die der Benutzer keine sofortige Aktion ergreifen muss.</span><span class="sxs-lookup"><span data-stu-id="dcefc-184">A notification bar is a dedicated area for displaying a brief, important messages that do not require the user to take immediate action.</span></span> <span data-ttu-id="dcefc-185">Bestimmte Hintergrundfarben und Symbole sind bestimmten Nachrichtentypen zugeordnet (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="dcefc-185">Specific background colors and icons are associated with specific types of messages (see below).</span></span>

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Beispiel zeigt Vorlagen für Benachrichtigungsleisten." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-187">Die am besten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-187">Top use cases</span></span>

* <span data-ttu-id="dcefc-188">Wichtige Meldungen, Fehler und Warnungen</span><span class="sxs-lookup"><span data-stu-id="dcefc-188">Critical messages, errors, and warnings</span></span>
* <span data-ttu-id="dcefc-189">Erfolgsmeldungen</span><span class="sxs-lookup"><span data-stu-id="dcefc-189">Success messages</span></span>
* <span data-ttu-id="dcefc-190">Informations- oder Werbenachrichten</span><span class="sxs-lookup"><span data-stu-id="dcefc-190">Informational or promotional messages</span></span>

## <a name="left-nav"></a><span data-ttu-id="dcefc-191">Linke Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="dcefc-191">Left nav</span></span>

<span data-ttu-id="dcefc-192">Verwenden Sie die linke Navigationsleiste, um mehrere Seiten auf Ihrer Registerkarte "Teams" zu durchsuchen. Im folgenden Beispiel befindet sich die linke Navigationsleiste zwischen der Kanalliste und dem Registerkarteninhalt.</span><span class="sxs-lookup"><span data-stu-id="dcefc-192">Use the left nav to browse multiple pages within your Teams tab. In the following example, the left nav is between the channel list and tab content.</span></span>

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Beispiel zeigt eine linke Navigationsvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-194">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-194">Top use cases</span></span>

* <span data-ttu-id="dcefc-195">Durchsuchen mehrerer Seiten auf einer Registerkarte "Teams"</span><span class="sxs-lookup"><span data-stu-id="dcefc-195">Browse multiple pages within a Teams tab</span></span>
* <span data-ttu-id="dcefc-196">Aufbrechen komplexer Apps in mehrere Seiten</span><span class="sxs-lookup"><span data-stu-id="dcefc-196">Break down complex apps into multiple pages</span></span>

## <a name="breadcrumb"></a><span data-ttu-id="dcefc-197">Breadcrumb</span><span class="sxs-lookup"><span data-stu-id="dcefc-197">Breadcrumb</span></span>

<span data-ttu-id="dcefc-198">Breadcrumbs sind eine Navigationshilfe, die die Hierarchie Ihrer App vermittelt.</span><span class="sxs-lookup"><span data-stu-id="dcefc-198">Breadcrumbs are a navigational aid that convey your app’s hierarchy.</span></span> <span data-ttu-id="dcefc-199">Sie helfen Benutzern zu verstehen, wie die Seite, die sie anzeigen, in die Gesamterfahrung passt, und bieten mit einem Klick Zugriff auf höhere Ebenen in dieser Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="dcefc-199">They help users understand how the page they’re viewing fits into the overall experience and afford one-click access to higher levels in that hierarchy.</span></span>

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Beispiel zeigt eine Breadcrumbvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-201">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-201">Top use cases</span></span>

* <span data-ttu-id="dcefc-202">Hierarchie kommunizieren</span><span class="sxs-lookup"><span data-stu-id="dcefc-202">Communicate hierarchy</span></span>
* <span data-ttu-id="dcefc-203">Navigation</span><span class="sxs-lookup"><span data-stu-id="dcefc-203">Navigation</span></span>

## <a name="toolbar"></a><span data-ttu-id="dcefc-204">Symbolleiste</span><span class="sxs-lookup"><span data-stu-id="dcefc-204">Toolbar</span></span>

<span data-ttu-id="dcefc-205">Eine Symbolleiste ist ein Container zum Gruppieren einer Gruppe von Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-205">A toolbar is a container for grouping a set of controls.</span></span>

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Beispiel zeigt eine Symbolleistenvorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-207">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-207">Top use cases</span></span>

* <span data-ttu-id="dcefc-208">Kontextbezogene Aktionen zu App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="dcefc-208">Contextual actions on app content</span></span>
* <span data-ttu-id="dcefc-209">Kontextfilter und -suche</span><span class="sxs-lookup"><span data-stu-id="dcefc-209">Contextual filter and find</span></span>
* <span data-ttu-id="dcefc-210">Navigation und Breadcrumbs</span><span class="sxs-lookup"><span data-stu-id="dcefc-210">Navigation and breadcrumbs</span></span>

## <a name="stage"></a><span data-ttu-id="dcefc-211">Stufe 1</span><span class="sxs-lookup"><span data-stu-id="dcefc-211">Stage</span></span>

<span data-ttu-id="dcefc-212">Die Phase bietet Benutzern eine Möglichkeit, eine Entität wie ein Bild, eine Datei oder eine Website in Teams zu öffnen, anstatt sie in einer anderen App oder einem anderen Browser zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="dcefc-212">Stage offers a way for users to open an entity—like an image, file, or website—in Teams instead of opening it in another app or browser.</span></span> <span data-ttu-id="dcefc-213">Der primäre Verwendungsfall der Phase ist das Anzeigen. Die Oberfläche sollte nicht für komplexe Interaktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="dcefc-213">The primary use case of stage is viewing; the surface should not be used for complex interactions.</span></span>

<span data-ttu-id="dcefc-214">(Implementierungshinweis: Erstellen Sie Ihre Phase mithilfe eines großen [Aufgabenmoduls.)](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)</span><span class="sxs-lookup"><span data-stu-id="dcefc-214">(Implementation note: Build your stage using a large [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span></span>

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Beispiel zeigt eine Stage-Vorlage." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="dcefc-216">Die am meisten verwendeten Fälle</span><span class="sxs-lookup"><span data-stu-id="dcefc-216">Top use cases</span></span>

* <span data-ttu-id="dcefc-217">Öffnen einer Entität in Teams anstelle einer anderen App oder eines anderen Browsers</span><span class="sxs-lookup"><span data-stu-id="dcefc-217">Open an entity in Teams instead of another app or browser</span></span>
* <span data-ttu-id="dcefc-218">Spotlightmedien oder andere Inhalte</span><span class="sxs-lookup"><span data-stu-id="dcefc-218">Spotlight media or other content</span></span>
